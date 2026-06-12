---
title: "USB Hard Drive Sharing"
date: 2008-07-09
forum: Server Platforms
---

### Post by sandsjh on 2008-07-09
I am running Ubuntu Server 8.04 LTS. I have a USB Hard Drive with one NTFS partition and would like to read/write share it.

I looked at the following places and did not find the information...
[http://www.zaphu.com/2008/05/29/ubuntu-guide-mount-and-share-a-usb-hard-drive-with-macs-using-netatalk/](http://www.zaphu.com/2008/05/29/ubuntu-guide-mount-and-share-a-usb-hard-drive-with-macs-using-netatalk/)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)
[http://tldp.org/LDP/sag/html/index.html](http://tldp.org/LDP/sag/html/index.html)
ubuntuforums.com search: external hard drive

---

### Post by Titan8990 on 2008-07-09
Share it with what?

---

### Post by windependence on 2008-07-09
You're probably not going to be able to write to it, although there are some  drivers available for this now.

To share it, your best bet is to install and configure SAMBA.

-Tim

---

### Post by sandsjh on 2008-07-09
Titan8990: Share it with my WinDoze boxes.

windependence: I have samba installed and sharing the home directories.

---

### Post by Titan8990 on 2008-07-09
What kind of issues are you having? 

Auth issues?

Can either box see the others shares?

---

### Post by sandsjh on 2008-07-09
I do not know how to operate the USB hard drive on Ubuntu Server. I can plug it in and that's about it :-(

The windows boxes can connect to the homes shares correctly.
I just do not know how to mount and share the external USB, especially since it is NTFS.

---

### Post by osjak on 2008-07-09
sandsjh, I have a NTFS USB drive connected to my Debian server. It is working fine if I use it from the server. Here's what I did to mount it.

1. Install ntfs-3g package. You may have to add an additional repository source on your computer, if it doesn't find it:
```
sudo apt-get install ntfs-3g
```
2. Backup your /etc/fstab just in case you screw something up:
```
cp /etc/fstab /etc/fstab.bak
```
3. Add a line for your drive to fstab:
```
/dev/sda1 /media/USBDRIVE ntfs-3g defaults,nls=utf8,gid=46 0 1
```
4. Mount it:
```
sudo mount /media/USBDRIVE
```

It works great for me when I access it from the server. However, I'm having some issues when I try using it from other desktops through Samba - it works fine on one desktop, but doesn't authorize from another one. I haven't had any time to troubleshoot it, so I have no solution to that yet. I have an ext3 drive shared the same way and it is working without any issues, so it's probably something in NTFS settings that's giving me hard time. If you get it working fine, please post your configuration files.

EDIT: In step #3 I assumed that your drive is /dev/sda1 and you have a directory created to mount it at /media/USBDRIVE. Edit those parameters to reflect your setup.

---

### Post by Titan8990 on 2008-07-09
The format will not have anything to do with it.

In Ubuntu USB drives should automount when you plug them in. If not this is how you would do it:

$sudo fdisk -l

Gives you a result as such:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  LinuxDisk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris

Disk /dev/sdc: 4060 MB, 4060086272 bytes
153 heads, 48 sectors/track, 1079 cylinders
Units = cylinders of 7344 * 512 = 3760128 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1080     3964904    c  W95 FAT32 (LBA)

```

Here I can see that my USB thumb drive is listed as sdc1. So to mount sdc1 I do:

$sudo mkdir /media/sdc1

$sudo mount /dev/sdc1 /media/sdc1

You can then view your drive at /media/sdc1/

Edit: What the user above me is doing is assuring that the drive mounts everytime on startup. If you do the above and boot your system without the USB drive attached then the bootup process will hault until you press CTRL+D whenever it goes to mount the drive.

---

### Post by sandsjh on 2008-08-24
Say I have a USB drive... want to format it to LinuxDisk (ext3???)... mount it on every boot... share it with windoz users and it have "everyone" write permissions?

---

