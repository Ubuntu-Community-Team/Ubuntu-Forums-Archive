---
title: "HELP PLEASE - Accidentally installed Porteus onto my C:\ drive where my Windows is..."
date: 2015-12-01
forum: Slackware and derivatives
---

### Post by luke01999 on 2015-12-01
So I was trying to install Porteus onto a USB to boot off of it, but accidentally first installed it somewhere onto my C:\ drive where my Windows is installed. I realised I messed something up, so then correctly installed it onto my USB. I restarted my PC to check it was OK, and then realised what I had done. Now when I try to boot Windows I just get:
 
'SYSLINUX 4.06 EDD 2012-10-23 Copyright (C) 1994-2012 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: '

So I'm in a bit of trouble. Thankfully, as I said, I was about to install Porteus onto my USB, so I can boot via that and access my files from my SSD (my C:\ drive) and my other hard drive. I have my laptop and phone now to use too which means I'm not completely without technology. I don't really have any idea where porteus installed itself to on my PC, or how to like remove it and fix my problem, so help would be greatly appreciated. Thanks.

---

### Post by VMC on 2015-12-01
Did you look inside that "C" partition to see what's there?
'*lsblk*' command will show what partitions are installed.

---

### Post by grahammechanical on 2015-12-01
Have you read the Porteus installation guide? 

[http://www.porteus.org/tutorials/37-installing/114-official-porteus-installation-guide-v-10.html](http://www.porteus.org/tutorials/37-installing/114-official-porteus-installation-guide-v-10.html)

By the way, Porteus is a derivative of Slackware. I would not think that a Ubuntu user forum was the best place to ask for advice. But just to be friendly.
> 
Porteus can be installed to hard drives, but it should be left in its  compressed state (otherwise known as a 'Frugal' installation).  Installing extracted files to a hard drive is not supported; it is  suggested that you install Slackware Linux instead if you wish to have  an Operating System installed to your system natively.

Creating a  'Frugal' installation is very similar to installing on a USB drive.  Porteus can be installed on it's own partition, or it can be installed  side by side with Windows or another Linux OS on the same partition.

It seems that Porteus is not installed in the same manner as Linux distributions such as Ubuntu. You put the compressed files on the partition. The key thing to keep in mind is not to overwrite the existing OS bootloader with the Porteus bootloader (syslinux). which is what I think that you have done.

> If you already have an OS installed on that drive and want to keep it  there, then you can run 'Porteus Installer' without clicking the option  to install a bootloader.  After the files are copied over, you'll just  need to point your existing bootloader to the Porteus data.

I would say that you need to re-install the Windows bootloader. And I cannot tell you how to do that.

Regards.

---

### Post by sandyd on 2015-12-01
Not a Ubuntu support request.
Moved to *Other OS*.

---

### Post by luke01999 on 2015-12-02
Apologies for posting in the wrong place - was not meaning to be ignorant, Linux/Ubuntu etc. is all brand new to me and I don't really know what anything is! Thanks for the replies, I'll investigate and get back to you in a bit.

---

### Post by luke01999 on 2015-12-02
Just wanted to thank grahammechanical for pointing me towards a solution. After googling solutions to fix the bootloader, I found [boot-repair-disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") which fixed my problem nice and easily :D Cheers guys, thread can be closed.

---

### Post by The Cog on 2015-12-02
Great news.

You can mark the thread solved yourself by using the Thread Tools pull-down menu at the top of the page.

---

