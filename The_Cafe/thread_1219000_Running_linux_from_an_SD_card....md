---
title: "Running linux from an SD card..."
date: 2009-07-21
forum: The Cafe
---

### Post by stwschool on 2009-07-21
Is it worthwhile? Will I get a speed boost from doing so? (obviously storing my /home folder on the hard drive - the card reader is an internal unit so presumably not bound by USB2 speed limitations).

---

### Post by philcamlin on 2009-07-21
i would think it would be extremely slow

my sd card in my camera was so slow it took 10 sec to save a picture

now imagine loading ubuntu :(

---

### Post by Whiffle on 2009-07-21
You won't get any performance boost, SD cards are slower reading and writing than hard drives.  Even the fastest SD Cards (Class 6), only read at 6 MB/s.  Hard drives read at 50MB/s or better (usually better).

---

### Post by tjalling on 2009-07-21
Well, even as an internal unit it is probably connected using USB. You should check that first.

Regards,
Tjalling

---

### Post by stwschool on 2009-07-21
Crap. No worries. I just thought I'd check it out as an idea. Cheers guys :)

---

### Post by MikeTheC on 2009-07-21
Well, I've had the thought cross my mind to try it with my new MacBook Pro; however, I already have a nice enough system that I'm running Ubuntu on, so what benefit would there actually be to me?

---

### Post by JohnFH on 2009-07-21
For easy comparison of drive speeds, insert the SD card, find out the device name (/dev/sd ...), then use hdparm to test the speed of it:

```

hdparm -t /dev/sda

```

This will test the read speed.  Note that the result is highly dependent on the quality of the card reader and the card itself.

I've installed Ubuntu on a 4Gb SDHC card in my eeepc, and it's slightly slower than a normal hard disk, but still very usable.  The main advantages are not speed, but it uses much less power than normal HDDs and is completely silent.

---

