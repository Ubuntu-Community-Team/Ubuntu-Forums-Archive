---
title: "POP_OS on my files menu will not go away"
date: 2020-02-26
forum: Ubuntu/Debian BASED
---

### Post by jarp53 on 2020-02-26
I downloaded the ISO for "pop os " to try it out , after I made the usb , I deleted the download , I am no longer using the usb, but  it is still showing as if the drive was plug in and I can see all the files but I can't delete them , can some one help me with this ?

---

### Post by yancek on 2020-02-26
What did you delete, the Pop OS iso file you downloaded?
How did you create the bootable usb, what software was used?
How do you 'see' the file and where are they located in the filesystem hierarchy, does it appear the usb is still available? See it in the file manager?
What exact method did you use to try to delete the files?  Did you do it as a normal user in a GUI?  Some other way?

---

### Post by jarp53 on 2020-02-26
I deleted the ISO files in my Download folder, I use Gparted to clean the usb, and Disk to restore  the ISO image into the usb , ( this is the way I always done it and have install several OS's with no problem in the past ); this is what the terminal shows when I try to delete the folder :
jr@jr-Z68X-UD3H-B3:/media/jr/Pop_OS 19.10 amd64$ sudo apt-get purge /media/jr/Pop_OS 19.10 amd64[sudo] password for jr: 
Reading package lists... Done
E: Unsupported file /media/jr/Pop_OS given on commandline
jr@jr-Z68X-UD3H-B3:/media/jr/Pop_OS 19.10 amd64$

and this is the first time an ISO has done that , I copy the ISO from the official POP site

---

### Post by jarp53 on 2020-02-26
NO Problem !!!!  some how the installation went to another drive , and that's what was showing up , thank you and sorry for the false alarm :oops:

---

### Post by CelticWarrior on 2020-02-28
'apt' or 'apt-get' are for managing packages (.deb files). 'apt-get purge <package>' removes (uninstalls) the software package and all its eventual user settings, while remove instead of purge would only uninstall the software. This isn't to be used for any file.

> and this is the first time an ISO has done that

No, it can't be true. Whenever you try to 'apt-get purge' against an ISO file it surely will give the same result and the same error message.

---

