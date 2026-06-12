---
title: "issue with lubuntu cd customization"
date: 2014-03-11
forum: Virtualisation
---

### Post by lance bermudez on 2014-03-11
I'm using the guide at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I have installed
sudo aptitude install squashfs-tools genisoimage

I'm using Lubuntu 13.04 desktop cd and I have it in a directory called lxde inside another directory called extract-cd. Also inside the lxde directory is another called edit that contains the squashfs that i extated to do the customization.

to do the customization i did
sudo cp /etc/resolv.conf edit/etc/
sudo mount --bind /dev/ edit/dev
sudo chroot edit
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
I installed the packages I wanted then delete the edit/etc/resolv.conf and unmounted the other stuff.

I did not change the kernal I just want to add some packages. I made the file system using 
chmod +w extract-cd/casper/filesystem.manifest
sudo chroot edit dpkg-query -W --showformat='${Package} ${Version}\n' > extract-cd/casper/filesystem.manifest
sudo cp extract-cd/casper/filesystem.manifest extract-cd/casper/filesystem.manifest-desktop
sudo sed -i '/ubiquity/d' extract-cd/casper/filesystem.manifest-desktop
sudo sed -i '/casper/d' extract-cd/casper/filesystem.manifest-desktop

sudo rm extract-cd/casper/filesystem.squashfs
sudo mksquashfs edit extract-cd/casper/filesystem.squashfs
printf $(sudo du -sx --block-size=1 edit | cut -f1) > extract-cd/casper/filesystem.size

cd extract-cd
sudo rm md5sum.txt
find -type f -print0 | sudo xargs -0 md5sum | grep -v isolinux/boot.cat | sudo tee md5sum.txt


then I used this to create the iso
sudo mkisofs -D -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-9.04.1-desktop-i386-custom.iso .

When I use virtual box to test the iso it errors out to busybox with (initramfs) what did I do wrong?
[ATTACH=CONFIG]251055[/ATTACH]

---

