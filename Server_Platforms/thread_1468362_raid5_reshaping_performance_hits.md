---
title: "raid5 reshaping performance hits"
date: 2010-05-01
forum: Server Platforms
---

### Post by speed32219 on 2010-05-01
Noob type questions.

Last night I added another 1.5TB disk to the 3ea. 1.5TB disk array. It started out at about speed=96,000K/sec and dropped  down this morning as the reshape size grew to,(reshape = 74.7% (1095748736/1465138496) **finish=3565.7min **speed=1726K/sec). 

Now within a 5-10 minute period using mdstat here is the output of mdstat again. (reshape = 75.2% (1102567552/1465138496) finish=103.0min speed=58644K/sec)  Notice the speed and time to finish.

Why such a big performance incresase/hit?  Could it be that there was no more data, it had been moved around?  (I was at about 70% utilization of a 2.7TB array, which means that reshaping an array with no or less data is faster)

I also started to watch a dvd on the server to see what the impact would be to the reshaping.  I was astonished at the speed and time difference.
(reshape = 74.7% (1095810304/1465138496) **finish=8096.5min speed=759K/sec**)

I also was monitoring cpu performance, Mem usage and swap using htop.  With the reshaping running by itself cpu % was varying from **37 to 51%**, but hovered around 50% mostly. (Celeron 775 P4 2.8Ghz)

When I started to watch the movie across the network CPU% dropped to **3%**.  Memory usage was low in both instances and reshaping took a big hit. 

Question, is there a tuning parameter for calculating and setting writing/reshaping and current usage/reading of the array?

Or is this normal for heavy reading of data (watching an ISO) off the array while reshaping?  Just trying to understand the performance characteristics of this raid5/lvm2 array.

---

### Post by ian dobson on 2010-05-01
Hi,

Harddisks don't have the same performance over the hole disk. The outside (sector 0) can hold the most data as it's the longest, so in one rotation the outmost track might hold 200sectors and the innermost only 100.

Once you start using the array the disk heads need to start seeking which really kills performance. 

If your array is a RAID5 array the at some point when the array is reshaped up to the point that no data needs to be moved about the reashape should run faster (in your case 1.5tb left to add).

Have a look here for afew tunables in the RAID system:-
[http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/](http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/)

Regards
Ian Dobson

---

