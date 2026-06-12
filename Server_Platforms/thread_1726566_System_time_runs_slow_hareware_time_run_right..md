---
title: "System time runs slow hareware time run right."
date: 2011-04-11
forum: Server Platforms
---

### Post by Raymond Day on 2011-04-11
I am running my Ubuntu 32 bit server on top of Windows 7 64 bit with VirualBox. It's a 2 core Atom.

It's been working good for about half a year. But the last about 6 weeks the system time only in Ubuntu is going slow. About -8 per 24 hours! I can only guess because I have more things running in my Windows 7 and Ubuntu.

I can set it right by coping the hareware time to system time with this command:

```
hwclock --hctosys
```

I want to run a crontab to have that command run every minute. But it don't seem to run.

I do:

```
crontab -e
```

My code looks like this:

```
* * * * * /hwclock --hctosys
#Set hareware time to system time every minute.
```

Wait a minute or longer and do ```
date
``` the time still is wrong.

So I guess the cron job is not running. What am I doing wrong?

-Raymond Day

---

### Post by SeijiSensei on 2011-04-11
The correct path is /sbin/hwclock, however you'd be much better off on a server running **[ntpd]("https://help.ubuntu.com/8.04/serverguide/C/NTP.html")**.

---

### Post by Raymond Day on 2011-04-11
The hareware clock stays at the right time. But the system time goes way to slow. Look at what I typed on this command line.

```
root@small:/etc/cron.d# hwclock -r
Mon 11 Apr 2011 11:22:42 AM EDT  -0.752376 seconds
root@small:/etc/cron.d# date
Mon Apr 11 11:16:38 EDT 2011
root@small:/etc/cron.d#
```

I just like to run a cron job about every min. or 5 min. But it's just not working.

I can set the time right on the command line with:

```
hwclock --hctosys
```

Right now my cron job file looks like this:

> 0-59 * * * * hwclock --hctosys #Set hareware time to system time every minute.

But I am not sure it every runs. At lest not every minute like I want it to. That would keep the system time right from the hareware time.

-Raymond Day

Just after I typed the last reply it seems like it's working now.

```
root@small:/etc/cron.d# hwclock -r
Mon 11 Apr 2011 11:34:03 AM EDT  -0.104052 seconds
root@small:/etc/cron.d# date
Mon Apr 11 11:33:57 EDT 2011
root@small:/etc/cron.d#
```

Time will tell if the time stays right now.

-Raymond Day

I made a new cron job that now looks like this reading it with "crontab -e":

```
0,2,4,6,8,10,12,14,16,18,20,22,24,26,28,30,32,34,36,38,40,42,44,46,48,50,52,54,56,58 * * * * hwclock -s #Every 2 minutes set system clock with harwere clock that is right.
```

I waited and did "date" command and it's still off.

Any one know if this is a good way to do this? Or is there some better way?

I just don't get why the cron job is not doing the hwclock -s every 2 minutes with the cron job.

-Raymond Day

To show for sure I did this:

```
root@small:/etc/cron.d# hwclock -r
datTue 12 Apr 2011 02:14:38 AM EDT  -0.292146 seconds
eroot@small:/etc/cron.d# date
Tue Apr 12 02:09:02 EDT 2011
root@small:/etc/cron.d#
```

I typed the "date" as it was still righting out the hwclock -r command.

The 2:14 AM time is right. The 2:09 AM is wrong and that's the system clock.

-Raymond Day

Looks like a full reboot fixed it!

It's been like this for 6 hours now and the time is staying right.

I rebooted Windows 7 and then started VirtualBox again.

Here is the same command line test and it's right now.

```
root@small:~# hwclock -r
datTue 12 Apr 2011 02:23:07 PM EDT  -0.638946 seconds
eroot@small:~# date
Tue Apr 12 10:23:07 EDT 2011
root@small:~#
```

I don't know mybe it will go off again with time. If so I will just reboot the hole thing.

I still don't get why a small test script I did is not running every 2 min. I set the cron job to run it. It looks like this:

```
#!/bin/bash
hwclock -s
clear
echo "It works"
```

But I never get the It works back on the command line. It should every 2 min.

But looks like I don't need this any more. I still like to know why my cron job don't run it?

-Raymond Day

---

### Post by rubylaser on 2011-04-12
**ntpd** as suggested previously is the preferred method to keep your clock in sync. 

But, the reason, your cron job was failing is you need to provide **full paths** to items to have them work via cron.  Here's a revised version of yours that would work (add run every 2 minutes, without listing out every 2 minute increment, and with the full path to hwclock.

```
*/2 * * * * /sbin/hwclock -s
```

---

### Post by Raymond Day on 2011-04-12
Thank you rubylaser.

Installed Install Guest Additions like a CD rom drive and with that VirtualBox reads my Windows 7 clock. Now the time should be right.

Looks like it's working good now. Stays right on time now.

---

### Post by Raymond Day on 2011-08-05
I thought the Guest Additions fixed the time. So about 2 weeks ago I deleted the cron job I still had. About a week after that I seen how the clock started to not keep time. To fast. So it must of been the cron job I had that worked.

But I deleted it and now it don't work and I with I would of copied it because now I can't get a cron job to work again. I like to have it set the system time with the hardware time every min.

But reading this I just did the path to the job and tested it like this:

```
root@small:~# date
Fri Aug  5 19:42:44 EDT 2011
root@small:~# date
Fri Aug  5 19:38:28 EDT 2011
root@small:~#
```

So it's working now. That last one set the time right. My cron job looks like this.

```
root@small:~# crontab -l
* * * * * /sbin/hwclock -s #Set hareware time to system time every minute.
```

This my help others I think if they run into something like this.

It should be fixed now.

-Raymond Day

---

