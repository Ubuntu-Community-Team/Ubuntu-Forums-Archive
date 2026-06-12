---
title: "Distribution upgrade gone wrong!"
date: 2010-08-06
forum: Server Platforms
---

### Post by renegadeandy on 2010-08-06
Hey!

I was running 8.something on my ubuntu server.

Today I decided to upgrade releases! So I started it , all via ssh cos the box is about 800 miles away and it was going just fine. However - I went away from the pc for about a hour, and my ssh session died. 

On reconnect it starts a new ssh session - and I dont know how to reconnect to the upgrade process and finish it off - somebody help me finish this!

---

### Post by Bachstelze on 2010-08-06
> **renegadeandy said:**
> 
On reconnect it starts a new ssh session - and I dont know how to reconnect to the upgrade process and finish it off - somebody help me finish this!

You can't (that's one thing screen is very useful for).  Depending on when the session died, you might be able to just do another

```
sudo apt-get dist-upgrade
```

---

### Post by renegadeandy on 2010-08-06
Ok, when I do that it says:

Could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg) is another process using it?

---

### Post by Bachstelze on 2010-08-06
Then you have another package management program running.  This is a bit weird, because normally, all running processes are terminated when your SSH session exit.  Paste the output of [font=monospace]ps aux[/font].

---

