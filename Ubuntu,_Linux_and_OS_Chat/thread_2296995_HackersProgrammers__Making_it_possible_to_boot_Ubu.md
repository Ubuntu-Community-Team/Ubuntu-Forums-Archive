---
title: "Hackers/Programmers :: Making it possible to boot Ubuntu up in Windows?"
date: 2015-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by SnowyForest on 2015-09-30
Hi all,

Do you think there's any good hackers/programmers out there that are good enough to be able to do this,
Ubuntu is installed on a external SSD, but you can open Ubuntu in windows itself.

---

### Post by sudodus on 2015-09-30
Welcome to the Ubuntu Forums :-)

Yes, if you install and run a virtual machine, for example VirtualBox, in Windows. Then you can run Ubuntu in the virtual machine.

(There was wubi, but it does not work with the new versions of Windows, and it is no longer developed and no longer supported.)

---

### Post by kurt18947 on 2015-09-30
There *used* to be something that did this called WUBI. It might still be around but I don't believe it is being developed and was only ever intended to provide sort of a preview with limited functionality. The common method seems to be a virtual machine. I have a *buntu host running Virtual Box and a Windows 10 guest. So far so good. The only thing that I found a little tricky was printing to a networked printer. The default virtual network adapter was using NAT; I could ping the printer but not get it to print. I configured a second virtual network adapter (there are 4 available) as bridged then reinstalled the Windows printer software. It seems to work fine.

---

### Post by mastablasta on 2015-09-30
with virtualbox you can run Ubuntu inside Windows inside Ubuntu :-O

---

### Post by luciano.x on 2015-09-30
Yes there are hackers that actually have written it many years ago. loadlin

But that won't work for you I guess.

---

### Post by coldraven on 2015-09-30
+1 for VirtualBox
[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by mastablasta on 2015-10-01
linuxliveUSB creator - enable launching Linux in windows option - will install portable virtualbox on the USB. you then only need to run virtualise.exe  or something like that and BOOM! you have Linux inside windows.

---

