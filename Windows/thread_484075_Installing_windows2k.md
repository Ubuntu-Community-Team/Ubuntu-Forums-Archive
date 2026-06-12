---
title: "Installing windows2k"
date: 2007-06-25
forum: Windows
---

### Post by nominal on 2007-06-25
I have no idea what's going on, but maybe you guys do.

I have ubuntu installed, but today I decided to completely wipe the HDD and install windows2k. Naturally I turned on the computer ejected the cd tray and popped in my windows2k cd. Nothing happened so I did a hard reset and turned on the computer with the cd still inside. Still, linux boots up as it always does. 

I wouldn't mind partitioning the HDD if i had to, but how can I install windows2k?

---

### Post by cogadh on 2007-06-25
Change your BIOS settings to allow booting from the CD.

---

### Post by nominal on 2007-06-25
its an HP...i can't do much besides push escape-- from there nothing helps
im running xubuntu, if that changes anything

should i login in and change something?

---

### Post by buuntuu! on 2007-06-25
there MUST be a way to enter BIOS! hitting F8 repeatedly while booting up does the trick for most systems, but F2 may also be an option... where do you get by esc?
it definitely has nothing to do with your xubuntusettings

---

### Post by w4ett on 2007-06-25
the keys for entering the bios setup on an HP are:  

F1, OR  F2            (Laptop, ESC)

then select your boot priority to cd as your primary boot device.

---

### Post by nominal on 2007-06-25
At the bios there is a subsection with BOOT

I went there, changed the order, so the cd option comes first. I have two cd drives, but there is only 1 boot from cd option. I did this about 4 times, still it never booted from the cd.

---

### Post by buuntuu! on 2007-06-25
is the cd ok? are the cd-drives working? try in another computer, if possible... i know this is not much of a help, but nothing else comes to my mind... sorry

---

### Post by nominal on 2007-06-25
everything works...it's ok, i've completely given up on the computer. it will remain a xubuntu computer forever.

---

### Post by DarkN00b on 2007-06-25
On my HP lappy, I have to hit F10 as soon as text shows up on the screen to enter BIOS.

---

### Post by dca on 2007-06-25
[DEL] or [F1] to enter BIOS.  Keep tapping both of those until the BIOS menu screen comes up, look for boot config or boot settings or boot blah blah blah...  Make sure the 1st boot device is set to your CD drive...  Or, boot up Ubuntu and slap the CD in the drive and make sure in the BOOTDISK directory there's stuff in it:  CDBOOT yada yada...

---

### Post by smoker on 2007-06-25
> **nominal said:**
> At the bios there is a subsection with BOOT

I went there, changed the order, so the cd option comes first. I have two cd drives, but there is only 1 boot from cd option. I did this about 4 times, still it never booted from the cd.

did you format the drive with fat32 or ntfs, windows won't recognize the drive, to install to, if it can't see it?

---

### Post by DarkN00b on 2007-06-26
One question that hasn't been asked.. Is the CD bootable? The last time I installed W2K I had to use a boot floppy.

---

### Post by nominal on 2007-06-26
Yeah there is a boot folder and all that on the CD...the computer does have a floppy drive, so that seems interesting. Where did you get the boot floppy from? Sounds like a viable idea that im willing to try.

*Edit*

I'm going to try this site [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

---

### Post by nominal on 2007-06-26
Problem solved!

I set up the 4 boot discs. IT failed the first time, but worked the second. It's working on the second disc right now, but everything should be going swell. Thanks to everyone who posted and tried to fix my problem. I guess HP doesn't like CD drives, and prefers floppies...

---

### Post by DarkN00b on 2007-06-26
> **nominal said:**
> Yeah there is a boot folder and all that on the CD...the computer does have a floppy drive, so that seems interesting. Where did you get the boot floppy from? Sounds like a viable idea that im willing to try.

*Edit*

I'm going to try this site [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Heh, you beat me to it. I spent some time this morning reading through NAT firewall logs. I was port scanned during the night from some computer in China (219.148.119.6).

---

