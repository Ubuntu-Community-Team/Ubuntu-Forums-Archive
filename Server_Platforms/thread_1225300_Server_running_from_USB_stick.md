---
title: "Server running from USB stick"
date: 2009-07-28
forum: Server Platforms
---

### Post by Dragonbite on 2009-07-28
I've had an idea which was in part prompted from a different thread.

The idea is this, I want to set up a server which will run from a USB stick (8GB), but stores all of the shared and LAMP (www and database) files onto a conventional hard drive.

What got me thinking was the idea that the hard disk may "spin down" when not in use and the USB stick should not take much electricity to keep going so this could reduce the electricity usage of the server box while the server remains ready for use immediately without having to do anything special (like turning it on before use, etc.).

Let's use sda1 as the usb stick to house the operating system aspect, and hda1 as the hard drive that houses the files. I was thinking that what I would place on the hard disk (hda1) in LVM partitions would be
[INDENT]/home
/var/www
/DATA (a custom directory with shared files)
Where do I find the MySQL database files for the LAMP?[/INDENT]

What else could or should I place on the hard disk, to keep from wearing out the USB stick too fast while leaving  the hard disk alone long enough for it to spin down?

Should I put the /var/log directory on the hard disk or will that be counter productive?  Should I look at a second USB pen drive (2 GB?) for just the /var/log files?

Right now, the server is a file and web server.  There is the possibility of adding Identity and network functions on it as well.

Since the flash disk is only 8 GB, I am thinking a cron job that dd's the entire flash drive into an ISO or something nightly so if the usb flash drive dies I can get another, use a Live CD and dd the ISO to the new USB drive and be back-in business very quickly.  Would this work?

Does this sound like it would work? What considerations should I keep in mind?  Any pitfalls that you can see?

---

### Post by Cowzor on 2009-07-28
If the delay between spinning up the drive and being able to use it are your main concern, why not get an internal SSD? the performance will be much better compared to USB and the ammount of time lost is negligable compared the difference in read and write speed between USB and SATA.

---

### Post by Jago6060 on 2009-07-28
I think its a great idea!  After reading this post, it actually sparked a conversation with my IT Director.  We came up with this setup following your idea.

-USB Drive with a live OS mounted
-Flash external hard drive for speed and lower energy consumption
-A bare bones box to house the processor and RAM
-Nightly backups of USB and external drive to both USB and external drive for redundancy purposes.

We figured this would be a good way to cut down on energy usage.  The hardware cost may outweigh the savings but you'd have to sit down and do the numbers.

---

### Post by Dragonbite on 2009-07-28
> **Cowzor said:**
> If the delay between spinning up the drive and being able to use it are your main concern, why not get an internal SSD? the performance will be much better compared to USB and the ammount of time lost is negligable compared the difference in read and write speed between USB and SATA.

USB flash drives are cheaper :) If this was a more professional location (small business, organization, etc.) then yes, I would go with an SSD instead. They are definitely more robust.

I don't think (or rather, I hope) the spinning up of the drive will slow things down much.

Since it is a home, the desktops spend a lot of time not on, and when they are being used it is only for a few hours at a time.  If the disk spins up when a computer is on and doesn't spin down until after they desktop is shut down it will still save hours of spinning time each day.

> **Jago6060 said:**
> I think its a great idea!  After reading this post, it actually sparked a conversation with my IT Director.  We came up with this setup following your idea.

-USB Drive with a live OS mounted
-Flash external hard drive for speed and lower energy consumption
-A bare bones box to house the processor and RAM
-Nightly backups of USB and external drive to both USB and external drive for redundancy purposes.

We figured this would be a good way to cut down on energy usage.  The hardware cost may outweigh the savings but you'd have to sit down and do the numbers.

By Live OS, do you mean like a LiveCD stored on a USB?  I don't want to have to reconfigure everything and run updates all over every time the system has to reboot or power outages.

Once installed, can also disconnect the CD and floppy disk drives. Not only for electricity purposes, but security (sort-of).

Even more ultimate would be using the LiveCD idea above but, if the system has enough ram, load the entire OS into RAM and then disconnect the USB drive!  I know with Darn Small Linux you have an option to load the entire LiveCD into RAM which is supposed to be incredibly fast!

---

### Post by Jago6060 on 2009-07-28
> 
Even more ultimate would be using the LiveCD idea above but, if the system has enough ram, load the entire OS into RAM and then disconnect the USB drive! I know with Darn Small Linux you have an option to load the entire LiveCD into RAM which is supposed to be incredibly fast!

I forgot all about that feature!  You're right, that would be a better alternative.  What if you had a machine with a huge amount of RAM?  Would that make things faster or just increase space for the OS once loaded into the RAM?

I've seen an HP desktop package at WalMart for $850 with a quadcore processor, 7GB DDR2 RAM, and a 750GB harddrive.  Plus its packaged with a 22" monitor.  You could wipe out Windows and load an OS into the RAM!(tell me if I'm off base with my assumptions)

---

### Post by Dragonbite on 2009-07-28
> **Jago6060 said:**
> I forgot all about that feature!  You're right, that would be a better alternative.  What if you had a machine with a huge amount of RAM?  Would that make things faster or just increase space for the OS once loaded into the RAM?

