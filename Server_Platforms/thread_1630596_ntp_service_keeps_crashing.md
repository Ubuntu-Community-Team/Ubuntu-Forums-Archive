---
title: "ntp service keeps crashing"
date: 2010-11-25
forum: Server Platforms
---

### Post by surfer on 2010-11-25
i have an ubuntu 10.10 installation on a (tiny) server. unfortunately the onboard clock runs way off when the computer is not running (i did buy a new battery but that didn't help much).

so i set up the ntp server in order to get the time right when the server starts from hibernation (and its system time is way off). but ntp crashes with the following error message:
```
$ grep ntp /var/log/syslog 
Nov 21 23:36:27 alix1c ntpd[1900]: time correction of 70551 seconds exceeds sanity limit (1000); set clock manually to the correct UTC time.

```
the [manpage]("http://manpages.ubuntu.com/manpages/maverick/man8/ntpd.8.html") says that this should not happen (at least not the first time), if i start the service with the '-g' option. and indeed, my /etc/default/ntp lists this as option.

so, is there a way to get the time set without having the server crash every time?

---

### Post by SeijiSensei on 2010-11-25
> **surfer said:**
> ```
$ grep ntp /var/log/syslog 
Nov 21 23:36:27 alix1c ntpd[1900]: time correction of 70551 seconds exceeds sanity limit (1000); set clock manually to the correct UTC time.
```

First set the time manually like this:

```
date --set='18:00:00 25-nov-2010'
```

You don't need to be precise, but try to be within five minutes of the actual time.

Next, run ntpdate to set the correct time in the OS:

```
ntpdate 0.pool.ntp.org
```

This uses one of the many NTP servers in the ntp.org pool.  Now fix your hardware clock like this:

```
hwclock --systohc
```

This sets the hardware clock to the system time that you set via ntpdate.  Given you have problems with the clock in your computer, I'd run hwclock at least once or twice a day from a cron job.  Once your clock is reasonably close to the actual time, ntpd should work correctly.

---

### Post by surfer on 2010-11-25
ok, i tried
```
$ sudo hwclock --systohc
```
and will check how that behaves next time i wake the server from hibernation.

i may try to set this up in a cron job if it works.

thanks a lot, SeijiSensei.

---

### Post by SeijiSensei on 2010-11-26
Most shutdown scripts run the "hwclock --systohc" command automatically. If you're really using hibernation instead of a complete shutdown, there's a good chance the hardware clock is never reset properly.  Why would you hibernate a server anyway?  Mine all run 24/7 or are completely shutdown.

---

### Post by surfer on 2010-11-26
it's a [tiny 'server']("http://pcengines.ch/") that i use exclusively to serve music (squeezeboxserver) and movies (mediatomb). there is no need for it to run permanently...

---

### Post by surfer on 2010-11-26
i just booted the device... the time seems to have stopped at the exact moment of the hibernation...

---

