---
title: "Raid 5 + LVM2 and replacing hard disks"
date: 2008-11-29
forum: Server Platforms
---

### Post by iler on 2008-11-29
Hi!

I'm considering replacing my raid 5 (software raid using 64bit Ubuntu 8.04) disks 4x500GB with 4x1TB disks and I have couple of questions. Is it possible to change those disks like one at a time eventually having 3TB as my raid 5 array size? If it is possible how will it show up in my current lvm2 setup where I have one volume group that takes all the available 1,5TB of space that I have in my raid 5 array. Will it eventually grow to 3TB or do I have to expand my volume group somehow? Thanks in advance!

---

### Post by Philio on 2008-11-29
Pretty sure that if you replace the first disk and rebuild the array it will only use it as a 500Gb drive.

---

### Post by iler on 2008-11-29
Thanks for the answer but that I already know. The question was will it use all the space that there is (3TB) when I replace all the four 500GB disks that I have now with four 1TB ones.

---

### Post by Philio on 2008-11-29
Well you could probably replace each disk one at a time, wait for the array to be rebuilt between disk swaps, then once all the disks have been replaced grow the partitions and LVM volumes.

I wouldn't recommend messing about with your hard drive partitions unless you know what your doing, the fact that your using RAID 5 suggests you have important data on the disks you don't want to loose and considering your asking the question in the first place I would opt for the safe option: Connect up the new drives and copy the data over. This would probably be quicker than waiting for the array to be rebuilt 4 times anyway!

---

### Post by iler on 2008-11-29
Well raid!=backup so of course I have backups somewhere else and this server isn't that important that I couldn't manage the downtime if I do something wrong. I just wanted to know if it's possible to get things working this way. Of course I could do as you suggested but I want to test and know how these system changes in raid arrays with lvm work out in real situations. There is a possibility that I might come up with a situation where this way is the only choice to do things. Just asking if anyone has done it this way and could tell me did it work :)

---

