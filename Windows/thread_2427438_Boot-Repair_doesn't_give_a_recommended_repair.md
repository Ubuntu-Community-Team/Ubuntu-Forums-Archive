---
title: "Boot-Repair doesn't give a recommended repair"
date: 2019-09-22
forum: Windows
---

### Post by imclueless24710 on 2019-09-22
Yesterday I installed windows 10 and when I started my computer this morning it didn't work and kept telling me to reboot. I have a gaming pc but don't know anything about computers. I tried a lot of stuff I found on google but I probably made it worse. If anyone can help me out and explain possible solutions in baby steps it would be much appreciated.This is the summary I got: [http://paste.ubuntu.com/p/JtCDg3YsFw/](http://paste.ubuntu.com/p/JtCDg3YsFw/)

---

### Post by yancek on 2019-09-22
There is no sign in your boot repair output of any Ubuntu or Linux system other than boot repair.  Did you have Ubuntu or some other Linux OS installed?
You have windows boot code in the MBR of the disk which is very unusual as windows 10 uses UEFI by default and has an EFI partition and no code in the MBR.  You don't show an EFI partition nor are there any of the boot files needed to boot windows.  Did you download and run boot repair on your windows system because it looks like you have overwritten your windows and may need to re-install it.
It also shows the 1TB drive has only one partition which has a vfat filesystem, something windows hasn't used for it's operating systems since windows 98.

To use boot repair you need an installation of Ubuntu or one of its derivatives on which to download and run it.  Did you have some Ubuntu installed?  No sign of it now.    I've never seen boot repair output like this before.  If you want to install with a dual boot of windows 10 and Ubuntu, read the Ubuntu documentation at the link below.  If all you want is windows, go to the microsoft site or a windows forum for advice.  FYI, the boot repair software is primarily designed to repair Linux systems but can do some repairs which will allow booting of windows.

   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by QIII on 2019-09-22
Did this machine have an earlier version of Windows previously?  Did it have a version of Ubuntu previously?

---

