---
title: "Ubuntu Server 12.04 reboots on install"
date: 2013-02-22
forum: Server Platforms
---

### Post by garethoftullamore on 2013-02-22
Hello,
I'm new to ubuntu but know my way around Windows, OS X, and have built several computers.  I just bought a pc to turn into a home server and thought I'd try Ubuntu server.

I have downloaded the Ubuntu Server 12.04.2 LTS i386 ISO file, confirmed the md5 hash, and burned it to a disk.  With the disk in the drive and my computer set to boot from CD first, my system will POST and run BIOS, and then start booting to the CD.  I get to the "choose your language" screen and select "English" and press enter.  This takes me to the disk menu with the different options: Install Ubuntu, check RAM, repair, etc.  With "Install Ubuntu Server" selected, I press enter.  The CD drive spins up and about 10-15 seconds later, the screen goes black and my computer reboots and the BIOS splash screen comes up again.

I've tried reburning the ISO, I tried choosing combinations of the additional options, I even tried installing 12.04 desktop and downloaded and burned the server ISO through Ubuntu, but it still reboots after I hit enter to "Install Ubuntu Server".

I'm running a Pentium 4 3.06Ghz with hyperthreading, 1GB RAM, 120GB SATA HDD, integrated video.

Thank you in advance for your help!

---

### Post by volkswagner on 2013-02-23
I would try burning the desktop version and see if you can boot into live mode.

What is the video chip on the MOBO?

Also Test the RAM.

---

### Post by garethoftullamore on 2013-02-23
I can run and install desktop via live CD just fine.

My graphics are 128MB Integrated Intel Graphics Media Accelerator 950.

I'll test the RAM again, but the first time it checked out fine.

---

### Post by varunendra on 2013-02-23
Have you verified the integrity of downloaded iso?
How to MD5Sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, if you [download Ubuntu]("http://www.ubuntu.com/download/desktop/alternative-downloads") iso via torrent, its integrity is guaranteed as hash checking is part of torrent protocol.

---

### Post by d4m1r on 2013-02-25
Does your CPU support PAE? 12.04 requires it by default.

My suggestion is to download 11.10 server, see if it installs (most likely will), and then just update to 12.04 over your network.

---

