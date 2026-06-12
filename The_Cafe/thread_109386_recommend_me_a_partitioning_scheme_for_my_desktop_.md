---
title: "recommend me a partitioning scheme for my desktop with various drives"
date: 2005-12-28
forum: The Cafe
---

### Post by riffic on 2005-12-28
so my beast is getting to be a little more than I can handle. I just added a 160 gb drive (xmas present from my girl), its going to be my new /dev/hda, and I am trying to figure out what to do with the rest of my storage scheme. 

heres what I have.. my previous boot drive was a 30 gb maxtor that was partitioned /boot, swap, and / , there's nothing really worth keeping on it so I'm probably going to use it in my new enclosure, as fat32. then I also had a 250 gb drive that was mounted as /home, it was mainly just used as mp3 storage but has become quite filled. I think my plan is to use the 160 and 250 drives together with LVM2 but I'd also like to be able to try out development branches of ubuntu in a seperate partition space from the main breezy install. lastly, I'd like to set aside like 20 gb or so for a windows install, just to **** around with games and stuff.

---

### Post by Rinzwind on 2005-12-28
I totally dig your setup.
Why not use another small disc to install your OS.
Use the large disc to be mounted seperatly and use that to hold anything worth while: music, movies, documents, images etc.

Just remake your setup.

---

### Post by riffic on 2005-12-28
ok, what just I did was made one 512mb /boot partition on the new 160 gb drive, formatted ext3. then I made 8 20gb logical partitions to use as part of my lvm2 volume group. then I made three logical volumes: two 20 gb volumes for breezy root and /home, and a third logical volume for my media. I'm not quite sure where to mount this volume, I think i'll put it in /media/music for now.

after I have enough free space on the 250gb drive, I'll do somewhat the same thing with it, break it up into 20gb chunks and use those partitions as part of my volume group. I'll probably create seperate partitions out of the free space on my lvm setup to go with a fresh install of dapper too. yay

---

### Post by riffic on 2005-12-29
so apparantly dapper doesn't like installing its kernel into the same /boot partition that I'm using for the breezy install + grub. I have 5 LVM logical volumes right now, breezy_root, breezy_home, dapper_root, dapper_home, and music. 

can anyone think of a way to make dapper and breezy both coexist, in their seperate lvm volumes? I'm kind of stumped, and I don't know grub well enough to make it work.

---

