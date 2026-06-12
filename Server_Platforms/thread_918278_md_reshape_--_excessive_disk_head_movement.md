---
title: "md reshape -- excessive disk head movement?"
date: 2008-09-12
forum: Server Platforms
---

### Post by Multi-Medea on 2008-09-12
I'm in the process of reshaping a raid6 array, and it's going very very slowly.  The drives sound as if there is A LOT of head movement going on (which would account for the delay).

Originally created a 5-disk (3+2) raid6 array.  While the array was building, /proc/mdstat was reporting ~40000KBps speeds, which is reasonable.  I added three more disks to bring the array to 6+2, and the reshaping is crawling along at ~5000KBps.

I know it's not the controller (tried it with a 3ware 8506-8 and a pair of SiI-3124-based controllers; same speed); the drives have all passed their fitness tests; the array is not mounted so there is no interference from there, in fact, nothing else is running on the machine.

I don't fully understand what the algorithm for reshaping is, but this much head activity cannot be natural.

Help?

/ji

---

### Post by syadnom on 2008-09-13
when reshaping the array, you are having to compute the parity twice.   Because this is not happening while the data is coming onto the drive, you must read off the drive, compute parity, and then write.

I double there is any way for you to speed up the process other than backing up the entire array, rebuild the array from scratch, then restore.

---

