---
title: "Post your hard drive performance results."
date: 2010-05-05
forum: The Cafe
---

### Post by phibit on 2010-05-05
I am curious to compare hard disk and RAID array performance results, to see the differences between Hardware RAID, FakeRAID, Software Raid, the different types of RAID (0, 1, 5, 0+1, ...), and no RAID at all.

I invite you to post a brief summary of your system setup, and the results of running bonnie++.

```
sudo apt-get install bonnie++ && bonnie++
```

**My Setup:**
[LIST]
[*]Hard Disks: 2x500GB Seagate Barracuda running in a Software (mdadm) RAID1. 
[*]RAM: 6GB DDR2
[*]CPU: 1.89GHz Intel Core 2 Duo E6300
[*]Filesystem: ext4
[*]Ubuntu version: 10.04
[/LIST]


**Results:**
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
phil-desktop    12G   429  95 65995  12 37384   7  2131  89 93821   7 262.3   9
Latency             43308us    7867ms    5064ms   31844us     610ms     290ms
Version  1.96       ------Sequential Create------ --------Random Create--------
phil-desktop        -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  8329  20 +++++ +++ 17328  31 12456  30 +++++ +++ 16061  29
Latency              4499us     918us     745us     614us     973us    5851us
1.96,1.96,phil-desktop,1,1273080348,12G,,429,95,65995,12,37384,7,2131,89,93821,7,262.3,9,16,,,,,8329,20,+++++,+++,17328,31,12456,30,+++++,+++,16061,29,43308us,7867ms,5064ms,31844us,610ms,290ms,4499us,918us,745us,614us,973us,5851us

```

Cheers!

---

### Post by Directive 4 on 2010-05-05
**Results:**
```
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
directive4       6G 44179  80 49453  17 17477   6 38956  76 46240   8 158.5   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 32493  87 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
directive4,6G,44179,80,49453,17,17477,6,38956,76,46240,8,158.5,1,16,32493,87,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++




```




**My Setup:**
[LIST]
[*]Hard Disks:1x320gb .
[*]RAM: 3gb
[*]CPU: 1.83GHz Intel Core 2 Duo T55500
[*]Filesystem: ext4
[*]Ubuntu version: 9.10
[/LIST]


umm, maybe good, maybe bad

---

### Post by phibit on 2010-05-06
Thanks for posting! The comparison of our results is as expected:

We have similar write speeds (though yours is overall a bit faster), I have around double block read speed from having a RAID1 with 2 disks to read from. But overall, I have more CPU overhead. Interesting!

---

### Post by sydbat on 2010-05-06
Completely off topic, but - When I first read the thread title I thought "gee, isn't this the kind of thing I keep finding in my spam folder??"

Please continue on topic...

---

### Post by The Real Dave on 2010-05-06
Here's my results. Care to tell me what it means please?

```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
beta             1G   269  95 43321  11 16657   5  1210  88 45068   5 119.3   4
Latency             65673us     780ms    1430ms   74939us     121ms    1332ms
Version  1.96       ------Sequential Create------ --------Random Create--------
beta                -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 15984  35 +++++ +++ 28284  44 22668  50 +++++ +++ 24291  42
Latency             11107us    1053us    2141us    7238us   15082us   16085us
1.96,1.96,beta,1,1273183999,1G,,269,95,43321,11,16657,5,1210,88,45068,5,119.3,4,16,,,,,15984,35,+++++,+++,28284,44,22668,50,+++++,+++,24291,42,65673us,780ms,1430ms,74939us,121ms,1332ms,11107us,1053us,2141us,7238us,15082us,16085us

```

Also, a hdparm test

```
dave@beta:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   816 MB in  2.00 seconds = 407.90 MB/sec
 Timing buffered disk reads:  138 MB in  3.02 seconds =  45.77 MB/sec

