---
title: "Resurrecting a beige box c. 1996"
date: 2005-12-20
forum: The Cafe
---

### Post by agds on 2005-12-20
I found an old, no-name computer sitting in the back room of the family business.  I'm hoping to resurrect it and install some flavor of Linux on it.  I haven't been able to discover much about it, apart from the fact that it has an Award Modular BIOS v4.51PG and a Pentium-S @ 100MHz.  It appears to have 16MB of RAM.  The BIOS suggests it first ran on October 18, 1996.  When I boot it, I get the following messages:
```
CMOS checksum error
CMOS battery failed
```
If I press F1, the next screen gets as far as "Updating ESCD... Success" before displaying:
```
Disk I/O error
Replace the disk, and press any key
```
It has some other apparently minor problems.  For instance, the processor fan needs to be reattached to the processor.  The main fan sounds like death when it first starts up after being idle for a while.  Mostly I'd like to know if it can be restored to working order--and if it has the necessary specs to run GUI-less Ubuntu or another distro.  Your thoughts?

---

### Post by John.Michael.Kane on 2005-12-20
sounds like it would make a good firewall box, stick two nic's in and your good to go..

---

### Post by Rackerz on 2005-12-20
100MHz? Now i haven't heard that in a while ..

---

### Post by xequence on 2005-12-20
Ive got a 75 mhz pentium with 16 MB ram in the basement :P

---

### Post by scole on 2005-12-20
Beat cha i have a 55mhz intel overdrive processor from the early 90s that was in a computer with 8mb of ram.

---

### Post by Iandefor on 2005-12-20
Those problems all look pretty fixable. As for a distro: [Damn Small Linux]("http://www.ubuntuforums.org/www.damnsmalllinux.org") or perhaps an Ubuntu server install.

---

### Post by agds on 2005-12-21
[QUOTE=scole]Beat cha i have a 55mhz intel overdrive processor from the early 90s that was in a computer with 8mb of ram.[/QUOTE]
Good Lord.  What do you use it for?

---

### Post by agds on 2005-12-21
[QUOTE=Iandefor]Those problems all look pretty fixable. As for a distro: [Damn Small Linux]("http://www.ubuntuforums.org/www.damnsmalllinux.org") or perhaps an Ubuntu server install.[/QUOTE]
Do you happen to know what I should do to fix them?

---

### Post by darth_vector on 2005-12-21
you can get a new cmos battery for about $3. that should fix your fist problem. if the fans are stuffed you can get very cheap replacements from your nearest computer shop.

i dont know about the disk error, but it sounds like the disk is stuffed. try putting in a disk you know is working. if you get the same error then its a motherboard fault or crappy ide cable.

---

### Post by jerrykenny on 2006-06-21
Echo Darths suggestion re the battery,

The disk error may simply be due to the boot order being wrong, ie its trying to read from an empty floppy bay ?

Be a good idea to check the ram using the facility in the install cd . . . . bad ram can waste a lot of time and be very frustrating. just type <memtest> at the boot prompt.

Any debian or ubuntu "server" installation will be fairly light . . . 

Good Luck

---

### Post by Sushi on 2006-06-21
While it might be tempting to "resurrect" such a machine, you need to figure out what you want to do with it. If you have the money, it might be more sensible to get a Mini-ITX-machine (for example) instead. Not only would the performance be a lot better, it would also be smaller, quieter, more capable and it would consume less power.

If you don't have the money... Well, then you need to ask yourself two questions:

a) Would this machine be useful?

b) Could I live with large, slow and humming box?

If the answer to both of those is "yes", then go for it!

I had an ancient machine (IIRC 120MHZ Pentium with 32MB of RAM), that I used for various things. But then I decided that I didn't really need it, it was too slow and the noise was driving me crazy.

---

### Post by Johnsie on 2006-06-21
I have an Amstard 286 with windows 3.1 and a 100mb hard disk... I dont wanna put Linux on it 'cos I havent changed any setting on it for about 10 years  and it still works :-)

---

### Post by renzokuken on 2006-06-21
lol.....i still have an IBM Aptiva 486, not a Pentium in sight.

i remember we got it for about £2000 with Windows 3.1. About a month later the first Pentiums appeared and i was really jealous

---

### Post by agds on 2006-06-21
[QUOTE=Sushi]While it might be tempting to "resurrect" such a machine, you need to figure out what you want to do with it. If you have the money, it might be more sensible to get a Mini-ITX-machine (for example) instead. Not only would the performance be a lot better, it would also be smaller, quieter, more capable and it would consume less power.

If you don't have the money... Well, then you need to ask yourself two questions:

a) Would this machine be useful?

b) Could I live with large, slow and humming box?

If the answer to both of those is "yes", then go for it!

I had an ancient machine (IIRC 120MHZ Pentium with 32MB of RAM), that I used for various things. But then I decided that I didn't really need it, it was too slow and the noise was driving me crazy.[/QUOTE]

Yeah, I ultimately decided it wasn't worth the trouble.  There seemed to be too many things wrong with the hardware, and I don't have enough days off from work to figure out what they are.  It's a shame because I really like the case; it's pleasantly compact for something of its vintage.  Maybe I can find a newer mobo and HDD that would fit in there…

Thanks, everyone, for your suggestions!

---

### Post by K.Mandla on 2006-09-17
I'm working on a 120Mhz machine now, trying to put the Drake on it.

I had to put a little extra memory in it, because the installer craps out with less than 36Mb (I had 32Mb; went up to 48Mb). And I had to put a different CDROM in it because the old one couldn't read 700Mb CDs. So far, setting up the hardware took 4 hours and installation is taking 2 hours. 

This'll be fun. :biggrin:

---

