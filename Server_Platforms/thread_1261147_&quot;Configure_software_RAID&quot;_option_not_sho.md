---
title: "&quot;Configure software RAID&quot; option not showing..."
date: 2009-09-08
forum: Server Platforms
---

### Post by edulacomadreja on 2009-09-08
I'm installing Ubuntu Server 9.04 on a new Intel mobo that actually has a hardware raid configuration. If I use the hardware raid (answering yes to the "Activate Serial ATA RAID devices?" question) it won't boot...

Maybe is cuz the hd's are different or something like that???

---

### Post by R.Bucky on 2009-09-08
Establishing a RAID array requires the same model hdd's. They can be of different size, but your paritions have to be the same size. For instance, if you have a 100GB hdd and a 200GB hdd, the maximum size of your array can be no larger than 100GB.

---

