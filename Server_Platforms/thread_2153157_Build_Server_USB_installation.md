---
title: "Build Server USB installation"
date: 2013-06-10
forum: Server Platforms
---

### Post by d.atanasov on 2013-06-10
Dear all, 

I am having trouble with the server edition of 12.04.2 LTS of Ubuntu. I am trying to install it on a machine via USB Pen Drive. Unfortunately I have not succeeded up to this moment because the installation aborts on the step where it has to "copy some important files from the CD". I have tried all variants which where existing on the web but with no luck. Can you suggest me a way to build properly the USB Pen drive installation ? 


cheers 

dinko

---

### Post by d.atanasov on 2013-06-13
No one has an idea ?

---

### Post by papibe on 2013-06-13
Hi d.atanasov.

I have not been able to install a server edition using an USB stick. There's a bug that references the CD, that to my knowledge, it hasn't been properly fixed.

There is a trick though, that some people swear about it, but it does not always work in my experience. You can found the details [here]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/815659") and [here]("http://ubuntuforums.org/showthread.php?t=831332").

Regards.

---

### Post by Cheesemill on 2013-06-13
Create the USB drive using dd if you're on a Linux machine or Win32 Disk Imager if you're on a Windows machine. Unlike all of the other methods used for creating a bootable USB these will create an exact copy of the iso file that won't have the issue you're facing.

For instructions check out this page, it's from the #! forums but works exactly the same with the Ubuntu Server images.
[http://crunchbang.org/forums/viewtopic.php?id=23267](http://crunchbang.org/forums/viewtopic.php?id=23267)

---

### Post by d.atanasov on 2013-06-14
Thanks for the replies. I will give you more info when try them next few days. In principle I thought that many of the server machines now a days work with installation either through PXE either through the usb stick. I did not think even for a second that there will not be a server installation from USB. But life is full of surprises :)

---

