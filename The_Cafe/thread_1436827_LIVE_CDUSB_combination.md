---
title: "LIVE CD/USB combination"
date: 2010-03-23
forum: The Cafe
---

### Post by dyingsun on 2010-03-23
Hi ppl,

I've been poking around trying to figure out how to customise a live CD/DVD and configure it to do all its write operations on a USB stick. I've found sites that walk you through the customisation process, but I can't find anything about how to configure them to suit my needs. 

Basically I need a lightweight live CD (or DVD, but CD would be preferable). It needs to have the packages I require, mostly programming tools, Apache/MySQL/PHP, Netbeans, Kate, openOffice, at least 2 browsers, an email client, a chat client such as Pidgin, ncftp, GiMP and other useful things. However, I need /home/damien to be on a USB stick, along with any config files for the applications, and also the webroot. 

Things that would be nice, but not essential, are music players with all codecs, a newsreader, softphone client, etc.

Doesn't have to be Ubuntu, though I would prefer it.


I gather its possible to do all this on a USB stick alone, but most of the machines i encounter don't support USB booting. It would save me a lot of time and hassle if I had a portable development environment, running from a CD and writing to a USB stick. Is this actually possible? Can somebody point me to some info that would help? I have tried googling but its not very effective when you're not sure exactly what you're searching for!


Thanks in advance
Damien

---

### Post by dyingsun on 2010-04-07
Bump. 
Nobody? :(

---

### Post by garvinrick4 on 2010-04-08
> **dyingsun said:**
> Hi ppl,

I've been poking around trying to figure out how to customise a live CD/DVD and configure it to do all its write operations on a USB stick. I've found sites that walk you through the customisation process, but I can't find anything about how to configure them to suit my needs. 

Basically I need a lightweight live CD (or DVD, but CD would be preferable). It needs to have the packages I require, mostly programming tools, Apache/MySQL/PHP, Netbeans, Kate, openOffice, at least 2 browsers, an email client, a chat client such as Pidgin, ncftp, GiMP and other useful things. However, I need /home/damien to be on a USB stick, along with any config files for the applications, and also the webroot. 

Things that would be nice, but not essential, are music players with all codecs, a newsreader, softphone client, etc.



I gather its possible to do all this on a USB stick alone, but most of the machines i encounter don't support USB booting. It would save me a lot of time and hassle if I had a portable development environment, running from a CD and writing to a USB stick. Is this actually possible? Can somebody point me to some info that would help? I have tried googling but its not very effective when you're not sure exactly what you're searching for!


Thanks in advance
Damien
The CD or DVD version of a install has no persistence (cannot hold  changes) the USB
version that uses FAT32 format will hold up to 4 gig of persistence in  some programs.
You can also use a USB say 16 gig and format it like a disk drive in  ext3 or ext4 and make a normal Linux install with full 16 gig  persistence. 
 But it is not possible in CD or DVD. There just is not any programs  available to my knowledge to perform this.

---

### Post by NightwishFan on 2010-04-08
Here is what I would do. Download a supergrub disk iso, and burn to a CD/DVD. Then use that to boot Ubuntu USB on a machine that does not support USB booting. Ubuntu has a tool pre-installed to install it on a USB.
[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso)

If that does not work, go with puppy linux.
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by dyingsun on 2010-04-10
Thats a couple of good ideas, thanks very much guys.

I never even thought of a grub disc. I have a 100gb external sitting here doing nothing atm anyway :)

Cheers!

---

