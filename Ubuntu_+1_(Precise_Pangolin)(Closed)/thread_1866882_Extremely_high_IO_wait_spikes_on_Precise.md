---
title: "Extremely high IO wait spikes on Precise"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2011-10-22
Anyone else suffering from this on UbuPP?!?!?

Never had these problems before installing Precise (uber laggy - hard locks)

```
vindsl@Zuul:~$ sar 5 12
Linux 3.1.0-1-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

12:18:27 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:18:32 AM     all     17.02      0.00      3.50      0.00      0.00     79.48
12:18:37 AM     all     15.62      0.00      6.61      0.20      0.00     77.58
12:18:42 AM     all     20.92      0.00      6.71      0.50      0.00     71.87
12:18:47 AM     all     17.37      0.00      4.39      0.20      0.00     78.04
12:18:52 AM     all     14.80      0.00      4.90      0.10      0.00     80.20
12:18:57 AM     all     19.42      0.00      5.51      0.20      0.00     74.87
12:19:02 AM     all     18.28      0.00      4.20      0.00      0.00     77.52
12:19:07 AM     all     14.21      0.00      4.70      0.00      0.00     81.08
12:19:12 AM     all     20.20      0.00      5.10      1.40      0.00     73.30
12:19:17 AM     all     17.28      0.00      4.40      0.20      0.00     78.12
12:19:22 AM     all     14.51      0.00      4.70      0.00      0.00     80.78
12:19:27 AM     all     20.12      0.00      4.30      0.20      0.00     75.38
Average:        all     17.48      0.00      4.92      0.25      0.00     77.35
vindsl@Zuul:~$ sar 5 12
Linux 3.1.0-1-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

12:24:11 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:24:16 AM     all     20.12      0.00      3.90      4.00      0.00     71.97
12:24:21 AM     all     50.60      0.10     11.08      6.09      0.00     32.14
12:24:26 AM     all     75.28      0.00      8.01      0.10      0.00     16.62
12:24:31 AM     all     74.35      0.00      9.02      4.01      0.00     12.63
12:24:36 AM     all     50.10      0.00      9.30      1.10      0.00     39.50
12:24:41 AM     all     58.76      0.00      6.61      1.40      0.00     33.23
12:24:46 AM     all     65.77      0.00     10.31      7.11      0.00     16.82
12:24:51 AM     all     58.46      0.00     10.81     11.11      0.00     19.62
12:24:56 AM     all     71.03      0.00      7.99      1.50      0.00     19.48
12:25:01 AM     all     66.07      0.00     10.01      0.00      0.00     23.92
12:25:06 AM     all     57.30      0.00     10.80      3.10      0.00     28.80
12:25:11 AM     all     61.50      0.00      8.50      0.00      0.00     30.00
Average:        all     59.11      0.01      8.86      3.29      0.00     28.73
vindsl@Zuul:~$ sar 5 12
Linux 3.1.0-1-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

12:25:56 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:26:01 AM     all     29.16      0.00      6.01     16.83      0.00     48.00
12:26:06 AM     all     31.47      0.00      7.69     14.09      0.00     46.75
12:26:11 AM     all     55.20      0.00     10.20      3.60      0.00     31.00
12:26:16 AM     all     76.48      0.00      7.81      0.70      0.00     15.02
12:26:21 AM     all     71.30      0.00      6.90      0.50      0.00     21.30
12:26:26 AM     all     59.16      0.00     11.51     11.81      0.00     17.52
12:26:31 AM     all     57.34      0.00     14.99     12.99      0.00     14.69
12:26:36 AM     all     27.13      0.00      7.21     64.33      0.00      1.33
12:26:41 AM     all     55.53      0.00     11.91     27.50      0.00      5.06
12:26:46 AM     all     48.01      0.00      7.67     35.46      0.00      8.86
12:26:51 AM     all     27.21      0.00      6.63     **[COLOR="Red"]60.64[/COLOR]**      0.00      5.52
12:26:56 AM     all      9.11      0.00      2.18     **[COLOR="Red"]88.71[/COLOR]**      0.00      0.00
Average:        all     45.44      0.00      8.37     **[COLOR="Red"]28.31[/COLOR]**      0.00     17.88
vindsl@Zuul:~$ sar 5 12
Linux 3.1.0-1-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

12:31:12 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:31:17 AM     all      0.60      0.00      0.60     **[COLOR="Red"]98.81[/COLOR]**      0.00      0.00
12:31:23 AM     all      1.25      0.00      1.16     **[COLOR="Red"]97.59[/COLOR]**      0.00      0.00
12:31:28 AM     all      1.34      0.00      0.72     **[COLOR="Red"]97.94[/COLOR]**      0.00      0.00
12:31:33 AM     all     10.29      0.00      1.76     **[COLOR="Red"]87.84[/COLOR]**      0.00      0.10
12:31:38 AM     all     10.12      0.00      1.69     **[COLOR="Red"]88.10[/COLOR]**      0.00      0.10
12:31:43 AM     all      1.58      0.00      1.68     **[COLOR="Red"]90.62[/COLOR]**      0.00      6.12
12:31:48 AM     all     18.62      0.00      3.10     19.02      0.00     59.26
12:31:53 AM     all     12.93      0.00      2.51      2.30      0.00     82.26
12:31:58 AM     all     18.94      0.00      5.41     13.93      0.00     61.72
12:32:03 AM     all     18.21      0.00      2.79      0.50      0.00     78.51
12:32:08 AM     all     11.30      0.00      2.50      1.00      0.00     85.20
12:32:13 AM     all     20.24      0.00      3.81      3.11      0.00     72.85
Average:        all     10.43      0.00      2.31     **[COLOR="Red"]50.26[/COLOR]**      0.00     37.01
vindsl@Zuul:~$ 
```

