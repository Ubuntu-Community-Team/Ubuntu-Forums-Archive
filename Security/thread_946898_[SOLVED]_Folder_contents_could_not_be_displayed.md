---
title: "[SOLVED] Folder contents could not be displayed"
date: 2008-10-13
forum: Security
---

### Post by davethewave83 on 2008-10-13
Is it possible to replace the "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "folder" " with a root password prompt? 

I know that I can sudo in terminal to gain access to the folder but often I prefer to use GUI, or I create a launcher on the desktop for gksu nautilus then browse the folder through that (or sudo su, invoke-rc.d gdm stop, sudo su and login as root then startx if you wanted to get rediculous) sorry for the pointless ranting, but anyways it would be so much easier if the "access denied" simply had a password prompt available for folders which are owned by root and have a chmod of say 600 etc.

---

### Post by cdenley on 2008-10-14
[http://brainstorm.ubuntu.com/idea/4347/](http://brainstorm.ubuntu.com/idea/4347/)

---

### Post by cariboo on 2008-10-14
Wait until Intrepid Ibex (v. 8.10) comes out at the end of the month, the feature you  want is now built in to Nautilus.

Jim

---

### Post by davethewave83 on 2008-10-14
Ok thanks!

---

