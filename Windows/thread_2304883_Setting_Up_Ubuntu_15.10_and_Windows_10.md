---
title: "Setting Up Ubuntu 15.10 and Windows 10"
date: 2015-11-30
forum: Windows
---

### Post by shane_faulkinbury2 on 2015-11-30
Okay I know I have to install Windows 10 first before Ubuntu!  I setup Windows 10 today then immediately booted to my Ubuntu 15.10 disk which got an error!  The 15.10 must be corrupt, but i'v tried downloading it twice and get the same error so I'm using my 15.04 disk and then upgrading.  Anyway after installing Windows and then going to Ubuntu I create a 700 GB partition using ext4 and then try to install and get this error.  "No root file system is defined.  Please correct this from the partition menu."  First off I do not know how to get to the partition menu and I do not know how to resolve this!  Any help would be greatly appreciated!

---

### Post by T.J. on 2015-11-30
You are not the only person to have had problems related to Windows 10. It likes to take over.  

In this case that message means that your setup was not properly configured.  You have to mark the partition as the root partition if you are configuring partitions manually.  The root partition is like Windows C: drive - where the operating system is meant to be installed.  If your installer cannot figure out how to configure automatically with Windows 10 installed, then you will have to configure the setup manually.  If you have Secure Boot enabled, it can cause issues as well.  If you have never configured it manually before I humbly suggest that you do a little reading before you do so.

Typically an install is divided into three partitions:  "root" (/)  "swap, and "home" (/home).

---

### Post by shane_faulkinbury2 on 2015-11-30
I'll turn Secure Boot off in BIOS and try that!

---

