---
title: "Cannot mount ext4 partition from USB drive"
date: 2014-05-31
forum: Virtualisation
---

### Post by happyraver1958-9 on 2014-05-31
I am running Ubuntu 12.04 under Oracle VirtualBox version 4.3.12, underlying OS is Windows 7, SP1.
I am trying to mount my old Fedora 19 partition, which is located in my external hard drive, which I have plugged in to a USB port in my laptop, where I'm running Windows 7.
Here's a transcript from my terminal:

[FONT=fixedsys][FONT=courier new]user@laptop-VirtualBox:/media$ sudo mount -v -t ext4 /dev/sdb6 /media/fedora19
[sudo] password for zac: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@laptop-VirtualBox:/media$ [/FONT]
[/FONT]
if I try to have mount guess the fs type:

[FONT=courier new]user@laptop-VirtualBox:/media$ sudo mount /dev/sdb6 /media/fedora19
mount: unknown filesystem type 'LVM2_member'
user@laptop-VirtualBox:/media$[/FONT]

I have researched this in the forums and Google'd it and I have not found anything similar to it; which is why I'm asking the question here.

Any guidance will be most appreciated!

happyraver1958-9

---

### Post by deadflowr on 2014-05-31
moved to virtualisation

---

### Post by ajgreeny on 2014-05-31
Is your fedora partition using LVM as it would appear from that error message?  Ubuntu could not deal with that in the past unless you had installed various packages to assist in mounting and reading LVM. It was one of the problems I had when trying to triple boot WinXP, Ubuntu and Fedora a few years ago, when fedora used LVM by default.  I have no idea if that is still so, but thought this worth mentioning, just in case.

---

### Post by oldfred on 2014-05-31
I have never used lvm, but have some links for info:

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by happyraver1958-9 on 2014-06-01
Well, I installed LVM2 and the GUI for it with the simple steps in this thread and it's working like a charm!
Thank you all so very much for your quick response and help with this simple issue. I learned a lot along the way as well.
Thanks again!

---

