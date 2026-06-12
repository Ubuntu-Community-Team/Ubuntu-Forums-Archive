---
title: "WinXP to Ubuntu Server"
date: 2008-04-19
forum: Server Platforms
---

### Post by garfonzo on 2008-04-19
I have a "server" running WinXP to serve files and a printer on my home LAN. The OS resides on a 20GB hard drive while all the user files reside on a second, 320GB internal hard drive. Eventually, I want to turn that into a Ubuntu Server and lose WinXP. 


I have two questions:

1) Can I install Ubuntu Server on the 20GB hard drive with 100% certainty that the 320GB (and all user files) will not be harmed/erased?

2) Would it be better to move all the user files on the 320GB hard drive off the drive, reformat the drive to ext3, and then put all the files back on the freshly formatted drive to be more Linux friendly?



Thanks!

Garfonzo

---

### Post by HermanAB on 2008-04-19
If the second drive is NTFS, then that is OK.  NTFS is a good file system.

If you are scared that you will accidentally damage the drive during the install, simply unplug it before you install.

---

