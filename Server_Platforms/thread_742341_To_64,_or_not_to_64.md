---
title: "To 64, or not to 64"
date: 2008-04-01
forum: Server Platforms
---

### Post by Deathrend on 2008-04-01
Ok, where to start.  I currently have three systems running Ubuntu server. (two 7.10's, one 8.04).  I also have two 2003 server PC's, one of which running VMWare server. 

 I'm wanting to turn the Host OS (2003 server) into a guest (Using VMWare Converter) then drop the system, and rebuild it using Ubuntu 8.04.

My plan is to then use this has a VMServer platform over2003 server.  I however don't want to lose this specific OS, because it hosts my RADIUS for Wireless/Cisco SSL VPN (Such a pain to set up..).

I'm trying to figure out what would be the best road to follow, as my PC isn't the best suited for 64bit OS's, however it WILL run them.

The PC I'm wanting to convert, is as follows:

Windows 2003 Server Enterprise Edition R2
Intel P4 3.2 Ghz (LGA775, HT)
4 GB GSkill DDR SDRAM
2x120Gb (Mirrored Raid) ATA133 HD's,  (ICH6 Raid I think)
4x1TB 3.0 Gb/s (3TB Raid 5) SATA HD's on LSI Logic Raid PCI-Express Raid card.

Currently, I used the system as a secondary backup, for an OpenFiler san (4TB/Raid-50) so other than the OS, I have

Plans for Usage:

-This will be for storage, files ranging from 5Mb, to 5Gb. (For the most part no small files).  As such, I will have a rather extensive file system (The rest of why I'm wanting to bounce the windows side of things).

-VMWare server: I would like to use 1.0.5 (I really dislike the web interface only approach of the Server 2 Beta), however it doesn't come packaged for 64bit OS's.

This thing really won't be used for any major applications, I have an old Proliant ML370 that I use for most of my applications (Which screams with Ubuntu 8.04).

Mind you, this is for home use, so I'm not really on a time crunch, I just enjoy breaking things to fix them at a later date..

To wrap things up, I just want to know if 64bit is the way to go, or if I can eve use it like I'm wanting to.  I've only spent a little time with VMWare server, so I'm not exactly sure of what it can, and can't do. (I spend most of my time working with ESX, hence the Client attachment.)

If all else fails, I have NT4 sitting on my desk!.. Don't ask..

---

### Post by Deathrend on 2008-04-02
After playing for a few hours, I have the PC down to a 6 gig (down from 32 gig)virtual drive, now it's just a matter of what to install.

I've personally never used a 64bit OS, so that has me iffy on the subject as well.

---