### Post by renegadeandy on 2010-08-06
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1852   628 ?        Ss   Jun26   0:04 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Jun26   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Jun26   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Jun26   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Jun26   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Jun26   0:42 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Jun26   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   Jun26   0:07 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   Jun26   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   Jun26   0:00 [kacpi_notify]
root       106  0.0  0.0      0     0 ?        S<   Jun26   0:00 [kseriod]
root       142  0.0  0.0      0     0 ?        S<   Jun26   0:08 [kswapd0]
root       186  0.0  0.0      0     0 ?        S<   Jun26   0:00 [aio/0]
root      1363  0.0  0.0      0     0 ?        S<   Jun26   0:00 [ksuspend_usbd]
root      1368  0.0  0.0      0     0 ?        S<   Jun26   0:00 [khubd]
root      1385  0.0  0.0      0     0 ?        S<   Jun26   0:00 [ata/0]
root      1393  0.0  0.0      0     0 ?        S<   Jun26   0:00 [ata_aux]
root      1449  0.0  0.0      0     0 ?        S<   Jun26   0:00 [scsi_eh_0]
root      1452  0.0  0.0      0     0 ?        S<   Jun26   4:41 [scsi_eh_1]
root      2302  0.0  0.0      0     0 ?        S<   Jun26   1:51 [kjournald]
root      2477  0.0  0.1   2876  1008 ?        S<s  Jun26   0:01 /sbin/udevd --daemon
dhcp      5030  0.0  0.0   2436   392 ?        S<s  Jun26   0:00 dhclient3 -e IF_METRIC=100 -p
root      5501  0.0  0.0   1716   508 tty4     Ss+  Jun26   0:00 /sbin/getty 38400 tty4
root      5502  0.0  0.0   1716   512 tty5     Ss+  Jun26   0:00 /sbin/getty 38400 tty5
root      5506  0.0  0.0   1716   508 tty2     Ss+  Jun26   0:00 /sbin/getty 38400 tty2
root      5508  0.0  0.1   1716   516 tty3     Ss+  Jun26   0:00 /sbin/getty 38400 tty3
root      5510  0.0  0.1   1716   516 tty6     Ss+  Jun26   0:00 /sbin/getty 38400 tty6
syslog    5557  0.0  0.1   1936   680 ?        Ss   Jun26   0:29 /sbin/syslogd -u syslog
root      5599  0.0  0.1   1868   536 ?        S    Jun26   0:00 /bin/dd bs 1 if /proc/kmsg of
klog      5601  0.0  0.4   3292  2080 ?        Ss   Jun26   0:00 /sbin/klogd -P /var/run/klogd
root      5614  0.0  0.0      0     0 ?        S    17:51   0:03 [pdflush]
103       5620  0.0  0.2   2824  1344 ?        Ss   Jun26   0:00 /usr/bin/dbus-daemon --system
root      6466  0.0  0.2  14048  1360 ?        Ss   Jun26   0:00 /usr/sbin/gdm
root      6467  0.0  0.5  14480  2740 ?        S    Jun26   0:00 /usr/sbin/gdm
root      6475  0.0  2.5  20320 13176 tty7     Ss+  Jun26   1:11 /usr/bin/X :0 -br -audit 0 -a
root      6566  0.0  0.6   9404  3104 ?        Ss   Jun26   1:06 /usr/bin/perl /home/andy/Desk
root      6573  0.0  0.0   1716   512 tty1     Ss+  Jun26   0:00 /sbin/getty 38400 tty1
andy      6589  0.0  0.1   1772   528 ?        Ss   Jun26   0:00 /bin/sh /usr/bin/startkde
andy      6690  0.0  0.0   4480   384 ?        Ss   Jun26   0:08 /usr/bin/ssh-agent /usr/bin/s
andy      6699  0.0  1.0  41548  5148 ?        Ss   Jun26   2:04 /usr/bin/seahorse-agent --exe
root      6733  0.0  0.0   1564   140 ?        S    Jun26   0:00 start_kdeinit --new-startup +
andy      6734  0.0  0.6  25632  3196 ?        Ss   Jun26   0:01 kdeinit Running...          
andy      6737  0.0  0.5  25452  2600 ?        S    Jun26   0:01 dcopserver [kdeinit] --nosid
andy      6740  0.0  1.1  25468  5820 ?        S    Jun26   0:37 klauncher [kdeinit] --new-sta
andy      6742  0.0  2.1  30640 11136 ?        S    Jun26   3:55 kded [kdeinit] --new-startup
andy      6747  0.0  0.0   1696   376 ?        S    Jun26   0:36 kwrapper ksmserver
andy      6749  0.0  1.3  26500  7160 ?        S    Jun26   0:00 ksmserver [kdeinit]         
andy      6750  0.0  1.8  29532  9644 ?        S    Jun26   0:04 kwin [kdeinit] -session 10d8d
andy      6752  0.0  2.1  30204 11268 ?        S    Jun26   0:12 kdesktop [kdeinit]          
andy      6754  0.0  2.3  32016 12268 ?        S    Jun26   2:01 kicker [kdeinit]            
andy      6755  0.0  0.9  25916  4804 ?        S    Jun26   0:00 kio_file [kdeinit] file /tmp/
andy      6760  0.0  1.3  22356  7108 ?        S    Jun26  15:14 /usr/bin/artsd -F 10 -S 4096
andy      6762  0.0  1.3  26244  6696 ?        S    Jun26   0:00 kaccess [kdeinit]           
andy      6765  0.0  2.0  24580 10720 ?        S    Jun26   0:00 ktip
andy      6768  0.0  1.6  27456  8360 ?        S    Jun26   8:33 klipper [kdeinit]           
andy      6770  0.0  1.6  33412  8540 ?        S    Jun26   2:31 knotify [kdeinit]           
andy      6774  0.0  2.1  30936 10804 ?        S    Jun26   0:26 korgac --miniicon korganizer
113      18410  0.1  0.3  64168  2024 ?        SNl  19:13   0:13 /usr/lib/teamspeak-server/tea
root     18481  0.0  0.2   3408  1032 ?        Ss   19:13   0:00 /usr/sbin/cron
root     18583  0.0  0.1   3956   696 ?        Ss   Aug01   1:09 /usr/bin/dirmngr --daemon --s
daemon   18611  0.0  0.0   2064   456 ?        Ss   19:13   0:00 /usr/sbin/atd
root     18802  0.0  0.2   5400  1064 ?        Ss   19:13   0:00 /usr/sbin/sshd
root     20604  0.0  0.5   8192  2632 ?        Ss   20:29   0:00 sshd: andy [priv]
andy     20606  0.0  0.2   8192  1512 ?        S    20:29   0:00 sshd: andy@pts/4 
andy     20607  0.0  0.6   6224  3564 pts/4    Ss+  20:29   0:00 -bash
root     20725  0.0  0.5   8192  2632 ?        Ss   21:22   0:00 sshd: andy [priv]
andy     20727  0.0  0.2   8192  1512 ?        S    21:22   0:00 sshd: andy@pts/6 
andy     20728  0.0  0.6   6224  3568 pts/6    Ss+  21:22   0:00 -bash
root     20760  0.1  0.5   8192  2632 ?        Ss   21:34   0:00 sshd: andy [priv]
andy     20762  0.0  0.2   8192  1516 ?        S    21:34   0:00 sshd: andy@pts/7 
andy     20763  1.9  0.6   6224  3552 pts/7    Ss   21:34   0:00 -bash
andy     20779  0.0  0.1   2744  1008 pts/7    R+   21:35   0:00 ps aux
root     22174  0.3  0.0   1680   508 ?        R    Jul04 187:29 /bin/sh /usr/bin/mysqld_safe
root     25555  0.0  0.0      0     0 ?        S    Jul04   0:36 [pdflush]
postgres 26619  0.0  0.7  41356  3756 ?        S    Jul04   0:23 /usr/lib/postgresql/8.3/bin/p
postgres 26622  0.0  0.2  41356  1320 ?        Ss   Jul04   3:42 postgres: writer process    
postgres 26623  0.0  0.2  41356  1156 ?        Ss   Jul04   2:24 postgres: wal writer process 
postgres 26624  0.0  0.2  41356  1364 ?        Ss   Jul04   0:51 postgres: autovacuum launcher
postgres 26625  0.0  0.2  12676  1092 ?        Ss   Jul04   0:34 postgres: stats collector pro
andy     30932  0.0  0.1   4108  1020 ?        Ss   Jul04   0:00 SCREEN
andy     30933  0.0  0.6   6084  3408 pts/3    Ss+  Jul04   0:00 /bin/bash
jonmace  31041  0.0  0.2   4180  1128 ?        Ss   Jul04   0:00 SCREEN
jonmace  31042  0.0  0.6   6084  3164 pts/5    Ss+  Jul04   0:00 /bin/bash
root     31434  0.0  0.3   7600  1860 ?        Ssl  17:10   0:00 /usr/sbin/console-kit-daemon

