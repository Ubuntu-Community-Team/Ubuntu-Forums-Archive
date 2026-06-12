---
title: "7x500 hd RAID 5 as 2.5tb???"
date: 2010-06-14
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-06-14
Ok so I have this RAID 5 array.
7 hds(500 each)
I made a new RAID 5 array in disk utility....
It says 3tb, which is perfectly fine.

Then when I go inside, I only have 2.5tb of usable space? Why is that? I should be getting 3tb of space, not 2.5tb

[img]http://img29.imageshack.us/img29/2926/watwu.jpg[/img]

---

### Post by JigglyWiggly_ on 2010-06-14
Actually I just noticed, 
[img]http://img535.imageshack.us/img535/9816/capturezw.jpg[/img]

I wonder what's taking that space...

---

### Post by The Real Dave on 2010-06-14
It could be the space reserved by the system. By defualt, the system reserves 5% of drive space so that if you fill the drive, it can still write to it, and not crash. 

It's only necessary for the system drives / and the like. If this raid array is only for storing data, your file dump like, you can safely lower the reserved space. You can probably put it to 0%, but to be safe, I always leave 1%

```
sudo tune2fs -m 1 /dev/md0
```

The above will lower the reserved space to 1% on md0. Back sure you backup any data on there, just in case.

---

### Post by benderisgreat on 2010-06-14
You are in fact getting the total capacity of the drives. The difference you see is due to the unit of space being used by the two respective programs i.e. gigabytes vs gibibytes. Manufacturers of drives specify capacity in gigabytes which are 10^9 = 1000.000.000 while memory sticks are sold in gibibytes which are 2^30=1073741824 bytes.
3TB is 3000.000.000.000 bytes while the properties window shows 2.7 TiB. 3 * 10^12 / 2^40 is about 2.7.

---

