---
title: "Harddisk spindown"
date: 2010-12-26
forum: Server Platforms
---

### Post by pvi on 2010-12-26
Im running Ubuntu server 10.10 as a NAS. To save my harddisk I want it to go to sleep after some period of inactivity (only harddisk, not whole system). To do this I installed laptop-mode tools and enabled the writecache (should wait 6 min before flushing with LM_AC_MAX_LOST_WORK_SECONDS conf parameter). But after the disk goes into sleep mode, it activates within a minute again.
 
I've tested this several times with the command sudo hdparm -y /dev/sda.
 
I thought maybe processes writing to disk was the reason for this, so I monitored the disk io for a certain period with iotop -o -b to see which processes did write to disk. This is the output for several minutes:
 
```

  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
 1889 be/4 root        0.00 B/s    3.80 K/s  0.00 %  0.00 % perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
 8701 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % sh /usr/share/awstats/tools/update.sh
  276 be/3 root        0.00 B/s  106.02 K/s  0.00 %  6.23 % [jbd2/sda1-8]
 8699 be/4 syslog      0.00 B/s   15.15 K/s  0.00 %  0.00 % rsyslogd -c4
  276 be/3 root        0.00 B/s   34.03 K/s  0.00 % 15.64 % [jbd2/sda1-8]
 8699 be/4 syslog      0.00 B/s   22.68 K/s  0.00 %  0.00 % rsyslogd -c4
 1243 be/4 postfix     0.00 B/s    0.00 B/s  0.00 %  0.00 % qmgr -l -t fifo -u
 1889 be/4 root        0.00 B/s    3.80 K/s  0.00 %  0.00 % perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
 8817 be/4 root        0.00 B/s  121.07 K/s  0.00 %  0.00 % webmincron.pl
 8817 be/4 root        0.00 B/s    3.79 K/s  0.00 %  0.00 % webmincron.pl
 8817 be/4 root        0.00 B/s   53.04 K/s  0.00 %  0.00 % [miniserv.pl]
 1889 be/4 root        0.00 B/s    3.80 K/s  0.00 %  0.00 % perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf

```
 
Its all in KB, so not much writing. I would expect the write cache big enough to handle this. The thing is, I cant figure out how big the write cache is. I mean the one in Ubuntu (I assume there is one), not of the drive itself.
 
Can anyone help me with this?

---

### Post by HermanAB on 2010-12-26
Howdy,

You have to stop the syslog daemon if you want the disk to spin down.

---

### Post by pvi on 2010-12-26
Hi,
 
Ok, but I'm not very familiar with unix. How can best do that (and that it stays of after reboot)? I have Webmin, should I set all the logs to 'Not Active'? Or just remove the /etc/init.d/rsyslog file?
 
The log is not needed for anything?

---

### Post by Vegan on 2010-12-26
disk vendors have low power drives, this way if they are busy they still do not draw a lot.

disks seem to be getting better and better for power consumption, in contrast to CPU and GPU offerings.

RAM can also be power hungry so avoid the fastest sticks and pick lower latency sicks.

---

### Post by pvi on 2010-12-26
But the reason is more to save the life of my harddisk not the power consumption (red some articles which state that constantly spinning disks will shorten its life considerably).
 
I set all my system logs to 'Not Active', but the disk still turns back within a minute.
 
Seems like webmin is giving trouble:
```

1876 be/4 root        0.00 B/s    3.79 K/s  0.00 %  0.00 % perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf

```
 
this is shown by iotop just before disk becomes active again.
 
Still dont understand why this isnt handled by the write cache.

---

### Post by HermanAB on 2010-12-27
Howdy,

You got to stop the syslog daemon with chkconfig for example.  There is a wizard for it somewhere.  Otherwise, every few seconds, some process will create a log message and syslog will write to the disk, so it will never spin down.

---

### Post by pvi on 2010-12-27
Disabled rsyslog with webmin. chkconfig shows following:
```
rsyslog                     off

```
So thats ok I guess.
 
But webmin seems to be the problem. Every minute miniserv.pl does something (see two posts up) that gets thedrive out of standby. Any suggestions for that (apart from maybe try to get webmin to work on apache2 or disable webmin all together)?

---

### Post by psusi on 2010-12-27
If you don't care about the power savings, then just forget about standby mode.  Hard disks are meant to spin for years; it is the starting and stopping that wears them out.  Also the drive write cache does not matter; as soon as you ask it to read or write, it spins up.

---

### Post by cariboo on 2010-12-27
I agree with psusi, hard drives are eventually going to die, purchase drives with a good 3-5 year warranty, and keep good/current backups.

---

### Post by Vegan on 2010-12-27
I backup daily. Take it from me, its worth the aggravation the day when the system croaks.

---

### Post by pvi on 2010-12-28
Ok, I'll leave it spinning I guess.

---

### Post by Probedriver on 2011-02-05
Go to 'Webin Configuration' -> 'Background Status Collection'

and set 
'[B]Collect system status in background' to Never
and 
'[/B][B]Collect available package updates' to No 

this will solve the problem 
[/B]

---

### Post by tiep on 2011-08-08
OK, I am trying to eliminate the disc writes from webmin.  I tried setting:

'[B]Collect system status in background' to Never
[/B]and [B]
'[/B][B]Collect available package updates' to No 

[/B]The problem remains - iotop shows  periodic disc writes resulting from:

**perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf**

Can anyone suggest a way to fix this?

---

### Post by bab1 on 2011-08-08
> **tiep said:**
> ...
Can anyone suggest a way to fix this?

Sure, but your not going to like it.  Get rid of Webmin.  

Applications that are poorly written: that do not take into consideration the needs of the user and are really not needed for the configuration of the server anyway should be removed.  If I'm not mistaken, this is why Webmin was dropped from the repos in the first place.

---

