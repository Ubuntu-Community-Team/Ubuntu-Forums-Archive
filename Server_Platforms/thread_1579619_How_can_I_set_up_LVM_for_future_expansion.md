---
title: "How can I set up LVM for future expansion?"
date: 2010-09-22
forum: Server Platforms
---

### Post by bizoday on 2010-09-22
Hello everyone,

First things first. I want to thank in advance the Ubuntu community as a whole for all of the help given to everyone. I myself have read through countless threads and stickies for help in using Ubuntu.

Currently, I have a project in setting up a web server using LAMP.  I have the server set up, dynamic DNS, a domain name, POSTFIX, courier, roundcube, the whole 9 yards.

My questions is: How can I add a hard drive to the current configuration without losing data and be ready for expansion as mail boxes fill up, data for websites fill in, etc?

After reading around,  I am still confused on how to use LVM, or at least convert to LVM.

I suppose, the first thing I will definitely have to do is clone my existing hard drive to the newer and larger hard drive and then set up LVM (to use like RAID 0?)

May I have some advice on how to correctly transfer my smaller hard drive to the newer and larger hard drive and how to set the newer one up for LVM for future expansion?

Thanks in advance!

---

### Post by scrooge_74 on 2010-09-23
I did something similar I have 4 disks (3 x 250GB and 1 500Gb with my old data) I set up 3 disks in LVM then copy data over after installing OS. Then that 500 GB disk I can either add it to the array or use it as backup for the other 3.

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

Latest Ubuntu will manage the creation of the LVM.

In a nut shell, you create the LVM and you tell it which disks or part of disk are part of it.

Then on top of it you create the volumes for your install then you install the OS.

After when you need more space you can tell the system while is running you want to add a disk or a partition to the LVM array and then you specify which section of your system you want it to use it (/home or more space for /var)

---

### Post by bizoday on 2010-09-30
Thank you so much for your help!

This is exactly what I want and how I want to do it. Thank you for your experience, and thank you for the how-to link.  

This is nice because I can then just expand certain folders where the majority of the data resides.

One question though, is there a theoretical limit to the size of the LVM for a certain directory?

For example:

is /var/www
max out at a certain size?

Thanks in advance!

---

### Post by scrooge_74 on 2010-09-30
Haven't found limitations in size. Just recomendations on the size of folders for issues as size of logs or allocation for caches or /usr space for example

---

