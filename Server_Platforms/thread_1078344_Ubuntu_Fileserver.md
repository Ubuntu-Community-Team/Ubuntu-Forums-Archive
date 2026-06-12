---
title: "Ubuntu Fileserver"
date: 2009-02-23
forum: Server Platforms
---

### Post by Jonnyuser on 2009-02-23
Hello. 

I have an Ubuntu based fileserver. 
It has 4 pieces 1TB HDD in RAID5, and LVM over it.

But I can't expand or reduce it because of the RAID5. 
What would be the solution where I cna have a rendundant and expandable storage ?

(For example if I would like to expand it one more 1TB HDD, besides keep the redundancy for data safety)

---

### Post by Cheesemill on 2009-02-23
It depends on whether you are using hardware or software RAID, if you have software RAID using mdadm then it is possible to extend the array on to more disks using the procedure described [here]("http://cobraftp.serveftp.com/pub/raid.pdf").

ALso check out [this]("http://ubuntuforums.org/showthread.php?t=1032273").

If you have hardware RAID it may be possible, you will have to check the documentation for your specific card.

Cheesemill.

---

