---
title: "Getting the data off an ex-raid0 disk"
date: 2009-06-05
forum: Server Platforms
---

### Post by epix_ian on 2009-06-05
I've got a disk that used to be part of a raid1 array [the subject was a typo - it really is a raid1!] but I've got no other details of the array. It has got, not surprisingly, some very important data that I want back!

I assume its almost trivial, but I cant find out: how do I get the data  off this disk?

Thanks

Ian

---

### Post by epix_ian on 2009-06-05
It is indeed trivial - just specify the type you want when mounting from the command line.

Please ignore me!

Ian

---

### Post by vpsville on 2009-06-05
A RAID 1 disk has all the data in the array, its a mirror.  So it should work just like a single disk if its mounted that way, and the data should be intact. :)

---

