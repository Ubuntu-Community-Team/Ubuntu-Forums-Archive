---
title: "Partition drive after install"
date: 2010-02-16
forum: Server Platforms
---

### Post by dhillis on 2010-02-16
How do you partion a drive in ntfs after intalling ubuntu server?  

I have the server running and can ping to it.  I used this tutorial [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver) .  Got to page 3 step 8.
 
Only thing is the computer I am using only has room for one hard drive.  Figured there has to be a way to do this with one hard drive using two different partitions.  If that's not possible please stop me before I go any farther.  

I installed the OS on 10 GB of a 2TB HDD.  I now want to partition the rest of the disk so I can share it.  

Thanks Guys

---

### Post by gobbledigook on 2010-02-16
firstly as the guide you are using suggests check output from 
```
sudo fdisk -l 
```
this will show your partitions as they are at the moment, then you can identify the free space and format it in several ways. 

use fdisk - cool if you are comfortable with the command line
use gparted from an ubuntu desktop live cd - boot from the live cd and run gparted, it is a graphical partitioning tool

---

### Post by dhillis on 2010-02-16
thanks..i'll try that when I get back to work tomorrow.  This has been quite a learning experience.  I just started using Ubuntu on one of my desktops about a month ago and am trying to set up a server today.  It is a file server for my classroom with a  2TB harddrive to store video clips and pictures for my classes.  Thanks for the help.

---

### Post by dhillis on 2010-02-18
well guys, i have the partitions now. Thanks for the help on that. Now I have a new problem. I thought that the partition /dev/sda2 got formatted on accident. I tried running the server but nothing happened. So i reinstalled it hoping I could get it on the sda2 partition without formatting the whole drive. 
 
Well it didn't format the first time and now I have to OS's on the /sda2 partition. How do I uninstall one of these without deleteing the other? Or do I need to delete the partition and reinstall the os.
 
This is ubuntu 9.10 server.
 
 
on edit: Does ntfs not show up using the fdisk -l command. I can't see /dev/sda4 by running fdisk -l but when i live boot from ubuntu desktop and use gparted i see that it is there....awnsered this myself....i think...i now see it says
"GPT (GUID Partition Table) Detected on '/dev/sda' The util fdisk doesn't support GPT. USe GNU Parted.

---

### Post by tlsarles on 2010-02-18
Go download GParted ISO.

Bootable mini-distro aimed at exactly what you want to do

---

