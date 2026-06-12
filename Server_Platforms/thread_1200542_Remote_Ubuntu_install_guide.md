---
title: "Remote Ubuntu install guide"
date: 2009-06-30
forum: Server Platforms
---

### Post by Gorlist on 2009-06-30
This tutorial is based from the following URLs which ive modified to work with my root 1and1 server. Im afraid I won't be able to provide a great deal of troubleshooting support.

[http://sbmonkey.wordpress.com/2008/0...by-step-guide/](http://sbmonkey.wordpress.com/2008/0...by-step-guide/)
[http://www.howtoforge.com/minimal-ub...server-install](http://www.howtoforge.com/minimal-ub...server-install)

Hopefully this tutorial will guide you through a successful install of Ubuntu Linux on your server platform with your own custom partition sizes, and without relying on a predefined 1and1 image.

Please make sure all data is backed up prior to attempting, including your psa.key if you intend to reinstall Plesk.

Reboot into recovery mode from the 1and1 control panel (e.g. Linux 64-bit Rescue System (debian/etch - 2.6.x)), this will boot your dedicated server into a ram mode. Login to it via ssh.

```
apt-get update
apt-get install nano
```
(or use vim)

Lets remove our out of date debootstrap and install a newer revision.
```
apt-get remove debootstrap
wget http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.13_all.deb
dpkg -i debootstrap_1.0.13_all.deb

```
Delete all, and any existing partitions (either using cfdisk or fdisk):
```
cfdisk /dev/sda
fdisk /dev/sda
```

Setup partitions as follows for example:
/dev/sda1 - 100MB (boot & flag as bootable)
/dev/sda2 - 4096MB (swap)
/dev/sda3 - remaining disk space (/)

```
mkfs.ext3 /dev/sda1
mkfs.ext3 /dev/sda3
mkswap /dev/sda2
```

```
mkdir /min
mount /dev/sda3 /min
mkdir /min/boot
mount /dev/sda1 /min/boot
```

Before running Debootstrap, if you want to change the mirrors edit:
```
nano /usr/share/debootstrap/scripts/hardy
```

Lets begin the instillation:
```

debootstrap hardy /min
```

Setup our hostname and network.
```
echo "myservername" > /min/etc/hostname
echo "127.0.0.1 localhost" > /min/etc/hosts
echo "127.0.1.1 myservername" > /min/etc/hosts

nano /min/etc/network/interfaces
```

Copy and paste the following:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Setup our fstab:
```
nano /min/etc/fstab
```

Copy and paste:

```
/dev/sda1 /boot ext3 defaults 0 1
/dev/sda2 none swap sw 0 0
/dev/sda3 / ext3 defaults 0 1
```

Mount & enter the chroot enviroment:
```
mount --bind /dev /min/dev
mount -t proc proc /min/proc
mount -t sysfs sysfs /min/sys
chroot /min
```

Setup our timezone:
```
tzselect
```

Install nano:
```
apt-get install nano
```

Edit the sources list again if you wish to change mirrors:
```
nano /etc/apt/sources.list
```

```
apt-get update
apt-get dist-upgrade

```
Set our root password (or leave blank to deactivate? - make sure you add a user):
```
passwd
```

And/Or:

```
adduser myusername
addgroup admin
adduser myusername admin
echo "%admin ALL=(ALL) ALL" >> /etc/sudoers
```

Now for gurb:
```
apt-get install linux-image-server grub
mkdir /boot/grub
update-grub
update-initramfs -u
```

Install our ssh server:
```
aptitude install openssh-server
```

And finish:
```
exit

grub-install --root-directory=/min --no-floppy --recheck /dev/sda
```

Reboot system into normal mode through your control panel, and connect normally through putty.

---

### Post by Gorlist on 2009-06-30
For a Ubuntu 8.04 source list: [http://repogen.simplylinux.ch](http://repogen.simplylinux.ch)

------
Plesk specific, you may want to add usrquota to your fstab:

```
/dev/sda3 / ext3 defaults,usrquota 0 1
```

Then install quota:

```
sudo apt-get install quota
```

It should automatically check your harddrives if done in that order, though if not do as follows:

```
sudo quotaoff -av
sudo quotacheck -avum
sudo quotaon -av
```

And reboot (you may need to remount the harddrive if you've not rebooted since adjusting the fstab before running the above.

On the mini Ubuntu install you might get perl locale errors, if so try the following:
```
sudo apt-get install language-pack-en
```

---

### Post by Gorlist on 2012-09-12
Still working fine with Ubuntu 12.04LTS, however this time I used Lenny (few teething problems with the 1and1 recovery image being so out of date).

Make sure you use the latest Debootstrap, Ext4 on SDA3, and obviously precise instead of hardy.

Plesk 11 installation no problems, however I preformed a complete backup of the stock 1and1 Plesk 11 install, then restored the license (saved having to phone them). Don't forget to harden your server.

---

