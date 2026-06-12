---
title: "Slow Performance on the server after 5-6 days"
date: 2007-10-04
forum: Server Platforms
---

### Post by tanman77 on 2007-10-04
For some reason, on my ubuntu server after 5-6 days everything slows right down to a crawl. I cannot get into my server through ssh, nor does apache work , which are the primary main functions I use. I can ping the server. Logging in locally causes problems and unstable, top and such don't work. They sit there and hang.

I would like to go through the process of troubleshooting this, but I don't really know where to start as troubleshooting linux servers are relatively new to me from the cli coming from the Windows World.

Any help would be most appreciated.

---

### Post by netlogic on 2007-10-04
did you go over your logs in /var/log/
type top
what is eating up most of your process?

---

### Post by tanman77 on 2007-10-04
> **netlogic said:**
> did you go over your logs in /var/log/
type top
what is eating up most of your process?

Now most of the MEM% is used up by apache2, and mysql. Sometimes I use torrentflux-brt, but that is hardly ever (based on python for the torrents).

I am not sure what to look for in the logs...what indications am i looking for?

---

### Post by p_quarles on 2007-10-04
You should start by looking at the Apache logs. It hardly uses any resources unless it's getting traffic, and won't slow down a decent system unless its getting *heavy* traffic. Same with MySQL. 

Find out who's been using it, and how.

---

### Post by netlogic on 2007-10-04
Have you also check your access.log and error.log on your apache?
/var/log/apache2/ 

-------also---------
how many instances of apache did you allowed?
check /etc/apache2/apache2.conf

------if the results are------
1. you are sharing a huge file
2. bored script kiddie is trying to constantly access that file multiple times within few split seconds to increase your load with multiple ip address, you need to block the range from your firewall.

-------------------------------------
what are you running on your apache?
you haven't tell us that yet.

---

### Post by tanman77 on 2007-10-04
I looked at the apache logs aand its just the IP address coming from me at the moment. There are some from overseas but they are very few.

I run WordPress 2.3 on this machine. It is a P4 running 512 MB of RAM with with a 80GB HDD.

 I did a screen dump of the command ps wuaxx. I i have blanked the username with xxx:

Here is the screen dump:

SER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2820  1884 ?        Ss   01:34   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    01:34   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   01:34   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    01:34   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   01:34   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   01:34   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   01:34   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   01:34   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   01:34   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   01:34   0:00 [kacpi_notify]
root       113  0.0  0.0      0     0 ?        S<   01:34   0:00 [kseriod]
root       134  0.0  0.0      0     0 ?        S    01:34   0:00 [pdflush]
root       135  0.0  0.0      0     0 ?        S    01:34   0:00 [pdflush]
root       136  0.0  0.0      0     0 ?        S<   01:34   0:00 [kswapd0]
root       137  0.0  0.0      0     0 ?        S<   01:34   0:00 [aio/0]
root      1807  0.0  0.0      0     0 ?        S<   01:34   0:00 [ksuspend_usbd]
root      1808  0.0  0.0      0     0 ?        S<   01:34   0:00 [khubd]
root      1828  0.0  0.0      0     0 ?        S<   01:34   0:00 [ata/0]
root      1829  0.0  0.0      0     0 ?        S<   01:34   0:00 [ata_aux]
root      1936  0.0  0.0      0     0 ?        S<   01:34   0:00 [scsi_eh_0]
root      1937  0.0  0.0      0     0 ?        S<   01:34   0:00 [scsi_eh_1]
root      2128  0.0  0.0      0     0 ?        S<   01:34   0:00 [kjournald]
root      2260  0.0  0.1   2296   628 ?        S<s  01:34   0:00 /sbin/udevd --daemon
root      3114  0.0  0.0      0     0 ?        S<   01:34   0:00 [kpsmoused]
root      3714  0.0  0.0   1648   508 tty4     Ss+  01:34   0:00 /sbin/getty 38400 tty4
root      3715  0.0  0.0   1648   504 tty5     Ss+  01:34   0:00 /sbin/getty 38400 tty5
root      3720  0.0  0.0   1652   512 tty2     Ss+  01:34   0:00 /sbin/getty 38400 tty2
root      3723  0.0  0.0   1648   508 tty3     Ss+  01:34   0:00 /sbin/getty 38400 tty3
root      3727  0.0  0.0   1652   512 tty6     Ss+  01:34   0:00 /sbin/getty 38400 tty6
root      3749  0.0  0.1   1700   668 ?        Ss   01:34   0:00 /sbin/syslogd
root      3767  0.0  0.1   1792   524 ?        Ss   01:34   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3769  0.0  0.2   2440  1380 ?        Ss   01:34   0:00 /sbin/klogd -P /var/run/klogd/kmsg
bind      3791  0.0  0.5  30732  3020 ?        Ssl  01:34   0:00 /usr/sbin/named -u bind
root      3851  0.0  0.1   1716   528 ?        S    01:34   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     3893  0.0  3.7 129276 19316 ?        Sl   01:34   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      3895  0.0  0.1   1636   532 ?        S    01:34   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      3954  0.0  0.2   6036  1236 ?        Ss   01:34   0:00 /usr/sbin/nmbd -D
root      3960  0.0  0.4   9292  2228 ?        Ss   01:34   0:00 /usr/sbin/smbd -D
root      3976  0.0  0.1   5084   964 ?        Ss   01:34   0:00 /usr/sbin/sshd
root      3980  0.0  0.2   9292  1044 ?        S    01:34   0:00 /usr/sbin/smbd -D
daemon    4005  0.0  0.0   1908   420 ?        Ss   01:34   0:00 /usr/sbin/atd
root      4016  0.0  0.1   2284   900 ?        Ss   01:34   0:00 /usr/sbin/cron
root      4044  0.0  1.2  22744  6536 ?        Ss   01:34   0:00 /usr/sbin/apache2 -k start
www-data  4074  0.0  3.2  31884 16620 ?        S    01:34   0:02 /usr/sbin/apache2 -k start
www-data  4075  0.0  2.9  30828 15216 ?        S    01:34   0:01 /usr/sbin/apache2 -k start
www-data  4076  0.0  3.2  32144 16836 ?        S    01:34   0:01 /usr/sbin/apache2 -k start
www-data  4077  0.0  3.2  31868 16576 ?        S    01:34   0:03 /usr/sbin/apache2 -k start
www-data  4078  0.0  3.1  31616 16052 ?        S    01:34   0:02 /usr/sbin/apache2 -k start
root      4079  0.0  1.2  10152  6368 ?        Ss   01:34   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
www-data  4223  0.0  2.9  31088 15292 ?        S    01:39   0:00 /usr/sbin/apache2 -k start
www-data  4225  0.0  2.9  30828 15248 ?        S    01:39   0:01 /usr/sbin/apache2 -k start
www-data  4226  0.0  3.0  31152 15600 ?        S    01:39   0:01 /usr/sbin/apache2 -k start
www-data  4227  0.0  3.1  31680 16136 ?        S    01:39   0:01 /usr/sbin/apache2 -k start
root      4633  0.0  0.0   1652   508 tty1     Ss+  10:44   0:00 /sbin/getty 38400 tty1
root      4809  0.0  0.4   7864  2372 ?        Ss   13:56   0:00 sshd: xxx [priv]
xxx  4811  0.0  0.2   8024  1524 ?        S    13:56   0:00 sshd: xxx@pts/0
xxx  4812  0.0  0.5   5488  2996 pts/0    Ss   13:56   0:00 -bash
xxx  4986  0.0  0.1   2564   992 pts/0    R+   14:08   0:00 ps waux