```

And for the craic, a temperature reading

```
dave@beta:~$ hddtemp /dev/sda
/dev/sda: Maxtor 2F040L0: 28°C

```

Setup:

    * Hard Disks: 1x40GB Maxtor IDE Harddrive [8MB cache AFIK]
    * RAM: 480Mb DDR
    * CPU: 2.8Ghz PIV (533Mhz,512KB) OC'd @ 3.23Ghz
    * Filesystem: ext4
    * Ubuntu version: 10.04

---

### Post by phibit on 2010-05-06
@The Real Dave

The results from bonnie++ are a bit confusing, but some reference points are the Sequential Output Block and Sequential Input Block. You're getting ~ 45MB/s , which is typical of 7200 RPM magnetic drives.

My hdparm -tT results are:
```

/dev/md0:
 Timing cached reads:   2588 MB in  2.00 seconds = 1293.95 MB/sec
 Timing buffered disk reads:  296 MB in  3.00 seconds =  98.55 MB/sec

```

I think I have 32M cache on both my 500GB drives.

---

### Post by nirvana21 on 2010-05-07
Here are my results:

```
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
stu              8G 84612  96 170477  43 73433  36 76501  88 204814  39 424.9   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
stu,8G,84612,96,170477,43,73433,36,76501,88,204814,39,424.9,1,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++
```

processor: AMD 955 @ 3.7GHz
motherboard: MSI 790FX-GD70
memory: 4GB DDR3 1333MHz
hard drives: 2x 640GB Western Digital Blacks (32MB cache) in a RAID0 (fake RAID) utilizing the AMD SB750 southbridge

---

### Post by phibit on 2010-05-07
Ouhhh there we go... Nice speeds! 204Mb/s block read is pretty awesome!

I wonder why RAID0 offers better read speeds than RAID1? Shouldn't RAID1 be able to read in a similar manner?

---

### Post by nirvana21 on 2010-05-07
> **phibit said:**
> Ouhhh there we go... Nice speeds! 204Mb/s block read is pretty awesome!

I wonder why RAID0 offers better read speeds than RAID1? Shouldn't RAID1 be able to read in a similar manner?

RAID 1 and RAID 0 are very different. RAID 1 clones data between multiple discs. It is good for fault tolerance. Theorictically it should have the performance of a single disc, altough I have seen it slightly lower.

RAID 0 splits the data between multiple discs. It is fast, but if one disc fails, then you lose all your data. I use this computer for gaming and general usage. So if I lose data its OK because I backup everything on my server. I am running this test on it right now. I will post results shortly.

---

### Post by nirvana21 on 2010-05-07
```
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
server           4G 52479  94 54811   6 29039   5 41354  78 135477  18 307.7   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  3962   7 +++++ +++  1268   3  2844  17 +++++ +++  1628   5
server,4G,52479,94,54811,6,29039,5,41354,78,135477,18,307.7,0,16,3962,7,+++++,+++,1268,3,2844,17,+++++,+++,1628,5


```

processor: Intel Celeron 430 1.8GHz
motherboard: Foxconn G31MXP-K
memory: DDR2 2GB 800Mhz
hard drives: 4x Western Digital RE2 750GB RAID 5
raid controller: Dell Perc i/5

---

### Post by phibit on 2010-05-07
That's an impressive setup! That means you effectively get 2.25 TB of storage, correct?

If you don't mind my asking, why are you using such an array? Are you running a server? And what made you choose RAID5 over RAID0+1?

---

### Post by nirvana21 on 2010-05-07
> **phibit said:**
> That's an impressive setup! That means you effectively get 2.25 TB of storage, correct?

If you don't mind my asking, why are you using such an array? Are you running a server? And what made you choose RAID5 over RAID0+1?

Yes, its about that much storage. It was all pretty cheap for how much storage I have. I got the RAID controller off Ebay for just under $100 and each hard drive was only $70 from Newegg. I choose RAID 5 because you utilize more storage without sacrificing redundancy as compared to RAID10. This system is just a file server and toy for playing with Linux.

I just realized I made a mistake. I didn't look at the performance until now. I forgot the OS was on a separate disk. I will update the performance numbers after the test completes.

---

### Post by Dark Aspect on 2010-05-07
**Setup**
Asus 1001P, same one in my sig, I find this thread interesting but unfortunately my aging Desktop is dead (Again) for the time being. So all I can post is my netbook, still might be good for comparison.

```
Version 1.03e       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
Asus-EEE-1001P      2G 10874  85 52615  35 18392  12 12760  90 48394   9 103.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 13055  93 +++++ +++ 15189  87 12872  95 +++++ +++ 20590  99
,2G,10874,85,52615,35,18392,12,12760,90,48394,9,103.9,0,16,13055,93,+++++,+++,15189,87,12872,95,+++++,+++,20590,99

