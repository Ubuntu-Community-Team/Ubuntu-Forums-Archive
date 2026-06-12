---
title: "Windows to Linux migration"
date: 2008-12-22
forum: Testimonials &amp; Experiences
---

### Post by rwk2095 on 2008-12-22
I am an experienced Windows XP user, and I just installed 8.10 Intrepid to investigate a migration to Linux.  The good news is that I got it running, and so far I am very impressed with the look and feel of Ubuntu.  I have some comments and suggestions about the installation process that I hope are seen as constructive.  I don't know where else to post them.

Background:  I was a programmer before retiring, and I now scratch out a meager subsistence as a financial trader.  I was an app designer/business analyst/manager, not a software engineer.  I depend on my computer for my livelihood, and I need a stable system.  There are two projects that I recently heard about that could make the migration to Linux feasible for me.  The first is Wine, a compatibility tool for running Windows apps.  I have at least one killer app that requires Windows.  The second is Lazarus, a write once/compile anywhere IDE for FreePascal that looks like the Delphi that I have been using for most my own software.

In researching the move, I found this article:  [ [http://www.linux.com/feature/113945](http://www.linux.com/feature/113945) ].  It describes creating a dual-boot installation with Linux on a second hard drive, but with minimal impact on the Windows installation.  This seems to be to be a perfectly reasonable goal (and one that other may want to follow, hence this post), and I decided that I did not want the Linux installer making **any** changes to my primary hard drive.  Unfortunately the article is nearly 4 years old.

The installation of Intrepid went well enough until the installation of Grub on /dev/hdb failed.  I stepped back in the process and came to a menu that allowed me to go with Lilo instead.  That worked (though I am leaving out several wasted steps), and I was able to boot into Linux.  It was difficult, frustrating and time-consuming, but I thought I finally understood the installation process at that point.  I was wrong.

After doing some reading, I found out about the long term support (LTS) version I probably should be using.  Since I had not really gotten into Linux at this point, I decided to redo the installation with 8.04 Hardy LTS.  This is where the real frustration set in, but I will skip the gory details.  Hardy installed Grub on /dev/hdb, but it would not boot.  It took me literally all day to get back up again with Intrepid via Lilo.

There are a lot of perfectly valid reasons for using Windows, as well as for moving to Linux.  The Ubuntu installation is fine for casual users and for serious hackers, but for someone like myself (and there are many) who needs a professional solution, I believe the installation need work.  First up, there needs to be a better pre-installation discussion of the issues and choices the user needs to consider, such as how to move files between the two OS's in a dual-boot setup.  Dual-boot on a second hard drive, as discussed in the above article, should be a supported strategy.  I believe it requires too great a leap of faith to blow away the Windows boot loader with Grub on the primary hard drive and Linux as the default choice.  The installation needs to be less intrusive.  The installation also needs to be divided into steps such that the steps can be executed separately and the installation interrupted and resumed.  The entire installation currently takes close to an hour, and there are simply too many ways that it can be spoiled and need to be re-done.

I really hope I can do this migration, because as I mentioned, there are some very good reasons to leave Windows and Microsoft.  I am starting to warm to the idea of free/open source software, and I like what I see in Ubuntu so far.

[Richard]

---

### Post by wolfen69 on 2008-12-22
i can assure you that your installation woes are not typical. i have done over 40 installs of ubuntu and have never had a problem with setting up a dual boot. it just works. perhaps a more up to date website is in order?

secondly, i think your pride is getting in the way of asking questions on the forum. please feel free to ask any and all questions you may have, in the appropriate section. this is the friendliest most helpful forum in the world. we are here to assist you in your quest for OS freedom.

---

### Post by mdsmedia on 2008-12-22
I think you're being unfair about the installation being too intrusive.

You're installing an operating system, not a Windows package.

The dual boot process is not simple for a beginner, but I've managed to install dual boot successfully several times, and I'm an accountant, not an IT Pro.

Linux wasn't designed to run as a second operating system, but a lot of work has been done to make it quite simple to run Linux alongside Windows or any other OS, including Linux itself. As a comparison, try installing Windows as a dual boot, after you've got Linux installed as your primary OS.

Linux, with GRUB (or Lilo), allows you to run multiple OSes on the one computer, one drive, several drives. You can change the default to booting Windows. I happily (well not happily, but trivially) choose Windows when I want to boot into Windows. Otherwise, I boot into Linux by default.

---

### Post by y@w on 2008-12-22
If you're looking to try out Ubuntu while making minimal changes to your Windows install/partitions, check out [Wubi]("http://wubi-installer.org/"). Otherwise a great alternative would be installing it in a virtual machine using VMware or whatever virtualization software you prefer.

---

### Post by 3rdalbum on 2008-12-22
The BIOS of PCs is made to assume that you are booting off your primary hard disk. Due to differences between BIOSes, you might find that GRUB or LILO won't be able to boot up your machine from the second hard disk, but the other might be able to.

Solution: Install Ubuntu on the primary hard disk, and have your /home on the secondary hard disk.

Your problems stemmed from this. Installing to a non-primary hard disk is not common, and some combinations of bootloader & BIOS have not been tested.

I also recommend using the latest version of Ubuntu where possible. Sticking with an LTS version is only really necessary for machines in a business environment where a longer support period is necessary.

---

### Post by armandh on 2008-12-22
the method I have found for a single drive that just works is...

use parted magic live partition utility to reduce a window partition [except vista: use vista's own partition utility]
leave the remaining space unpartitioned.

during ubuntu setup answer the partition question 
"use largest unpartitioned space"

this will set up ubuntu and a swap partition in an extended partition [and install a grub menu which works just fine]

---

### Post by zero244 on 2008-12-22
If you have a Windows app that you must use. Consider installing a virtual machine within Ubuntu and run your Windows apps in a VM.
I think this is a much better way to run Windows applications.
There are a few free VM players that work great.
Running Windows in a virtual machine is fine for most windows applications, providing they dont require 3D acceleration.
You can run MS Office perfectly well in a VM.
Good luck

---

### Post by stalkingwolf on 2008-12-23
Another option you might want to consider is  The Wubi install
provided with 8.04 and 8.10.  pretty simple actually even I did it
successfully.

Simply put your LiveCD in while in windows. A box will pop up. Select the
"Install inside widdows " choice ( or something similar). It will install
Ubuntu inside windows , just like any other windows package.  Choose your username,password, and the size you want the file, and Bobs your Uncle.

It can be removed in the same way you uninstall any other winprogram.

---