---

### Post by tanman77 on 2007-10-04
I am also not sure where I can find the max instances int he apache2.conf file. I just left it on the defaults.

UPDATE:
The load is also quite low when this occurs: 0.0 0.1 thereabouts

---

### Post by netlogic on 2007-10-04
That wouldn't matter at this point. It seems like your CPU is spiking and you say your logs don't say anything. At this point, you should consider installing webalizer or other apache monitoring tool. I don't use wordpress, so I'm not sure if that is causing it or not.  I am also going to make an assumption that you are frequently applying the security updates. I am still leaning on it is focused around your apache and you should spend time monitoring your logs more often to pinpoint later time. by the way, do you have time periods of when the crashes occur?

---

### Post by tanman77 on 2007-10-10
> **netlogic said:**
> That wouldn't matter at this point. It seems like your CPU is spiking and you say your logs don't say anything. At this point, you should consider installing webalizer or other apache monitoring tool. I don't use wordpress, so I'm not sure if that is causing it or not.  I am also going to make an assumption that you are frequently applying the security updates. I am still leaning on it is focused around your apache and you should spend time monitoring your logs more often to pinpoint later time. by the way, do you have time periods of when the crashes occur?

Well after 5 days or so, the same type of symptoms appear.I can log into ssh. But I cannot load top or htop. nor can run apt-get. even when using sudo...apache seeems to be still working. but none of those other apps work..Webmin doesn't load either, but using ps does

I would like to use this time to track down what this problem is. Thank you anyone that can help me....Thanking you.

---

### Post by James79 on 2007-10-10
Have you tried a ram test?

---

### Post by tanman77 on 2007-10-10
No I haven't If you don't mind me asking...how do I do a ram test? I did a google on it and they refer to a product called memtest86?

---

### Post by James79 on 2007-10-10
Boot your server from the Ubuntu install disk. One of the options on the menu will be to run a ram test.

I highly suggest you let this run for several hours before assuming a conclusive result. I prefer letting it run overnight or while I'm away at work.

---

### Post by netlogic on 2007-10-11
Since, this can be another issue with the hardware. Do you have a high quality CPU FAN? Have you been checking your CPU TEMP?

---

### Post by tanman77 on 2007-10-11
Thanks all for the help. 

I'll post whatever results I find here.

---

### Post by tanman77 on 2007-10-11
I ran the memtest for 14 hours and so far have come up with 14 successes. 

I am uncertain about what the CPU temperature is, but I would expect it to have the same problems occuring after I do a restart, because the temperature would be the same. Yet when I restart the server, the problems go away....which points to a general direction of a leak of some kind.

Is there any indicators that I could run to see if there is anything being funny? Many thanks.

---

### Post by netlogic on 2007-10-11
I can't think of anything right now, but which kernel are you using?
you can find out by typing  "uname -a"
Have you tried with a different kernel?

---

### Post by tanman77 on 2007-10-11
Linux xxx 2.6.20-16-server

---

### Post by netlogic on 2007-10-12
can you try the i386 and generic version?
linux-image-2.6.20-16-386 
linux-image-2.6.20-16-generic

---

