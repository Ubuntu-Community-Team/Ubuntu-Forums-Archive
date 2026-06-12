---
title: "[SOLVED] Hard Drive Size for Virtual box"
date: 2008-05-15
forum: Virtualisation
---

### Post by SILLAT on 2008-05-15
hey yall, i need a little expert advice from this forum
i'm planing to run windows xp in virtual box on my ubuntu hardy 8.04 pc .. my hard drive is 40 gigs,768mb ddr,2ghz cpu
How much hard drive space do u think i should allocate to Win XP virtual machine in virtual box and where on my hard drive should i 
place the image file for the virtual disk ?

---

### Post by Inxsible on 2008-05-15
Depending on what you want to do with the XP, I would say about 15 GB.

If you are planning on installing heavy apps in XP like huge games and other software, you may need more.

---

### Post by SILLAT on 2008-05-15
thanks inxsible but i'm not planing on running any intensive games or any game for tht matter in xp i jus want it for mostly school or business use applications, mostly for M$ office (i use O O 4myself but i need m$ for work purpose)

---

### Post by HotShotDJ on 2008-05-15
> **SILLAT said:**
> How much hard drive space do u think i should allocate to Win XP virtual machine in virtual box and where on my hard drive should i place the image file for the virtual disk ?The location of the image is typically /home/USER/.VirtualBox/VDI -- this is the default location used by VirtualBox.  Unless you want to place the virtual disk on an external drive, there is really no reason to change this.

For Windows 2000, I used a 10 gig virtual drive, which was plenty.  I now have a Vista Home Premium installation for which I created a 20 gig virtual drive -- the VDI is currently at 12.6 gig.  Since I've never worked with Windows XP, I really don't know what it requires.  Nor do I know what you plan on doing with your virtual OS.  Since you've only got a 40 Gig harddrive to begin with, you might go with 10 gigs for the virtual drive (I wouldn't try anything smaller) and see how that works for you.  You can always reinstall windows onto a larger virtual drive later.

---

### Post by Inxsible on 2008-05-15
> **SILLAT said:**
> thanks inxsible but i'm not planing on running any intensive games or any game for tht matter in xp i jus want it for mostly school or business use applications, mostly for M$ office (i use O O 4myself but i need m$ for work purpose)Then 10-15 Gigs would be quite sufficient.

---

### Post by BlueSkyNIS on 2008-05-15
I use 10Gb and it's plenty enough :)

---

### Post by SILLAT on 2008-05-15
where is  /home/USER/.VirtualBox/VDI -- default location used by VirtualBox located? is it in your /home directory or /usr directory
i was planning on using gparted to make a new partition for win xp installation is that a good idea..

---

### Post by HotShotDJ on 2008-05-15
> **SILLAT said:**
> where is  /home/USER/.VirtualBox/VDI -- default location used by VirtualBox located? is it in your /home directory or /usr directory
i was planning on using gparted to make a new partition for win xp installation is that a good idea..There is no need for a separate partition for WinXP unless you are dual-booting, which is not what you will be doing.  The VDI (this is the file that is your virtual disk) is located right where I said it is located.  Just replace USER with your own user name and that is the path. (REMEMBER:  /usr does NOT stand for "user".  It stands for "Unix System Resources" -- Files here are "read-only" for normal users and would not be an appropriate place for any files that require "read-write" access by users, such as a VirtualBox virtual filesystem).

---

### Post by jen1963 on 2008-05-15
When you set the Virtual Disk up use the Dynamically Expanding Image instead of a fixed size and set the starting size at 10 gig.
With the Dynamic option set, the drive should expand as needs then dictate...

---

### Post by HotShotDJ on 2008-05-15
> **jen1963 said:**
> When you set the Virtual Disk up use the Dynamically Expanding Image instead of a fixed size and set the starting size at 10 gig.
With the Dynamic option set, the drive should expand as needs then dictate...No, no, no.  With the Dynamically Expanding Image, the size you set is not the starting size.  It is the MAXIMUM size.  But the actual VDI will only be as large as required to hold the files currently stored on it.  It will not expand past the size you used to create it, and the maximum size cannot be increased once the VDI has been created.

---

