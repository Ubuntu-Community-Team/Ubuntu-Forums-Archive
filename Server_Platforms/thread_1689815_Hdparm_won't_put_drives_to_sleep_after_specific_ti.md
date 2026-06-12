---
title: "Hdparm won't put drives to sleep after specific time"
date: 2011-02-17
forum: Server Platforms
---

### Post by SJI on 2011-02-17
Folks,

I've just put together a 10.04 server using a GA-D525TUD atom board.
I've installed gnome desktop too.

I'm trying to get 4 sata drives to go into standby, but hdparm seems to be ignoring the settings.

If i issue hdparm -y /dev/sdx the drive duly goes into standby and stays in standby until accessed.

I've put entries in rc.local along with the hdparm.conf settings, but still no joy.

Anyone?

Hdparm.conf:
/dev/sdb {
  spindown_time = 244
}

/dev/sdc {
  spindown_time = 244
}

/dev/sdd {
  spindown_time = 244
}

/dev/sde {
  spindown_time = 244
}

rc.local:
/sbin/hdparm -S 244 /dev/sdb
/sbin/hdparm -S 244 /dev/sdc
/sbin/hdparm -S 244 /dev/sdd
/sbin/hdparm -S 244 /dev/sde

uname -a:
Linux lithium 2.6.32-28-generic-pae #55-Ubuntu SMP Mon Jan 10 22:34:08 UTC 2011 i686 GNU/Linux


Thanks.

---

### Post by psusi on 2011-02-17
244 means don't spin down until after 44 minutes of no activity.  You should use a lower number, like 12, which will give 60 seconds.

---

### Post by SJI on 2011-02-17
244 is 2hrs.

For testing i've tried setting the spindown time to 5 minutes but hdparm doesn't want to play.

---

### Post by psusi on 2011-02-17
> **SJI said:**
> 244 is 2hrs.

For testing i've tried setting the spindown time to 5 minutes but hdparm doesn't want to play.

Opps, I read that backwards.  Either your drive does not support auto standby, or something keeps accessing it.  If you can manually standby and it remains that way, that would eliminate the second possibility.

You might also try -B.  I have heard that some drives will not allow -S with certain values for -B.

---

### Post by SJI on 2011-02-17
The drives are Hitachi HDS722020ALA330.

If i put one of the drives into my other D510MO Atom machine hdparm sends the drive to sleep as expected.

I'll experiment with -B and see where it leads.

---

### Post by koenn on 2011-02-17
> **psusi said:**
> or something keeps accessing it. 


it's a server. It might be doing stuff and logging it, all the time.

---

### Post by SJI on 2011-02-17
> **koenn said:**
> it's a server. It might be doing stuff and logging it, all the time.

All logging and system functions are on /dev/sda

The other 4 drives are simply storage for the lan and nothing is accessing them currently.

---

### Post by SJI on 2011-02-17
> **psusi said:**
> You might also try -B.  I have heard that some drives will not allow -S with certain values for -B.

No joy with -B settings :(

Out of curiosity i've swapped a drive out for a Western Digital Green unit (WDC WD1000FYPS-01ZKB0) and it isn't going to standby either.

---

### Post by SJI on 2011-02-17
More info.


I've stopped the GDM.
Drives are ext2 formatted so that should exclude journalling access.

Still no sleeping.

---

### Post by psusi on 2011-02-17
Ohh, it's udisks checking the SMART status of the drive I bet.  If the drive is in standby, that will wake it up.  Udisks checks to see if the drive is in standby first, and if it is, skips the SMART check.  I bet that the smart check also resets the timeout, and since you are using a timeout longer than the smart check interval, it never goes to standby.

---

### Post by SJI on 2011-02-18
I've almost cracked it.

I've disabled upowerd, udisks and gnome-power-manager and can now spindown 3 of the four drives.

/dev/sdb still refuses to spindown even if it's not mounted :confused:

---

### Post by psusi on 2011-02-18
Why don't you just use a shorter timeout?  Like 10 minutes?

---

### Post by SJI on 2011-02-18
> **psusi said:**
> Why don't you just use a shorter timeout?  Like 10 minutes?

With a 2hr standby time the drives will be spun up once a day if they're accessed at all.  

With a 10 minute standby they'd be up and down all day like a *****'s underwear. :|

---

### Post by psusi on 2011-02-18
> **SJI said:**
> With a 2hr standby time the drives will be spun up once a day if they're accessed at all.  

With a 10 minute standby they'd be up and down all day like a *****'s underwear. :|

How on earth do you figure that?  You would need to have an access pattern where you only touch the disk every 10-20 minutes, over and over for half the day, then don't touch it at all for the next 12 hours.

Most people are either using the system or not.  When they are, they get activity more frequently than once every 10 minutes, and then when they walk away, there's nothing for hours, so you may as well spin down.

---

### Post by SJI on 2011-02-18
> **psusi said:**
> How on earth do you figure that?  You would need to have an access pattern where you only touch the disk every 10-20 minutes, over and over for half the day, then don't touch it at all for the next 12 hours.

Most people are either using the system or not.  When they are, they get activity more frequently than once every 10 minutes, and then when they walk away, there's nothing for hours, so you may as well spin down.


I work on my local drives almost all of the time and periodically I update lan storage. Easily giving over 10 minutes between accesses to the shares.

2hr spindown time suits my access pattern.

---

### Post by psusi on 2011-02-18
> **SJI said:**
> I work on my local drives almost all of the time and periodically I update lan storage. Easily giving over 10 minutes between accesses to the shares.


Then let it spin down after 2 minutes, then it can spend the next half hour resting ;)

A dozen or two start/stops a day won't hurt the drive.

---

### Post by SJI on 2011-02-18
> **psusi said:**
> Then let it spin down after 2 minutes, then it can spend the next half hour resting ;)

A dozen or two start/stops a day won't hurt the drive.

Interestingly the minimum spindown time on a 1TB WD green drive is 10 minutes.
If you specify a -S value lower than this it assumes 10 minutes.

I've got a script running at the moment that will email me as each drive changes it's state. First drive has just gone to standby on queue :D

It should also show if the drives get woken up periodically overnight by errant processes.

---

### Post by jobsonandrew on 2011-09-28
Thanks very much SJI for pointing out the 10 minute minimum value. I have a 2TB WD green power and used this command:

```
sudo hdparm -S121 /dev/sdb
```
10 mins plus 5 secs for good luck ;)

works very well. I understand that this isn't persistent after a reboot though, so I'll add the command to my /etc/rc.local

thanks again

---

### Post by rubylaser on 2011-09-28
You could just add it to your /etc/hdparm.conf file like this...

```
/dev/sdb {
spindown_time = 121
}
```

That will run it automatically at boot.

---

