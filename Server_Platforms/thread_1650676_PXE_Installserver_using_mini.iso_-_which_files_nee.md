---
title: "PXE Installserver using mini.iso - which files needed?"
date: 2010-12-22
forum: Server Platforms
---

### Post by m.dr on 2010-12-22
I am trying to set up a PXE InstallServer using the mini.iso.

I am following this tutorial by agibby5.

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

It uses tftpd-hpa, nfs, syslinux and dhcp3.

He uses a full ubuntu iso for the tutorial however I wanted to use a mini.iso.

So in the following 5 commands to copy over necessary files my files in mini.iso don't match. Looking to see if anyone has used the mini.iso and then what files to setup under tftp and such.

I understand I need to copy over the kernel and ininrd files? I think the initrd file in mini.iso is initrd.gz and not sure what the kernel files is.

Trying to see if someone can point me to a tutorial for PXEInstallserver with the mini.iso.

Thanks!
--------------------
sudo mkdir /mnt/loop

sudo mount -o loop -t iso9660 /location/of/ISO/ubuntu-9.10-desktop-i386.iso /mnt/loop

sudo cp /mnt/loop/casper/vmlinuz /var/lib//tftpboot/ubuntu/9.10/i386

sudo cp /mnt/loop/casper/initrd.lz /var/lib/tftpboot/ubuntu/9.10/i386

sudo cp -R /mnt/loop/* /srv/install/ubuntu/9.10/i386
sudo umount /mnt/loop

---

