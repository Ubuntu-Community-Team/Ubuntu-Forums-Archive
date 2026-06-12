---
title: "new hard drive"
date: 2009-09-21
forum: Server Platforms
---

### Post by rmb938 on 2009-09-21
I am switching my main hard drive 120GB to a new faster one of 200GB. Is there a way to transfer everything including the ubuntu 9.04 OS onto the new hard drive?

---

### Post by steffmeister on 2009-09-21
you can make an image of your current hard drive and write it on the new. familiar with clonezilla? i did that last month.

---

### Post by rmb938 on 2009-09-21
ok I will look into that

---

### Post by hessiess on 2009-09-21
Mounting both drives on a live cd and using "cp -a" to move the data from one to the other would also work.

---

### Post by openfly on 2009-09-21
Better to use rsync to be honest, but you'll want to avoid running it on /dev and /proc.

---

### Post by trundlenut on 2009-09-21
I would say use clonezilla, it's quite straightforward to use.

---

