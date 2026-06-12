---
title: "Help installing ssh"
date: 2007-05-18
forum: Server Platforms
---

### Post by chimerical_brio on 2007-05-18
Whenever I try installing ssh (sudo apt-get install ssh), I get prompted as to whether I want to install two new packages, say yes, and then am told this:

"Media change: please insert the disc labeled 'Ubuntu-Server 7.04 _Feisty Fawn_ - Released i386 (20070415)' in the drive '/cdrom/' and press enter

So I put the disc I used to install Feisty server into my main cdrom drive, and press enter (yes, after waiting a few minutes for it to recognize it)-no luck. So, just to be careful, I pop it into my other drive, and again, didn't work. And I can't get out of it.

So I ctrl+z out of it to the command line, but then, whenever I try using apt (for instance, sudo apt-get update), I get the error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavalable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What should I do? How do I install ssh without using the disk? How do I stop this error? Thanks.

---

### Post by smdeep on 2007-05-18
Just comment out the line in /etc/apt/sources.list for the cdrom. Do a apt-get update, and then install. This time it should not ask you for the disk.

HTH

---

### Post by gaten on 2007-05-18
> So I ctrl+z out of it to the command line, but then, whenever I try using apt (for instance, sudo apt-get update), I get the error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavalable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

The reason you are getting that error is because you are sending the program to the background with CTRL+Z. 

What you are looking for is CTRL+C, that will kill the process.

---