In the example above, io wait locked up my machine for 5 solid minutes. 

Boom, dead, fail!

Luckily, it came back up, and allowed me to copy n' paste the forensics to Tomboy.

Normally, when this happens, I have to reach for the reset button, as it never recovers.

Anyway, I'm interested in knowing if this is happening to anyone else...

Thanks!

---

### Post by ranch hand on 2011-10-22
No, not here.

Ran same command 4 times over 15 minutes had 2 small spikes of 6.38 and 9.25.  Have never had a lock up on either install.

Disclaimer: am never on either install for more than 45 minutes average.  30 to 60 minutes is the spread.

---

### Post by dino99 on 2011-10-22
here is mine

oem@oem-desktop:~$ sar 5 12
Linux 3.1.0-1-generic-pae (oem-desktop) 	22/10/2011 	_i686_	(4 CPU)

11:07:08        CPU     %user     %nice   %system   %iowait    %steal     %idle
11:07:13        all      0,35      0,00      0,30      0,15      0,00     99,20
11:07:18        all      0,15      0,00      0,20      0,10      0,00     99,55
11:07:23        all      0,90      0,00      0,50      0,00      0,00     98,60
11:07:28        all      0,65      0,05      0,40      0,00      0,00     98,90
11:07:33        all      0,80      0,00      0,45      0,00      0,00     98,75
11:07:38        all      0,15      0,00      0,25      0,00      0,00     99,60
11:07:43        all      0,25      0,00      0,25      0,00      0,00     99,50
11:07:48        all      0,25      0,05      0,30      0,00      0,00     99,40
11:07:53        all      0,25      0,00      0,25      0,00      0,00     99,50

Average:     all      0,78      0,01      0,40      0,04      0,00     98,76

---

### Post by tista on 2011-10-22
Here is mine ;) :
```
tista@VPCZ21AJ:~$ sar 5 12
Linux 3.1.0-1-generic (VPCZ21AJ) 	10/22/2011 	_x86_64_	(4 CPU)

08:52:22 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
08:52:27 PM     all      1.15      0.00      0.40      0.05      0.00     98.40
08:52:32 PM     all      0.80      0.00      0.40      0.00      0.00     98.80
08:52:37 PM     all      1.10      0.00      0.63      0.00      0.00     98.27
08:52:42 PM     all      0.80      0.00      0.40      0.00      0.00     98.81
08:52:47 PM     all      0.82      0.00      0.38      0.00      0.00     98.80
08:52:52 PM     all      0.92      0.00      0.46      0.05      0.00     98.58
08:52:57 PM     all      0.79      0.00      0.59      0.00      0.00     98.62
08:53:02 PM     all      1.11      0.00      0.56      0.00      0.00     98.33
08:53:07 PM     all      0.69      0.00      0.40      0.00      0.00     98.91
08:53:12 PM     all      0.61      0.00      0.36      0.00      0.00     99.03
08:53:17 PM     all      1.33      0.00      0.44      0.00      0.00     98.23
```

---

### Post by paul_in_london on 2011-10-22
And mine:

