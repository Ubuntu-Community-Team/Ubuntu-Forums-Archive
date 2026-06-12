---
title: "Server Hard Drive accessed every 3 seconds when idle"
date: 2006-07-03
forum: Server Platforms
---

### Post by Hellsteeth on 2006-07-03
I have a silenced, headless, AMD based server for home use running Dapper with Samba, Squid, Dans Guardian, Apache 2, SSHD and Webmin.
As it is headless, neither X or GDM is set to run automatically.

Previously I ran Breezy and Hoary on the same machine without problems, however under Dapper I notice the hard drive is being accessed every three seconds (i.e. the red HD LED flashes every 3 seconds). I have tried disabling all of the above mentioned servers as well as working my way down the list obtained with the command ps -A. The only noticeable change occurred when I killed hald, the daemon for Hardware Abstraction Layer. However I assume this is required.

My only worries are the unnecessary wear on the machine and curiosity as to what is going on.

Many thanks for your thoughts.



Here is my list of running processes.


# ps -A

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  151 ?        00:00:00 pdflush
  152 ?        00:00:00 pdflush
  154 ?        00:00:00 aio/0
  153 ?        00:00:00 kswapd0
  741 ?        00:00:00 kseriod
 1756 ?        00:00:00 ata/0
 1757 ?        00:00:00 ata_hotplug/0
 1850 ?        00:00:00 khubd
 1861 ?        00:00:00 khpsbpkt
 1879 ?        00:00:00 knodemgrd_0
 1958 ?        00:00:00 kjournald
 2190 ?        00:00:00 udevd
 3051 ?        00:00:00 shpchpd_event
 3116 ?        00:00:00 w1_control
 3126 ?        00:00:00 w1_bus_master1
 3503 ?        00:00:00 kjournald
 3504 ?        00:00:00 kjournald
 3854 ?        00:00:00 acpid
 3944 ?        00:00:00 syslogd
 3970 ?        00:00:00 dd
 3972 ?        00:00:00 klogd
 3997 ?        00:00:00 hpiod
 4000 ?        00:00:00 python
 4047 ?        00:00:00 cupsd
 4112 ?        00:00:00 freshclam
 4128 ?        00:00:00 dbus-daemon
 4143 ?        00:00:01 hald
 4144 ?        00:00:00 hald-runner
 4149 ?        00:00:00 hald-addon-acpi
 4203 ?        00:00:00 hald-addon-stor
 4204 ?        00:00:00 hald-addon-stor
 4261 ?        00:00:00 nmbd
 4263 ?        00:00:00 smbd
 4281 ?        00:00:00 sshd
 4286 ?        00:00:00 smbd
 4335 ?        00:00:00 xinetd
 4347 ?        00:00:00 ntpd
 4363 ?        00:00:00 hcid
 4367 ?        00:00:00 sdpd
 4382 ?        00:00:00 krfcommd
 4395 ?        00:00:00 mdadm
 4418 ?        00:00:00 squid
 4420 ?        00:00:00 squid
 4430 ?        00:00:00 unlinkd
 4431 ?        00:00:00 dansguardian
 4432 ?        00:00:00 dansguardian
 4433 ?        00:00:00 dansguardian
 4434 ?        00:00:00 dansguardian
 4435 ?        00:00:00 dansguardian
 4436 ?        00:00:00 dansguardian
 4437 ?        00:00:00 dansguardian
 4466 ?        00:00:00 dansguardian
 4467 ?        00:00:00 dansguardian
 4468 ?        00:00:00 dansguardian
 4469 ?        00:00:00 dansguardian
 4470 ?        00:00:00 atd
 4483 ?        00:00:00 cron
 4510 ?        00:00:00 apache2
 4511 ?        00:00:00 apache2
 4512 ?        00:00:00 apache2
 4520 ?        00:00:00 apache2
 4939 ?        00:00:00 miniserv.pl
 4955 tty1     00:00:00 getty
 4958 tty2     00:00:00 getty
 4959 tty3     00:00:00 getty
 4960 tty4     00:00:00 getty
 4961 tty5     00:00:00 getty
 4962 tty6     00:00:00 getty
 4976 ?        00:00:00 dhclient3
 4988 ?        00:00:00 dhclient3
 5009 ?        00:00:00 sshd
 5011 ?        00:00:00 sshd
 5012 pts/0    00:00:00 bash
 5029 pts/0    00:00:00 su
 5030 pts/0    00:00:00 bash
 5042 pts/0    00:00:00 ps

---

### Post by faultyCPU on 2006-07-03
look at iostat o/p just in case

---

### Post by MJN on 2006-07-03
It's likely to kupdated flushing the buffers to disc - it defaults to do this every 5 seconds however so if you're accurate with the 3 seconds timing then perhaps not.
 
Anyway, in case it's of use, check out [http://www.cs.cmu.edu/~mukesh/hacks/spindown/t1.html]("http://www.cs.cmu.edu/~mukesh/hacks/spindown/t1.html") where the daemon is discussed. Furthermore, it's part of a wider HowTo on keeping discs spun down and so the strategies discussed should be of direct relevance to your needs (conceding that you don't mind them idling, but rather just no head movement).
 
Mathew

---

### Post by Hellsteeth on 2006-07-03
Interesting thoughts, thank you MJN and faultyCPU. 
I did not have either of these installed so I have just installed the iostat and noflushd packages and will see what infomation and affects they have.

Cheers

---

### Post by MJN on 2006-07-03
Do report back with any outcome - this sort of issue periodically rears its head yet given the number of potential causes the 'solutions' are often never achieved..

---