```

Anyway, I have not a clue what that means. but I am sure its horrible since its a netbook.

---

### Post by The Real Dave on 2010-05-07
```
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
serverII       480M 26166  99 43843  31 11577   9 23312  67 27938   6 160.0   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 12566  96 +++++ +++ 20457  99 14688 100 +++++ +++ 17607  85
serverII,480M,26166,99,43843,31,11577,9,23312,67,27938,6,160.0,1,16,12566,96,+++++,+++,20457,99,14688,100,+++++,+++,17607,85

```

Results for my encoding server.

Setup

CPU: 2.6GHz Intel Celeron [128K]
RAM: 256Mb DDR
HDD: 20+80GB Seagate IDE [8Mb]

* Small [~50MB] /boot partition on the 20GB drive
* 1GB RAID0 swap [500MB per drive, md0]
* ~99GB RAID0 / [remaining space on drives]

Both drives are on the same cable. Shows how little things like that, and the drives being the same effect performance. 

80GB Drive
```
/dev/sda:
 Timing cached reads:   470 MB in  2.00 seconds = 234.84 MB/sec
 Timing buffered disk reads:   60 MB in  3.02 seconds =  19.89 MB/sec

```

20GB Drive
```
/dev/sdb:
 Timing cached reads:   478 MB in  2.00 seconds = 238.76 MB/sec
 Timing buffered disk reads:  104 MB in  3.02 seconds =  34.42 MB/sec

```

1GB Swap, identical Soft Raid0
```
/dev/md0:
 Timing cached reads:   462 MB in  2.00 seconds = 230.57 MB/sec
 Timing buffered disk reads:   78 MB in  3.02 seconds =  25.81 MB/sec

```

~99GB / , unidentical Soft Raid0
```
/dev/md1:
 Timing cached reads:   466 MB in  2.00 seconds = 232.49 MB/sec
 Timing buffered disk reads:   80 MB in  3.03 seconds =  26.38 MB/sec

```

Turns out that I get roughly the average of the two drives by themselves, which ain't bad at all. Just posting for thought food :)

And of course, temps
```
/dev/sda: ST380012A: 33°C
/dev/sdb: ST320014A: 27°C

```

---

### Post by phibit on 2010-05-07
> **Dark Aspect said:**
> **Setup**
Asus 1001P, same one in my sig, I find this thread interesting but unfortunately my aging Desktop is dead (Again) for the time being. So all I can post is my netbook, still might be good for comparison.

```
Version 1.03e       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
Asus-EEE-1001P      2G 10874  85 52615  35 18392  12 12760  90 48394   9 103.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 13055  93 +++++ +++ 15189  87 12872  95 +++++ +++ 20590  99
,2G,10874,85,52615,35,18392,12,12760,90,48394,9,103.9,0,16,13055,93,+++++,+++,15189,87,12872,95,+++++,+++,20590,99

