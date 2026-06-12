---
title: "W95 fat32 (lba)"
date: 2013-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by abdorefky on 2013-05-03
what is W95 FAT32 (LBA) partition system ? 
[http://imageshack.us/photo/my-images/90/screenshotat20130415135.png/](http://imageshack.us/photo/my-images/90/screenshotat20130415135.png/)

ty

---

### Post by snowpine on 2013-05-03
Probably a hidden factory-installed restore partition from Dell.
You can browse to it with file manager and see what's on it. :)

---

### Post by abdorefky on 2013-05-03
how to browse it while its hidden ? and how did u know that its hidden ? :)

---

### Post by abdorefky on 2013-05-04
here is my strange partitions . as u can see gparted detected sda 1 and 2 as fat32 
but in terminal it shows another differant names ! 
what is the differant between those fats 

[IMG]http://imageshack.us/a/img90/8581/screenshotat20130415135.png[/IMG]

---

### Post by snowpine on 2013-05-04
These are small partitions installed at the factory by Dell for restore/utility purposes. Nothing to worry about since you have 286gb free space in your Linux partition! :)

---

### Post by abdorefky on 2013-05-07
how can i mount this hidden partition ?

---

### Post by CharlesA on 2013-05-07
> **snowpine said:**
> These are small partitions installed at the factory by Dell for restore/utility purposes. Nothing to worry about since you have 286gb free space in your Linux partition! :)

Spot on.

> **abdorefky said:**
> how can i mount this hidden partition ?

The same way you mount anything else. You shouldn't need to, though as those partitions are used by the built-in recovery mode.

---

### Post by abdorefky on 2013-05-22
i have managed to open the partition by luck when i was testing something on ubuntu 13.04 live cd , 
but i would like to know about these questions :
1: what is the LBA ( looks like a processor flag as gparted say )
2: is there differance between ( w95 fat32) and (fat32) 
ty

---

