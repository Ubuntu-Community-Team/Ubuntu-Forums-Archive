---
title: "meaning content of /proc/mdstat"
date: 2011-01-28
forum: Server Platforms
---

### Post by titotti32 on 2011-01-28
i was confused when i saw a content of /proc/mdstat
anybody can explain this to me?

```
 md2 : active raid1 sda3[0] sdb3[1] 
```
what's mean of "sda3[0]" and "sdb3[1]"?

```
 4883648 blocks [2/2] [UU] 
```
what's mean of [2/2] and [UU]?

and this's content of my /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sda3[0] sdb3[1]
      4883648 blocks [2/2] [UU]

md1 : active raid1 sdb2[2] sda2[0]
      195310144 blocks [2/1] [U_]
      [=>...................]  recovery =  8.5% (16775552/195310144) finish=17.0min speed=259783K/sec

md0 : active raid1 sdb1[1] sda1[0]
      39061952 blocks [2/2] [UU]

unused devices: <none>

```

Any help would be greatly appreciated :)

---

### Post by sh1ny on 2011-01-29
[http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO.html#toc6.2](http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO.html#toc6.2)

[http://tldp.org/FAQ/Linux-RAID-FAQ/x37.html#failrecover](http://tldp.org/FAQ/Linux-RAID-FAQ/x37.html#failrecover)

You don't need to care about [0],[1] ( the order of the devices in the array i'd presume ) or that other stuff. Basically, when things are going down you will have a [U_] ( an underscore ). Which you have.

---

### Post by Plecebo on 2011-02-12
I know this is closed but to elaborate on what information has been correctly provided for future users. 

> what's mean of "sda3[0]" and "sdb3[1]"?
This means sda3 is the first drive in your array, and sdb3 is the 2nd drive in your array. Usually this isn't too important, unless you have a failure. 

> what's mean of [2/2] and [UU]?
This tells your array consists of 2 drives (the top number) and 2 drives are functional (the bottom number). Both of your drives are "up" ([UU])

as sh1ny mentioned, from your cat /proc/mdstat
```
md1 : active raid1 sdb2[2] sda2[0]
      195310144 blocks [2/1] [U_]
      [=>...................]  recovery =  8.5% (16775552/195310144) finish=17.0min speed=259783K/sec
```

This indicates that you have a 2 drive array but only one drive is fully working (2/1) it shows that the 2nd drive had some issues ([U_]) which in this case is drive #2 (sdb2[2]). They appear to have been addressed however as the array is currently degraded, but rebuilding (likely it is functional (because md1 is a raid1 array and it is currently up (md1: active raid1), but you are vulnerable to a failure of sda2 (which would result in a loss of the data on the array since it is degraded) or a failure of sdb2 (in which case the array would continue to operate degraded until you fixed the issue with the 2nd drive and rebuilt the array).

Further your recovery is about 8.5% completed, and should take another 17 minutes or so at its current rate. 

There is a lot of information packed into the /proc/mdstat that can give you a good idea of your overall array health.

---

