---
title: "cron script brings system to its knees"
date: 2009-01-03
forum: Server Platforms
---

### Post by osjak on 2009-01-03
I have an Ubuntu web server. Recently I have wrote a simple shell script to backup the web directory and dump the MySQL database. Those two are gzipped individually, then tarred into one tarball, it gets encrypted, split into 700Mb chinks and transferred to an off-site storage server. The script does the job correctly when it's started from console and as a cron job. The only difference is that when it is started by cron, it takes all systems resources and my website stops responding for the time it is running. Here is what dstat shows:
```
admin@www1:~$ dstat
----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| read  writ| recv  send|  in   out | int   csw 
 22   2  76   0   0   0|  51k   78k|   0     0 | 0.7B  7.4B|  71   156 
 39  34   0  27   0   0|  15M 1556k|1947B 2140B|   0     0 | 126    46k
 29  24   0  47   0   0|  11M   19M|2726B 1906B|   0     0 | 152    32k
 10  12   0  77   0   1|5128k   32M|3684B 2028B|   0     0 | 281    15k
 38  46   0  16   0   0|  18M   12k|1771B 1143B|   0     0 | 140    53k
 36  26   0  38   0   0|  11M   11M|1536B  522B|   0     0 | 114    31k
 17  32   0  51   0   0|  10M   12M|1158B 1341B|   0     0 | 114    27k
 29  38   0  32   1   0|  11M   18M|1900B 1920B|   0     0 | 134    26k
  7  15   0  78   0   0|4612k   33M|1690B 1083B|   0     0 | 120    13k
 30  59   0  11   0   0|  18M 8192B|1881B 1604B|   0     0 | 144    55k
 29  32   0  39   0   0|  12M   13M| 914B  636B|   0     0 | 128    37k
 19  35   0  44   1   1|  12M   14M|1964B 1718B|   0     0 | 135    35k
 14  24   0  62   0   0|7904k   10M|1945B 6809B|   0     0 | 165    22k
 46   9   0  45   0   0|2968k   32M|1879B 1163B|   0     0 | 130  2054 
 31  34   0  35   0   0|  13M 4416k|1972B   14k|   0     0 | 149    37k
 33  36   0  28   0   3|  15M 7208k|2618B 3943B|   0     0 | 142    44k

```
As you can see the hard drive is maxed out. This doesn't happen when I start the same script manually from an ssh session. Does anyone have any idea on why this is happening?

---

### Post by Spiny Norman on 2009-01-11
Could you give perhaps the version of server you are running and show the scripts?

---

### Post by osjak on 2009-01-11
Norman, thank you for responding. This turned out to be a number of unrelated issues which happened at the same time, just bad timing I guess. One of them was the hosting company network issues, which made the server look non-responding.

---

