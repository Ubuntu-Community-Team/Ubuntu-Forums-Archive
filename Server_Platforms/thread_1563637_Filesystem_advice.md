---
title: "Filesystem advice"
date: 2010-08-29
forum: Server Platforms
---

### Post by BarryDocks on 2010-08-29
I have the luxury of using 2 separate drives on my new server as a stripped raid (software) array for web proxy-cache data, etc.  Obviously I want this to be as fast as possible, I would be grateful on advice as to the most suitable file system to use for this purpose?  I was thinking of ext2 or resierfs?
Thanks

---

### Post by BarryDocks on 2010-09-11
bump
anyone?

---

### Post by ian dobson on 2010-09-11
Hi,

resierfs may not have a very rosy future. ext2 is an old fs, maybe ext4 as a further development of ext2/3. for web caching you'll be mainly dealing with reading/writing lots of small files so ext4 might be the best way to go.

If you don't plan to use a seperate boot drive/hardware RAID:-
I'm not sure if you can boot from a stripped drive (does grub support it?) so the best idea would be to create a small mirrored boot partition and a second partition (stripped) for your cache data.

Regards
Ian Dobson

---

