---
title: "Raid 5 question"
date: 2009-08-27
forum: Server Platforms
---

### Post by whaase on 2009-08-27
I started my raid 5 with 4*1TB drives and I plan to grow it... A lot. I currently have room for 12 drives. I'm wondering though, is there a limit to the amount of drives on 1 raid? Or is there a guide line for the maximum amount?

2 question is, if a drive was to fail, how do you phisically know what drive it is? How do you match something like sdc1 to a "real" drive?

Thanks!

---

### Post by datarhythm on 2009-08-29
For RAID5, a good number is no more than 8 drives, but there is no reason why you can't go to 12 drives. Personally, I'd do 2x6 drive arrays and throw them all into the same LVM if you want one big volume. No limit that I'm aware of, just that when it rebuilds you have to keep in mind that it not only looks at how big the drives are but also how many there are. 

So the more drives you have, and the bigger in size they are, the longer it will take to rebuild and (with more drives and longer time within a single array) the more likelihood of a second drive failure while it rebuilds.

As for what drive belongs to what 'sd_', try this command (sda as an example):

```
hdparm -i /dev/sda | grep Serial
```

That should tell you make/model/serial that you can look physically at the drives.

---

### Post by insane_alien on 2009-08-29
with 12 you should probably consider RAID6 or multiple arrays as mentioned before.

---

### Post by whaase on 2009-08-29
Great info, thanks guys.

Walter

---

