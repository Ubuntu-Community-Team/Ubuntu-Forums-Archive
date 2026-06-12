---
title: "rsync log files"
date: 2013-02-27
forum: Server Platforms
---

### Post by OrangeMadness on 2013-02-27
I am running the following command every 5 minutes:

```
rsync -av --filter='include */*_???_det*' --filter='-! */' --log-file="/usr/local/rsync/rsync.log.$(date +%Y%m%d%H%m%S)" /mnt/processed/data/ /usr/local/rad-data/
```      *******
      A nice time-saving tip here for those who might want to use rsync at some stage:
      I was trying to filter the files I am synchronising with --filter='include */*_???_det*'  this
      did not work until i excluded everything else with --filter='-! */'  
      *******

Onward with my questions:

1. Athough I am running this every five minutes rsync is grouping my log files hourly:

```
-rw-r--r--  1 eclipse adm  48824 Feb 27 06:55 rsync.log.20130227**06**0201
-rw-r--r--  1 eclipse adm  48180 Feb 27 07:55 rsync.log.20130227**07**0201
-rw-r--r--  1 eclipse adm  45131 Feb 27 08:50 rsync.log.20130227**08**0201
```It would be so much better if I could get one log file for each every 5min occurring transaction.

2. There is a lot of redundant information in there

Small part of the log file:
```
2013/02/27 08:55:12 [8003] .d....og... 20130225/
2013/02/27 08:55:12 [8003] .d....og... 20130226/
2013/02/27 08:55:12 [8003] .d..t.og... 20130227/
2013/02/27 08:55:12 [8003] >f+++++++++ 20130227/20130227_065252_20130227_064809_433_det.csv
2013/02/27 08:55:12 [8003] >f+++++++++ 20130227/20130227_065354_20130227_065307_437_det.csv
```Apparrently:
.d....og...  means the directory is in sync
.d..t.og...  means changes have been made to this dir
f+++++++++ means file copied to directory

I would like to keep only f+++++++++ entries, and just maybe .d..t.og... entries as this is quite a big list (a directory for every day of the year) and previous days don't really matter.


Thanks for looking, any help appreciated.

---

### Post by papibe on 2013-02-27
Hi OrangeMadness.

You are repeating month (%m) instead of minute (%M) on the minute part.

Change it, and should work:
```
$(date +%Y%m%d%H**[COLOR="Red"]%M[/COLOR]**%S)
```
Let us know how it goes.
Regards.

---

### Post by OrangeMadness on 2013-02-27
> **papibe said:**
> Hi OrangeMadness.

You are repeating month (%m) instead of minute (%M) on the minute part.

Change it, and should work:
```
$(date +%Y%m%d%H**[COLOR=Red]%M[/COLOR]**%S)
```Let us know how it goes.
Regards.

Works like a charm now :D

```

-rw-r--r--  1 eclipse adm  3877 Feb 27 09:40 rsync.log.2013022709**40**01
-rw-r--r--  1 eclipse adm  4153 Feb 27 09:45 rsync.log.2013022709**45**01

```Got a little bit scared with first log file
```
2013/02/27 09:40:13 [8178] .d..t.og... 20130227/
```Apparently something has been modified and I don't have any >f+++++++++ entries
```

-rwxr-xr-x  1 eclipse adm     34 Feb 27 09:40 20130227_074032_20130227_073808_439_det.csv
-rwxr-xr-x  1 eclipse adm     34 Feb 27 09:40 20130227_074059_20130227_073831_433_det.csv
```Two files added with that rsync...

```
2013/02/27 09:45:12 [8217] >f+++++++++ 20130227/20130227_074032_20130227_073808_439_det.csv
2013/02/27 09:45:12 [8217] >f+++++++++ 20130227/20130227_074059_20130227_073831_433_det.csv
2013/02/27 09:45:12 [8217] >f+++++++++ 20130227/20130227_074336_20130227_074307_437_det.csv
```All information included in the next file, so no problem! 

Thank you papibe!

---

### Post by marty331 on 2013-03-14
Adding this parameter is exactly what I needed!


 --log-file="/home/user/rsync/rsync.log.$(date +%Y%m%d%H%m%S)"

---

### Post by papibe on 2013-03-14
Note that your using the month on the minute part again.

---

