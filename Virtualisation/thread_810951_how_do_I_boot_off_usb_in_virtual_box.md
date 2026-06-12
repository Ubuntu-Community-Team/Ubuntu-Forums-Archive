---
title: "how do I boot off usb in virtual box"
date: 2008-05-28
forum: Virtualisation
---

### Post by gatorbrit on 2008-05-28
I want to install win2k in virtual box.  But I don't have a working CDROM, so I have a bootable usb drive with the win2k files etc on it.  How do I tell virtual box to boot from this USB stick instead of a cd?


Thanks

---

### Post by bradmkjr on 2008-05-29
simple, make an ISO file out of the contents.

[http://linuxcommand.org/man_pages/mkisofs8.html](http://linuxcommand.org/man_pages/mkisofs8.html)

this maybe a little tricky to get it to work, to make it bootable. But It will be much easier then booting off of usb in a virtual machine.

[http://www.linuxforums.org/forum/linux-applications/1281-bootable-iso-images.html](http://www.linuxforums.org/forum/linux-applications/1281-bootable-iso-images.html)

Also if you do have access to a second computer with a working cd drive, use that computer to make the iso, it will be easier.

Good Luck
Bradford Knowlton
[http://x86v.com/](http://x86v.com/)

---

### Post by gatorbrit on 2008-05-29
Thanks for the reply - would i just put the ISO in some folder on the c drive and then point the virtual machine to that?

---

### Post by bradmkjr on 2008-05-29
virtual box does the best job of iso management out of any virtualization product I have seen so far. They keep a list of isos you ahve used and makes it very simple to set the virtual machine to use any of the recent isos. I recommend setting up a directory for ISO, because over time you may collect a few, such as windows, ubuntu, knoppix etc. They are not small files, generally enough to fill a cd so plan accordingly and store them somewhere where you have plenty of space. They can even be on an external hard drive if you have that option. Even that will be faster then a regular cd rom drive.

Good Luck,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by cabez0n on 2009-04-03
Exactly, VirtualBox is able to boot form an ISO. 
I just downloaded debian netinst and after make a virtual drive for that image, you go into the properties-->Cd/rom And then check to boot the iso file. 

After you start and debian boots right away !! 

Cheers!

---

### Post by zerlgi3 on 2009-08-12
Please see
[http://forums.virtualbox.org/viewtopic.php?f=6&t=11368&p=91772#p91772](http://forums.virtualbox.org/viewtopic.php?f=6&t=11368&p=91772#p91772)

Summary: Create a raw vmdk file pointing at your USB stick, which is typically /dev/sdb or /dev/sdc (full instructions in forum post)

Can also create a raw vmdk file from a usb diskimage (usefull for netbook.img)

---

