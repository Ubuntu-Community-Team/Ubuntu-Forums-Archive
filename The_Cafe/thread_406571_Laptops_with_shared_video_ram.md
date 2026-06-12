---
title: "Laptops with shared video ram"
date: 2007-04-11
forum: The Cafe
---

### Post by Xenogis on 2007-04-11
I have been trying to increase my laptops performance (it is a Toshiba Satellite a75-s209) when I noticed something. The system monitor shows me as having 376 MB of RAM even though my laptop has a sticker on it that says 512 MB. The video card shares the ram but only uses (or is only supposed to use) 64 MB. Memtest86 shows 383 MB of ram...


Anyway, does anyone else here have a laptop that shares the system ram with the video card? If you do can you tell me what the system monitor reports and how much ram everything is supposed to use?

---

### Post by siimo on 2007-04-11
Your video card seems to be using 128mb.  Go into the BIOS it might be configurable and you may be able to reduce it to 64 or less.

---

### Post by koshatnik on 2007-04-11
For an Intel based machine, del at bootup to enter bios, go to advanced tab and then go to the option marked "DVMNT Maximum Memory"

Change it from 128 mb to 64mb

save and exit.

---

