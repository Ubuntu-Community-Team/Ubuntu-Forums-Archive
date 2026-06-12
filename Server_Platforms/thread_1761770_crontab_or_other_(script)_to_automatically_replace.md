---
title: "crontab or other (script) to automatically replace file"
date: 2011-05-18
forum: Server Platforms
---

### Post by Karchion on 2011-05-18
I have been searching for a few hours now trying to figure out the best way to have Ubuntu Server 8.10 copy and replace a file every week.

So for example:

File A (original file)

File B (replacement file)

I would want to copy File B from its location and replace File A each week automatically with out removing or destroying File B.

I've thought of doing a cron since I already have a job set for email piping. but I'm unsure of the best way to complete this task.

Any Ideas?

Thanks,

Karchion

---

### Post by DaithiF on 2011-05-18
Hi, add an entry to your crontab (ie, run crontab -e)

eg. something like:
```
0 7 * * 1 cp /path/to/fileB /path/to/fileA
```
would copy b onto a at 7am each Monday.

the 5 date/time fields are: minute, hour, day of month, month, day of week (0 = sunday)

---

### Post by Karchion on 2011-05-18
> **DaithiF said:**
> Hi, add an entry to your crontab (ie, run crontab -e)

eg. something like:
```
0 7 * * 1 cp /path/to/fileB /path/to/fileA
```would copy b onto a at 7am each Monday.

the 5 date/time fields are: minute, hour, day of month, month, day of week (0 = sunday)


Thank you,

So with that said I have one more twist that I'm not sure can be accomplished....

Lets say I have

File A

File B

File C

File D

I want File A to copy and replace D week one, File B to copy and replace the already replaced file D on week two, File C to replace D (already replaced twice) on week three, and then to start over again on the following week.

So in summary I want D to be replaced by File A,B,C on every third week corresponding to the last time it replaced D.

I again have thought about this for many hours and have not come to a good conclusion. I dont think it may be possible

---

### Post by Karchion on 2011-05-18
I was thinking that this could be fully automated, however it does not appear that can be the case, I think the only way to get this to work is to set the dates of the replacement.

```


0 8 25 5 * cp /path/to/file A /path/to/file D

0 8 1 6 * cp /path/to/file B /path/to/file D

0 8 8 6 * cp /path/to/file C /path/to/file D

0 8 15 6 * cp /path/to/file A /path/to/file D


```

---

### Post by DaithiF on 2011-05-18
you can automate it.

figure out what week it is using the date command, and depending on the result pick the right file to copy.

date +%U gives week of the year, but you would hit a problem at the end of the year when week number rolls from 52 to 0 ... your sequence would go awry at this point.

so the more robust way would be to look at seconds since the epoch, and do some arithmetic based on that to decide if today is in week 0, 1 or 2

there are 604,000 seconds in a week, and therefore 1,814,400 seconds in 3-week period.  so a calculation of:
(seconds since epoch % 1814400) / 604000 will give a result of either 0, 1, or 2.

putting this into a script:
```

#!/bin/bash
seconds=$(date +%s)
seconds_in_week=604000
seconds_in_3weeks=1814400

result=$(( $seconds % seconds_in_3weeks / $seconds_in_week ))
case $result in
  0)
  file=B;;
  1)
  file=C;;
  2)
  file=A;;
esac
echo cp /path/to/$file /path/to/D

```

test it for various dates by using the -d parameter to the date line, e.g.:
```
seconds=$(date -d "25 may 2011" +%s)

```and once happy remove the echo prefix to the copy line.

your (single) cron job then just needs to call this script once each week.

---

### Post by Karchion on 2011-05-18
> **DaithiF said:**
> you can automate it.

figure out what week it is using the date command, and depending on the result pick the right file to copy.

date +%U gives week of the year, but you would hit a problem at the end of the year when week number rolls from 52 to 0 ... your sequence would go awry at this point.

so the more robust way would be to look at seconds since the epoch, and do some arithmetic based on that to decide if today is in week 0, 1 or 2

there are 604,000 seconds in a week, and therefore 1,814,400 seconds in 3-week period.  so a calculation of:
(seconds since epoch % 1814400) / 604000 will give a result of either 0, 1, or 2.

putting this into a script:
```

#!/bin/bash
seconds=$(date +%s)
seconds_in_week=604000
seconds_in_3weeks=1814400

result=$(( $seconds % seconds_in_3weeks / $seconds_in_week ))
case $result in
  0)
  file=B;;
  1)
  file=C;;
  2)
  file=A;;
esac
echo cp /path/to/$file /path/to/D

```test it for various dates by using the -d parameter to the date line, e.g.:
```
seconds=$(date -d "25 may 2011" +%s)

```and once happy remove the echo prefix to the copy line.

your (single) cron job then just needs to call this script once each week.


I have to say Ingenious!

Thank You so much for your insight..... I would have never thought to break it down to seconds and I have tested the script since today is the day it would take effect and it worked perfectly.

Again Thank You

---

