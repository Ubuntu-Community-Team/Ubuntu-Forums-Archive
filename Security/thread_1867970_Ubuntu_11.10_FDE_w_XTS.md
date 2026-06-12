---
title: "Ubuntu 11.10 FDE w/ XTS"
date: 2011-10-23
forum: Security
---

### Post by ztux on 2011-10-23
In this guide I'm going to show you how to install Ubuntu 11.10 with full disc encryption with XTS. I'm using the desktop installer, the alternate installer does not support this mode. I've  done this setup on earlier versions of Ubuntu, but it isn't quite the same with 11.10

I have two partitions on the HDD, sda1(/boot) and sda2(LUKS/LVM).

After booting the installer from USB and configuring the network, I install lvm2.

```
sudo apt-get install lvm2
```Next I create the LUKS volume with cryptsetup.

```
sudo cryptsetup luksFormat -c aes-xts-plain -s 512 -h sha512 /dev/sda2
```Now open the LUKS and setup the LVM.

```
sudo cryptsetup luksOpen /dev/sda2 pvcrypt
sudo vgcreate vg /dev/mapper/pvcrypt
sudo lvcreate -n root -L 1G vg
sudo lvcreate -n tmp -L 1G vg
sudo lvcreate -n opt -L 1G vg
sudo lvcreate -n var -L 2500M vg
sudo lvcreate -n swap -L 4G vg
sudo lvcreate -n usr -L 9G vg
sudo lvcreate -n home -l 100%FREE vg

```Activate swap.

```

sudo mkswap /dev/mapper/vg-swap

```For some reason, the installer does not let me format the volumes, so I do it manually. Example:

```
sudo mkfs.ext4 /dev/mapper/vg-root
```Begin  the installation process now. Don't connect to the internet, it seems  there's another bug that will cause the installer to hang if you try  install the updates during installation. When you get to installation  type, select 'something else'/manual and configure the LVs with the  appropriate mount points.

DO NOT RESTART YET!! After the  installation has finished, DO NOT RESTART! We are not done. We need to  mount the installation and configure some stuff.

```
cd /mnt
sudo mkdir ubuntu
sudo mount /dev/mapper/vg-root ubuntu
sudo mount /dev/mapper/vg-home ubuntu/home
etc...
```Chroot in and install lvm2. Re-connect your network here. 

```
sudo chroot ubuntu
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
apt-get update
apt-get install lvm2 cryptsetup

```Add the encrypted volume's UUID to /etc/crypttab

```
echo "pvcrypt UUID=`blkid -s UUID -o value /dev/sda2` none luks" | tee -a /etc/crypttab
```Make sure the initrd is up to date.

```
update-initramfs -u
```And it's done! Go ahead and reboot.

---

### Post by rookcifer on 2011-10-24
> **ztux said:**
> NOTE: This guide is currently incomplete.

I'm installing Ubuntu 11.10 to my laptop with full disc encryption using  the XTS cipher.

XTS is not a cipher.  It is a [mode of operation]("http://en.wikipedia.org/wiki/Block_cipher_modes_of_operation").  The cipher used is AES with the option to use Twofish and maybe one other.  But there is really no reason to use anything but AES.

XTS is the newer mode of operation standard but CBC-ESSIV is still highly secure and thus I see no reason to go through the pain of getting XTS setup.  It will eventually make it's way into the mainstream installer I imagine.

---

### Post by ztux on 2011-11-01
Thanks for the correction. I've done this setup before, on earlier versions of Ubuntu, so I took it as a challenge to get it working in this version. Like some other users, I like having options and having my computer work my way. That's what Linux is about.

---

### Post by Ms. Daisy on 2011-11-01
Hello ztux. I've got a few noob questions for you.  In the first code of your guide, it says```
audo apt-get install lvm2 
```Should it be sudo instead of audo? 

And I presume that this guide is for a new install, not an upgrade?

---

### Post by ztux on 2011-11-05
Right, it should say sudo. I'll fix it. And yes, this is for a clean install.

Are you trying to do an upgrade? Make sure the options field of crypttab does not have an 'lvm=' option set. It's in the earlier versions of some guides but it breaks this version of Ubuntu. There's no need to include additional modules, the default initrd will include all the necessities.

---

### Post by Rex_Regis on 2011-11-26
Not sure if it a problem with my setup or if it's required, but I had to reformat all the LVs again in the screen where you choose the mount points. Both a test install in virtual box and an install on my laptop required this.

Since I just formatted all the LVs from xterm, I did not choose to format them in the installer. Then the installer hung. Tried a second time, choosing to format them again and installer continued.

Thank you for the guide. I've always used the alternate disc (since it supports LVM at bootup), but this method is far better, at least for me.

---

### Post by JustinR on 2011-12-17
This is kind of an older thread, but does any one know why it doesn't work in the alternate cd anymore? Things like LVM and cryptsetup are supported on the alternate disk, but doesn't install the lvm2 and cryptsetup packages on the actual system installation after you take the time to set it all up in the installer. Also, the removal of aptitude/fdisk/apt-get/dpkg make it implausible to use the alternate cd anymore.

I spent last night from 8PM to 2:30AM nonstop trying to get it to work with the alternate CD (like I did with all the other previous installations) before finally giving up and installing it with the desktop cd (which doesn't have the more advanced text installer). Did they remove it because of space restrictions on the cd?

And btw, here is an older guide I found detailing how to make this work too:[http://and1equals1.blogspot.com/2009/10/encrypting-your-hdd-with-plausible.html](http://and1equals1.blogspot.com/2009/10/encrypting-your-hdd-with-plausible.html) (it doesn't use the LUKS part of cryptsetup though)

---

### Post by optimumpro on 2012-12-07
Hello. I have done everything according to your directions. However, the installer won't let me set mount points. Any help would be appreciated.

---

