---
title: "Daily + nVidia borked"
date: 2012-01-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-01-23
I know I saw some discussion regarding this recently but can't find it now :(

Anyway I'd been asked to try Precise amd64 a while back by the developer of the Boot Info Script but I never could get an install to complete and boot to a usable DE.

Now I'm guessing this is the last week before Alpha 2 iso-testing so I decided to have a fresh look. With my "GeForce 7025 / nForce 630a" things are a nightmare after beginning the install:

[ATTACH]211332[/ATTACH]

I forgot to turn the flash off :(

Previously I'd just get stuck in a low graphics prompt but nothing I'd do would get me into a working DE. But I could upgrade from Oneiric and things were largely OK.

Does any of this seem familiar to anyone?

---

### Post by ventrical on 2012-01-23
Yes... familiar on Acer Extensa AMD 64Athalon2X with ATI Radeon 1250.  There is a regression for the graphics cards (at least mine) but Precise works great on 32bit mode on that machine.

---

### Post by kansasnoob on 2012-01-23
> **ventrical said:**
> Yes... familiar on Acer Extensa AMD 64Athalon2X with ATI Radeon 1250.  There is a regression for the graphics cards (at least mine) but Precise works great on 32bit mode on that machine.

That actually was i386. I'm also looking into a Brasero bug.

---

### Post by kansasnoob on 2012-01-23
Maybe the whole 12/23 daily is borked :(

I'm just trying the same disc on my Intel box and it almost seems to freeze, but then continues. I'll post back when the installation completes.

---

### Post by Quackers on 2012-01-23
Did you try the nomodeset boot option?

---

### Post by kansasnoob on 2012-01-23
> **Quackers said:**
> Did you try the nomodeset boot option?

Not yet. I'm currently trying the same iso with my Intel hardware. There was a looooooooooooooooooooong pause after selecting to DL updates and third party software, so long I thought it was frozen, but then the installation began.

Just BTW I did check the md5sum and disc integrity, I'm strict about that :D

---

### Post by kansasnoob on 2012-01-23
Well, installation on that Intel box took nearly an hour but it was successful.

But the boot time is about 3 minutes :(

I'm guessing we need to just be patient until iso-testing begins, presumably about January 30th or 31st :)

---

### Post by Quackers on 2012-01-23
> **kansasnoob said:**
> Not yet. I'm currently trying the same iso with my Intel hardware. There was a looooooooooooooooooooong pause after selecting to DL updates and third party software, so long I thought it was frozen, but then the installation began.

Just BTW I did check the md5sum and disc integrity, I'm strict about that :D

I asked because with all of the kernels I've used in the last couple of years on this hardware, I got a screen similar to yours with just one of them. Using the nomodeset option allowed the installation to proceed. 
I have no idea why one kernel out of 40 or 50 would require it, but it did :-)

EDIT
boot times do seem to have increased just lately.

---

### Post by VMC on 2012-01-23
Mines borked for a different reason. Very long boot. Usually 20 seconds. With *NVIDIA-Linux-x86_64-290.run* installed it's now 1 minute.

---