```

Anyway, I have not a clue what that means. but I am sure its horrible since its a netbook.

Actually, it looks like your performance, at least for block read/write, is on par with some desktops we've seen!

---

### Post by phibit on 2010-05-07
@The Real Dave

Hmmm.. I'm actually surprised that your RAID0 isn't giving you more of a performance boost! Maybe since it's a softraid, the CPU might be a limiting factor? I've seen plain RAID0s with upwards of 90MB/s block read/write!

---

### Post by phibit on 2010-05-07
Just for the sake of it, I'll post some hdparm results for some of my other drives.

Again, my RAID1 (2 x Seagate 500GB w/ 32 MB cache)
```
/dev/md0:
 Timing cached reads:   2514 MB in  2.00 seconds = 1256.63 MB/sec
 Timing buffered disk reads:  220 MB in  3.02 seconds =  72.75 MB/sec
```

An old Maxtor 200GB drive with 16MB cache:
```
/dev/sdc:
 Timing cached reads:   2280 MB in  2.00 seconds = 1139.85 MB/sec
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.10 MB/sec
```

A newer Seagate 1TB drive with 32 MB cache: 
```
/dev/sdd:
 Timing cached reads:   2462 MB in  2.00 seconds = 1231.13 MB/sec
 Timing buffered disk reads:  380 MB in  3.01 seconds = 126.33 MB/sec
```

Weird that my 1TB drive reads faster than my RAID1 array...

---

### Post by nirvana21 on 2010-05-07
> **phibit said:**
> Weird that my 1TB drive reads faster than my RAID1 array...

It's not that weird. Hard drive manufacturers focus on increasing capacity and speed. Higher density drives are faster. So newer and larger hard drives are faster. Besides, RAID1 is theoretically only as fast as one individual drive.

---

### Post by karthick87 on 2010-05-08
Here are my results,

```

  	 	 	 	 	 	  Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-  
                     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--  
 Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP  
 Learners-desktop 4G 49647  76 46733   9 26988   6 65761  86 65987  10 139.7   0  
                     ------Sequential Create------ --------Random Create--------  
                     -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--  
               files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  
                  16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++  
 Learners-desktop,4G,49647,76,46733,9,26988,6,65761,86,65987,10,139.7,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++
 
```
[COLOR=Red]
Hddtemp[/COLOR]

  	 	 	 	 	```
 karthick@Learners-desktop:~$ sudo hddtemp /dev/sda  
 /dev/sda: ST3160813AS: 40°C  
 
```


  	 	 	 	 	 	  [COLOR=Red]Hdparm[/COLOR]




```
karthick@Learners-desktop:~$ sudo hdparm -Tt /dev/sda  
 

 /dev/sda:  
 Timing cached reads:   3338 MB in  2.00 seconds = 1669.57 MB/sec  
  Timing buffered disk reads:  334 MB in  3.02 seconds = 110.78 MB/sec  
 
```


[COLOR=Red]Details:[/COLOR]
[COLOR=Black]Hardisk: 160 GB
Processor: Core 2 Duo

[/COLOR]

---

### Post by Phrea on 2010-05-08
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
pb2              8G   311  99 101134  18 46417  14  3763  82 122681   8 209.5   2
Latency             26130us    1442ms    1241ms   77106us     135ms     661ms
Version  1.96       ------Sequential Create------ --------Random Create--------
pb2                 -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 19760  27 +++++ +++ 23638  18 21742  27 +++++ +++ 24594  21
Latency              5372us    1219us     748us    1271us     260us     148us
1.96,1.96,pb2,1,1273295329,8G,,311,99,101134,18,46417,14,3763,82,122681,8,209.5,2,16,,,,,19760,27,+++++,+++,23638,18,21742,27,+++++,+++,24594,21,26130us,1442ms,1241ms,77106us,135ms,661ms,5372us,1219us,748us,1271us,260us,148us
```

WD 320GB hdd
AMD Phenom II 940
4GB mem

Not really sure how to interpret these results, but there you are.

