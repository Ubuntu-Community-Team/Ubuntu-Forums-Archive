---
title: "Lost raid folders...somehow?"
date: 2012-05-03
forum: Server Platforms
---

### Post by MyD0j0 on 2012-05-03
I have a raid 5 software array:

```

root@CentralD0j0:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[3] sdc1[1] sdb1[0]
      1953518592 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

We recently had a power loss during a storm and when I rebooted, my raid was missing several folders...everything that had data in them.  I've only had this array for a couple months and no way to back it up because I was saving to get a backup drive that could hold my almost 1Tb of data.

Most of the data was in 
/BigDisk/MultiMedia/Music
/BigDisk/MultiMedia/Movies
/BigDisk/MultiMedia/Pictures
/BigDisk/NetUsers/User1
/BigDisk/NetUsers/User2
/BigDisk/NetUsers/User3
/BigDisk/NetUsers/User4

The Music, Movies and Pictures are gone as well as NetUsers (the individual user folders in NetUsers held backups from local machines on the network)


I am at a loss for how these sub-directories just up and disappeared while the raid array seems fine...Anyone have any thoughts on how I might be able to restore...I don't see  a .trash folder that I might be able to retrieve from (accidental  delete???)  Most of this is home movies and pictures that I really would  like to get back.  If it were anything else, I could live without and suck it up...

---

### Post by rubylaser on 2012-05-03
What filesystem are you using on your array?  I'm assuming ext4.  If so, you could give [extundelete]("http://extundelete.sourceforge.net/options.html") a try.  It's --restore-file or --restore-directory options should be what you're looking for.

---