```
paul@precise-64:~$ sar 5 12
Linux 3.1.0-1-generic (precise-64)      22/10/11        _x86_64_        (2 CPU)

15:24:21        CPU     %user     %nice   %system   %iowait    %steal     %idle
15:24:26        all     49.45      0.00     12.29      0.00      0.00     38.26
15:24:31        all     48.75      0.00     14.41      0.20      0.00     36.64
15:24:36        all     47.70      0.00     13.90      0.00      0.00     38.40
15:24:41        all     51.35      0.00     11.91      0.10      0.00     36.64
15:24:46        all     51.45      0.00     12.79      0.00      0.00     35.76
15:24:51        all     52.80      0.00     11.50      0.00      0.00     35.70
15:24:56        all     49.70      0.00     12.20      0.00      0.00     38.10
15:25:01        all     50.80      0.00     12.10      0.00      0.00     37.10
15:25:06        all     51.20      0.00     11.62      0.00      0.00     37.17
15:25:11        all     50.15      0.00     11.59      0.00      0.00     38.26
15:25:16        all     48.80      0.00     12.60      0.00      0.00     38.60
15:25:21        all     50.55      0.00     11.91      0.00      0.00     37.54
Average:        all     50.23      0.00     12.40      0.03      0.00     37.35
paul@precise-64:~$
```

---

### Post by VinDSL on 2011-10-22
Hrm...

I just reinstalled Linux 3.0.0-12.20

Here are the results (broken down):


[COLOR="DarkOrange"]**_Sitting idle @ desktop_**[/COLOR]
```
vindsl@Zuul:~$ sar 5 12
Linux 3.0.0-12-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

02:05:52 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
02:05:57 PM     all     19.02      0.00      3.90      0.00      0.00     77.08
02:06:02 PM     all     21.58      0.00      4.50      0.00      0.00     73.93
02:06:07 PM     all     15.70      0.00      3.60      0.00      0.00     80.70
02:06:12 PM     all     18.40      0.00      3.40      0.20      0.00     78.00
02:06:17 PM     all     20.92      0.00      4.20      0.00      0.00     74.87
02:06:22 PM     all     16.13      0.00      3.11      0.20      0.00     80.56
02:06:27 PM     all     18.58      0.00      4.20      0.00      0.00     77.22
02:06:32 PM     all     22.08      0.10      5.09      2.30      0.00     70.43
02:06:37 PM     all     15.42      0.00      3.90      0.20      0.00     80.48
02:06:42 PM     all     19.00      0.00      3.90      0.20      0.00     76.90
02:06:47 PM     all     21.22      0.00      3.70      0.10      0.00     74.97
02:06:52 PM     all     15.07      0.00      3.29      0.00      0.00     81.64
Average:        all     18.59      0.01      3.90      0.27      0.00     77.23
vindsl@Zuul:~$

```


[COLOR="DarkOrange"]**_Logging into Facebook_**[/COLOR]
```
vindsl@Zuul:~$ sar 5 12
Linux 3.0.0-12-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

02:07:26 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
02:07:31 PM     all     27.97      0.10      7.39      0.40      0.00     64.14
02:07:36 PM     all     16.82      0.00      4.90      0.90      0.00     77.38
02:07:41 PM     all     49.35      0.00     28.27      0.10      0.00     22.28
02:07:46 PM     all     48.30      0.00     10.50      0.90      0.00     40.30
02:07:51 PM     all     16.40      0.00      4.20      0.20      0.00     79.20
02:07:56 PM     all     28.37      0.00      6.39      0.50      0.00     64.74
02:08:01 PM     all     45.49      0.00     10.12     17.33      0.00     27.05
02:08:06 PM     all     73.53      0.00     10.89      1.30      0.00     14.29
02:08:11 PM     all     77.60      0.00     12.00      1.60      0.00      8.80
02:08:16 PM     all     75.38      0.00      8.51      1.30      0.00     14.81
02:08:21 PM     all     74.35      0.00      8.72      3.81      0.00     13.13
02:08:26 PM     all     54.35      0.00     11.81     18.92      0.00     14.91
Average:        all     48.99      0.01     10.31      3.93      0.00     36.76
vindsl@Zuul:~$

```


