---
title: "debug log on??"
date: 2009-02-07
forum: Server Platforms
---

### Post by mansonthomas on 2009-02-07
Hi,

Watching my log files, I noticed that a debug file log is used and is particularly big : 
[PHP]
-rw-r-----  1 syslog      adm  53056094 2009-02-08 01:42 debug          
-rw-r-----  1 syslog      adm  58415003 2009-02-07 07:06 debug.0        
-rw-r-----  1 syslog      adm   3888366 2009-02-06 07:23 debug.1.gz     
-rw-r-----  1 syslog      adm   3499178 2009-02-05 06:42 debug.2.gz     
-rw-r-----  1 syslog      adm   6097559 2009-02-04 07:06 debug.3.gz     
-rw-r-----  1 syslog      adm   3294832 2009-02-03 06:49 debug.4.gz     
-rw-r-----  1 syslog      adm   4145225 2009-02-02 06:42 debug.5.gz     
-rw-r-----  1 syslog      adm   3437011 2009-02-01 06:47 debug.6.gz  [/PHP]   


with this content : 

[PHP]Feb  8 01:42:19 home kernel: [7264013.883380] syslogd(5109): dirtied inode 5210456 (debug) on md2
Feb  8 01:42:19 home kernel: [7264013.883448] syslogd(5109): dirtied inode 5210163 (syslog) on md2
Feb  8 01:42:19 home kernel: [7264014.090234] md2_raid1(2365): WRITE block 1455874432 on sda3
Feb  8 01:42:19 home kernel: [7264014.090286] md2_raid1(2365): WRITE block 1455874432 on sdb3
Feb  8 01:42:19 home kernel: [7264014.105788] smbd(6113): READ block 107551704 on md2
Feb  8 01:42:19 home kernel: [7264014.105822] smbd(6113): READ block 107551952 on md2
Feb  8 01:42:22 home kernel: [7264017.040078] kjournald(2411): WRITE block 500499848 on md2
Feb  8 01:42:22 home kernel: [7264017.040147] md2_raid1(2365): WRITE block 1455874432 on sda3
Feb  8 01:42:22 home kernel: [7264017.040196] md2_raid1(2365): WRITE block 1455874432 on sdb3
Feb  8 01:42:22 home kernel: [7264017.059835] kjournald(2411): WRITE block 500507584 on md2
Feb  8 01:42:22 home kernel: [7264017.059850] kjournald(2411): WRITE block 500377288 on md2
Feb  8 01:42:22 home kernel: [7264017.059859] kjournald(2411): WRITE block 500499856 on md2
Feb  8 01:42:22 home kernel: [7264017.059867] kjournald(2411): WRITE block 500507592 on md2
Feb  8 01:42:22 home kernel: [7264017.059877] kjournald(2411): WRITE block 500377296 on md2
Feb  8 01:42:22 home kernel: [7264017.060411] kjournald(2411): WRITE block 173536 on md2
Feb  8 01:42:22 home kernel: [7264017.060426] kjournald(2411): WRITE block 173544 on md2
Feb  8 01:42:22 home kernel: [7264017.060436] kjournald(2411): WRITE block 173552 on md2
Feb  8 01:42:22 home kernel: [7264017.060445] kjournald(2411): WRITE block 173560 on md2
Feb  8 01:42:22 home kernel: [7264017.060455] kjournald(2411): WRITE block 173568 on md2
Feb  8 01:42:22 home kernel: [7264017.060466] kjournald(2411): WRITE block 173576 on md2
Feb  8 01:42:22 home kernel: [7264017.060475] kjournald(2411): WRITE block 173584 on md2
Feb  8 01:42:22 home kernel: [7264017.060485] kjournald(2411): WRITE block 173592 on md2
Feb  8 01:42:22 home kernel: [7264017.060495] kjournald(2411): WRITE block 173600 on md2
Feb  8 01:42:22 home kernel: [7264017.060505] kjournald(2411): WRITE block 173608 on md2
Feb  8 01:42:22 home kernel: [7264017.061003] kjournald(2411): WRITE block 173616 on md2
Feb  8 01:42:22 home kernel: [7264017.271317] md2_raid1(2365): WRITE block 1455874432 on sda3
Feb  8 01:42:22 home kernel: [7264017.271350] md2_raid1(2365): WRITE block 1455874432 on sdb3
Feb  8 01:42:24 home kernel: [7264019.523624] smbd(6113): READ block 107551960 on md2
Feb  8 01:42:24 home kernel: [7264019.523666] smbd(6113): READ block 107552208 on md2
Feb  8 01:42:27 home kernel: [7264022.040082] kjournald(2411): WRITE block 500499856 on md2
Feb  8 01:42:27 home kernel: [7264022.040148] md2_raid1(2365): WRITE block 1455874432 on sda3
Feb  8 01:42:27 home kernel: [7264022.040197] md2_raid1(2365): WRITE block 1455874432 on sdb3
Feb  8 01:42:27 home kernel: [7264022.059748] kjournald(2411): WRITE block 500507592 on md2
Feb  8 01:42:27 home kernel: [7264022.059764] kjournald(2411): WRITE block 500377296 on md2
Feb  8 01:42:27 home kernel: [7264022.059811] kjournald(2411): WRITE block 173624 on md2
Feb  8 01:42:27 home kernel: [7264022.059820] kjournald(2411): WRITE block 173632 on md2
Feb  8 01:42:27 home kernel: [7264022.059829] kjournald(2411): WRITE block 173640 on md2
Feb  8 01:42:27 home kernel: [7264022.059838] kjournald(2411): WRITE block 173648 on md2
Feb  8 01:42:27 home kernel: [7264022.060544] kjournald(2411): WRITE block 173656 on md2
Feb  8 01:42:27 home kernel: [7264022.271332] md2_raid1(2365): WRITE block 1455874432 on sda3
Feb  8 01:42:27 home kernel: [7264022.271387] md2_raid1(2365): WRITE block 1455874432 on sdb3[/PHP]




Any idea of why the raid system and kjournald are logging in this file ? 


Thomas.

---

