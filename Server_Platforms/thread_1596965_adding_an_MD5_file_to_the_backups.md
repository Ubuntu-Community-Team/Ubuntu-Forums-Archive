---
title: "adding an MD5 file to the backups"
date: 2010-10-14
forum: Server Platforms
---

### Post by Vegan on 2010-10-14
I am aware of MD5SUMMER and I was wondering if I can use that to add another check to my backups.

I also know of PAR2 and that is another idea that I wanted to explore.

---

### Post by jbrown96 on 2010-10-14
Of course you can, but you have to remember that the MD5 sum can't be inside the backup archive...

---

### Post by Vegan on 2010-10-15
I decided to use par2 so that if any of the backups become damaged, they can be recovered.

par2 can detect and repair errors

---

### Post by CharlesA on 2010-10-15
What did you use to create the par2 archive?

---

### Post by Vegan on 2010-10-15
```
sudo apt-get install par2
```

---

### Post by CharlesA on 2010-10-16
Thanks. I poked around and mostly saw stuff mentioning "pypar2."

---

### Post by Vegan on 2010-10-16
Removable disks are a tad on the dodgy side, par2 can help.

Tape may be obsolete in the face of USB hard disks and walls of servers, but what does a consumer level shop have available?

I have a 160 GB USB disk and more recently I now have a 320 GB USB disk.

Last time I looked, a LTO5 tape drive was $1999 plus taxes and shipping. Tapes for the drive are $120 a pop. LTO5 is 1.5TB native capacity, 190 MB per second with hardware compression available.

USB case for a HD is 99 cents, SAS controller is $200 or so.

And I have not yet mentioned disk cloning.
:guitar:

---