[COLOR="DarkOrange"]**_Loading Cafe World (Zynga) Flash game on Facebook_**[/COLOR]
```
vindsl@Zuul:~$ sar 5 12
Linux 3.0.0-12-generic (Zuul) 	10/22/2011 	_i686_	(2 CPU)

02:08:29 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
02:08:34 PM     all     50.85      0.00     12.99     19.98      0.00     16.18
02:08:39 PM     all     63.56      0.00     11.91      8.81      0.00     15.72
02:08:44 PM     all     55.66      0.00     12.41     13.31      0.00     18.62
02:08:49 PM     all     55.06      0.00     11.01     13.11      0.00     20.82
02:08:54 PM     all     44.04      0.09     14.74     34.12      0.00      7.02
02:08:59 PM     all     17.53      0.00      5.40     71.66      0.00      5.40
02:09:04 PM     all      3.95      0.00      3.16     89.33      0.00      3.56
02:09:09 PM     all      6.95      0.00      1.74     91.31      0.00      0.00
02:09:14 PM     all     17.42      0.00      5.11     63.56      0.00     13.91
02:09:19 PM     all     54.71      0.00      9.72     19.04      0.00     16.53
02:09:24 PM     all     61.30      0.00     10.70      6.90      0.00     21.10
02:09:29 PM     all     69.50      0.00     11.20      2.30      0.00     17.00
Average:        all     41.80      0.01      9.25     36.00      0.00     12.94
vindsl@Zuul:~$
```


Linux 3.1.0-1-generic locks up this machine for 5 minutes (or hard locks it) doing this drill.  Bam, fail, loser!

Linux 3.0.0-12-generic lags out for about 20-30 seconds, and recovers nicely, once the game is fully loaded.

I judge this ancient iron isn't ready for Linux 3.1 yet... ;)

Thanks, all!

---

### Post by ventrical on 2011-10-22
dale@ubuntu:~$ sar 5 12
Linux 3.1.0-1-generic (ubuntu)     11-10-22     _i686_    (2 CPU)

05:38:13 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
05:38:18 PM     all      9.30      0.00      4.90      4.60      0.00     81.20
05:38:23 PM     all      4.30      0.00      3.60      0.30      0.00     91.81
05:38:28 PM     all      3.50      0.00      2.80      0.00      0.00     93.69
05:38:33 PM     all     14.50      0.00     18.80      0.40      0.00     66.30
05:38:38 PM     all      3.31      0.00      3.41      0.20      0.00     93.08
05:38:43 PM     all      9.57      0.00      3.99      0.20      0.00     86.24
05:38:48 PM     all     19.92      0.00     10.41      0.20      0.00     69.47
05:38:53 PM     all      7.61      0.00      4.20      0.30      0.00     87.89
05:38:58 PM     all      5.69      0.00      3.40      0.80      0.00     90.11
05:39:03 PM     all      9.90      0.00     12.60      0.20      0.00     77.30
05:39:08 PM     all      5.21      0.00      8.81      0.00      0.00     85.99
05:39:13 PM     all     10.41      0.00      3.20      0.20      0.00     86.19
Average:        all      8.60      0.00      6.68      0.62      0.00     84.10
dale@ubuntu:~$ 


 I have some video problems with the new kernel. You tube works great but when I log on to CBSNEWS and then try to watch the video it goes all buggy. I too had a major freeze up earlier. I'll try to get up that video.

---

### Post by ventrical on 2011-10-22
Heres the video.

[http://www.youtube.com/watch?v=udZD9c5bO3I](http://www.youtube.com/watch?v=udZD9c5bO3I)

 It only happens with the new RC kernel in Precise.  Also, desktop recorder is working but when you try to send a recorded desktop .ogg it will just produce the green youtube screen of death. GYSOD ! :)

 I think there is a real bug here.

---

### Post by VinDSL on 2011-10-23
Been using Linux 3.0.0-12-generic for the past day.

This machine is acting normal again - totally consistent with previous behavior.

I'm still getting some slowness, when loading complex Flash games, but no lock ups.

This is my "new normal", I guess.  LoL!  :D

I'll wait a week or two, before giving Linux 3.1 another whirl...

---

### Post by xyzzyman on 2011-10-23
> **VinDSL said:**
> Been using Linux 3.0.0-12-generic for the past day.

This machine is acting normal again - totally consistent with previous behavior.

I'm still getting some slowness, when loading complex Flash games, but no lock ups.

This is my "new normal", I guess.  LoL!  :D

I'll wait a week or two, before giving Linux 3.1 another whirl...

I came here to add the same thing. No slowness here with 3.0 and all system hangs resolved upon rollback.

