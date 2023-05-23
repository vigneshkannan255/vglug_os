## Downloading ISO 
curl -X GET -OL https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-11.7.0-amd64-netinst.iso

## Installing xorriso for ISO editing
sudo apt-get install -y xorriso

## Decompress ISO
xorriso -osirrox on -indev "debian-11.7.0-amd64-netinst.iso" -extract / iso && chmod -R +w iso

 cp filesystem.squashfs ./iso/casper/
 md5sum iso/.disk/info > iso/md5sum.txt
 sed -i 's|iso/|./|g' iso/md5sum.txt
 xorriso -as mkisofs -r -V "Ubuntu custom amd64" -o ubuntu-20.04.4-custom-amd64.iso -J -l -b isolinux/isolinux.bin
