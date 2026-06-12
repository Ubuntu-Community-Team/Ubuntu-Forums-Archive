---
title: "raid 5 takes n-2 drives and not n-1!!!"
date: 2006-12-08
forum: Server Platforms
---

### Post by jimx on 2006-12-08
Hello,i'm trying to create a raid 5 array with 4x250GB sata2 WD drives.When i go to create md0 with 3 disks and 1 spare after it finishes,shows total capacity 500GB.I think that it would be 750GB.

I'm starting a clean install from "Edgy Eft 6.10 Server cd".
I have an MSI P965 board with a Intel core 2 duo 2.13Ghz.

I'm using Ubuntu because i like the community that has and the users that help a lot with problems.

---

### Post by ColdCanuck on 2006-12-08
Actually RAID-5 is N-1. You have 4 drives: 1 spare not in the RAID set and a 3 drive RAID set, which using N-1 gives 2 * the size of the drive, which is what you are seeing. If you want 3 * the drive capacity, lose the spare and make a 4 drive RAID set. 

You should review some of the many excellent HOWTOs on RAID,

([http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)) for example

 before you do this as there are significant policy issues in not having the spare. You need to understand these in order to make an informed decision whether to have a spare drive in the RAID.

---

### Post by jimx on 2006-12-08
Thanks for the quick reply!

I'll read this "How to" and i'll try again.

---