---

### Post by VinDSL on 2011-10-24
> **xyzzyman said:**
> I came here to add the same thing. No slowness here with 3.0 and all system hangs resolved upon rollback.
Sweet!

I'll mark this one as solved. :)

---

### Post by fjgaude on 2011-10-24
> **tista said:**
> Here is mine ;) :
```
tista@VPCZ21AJ:~$ sar 5 12
Linux 3.1.0-1-generic (VPCZ21AJ) 	10/22/2011 	_x86_64_	(4 CPU)

08:52:22 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
08:52:27 PM     all      1.15      0.00      0.40      0.05      0.00     98.40
08:52:32 PM     all      0.80      0.00      0.40      0.00      0.00     98.80
08:52:37 PM     all      1.10      0.00      0.63      0.00      0.00     98.27
08:52:42 PM     all      0.80      0.00      0.40      0.00      0.00     98.81
08:52:47 PM     all      0.82      0.00      0.38      0.00      0.00     98.80
08:52:52 PM     all      0.92      0.00      0.46      0.05      0.00     98.58
08:52:57 PM     all      0.79      0.00      0.59      0.00      0.00     98.62
08:53:02 PM     all      1.11      0.00      0.56      0.00      0.00     98.33
08:53:07 PM     all      0.69      0.00      0.40      0.00      0.00     98.91
08:53:12 PM     all      0.61      0.00      0.36      0.00      0.00     99.03
08:53:17 PM     all      1.33      0.00      0.44      0.00      0.00     98.23
```

Yours is a lot better than mine:
```
frank@cutie:~$ sar 5 12
Linux 3.0.0-12-generic (cutie) 	10/24/2011 	_x86_64_	(4 CPU)

03:16:44 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
03:16:49 PM     all      5.05      0.00     10.64      0.05      0.00     84.26
03:16:54 PM     all      5.39      0.00     10.63      0.10      0.00     83.87
03:16:59 PM     all      6.10      0.00     11.04      3.15      0.00     79.71
03:17:04 PM     all      5.95      0.00     11.51      1.40      0.00     81.14
03:17:09 PM     all      5.64      0.00     10.49      0.20      0.00     83.67
03:17:14 PM     all      5.90      0.00     11.31      0.10      0.00     82.69
03:17:19 PM     all      5.55      0.00     10.95      0.10      0.00     83.40
03:17:24 PM     all      5.80      0.00     11.10      0.10      0.00     83.00
03:17:29 PM     all      5.20      0.00     10.85      0.10      0.00     83.85
03:17:34 PM     all      5.55      0.00     11.10      0.20      0.00     83.15
03:17:39 PM     all      5.55      0.00     11.10      0.10      0.00     83.25
03:17:44 PM     all      5.55      0.00     11.15      0.20      0.00     83.10
Average:        all      5.60      0.00     10.99      0.48      0.00     82.92
```

Tista, you have a fast box.

---

### Post by effenberg0x0 on 2011-10-24
Seems stable here. Clementine does create some random cpu usage though.

```

[08:53 ][al:AL-DESK:/usr/share/applications]
$ sar 5 12
Linux 3.1.0-030100-generic (AL-DESK)     24-10-2011     _x86_64_    (6 CPU)

20:53:49        CPU     %user     %nice   %system   %iowait    %steal     %idle
20:53:54        all      2,46      0,10      2,83      0,00      0,00     94,61
20:53:59        all      2,52      0,00      1,57      0,03      0,00     95,88
20:54:04        all      2,04      0,00      1,27      0,13      0,00     96,56
20:54:09        all      2,30      0,07      2,86      3,78      0,00     90,99
20:54:14        all      2,65      0,00      1,27      0,21      0,00     95,87
20:54:19        all      2,00      0,00      1,42      0,13      0,00     96,46
20:54:24        all      2,41      0,07      3,02      0,14      0,00     94,37
20:54:29        all      2,67      0,00      1,30      0,14      0,00     95,89
20:54:34        all      1,95      0,00      1,44      0,00      0,00     96,62
20:54:39        all      2,81      0,00      1,66      0,73      0,00     94,80
20:54:44        all      2,63      0,17      2,50      0,13      0,00     94,57
20:54:49        all      2,15      0,00      1,15      0,29      0,00     96,41
Average:        all      2,37      0,03      1,85      0,48      0,00     95,26

[08:54 ][al:AL-DESK:/usr/share/applications]
$ 

```

---

