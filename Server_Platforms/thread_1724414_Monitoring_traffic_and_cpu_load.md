---
title: "Monitoring traffic and cpu load"
date: 2011-04-08
forum: Server Platforms
---

### Post by ethernaly on 2011-04-08
Hello all,
my servers are configured with:
Ubuntu 10.10 server 64bit;
Lighttpd
MySQL-Server

I need to make graphs for traffic (bandwidth usage) and cpu load every month.

I tried to configure mrtg but after 48h, it didn't produce graphs.

Have you got some suggestions? (I can't install apache2)


Thanks in advance,

best regards


EDIT:
I forgive to say that I also tried HotSaNIC.
but give me some strange error while using "diagrams.pl"
> creating images for eth0 ...
Use of uninitialized value $xs in print at ./diagrams.pl line 148 (#1)
    (W uninitialized) An undefined value was used as if it were already
    defined.  It was interpreted as a "" or a 0, but maybe it was a mistake.
    To suppress this warning assign a defined value to your variables.
    
    To help you figure out what was undefined, perl will try to tell you the
    name of the variable (if any) that was undefined. In some cases it cannot
    do this, so it also tells you what operation you used the undefined value
    in.  Note, however, that perl optimizes your program and the operation
    displayed in the warning may not necessarily appear literally in your
    program.  For example, "that $foo" is usually optimized into "that "
    . $foo, and the warning will refer to the concatenation (.) operator,
    even though there is no . in your program.
    
Use of uninitialized value $ys in print at ./diagrams.pl line 148 (#1)
  hour    x TEST/traffic/eth0-hour.png
Use of uninitialized value $xs in printf at ./diagrams.pl line 220 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 220 (#1)
  6 hours 0x0 TEST/traffic/eth0-6h.png
  day     0x0 TEST/traffic/eth0-day.png
  week    0x0 TEST/traffic/eth0-week.png
  month   0x0 TEST/traffic/eth0-month.png
  year    0x0 TEST/traffic/eth0-year.png

creating images for lo ...
  hour    x TEST/traffic/lo-hour.png
  6 hours 0x0 TEST/traffic/lo-6h.png
  day     0x0 TEST/traffic/lo-day.png
  week    0x0 TEST/traffic/lo-week.png
  month   0x0 TEST/traffic/lo-month.png
  year    0x0 TEST/traffic/lo-year.png

----- modules/system -----
creating images for loadavg...
  load:
Use of uninitialized value $xs in printf at ./diagrams.pl line 147 (#1)
    (W uninitialized) An undefined value was used as if it were already
    defined.  It was interpreted as a "" or a 0, but maybe it was a mistake.
    To suppress this warning assign a defined value to your variables.
    
    To help you figure out what was undefined, perl will try to tell you the
    name of the variable (if any) that was undefined. In some cases it cannot
    do this, so it also tells you what operation you used the undefined value
    in.  Note, however, that perl optimizes your program and the operation
    displayed in the warning may not necessarily appear literally in your
    program.  For example, "that $foo" is usually optimized into "that "
    . $foo, and the warning will refer to the concatenation (.) operator,
    even though there is no . in your program.
    
Use of uninitialized value $ys in printf at ./diagrams.pl line 147 (#1)
  hour    0x0 TEST/system/load-hour.png
  6 hours 0x0 TEST/system/load-6h.png
  day     0x0 TEST/system/load-day.png
  week    0x0 TEST/system/load-week.png
  month   0x0 TEST/system/load-month.png
  year    0x0 TEST/system/load-year.png

creating images for processes...
  proc:
Use of uninitialized value $xs in printf at ./diagrams.pl line 232 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 232 (#1)
  hour    0x0 TEST/system/proc-hour.png
  6 hours 0x0 TEST/system/proc-6h.png
  day     0x0 TEST/system/proc-day.png
  week    0x0 TEST/system/proc-week.png
  month   0x0 TEST/system/proc-month.png
  year    0x0 TEST/system/proc-year.png

creating images for CPU-usage...
  cpu3:
Use of uninitialized value $xs in printf at ./diagrams.pl line 360 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 360 (#1)
  hour    0x0 TEST/system/cpu3-hour.png
  6 hours 0x0 TEST/system/cpu3-6h.png
  day     0x0 TEST/system/cpu3-day.png
  week    0x0 TEST/system/cpu3-week.png
  month   0x0 TEST/system/cpu3-month.png
  year    0x0 TEST/system/cpu3-year.png
  cpu0:
  hour    0x0 TEST/system/cpu0-hour.png
  6 hours 0x0 TEST/system/cpu0-6h.png
  day     0x0 TEST/system/cpu0-day.png
  week    0x0 TEST/system/cpu0-week.png
  month   0x0 TEST/system/cpu0-month.png
  year    0x0 TEST/system/cpu0-year.png
  cpu1:
  hour    0x0 TEST/system/cpu1-hour.png
  6 hours 0x0 TEST/system/cpu1-6h.png
  day     0x0 TEST/system/cpu1-day.png
  week    0x0 TEST/system/cpu1-week.png
  month   0x0 TEST/system/cpu1-month.png
  year    0x0 TEST/system/cpu1-year.png
  cpu:
  hour    0x0 TEST/system/cpu-hour.png
  6 hours 0x0 TEST/system/cpu-6h.png
  day     0x0 TEST/system/cpu-day.png
  week    0x0 TEST/system/cpu-week.png
  month   0x0 TEST/system/cpu-month.png
  year    0x0 TEST/system/cpu-year.png
  cpu2:
  hour    0x0 TEST/system/cpu2-hour.png
  6 hours 0x0 TEST/system/cpu2-6h.png
  day     0x0 TEST/system/cpu2-day.png
  week    0x0 TEST/system/cpu2-week.png
  month   0x0 TEST/system/cpu2-month.png
  year    0x0 TEST/system/cpu2-year.png

creating images for memory-usage...
  mem:
Use of uninitialized value $xs in printf at ./diagrams.pl line 541 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 541 (#1)
  hour    0x0 TEST/system/mem-hour.png
  6 hours 0x0 TEST/system/mem-6h.png
  day     0x0 TEST/system/mem-day.png
  week    0x0 TEST/system/mem-week.png
  month   0x0 TEST/system/mem-month.png
  year    0x0 TEST/system/mem-year.png

creating images for swapfile-usage...
  mem:
Use of uninitialized value $xs in printf at ./diagrams.pl line 609 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 609 (#1)
  hour    0x0 TEST/system/swap-hour.png
  6 hours 0x0 TEST/system/swap-6h.png
  day     0x0 TEST/system/swap-day.png
  week    0x0 TEST/system/swap-week.png
  month   0x0 TEST/system/swap-month.png
  year    0x0 TEST/system/swap-year.png

creating images for user-stats...
  users:
Use of uninitialized value $xs in printf at ./diagrams.pl line 686 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 686 (#1)
  hour    0x0 TEST/system/users-hour.png
  6 hours 0x0 TEST/system/users-6h.png
  day     0x0 TEST/system/users-day.png
  week    0x0 TEST/system/users-week.png
  month   0x0 TEST/system/users-month.png
  year    0x0 TEST/system/users-year.png

creating images for interrupts...
Use of uninitialized value $xs in printf at ./diagrams.pl line 812 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 812 (#1)
  hour    0x0 TEST/system/irq-hour.png
  6 hours 0x0 TEST/system/irq-6h.png
  day     0x0 TEST/system/irq-day.png
  week    0x0 TEST/system/irq-week.png
  month   0x0 TEST/system/irq-month.png
  year    0x0 TEST/system/irq-year.png

creating images for uptime...
  uptime:
Use of uninitialized value $xs in printf at ./diagrams.pl line 865 (#1)
Use of uninitialized value $ys in printf at ./diagrams.pl line 865 (#1)
  day     0x0 TEST/system/uptime-day.png
  week    0x0 TEST/system/uptime-week.png
  month   0x0 TEST/system/uptime-month.png
  year    0x0 TEST/system/uptime-year.png

---

### Post by rubylaser on 2011-04-08
I normally use munin for simple monitoring tasks like this.  Here are directions to set it up with Lighttpd.

[http://linhost.info/2010/06/install-munin-in-five-minutes-on-ubuntu-10-04/]("http://linhost.info/2010/06/install-munin-in-five-minutes-on-ubuntu-10-04/")

---

### Post by SeijiSensei on 2011-04-08
[MRTG]("http://oss.oetiker.ch/mrtg/") will collect and graph nearly anything including CPU loads, though it's original purpose was to monitor routers.  [ntop]("http://www.ntop.org/overview.html") is another excellent, easy-to-install traffic monitor.

---

### Post by ethernaly on 2011-04-08
munin seems to be what I need!

Now I need "only" to customize report and find if I can send automatic report to an email address.

REALLY THX!

---

### Post by rubylaser on 2011-04-08
All you'd need to do is get the URL's of the images that you want to send from munin, and write a simple bash script to download them, and use mail to attach them to an email..

I normally use mutt
```
apt-get install mutt
```

```
#! /bin/bash
wget http://10.1.1.80/munin/url/server_name/diskstats_iops/cciss_c0d0-week.png
wget http://10.1.1.80/munin/url/server_name/cpu-week.png
tar czf reports.tar.gz cciss_c0d0-week.png cpu-week.png
mutt -s "Webserver Reports - dated `date +'%m-%d-%y"'`" -a reports.tar.gz user@emailaddress < /root/email_body.txt
echo "Reports Sent"
rm cciss_c0d0-week.png cpu-week.png

```

You'll just need to make a file at /root/email_body.txt that's the body of your email.  Something like this...
```

echo Attached are the utitlization reports.

echo Thanks,
echo System Administrator
```

^ The above is untested, so it might not work out of the box.

---

### Post by garycahill on 2011-05-24
iowait and vmstat are a very quick way of checking this stuff out too. Not forgetting top.

gary

---

### Post by brettg on 2011-05-25
Concur with mrtg and ntop. I've also used darkstat with success.

---