---

### Post by Jive Turkey on 2010-05-08
My specs are comparable to the OP but I think my performance was significantly lower, maybe to do with lower free space or my bios settings or something.

Q9550 2.83 GHz
8 GB ram
500 GB Seagate Barricuda 32MB cache 2 partitions Ext4 encrypted home no raid
ICH10 southbridge
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
plug1           16G    27  99 53977  93 26510  53  2575  88 71036  61  97.6   9
Latency               442ms     299ms    1524ms   59933us     457ms    1917ms
Version  1.96       ------Sequential Create------ --------Random Create--------
plug1               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  1414  14 +++++ +++  8401  31  2167  20 +++++ +++  8354  28
Latency               113ms    4515us    4733us    1576us    1219us    3225us
1.96,1.96,plug1,1,1273285994,16G,,27,99,53977,93,26510,53,2575,88,71036,61,97.6,9,16,,,,,1414,14,+++++,+++,8401,31,2167,20,+++++,+++,8354,28,442ms,299ms,1524ms,59933us,457ms,1917ms,113ms,4515us,4733us,1576us,1219us,3225us
```
After messing about in the bios, changing some of the SATA/IDE settings and enabling AHCI I re ran the test and got this( same system as above but with "Native SATA mode" enabled and AHCI enabled in bios:```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
plug1           16G    30  94 43387  66 27484  45  2637  74 69661  49  90.0   5
Latency              1552ms    6691ms    4362ms     123ms     716ms    4346ms
Version  1.96       ------Sequential Create------ --------Random Create--------
plug1               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  1953  15 +++++ +++ 15050  43  2314  18 +++++ +++ 13791  38
Latency               546us    2658us    4367us    1525us     514us    2301us
1.96,1.96,plug1,1,1273353779,16G,,30,94,43387,66,27484,45,2637,74,69661,49,90.0,5,16,,,,,1953,15,+++++,+++,15050,43,2314,18,+++++,+++,13791,38,1552ms,6691ms,4362ms,123ms,716ms,4346ms,546us,2658us,4367us,1525us,514us,2301us

