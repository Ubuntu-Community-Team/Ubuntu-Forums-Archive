---
title: "Anyone have a 1TB Hitachi SATA drive? How much usable space after ext3 format?"
date: 2007-08-12
forum: The Cafe
---

### Post by MetalMusicAddict on 2007-08-12
Like the title says. I'm buying one tomorrow and I can't find a answer through Google. :-k


EDIT: Answer 870GB. Kinda disappointing. :(

---

### Post by tigerpants on 2007-08-12
Thatsa spicy meatballs. You must have alot of pron to archive :)

---

### Post by teet on 2007-08-12
My guess would be 976.5625 GB

I could be WAY off though.  I just tried to figure out how a 10 gb drive would be reported and then multiplied that answer by 100.

-teet

---

### Post by hardyn on 2007-08-12
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

1,000GB * 1,000,000,000 / 1,073,741,824 = 931GB

---

### Post by Steveway on 2007-08-12
And don't forget the size that ext3 takes for itself.
That were 5 percent or so, dunno.

---

### Post by yatt on 2007-08-12
You should have about 930GiB of space.

---

### Post by MetalMusicAddict on 2007-09-14
Answer: 870GB after a EXT3 format. Kinda disappointing. :( [PIC]("http://img483.imageshack.us/img483/3348/dscf4568smallti5.jpg")

---

### Post by sr20ve on 2007-09-14
I was thinking 953.7 GB.

---

### Post by Dimitriid on 2007-09-14
[QUOTE=MetalMusicAddict;3365834]Answer: 870GB after a EXT3 format. Kinda disappointing. :( [PIC]("http://img483.imageshack.us/img483/3348/dscf4568smallti5.jpg")

That does seems excessive for just formatting it, maybe something is wrong?

---

### Post by Officer Dibble on 2007-09-14
> **MetalMusicAddict said:**
> Like the title says. I'm buying one tomorrow and I can't find a answer through Google. :-k


EDIT: Answer 870GB. Kinda disappointing. :(

A BIOS upgrade may help here... what's yer motherboard?

---

### Post by MetalMusicAddict on 2007-09-14
Nope. Everything's very new and up to date. ;) gParted reports it as a 930GB drive and so does Partition Magic. [PIC]("http://img389.imageshack.us/img389/5775/gpfd8.png") After the EXT3 format the partition table looks to use 60BG because Nautilus says 870GB of space available. [PIC]("http://img443.imageshack.us/img443/5566/38801846mq2.png")

A 1TB drive might be *technically* true but it's mostly marketing for now.

---

### Post by southernman on 2007-09-14
I am sure you know this already, but just to put it out there in case someone else isn't. You can reset the amount of reserved space by "Modifying reserved space"
> 
sudo tune2fs -m 1 /dev/xdxN

Changes the reserved space from 5% to 1% and in the case of a TB drive, that would net you 40.96GB +/-... if my calculations are right that is! ;) (Basing on 1024GB)

You can also do this when doing a fresh install by manually setting the partition table.

**[edited]**
Basing on the number gparted reports of 930GB, the added usuable space should increase by 37.2GB.

---

### Post by MetalMusicAddict on 2007-09-14
southernman. Can you do this on drives with existing data?

---

### Post by southernman on 2007-09-14
I've done it on my main hard drive... all partitions. Didn't hurt a thing, in my case. YMMV

It should be safe, it's not effecting your data at all.

---

### Post by d0ida on 2010-08-04
I just got a 1TB Toshiba Canvio portable hard drive and changed the default format from NTFS to ext4 and was horrified to see I lost over 40GB of space.  Then I found this thread and tried 
 
sudo tune2fs -m 1 /dev/sdb1

and regained all but 9.5Gb!  I am so glad I learned about this here!  I was afraid to set the reserved space to 0% because a poster on another forum mentioned it gave him or her problems.  

Does anyone know if taking away the reserved space on an external portable hard drive makes a difference?  I am only using it for data storage.

---

