---
title: "Need help with Amanda"
date: 2007-11-28
forum: Server Platforms
---

### Post by Bubnoff on 2007-11-28
******UPDATE - SOLVED******* 
Stupid conf file mistake. Here's another good tutorial that I found to be a bit more foolproof.
Its for Debian Etch, but works all the same:
[http://www.howtoforge.com/disk_based_backups_amanda_debian_etch](http://www.howtoforge.com/disk_based_backups_amanda_debian_etch)
********************************************************************************


Well I followed the tutorial here:

[http://ubuntuforums.org/showthread.php?p=2470030](http://ubuntuforums.org/showthread.php?p=2470030)

I'm using Gutsy instead of Dapper. I want to back up to a secondary
HD. It is mounted to /backups. I get this error after running this command (for ((i=1; $i<=9; i++)); do amlabel DailySet1 DailySet1-0$i slot $i; done):

Error:

"/etc/amanda/DailySet1/amanda.conf", line 262: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 262: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 264: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 264: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 266: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 266: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 267: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 268: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 286: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 286: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 288: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 288: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 290: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 290: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 291: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 292: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 292: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 293: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 294: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 294: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 295: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 296: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 298: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 298: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 300: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 300: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 302: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 302: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 303: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 304: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 304: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 305: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 306: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 306: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 307: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 308: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 310: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 310: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 312: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 312: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 314: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 314: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 315: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 316: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 316: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 317: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 318: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 318: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 319: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 320: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 322: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 322: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 324: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 324: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 326: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 326: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 327: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 328: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 328: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 329: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 330: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 330: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 331: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 332: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 334: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 334: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 336: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 336: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 339: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 339: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 340: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 341: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 341: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 342: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 343: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 343: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 344: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 345: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 347: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 347: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 349: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 349: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 351: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 351: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 352: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 353: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 353: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 354: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 355: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 355: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 356: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 357: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 359: DUMPTYPE, INTERFACE or TAPETYPE expected
"/etc/amanda/DailySet1/amanda.conf", line 359: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 361: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 361: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 363: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 363: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 364: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 365: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 365: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 366: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 367: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 367: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 368: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 369: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 121: tapetype HARDDISK not defined
amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"

My conf is attached;

Thanks -

Bub

PS: line numbers do not correspond to error as I had to
cut it down in order to attach it.

---