```

---

### Post by Jive Turkey on 2010-05-08
> **sydbat said:**
> Completely off topic, but - When I first read the thread title I thought "gee, isn't this the kind of thing I keep finding in my spam folder??"

Oh thank goodness I thought I was the only one who got that stuff.

---

### Post by The Real Dave on 2010-05-08
> **phibit said:**
> @The Real Dave

Hmmm.. I'm actually surprised that your RAID0 isn't giving you more of a performance boost! Maybe since it's a softraid, the CPU might be a limiting factor? I've seen plain RAID0s with upwards of 90MB/s block read/write!

Possibly, but I've never seen the CPU usage spike under using the RAID :confused:

---

### Post by nirvana21 on 2010-05-08
> **The Real Dave said:**
> Possibly, but I've never seen the CPU usage spike under using the RAID :confused:

You would have to have a very underpowered processor or under very heavy load to have your processor effect your array performance.

---

### Post by The Real Dave on 2010-05-08
> **nirvana21 said:**
> You would have to have a very underpowered processor or under very heavy load to have your processor effect your array performance.

Ah ok, cheers. Probably the fact that both drives are on the same channel, or that the drives are dissimilar so.

---

### Post by rfry11 on 2010-05-08
> Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ryan-desktop     7G    81  96 37067  14 18511   7   997  97 47953   4 156.3   4
Latency               106ms    2123ms    2144ms   33867us     147ms    1338ms
Version  1.96       ------Sequential Create------ --------Random Create--------
ryan-desktop        -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 14759  48 +++++ +++ 25042  59 19757  64 +++++ +++ 22463  55
Latency               954us    1163us    1136us     946us     921us     941us
1.96,1.96,ryan-desktop,1,1273316020,7G,,81,96,37067,14,18511,7,997,97,47953,4,156.3,4,16,,,,,14759,48,+++++,+++,25042,59,19757,64,+++++,+++,22463,55,106ms,2123ms,2144ms,33867us,147ms,1338ms,954us,1163us,1136us,946us,921us,941us


Specs: 
Pentium D 2.88GHZ
4GB RAM
80GB SATA HDD, 45GB NTFS Win7 partition, everything else ext4 Ubuntu 10.04 partition.
1TB SATA HDD, NTFS
No raid or anything like that.

---

### Post by nirvana21 on 2010-05-08
> **The Real Dave said:**
> or that the drives are dissimilar so.

That will do it. You can only get optimal performance from the same model drives.

---

### Post by ubunterooster on 2010-05-08
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
josiah-desktop  15G   286  99 62925  10 71557  12  4537  97 267251  21  4990 103
Latency             36445us    2549ms    1396ms    6960us   27602us     400ms
Version  1.96       ------Sequential Create------ --------Random Create--------
josiah-desktop      -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 19188  21 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               715us     335us     532us     267us      34us     543us
1.96,1.96,josiah-desktop,1,1273337272,15G,,286,99,62925,10,71557,12,4537,97,267251,21,4990,103,16,,,,,19188,21,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,36445us,2549ms,1396ms,6960us,27602us,400ms,715us,335us,532us,267us,34us,543us



128GB patriot torx, CPU clocked @ 800Mhz

---

### Post by Phrea on 2010-05-08
[http://ubuntuforums.org/showpost.php?p=9259491&postcount=20](http://ubuntuforums.org/showpost.php?p=9259491&postcount=20)

Can somebody interpret it for me? :)

---

### Post by Dark Aspect on 2010-05-08
> **phibit said:**
> Actually, it looks like your performance, at least for block read/write, is on par with some desktops we've seen!

Cool,

I actually find the Asus EEE's performance to be okay as whole. But I noticed a mild amount of lag in somethings so I figured the hard drive must be slow. Maybe I need to run some benchmarks on the GPU, RAM and CPU.

For example: Firefox, Open Office and vuze run slow where as Gnome, Gimp and even Open Arena run fine. I've yet to figure out why, I think firefox doesn't like Atom based CPUs.

---

### Post by The Real Dave on 2010-05-08
> **ubunterooster said:**
> 
128GB patriot torx, CPU clocked @ 800Mhz

An SSD with an 800Mhz CPU? A netbook I presume?

---

### Post by ubunterooster on 2010-05-08
ROFLMAO; it's actually a underclocked 3.1 Ghz desktop with 8GB RAM, 4 TB of storage, uses 55 watts and does a complete boot in under 20sec (5 sec from GRUB to desktop)

---

### Post by The Real Dave on 2010-05-09
> **ubunterooster said:**
> ROFLMAO; it's actually a underclocked 3.1 Ghz desktop with 8GB RAM, 4 TB of storage, uses 55 watts and does a complete boot in under 20sec (5 sec from GRUB to desktop)

Wow, that's very underclocked. And you use that as a workstation, not a server?

---

### Post by OrbJinzo on 2010-05-09
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
kubuntu          6G   233  98 71282  16 31948   9  1278  91 61531   6 169.4   4
Latency             45500us    1223ms    1083ms     125ms     373ms     934ms
Version  1.96       ------Sequential Create------ --------Random Create--------
kubuntu             -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 15314  28 +++++ +++ 22812  31 24827  47 +++++ +++ 28841  38
Latency               913us    1077us    1755us    1117us     846us     901us
1.96,1.96,kubuntu,1,1273389720,6G,,233,98,71282,16,31948,9,1278,91,61531,6,169.4,4,16,,,,,15314,28,+++++,+++,22812,31,24827,47,+++++,+++,28841,38,45500us,1223ms,1083ms,125ms,373ms,934ms,913us,1077us,1755us,1117us,846us
```