I've seen an HP desktop package at WalMart for $850 with a quadcore processor, 7GB DDR2 RAM, and a 750GB harddrive.  Plus its packaged with a 22" monitor.  You could wipe out Windows and load an OS into the RAM!(tell me if I'm off base with my assumptions)

Loading into Ram, I think, speeds up the read/write time because it's going to read into wha? RAM! And it's already there!  And what is it going to write from?.. RAM!

The down side is if you have a 700 MB Live CD loaded into RAM, then that means you are running 700 MB less Ram than the system has.  Although with 7 GB of RAM I hardly think you'll notice ;)

Wow.. a system with those stats, I would look at setting it up as an LTSP server and try getting some low-powered thin clients around the house (or netbooks/nettops)!

---

### Post by Jago6060 on 2009-07-28
That's actually something that we want to do at work.  I Haven't figured out yet exactly what kind of computer I need to act as a thin client though.  We have a bunch of Compaq Evo T20's but I can't see how to do anything with them to make them ubuntu thin clients.  They're set up to connect to a Citrix server.  They have no CD drive but there are USB ports.  Do these sound like candidates for ubuntu thin clients or should the thin clients be actual computers?

---

### Post by Dragonbite on 2009-07-28
> **Jago6060 said:**
> That's actually something that we want to do at work.  I Haven't figured out yet exactly what kind of computer I need to act as a thin client though.  We have a bunch of Compaq Evo T20's but I can't see how to do anything with them to make them ubuntu thin clients.  They're set up to connect to a Citrix server.  They have no CD drive but there are USB ports.  Do these sound like candidates for ubuntu thin clients or should the thin clients be actual computers?

If they can PXE boot then they should work.

I have some old Dell GX100's (P3s @ 700 MHz) which I was able to once I updated the BIOS. 

There are some sites on minimal thin client OSs which you can customize to connect to your server. I can't think where I saw that before but I'm pretty sure if you can set them to boot and connect to a windows terminal server (like what we have here at work) then you should be able to point them to a Linux Terminal Server.

---

### Post by Jago6060 on 2009-07-28
I think I understand.  With the thin clients I'm testing, you can set up a new connection but you have to select a type of emulation.  There isn't a linux selection.  I think I'm going to skip on these thin clients though, I just found out they only have 16MB of RAM.  I doubt that will run the programs we need.  You wouldn't happen to know off the top of your head if you can have a windows box boot and grab items from a linux box would you?  I guess what I mean is have a windows thin client that is served by a Linux thin client server?  Let me know if you need clarification, I think I was a bit cryptic in my phrasing.

---

### Post by Dragonbite on 2009-07-29
Here's are a few links with some information on Thin Clients :
[[COLOR="Blue"]https://help.ubuntu.com/community/ThinClientHowto[/COLOR]]("https://help.ubuntu.com/community/ThinClientHowto")

[[COLOR="Blue"]https://help.ubuntu.com/community/ThinClients[/COLOR]]("https://help.ubuntu.com/community/ThinClients")

[[COLOR="Blue"]https://help.ubuntu.com/community/UbuntuLTSP[/COLOR]]("https://help.ubuntu.com/community/UbuntuLTSP")

If  the system can PXE boot, then you should be able to set it up so that it boots to the network and doesn't even require a hard drive in the thin client.

There is also this link [[COLOR="Blue"]This page describes the steps needed to setup a windows DHCP server in order to run the LTSP Ubuntu[/COLOR]]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP")

I think, though, that you are refering to a thin client that currently boots to a Windows terminal server and wanting it to boot to a Linux one. I don't know if one of the fore-mentioned links have anything on them.

This may be worth posting as a new thread in the server section. I know there are a few people who are more knowledgeable about LTSP than I am who may be able to answer your question better.

---

### Post by shubham on 2009-09-15
hi buddy ! you see even i had a similar brainstorm of running a whole server  on a pen drive but to be honest i  don't have all the technical skills and the basic ubuntu knowledge(ubuntu server to be precise) . well actually i dont know much about servers ! i have a core2 duo , 1gb ram , 160 gb sata hard disk with ubuntu and win xp installed side by side . so could you pls help me out with how to basicly make a pendrive into the server os (or what ever it exactly is !) .i know its a big favour , i am asking you ,  so pls help me . thanks

---

### Post by Dragonbite on 2009-09-15
My initial thoughts are when going through the partition setup, make sure you select /dev/sda1 or whatever the USB drive will be listed as.

Since I do not have any Sata drives, I find my hard drives at /dev/hda1 and so the USB should be "sda" instead of "hda".  A little bit of hunting and pecking should help me determine if "1" is the CD-Rom or not.

---

### Post by Jago6060 on 2009-09-15
> **Dragonbite said:**
> My initial thoughts are when going through the partition setup, make sure you select /dev/sda1 or whatever the USB drive will be listed as.

Since I do not have any Sata drives, I find my hard drives at /dev/hda1 and so the USB should be "sda" instead of "hda".  A little bit of hunting and pecking should help me determine if "1" is the CD-Rom or not.


I wonder if ubuntu records somewhere what kind of cpu/ram/etc. it was installed with, and would this cause an issue if moving the filesystem around to different computers with different specs?

---