---

### Post by Bachstelze on 2010-08-06
Okay, so you're running graphical.  You said you ran the upgrade over SSH, with which command?

---

### Post by renegadeandy on 2010-08-06
I wasnt aware it had any graphics actually - wasnt meant to...

I followed per [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

specifically :

Install update-manager-core if it is not already installed:   
sudo apt-get install update-manager-core 
edit /etc/update-manager/release-upgrades and set Prompt=normal  
Launch the upgrade tool:   
sudo do-release-upgrade
Follow the on-screen instructions.

---

### Post by Bachstelze on 2010-08-06
You also have two screen sessions opened: one as user "andy", probably you, and one as user "jonmace".  If you don't know about those, it could mean something bad.  As for your update problem, I don't see anything there that would claim the dpkg lock, maybe try running the same command again.

---

### Post by renegadeandy on 2010-08-06
I did try. It then said i needed to run

dpkg --configure -a

So i did that - and it LOOKS like its kicking off the update again! haha!

---

### Post by CharlesA on 2010-08-06
Hope it finishes up for you.

Mark the thread as solved if it does. :)

---

### Post by renegadeandy on 2010-08-06
Hmmmm - so it finished configuring etc.

If i do cat /etc/lsb-release it gives:

DISTRIB_ID=Ubuntu
RELEASE = 8.10
CODENAME=INTREPID

If i try doing do-release-upgrade it now says:

current dist not found in meta-release file

eek! Help!

---

### Post by CharlesA on 2010-08-06
What about uname -a?

---

### Post by renegadeandy on 2010-08-07
Linux server 2.6.24-23-server #1 SMP Wed Apr 1 22:22:14 UTC 2009 i686 GNU/Linux

---