Kubuntu 10.04
Core2Quad Q6600
400gb Western Digital Caviar drive
3gb ram.
Nvidia 9500gt 1gb video card

---

### Post by Jose Catre-Vandis on 2010-05-09
Processor: Atom 330 Dual Core 1.6ghz
Ram : 2Gb (512 reserved for ION graphics)
HDD: 250Gb Seagate ST9250315AS
Xubuntu 10.04

Output:
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
lynx             3G    60  99 54904  48 24317  17   588  99 64089  12 153.7   7
Latency               184ms     622ms     723ms   34406us     244ms     851ms
Version  1.96       ------Sequential Create------ --------Random Create--------
lynx                -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 10852  62 +++++ +++ 13640  49 11197  62 +++++ +++ 15124  55
Latency             12364us    7308us    3978us    3736us    7449us     254us
1.96,1.96,lynx,1,1273398430,3G,,60,99,54904,48,24317,17,588,99,64089,12,153.7,7,16,,,,,10852,62,+++++,+++,13640,49,11197,62,+++++,+++,15124,55,184ms,622ms,723ms,34406us,244ms,851ms,12364us,7308us,3978us,3736us,7449us,254us

```

---

### Post by scouser73 on 2010-05-09
My setup:

[LIST] HD: 82GB Hitachi Drive [/LIST]
[LIST] RAM: 1GB [/LIST]
[LIST] External HD: 1TB Maxtor x 1, 500GB Maxtor x 4 [/LIST]
[LIST] CPU: Intel(R) Celeron(R) CPU 2.80GHz [/LIST]
[LIST] Filesystem: EXT4 [/LIST]
[LIST] Ubuntu Version: Ubuntu 10.04 [/LIST]


```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
Desktop          2G    80  61 51211  25 20479  11   693  61 60761  12 175.8  12
Latency               278ms    1225ms    1595ms   32301us     138ms     847ms
Version  1.96       ------Sequential Create------ --------Random Create--------
Desktop             -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 11183  39 +++++ +++ 16105  38 13268  44 +++++ +++ 14685  36
Latency             12775us   18440us   24363us   16138us    9788us   20215us
1.96,1.96,Desktop,1,1273410859,2G,,80,61,51211,25,20479,11,693,61,60761,12,175.8,12,16,,,,,11183,39,+++++,+++,16105,38,13268,44,+++++,+++,14685,36,278ms,1225ms,1595ms,32301us,138ms,847ms,12775us,18440us,24363us,16138us,9788us,20215us
```

---

### Post by nirvana21 on 2010-05-09
> **The Real Dave said:**
> Wow, that's very underclocked. And you use that as a workstation, not a server?

It could be that he has processor power saving modes enabled. For example, my processor (3.7GHz) drops its multiplier down to 4x when idling, which is 800MHz.

---

### Post by phibit on 2010-05-09
Wow, a lot of these results are somewhat surprising! What I'm most impressed by is the laptop drive performances. Some of you guys posted laptops that do 60MB/s sequential read, that's awesome!

> **nirvana21 said:**
> It's not that weird. Hard drive manufacturers focus on increasing capacity and speed. Higher density drives are faster. So newer and larger hard drives are faster. Besides, RAID1 is theoretically only as fast as one individual drive.

I guess what you're saying really is true, as demonstrated by these results!

What about some SSD performances? I'm curious to see what all the hype is about... Some boast 220 MB/s sequential read!

---

### Post by phibit on 2010-05-09
> **ubunterooster said:**
> 
128GB patriot torx, CPU clocked @ 800Mhz

Oh here we go, an SSD with ~ 260MB/s sequential read... 5 second boot from GRUB?!?! Amazing.

---

### Post by ubunterooster on 2010-05-10
> **The Real Dave said:**
> Wow, that's very underclocked. And you use that as a workstation, not a server?

Main use is a file server but it is my main computer.

---

