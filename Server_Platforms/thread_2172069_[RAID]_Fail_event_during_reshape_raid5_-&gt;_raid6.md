---
title: "[RAID] Fail event during reshape raid5 -&gt; raid6"
date: 2013-09-03
forum: Server Platforms
---

### Post by ValiDOM on 2013-09-03
I started reshaping a 3-device raid5 to a 4-device raid6. After some  hours, I got a fail event on a harddrive which was already used in the  raid5. 

There are two different raid-groups on these harddrives, a reshape of  the second one has not yet started. 

What would you suggest? 
* stop the reshape, go back to raid5 and start rebuild to the new disk  (how?) 
* just wait, hope and pray... ( there is no backup, I do not have  harddrives to backup to as this is just to much...) 

```

md0 : active raid6 sdc2[0] sde2[4](F) sdb2[3] sdd2[1] 
      2858420224 blocks super 0.91 level 6, 64k chunk, algorithm 18  [4/2] [UU__] 
      [=>...................]  reshape =  7.8% (112662528/1429210112)  finish=4938.2min speed=4442K/sec 

md1 : active raid5 sdc1[0] sde1[2] sdb1[3](S) sdd1[1] 
      1048575744 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU] 
```

(md1 not mounted, sde1 will fail once used/checked and the raid5 will  automatically start rebuild on sdb1) 

Thanks! 
Vali

---

