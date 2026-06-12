---
title: "Browsing Mounted Partition"
date: 2009-05-29
forum: System76 Support
---

### Post by DieUbunt on 2009-05-29
Hi,

Could somebody tell me where find out all mounted partition by terminal?
I need to browsing all stuff in mounted partitions by terminal.
Thanks;) in advance

---

### Post by madverb on 2009-05-29
ls /media

---

### Post by DieUbunt on 2009-05-29
> **madverb said:**
> ls /media
I mean internal mounted partition
In /media I find only external mass storage

---

### Post by madverb on 2009-05-29
Do you mean the root partition?

ls /

---

### Post by DieUbunt on 2009-05-29
> **madverb said:**
> Do you mean the root partition?

ls /
Yes
I would like to know where could I find out all my partitions on board?
As well as in /media I find all stuff about external mass storage where
could I find all data about all my internal partitions browsing by terminal
starting from root /?
thanks

---

### Post by madverb on 2009-05-29
cat /etc/mtab will show you where all your partitions are mounted to.

---

### Post by DieUbunt on 2009-05-29
> **madverb said:**
> cat /etc/mtab will show you where all your partitions are mounted to.
Thanks a lot

---

