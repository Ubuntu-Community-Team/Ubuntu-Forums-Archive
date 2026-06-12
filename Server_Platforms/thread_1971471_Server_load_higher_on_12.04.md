---
title: "Server load higher on 12.04"
date: 2012-05-02
forum: Server Platforms
---

### Post by jrtboht on 2012-05-02
I upgraded to 12.04 (from 11.10) yesterday and my average system load has gone from just under 1.0 most of the time to a fairly constant 1.5.  Is this normal?  Is it ok to be constantly that high?

---

### Post by CharlesA on 2012-05-02
What does htop or top say?

System specs would be nice.

---

### Post by jrtboht on 2012-05-02
Here are the specs and output from uptime and top.  Thanks!

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 3000+
stepping        : 0
cpu MHz         : 2158.020
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips        : 4316.04
clflush size    : 32
cache_alignment : 32
address sizes   : 34 bits physical, 32 bits virtual
power management: ts
MemTotal:         960508 kB
MemFree:          280252 kB
Buffers:          167784 kB
Cached:           376460 kB
SwapCached:            0 kB
Active:           382536 kB
Inactive:         254752 kB
Active(anon):      93084 kB
Inactive(anon):     1628 kB
Active(file):     289452 kB
Inactive(file):   253124 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:         69576 kB
HighFree:            984 kB
LowTotal:         890932 kB
LowFree:          279268 kB
SwapTotal:       2813948 kB
SwapFree:        2813948 kB
Dirty:                20 kB
Writeback:             0 kB
AnonPages:         93088 kB
Mapped:            24984 kB
Shmem:              1672 kB
Slab:              30256 kB
SReclaimable:      23536 kB
SUnreclaim:         6720 kB
KernelStack:         888 kB
PageTables:         3096 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3294200 kB
Committed_AS:     610912 kB
VmallocTotal:     122880 kB
VmallocUsed:        5696 kB
VmallocChunk:     113928 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       18424 kB
DirectMap2M:      894976 kB
```


```
root@webserver:~# uptime
 16:58:08 up 1 day,  3:02,  2 users,  load average: 1.66, 1.47, 1.43
```

```
 top
top - 16:59:15 up 1 day,  3:03,  2 users,  load average: 1.51, 1.48, 1.44
Tasks:  81 total,   1 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.8%us, 67.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    960508k total,   678504k used,   282004k free,   167732k buffers
Swap:  2813948k total,        0k used,  2813948k free,   376004k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  768 bind      20   0 50608  18m 2920 S 99.7  1.9   1601:12 named
  767 mysql     20   0  315m  43m 6964 S  0.3  4.6  15:53.66 mysqld
25468 root      20   0 17412 4884 3920 S  0.3  0.5   0:00.12 sshd
25648 root      20   0  2700 1056  832 R  0.3  0.1   0:00.04 top
    1 root      20   0  3508 1848 1228 S  0.0  0.2   0:00.77 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kthreadd
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.19 ksoftirqd/0
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.23 watchdog/0
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.16 sync_supers
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd
   15 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd
   18 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.02 khungtaskd
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kswapd0
   23 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd
   24 root      39  19     0    0    0 S  0.0  0.0   0:00.00 khugepaged
   25 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark
   26 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea
   27 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto
   35 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld
   36 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kworker/u:2
   55 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 devfreq_wq
  182 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
  192 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
  193 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 firewire
  194 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  195 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
  196 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kworker/u:3
  220 root      20   0     0    0    0 S  0.0  0.0   0:04.15 jbd2/sda1-8
  221 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-unwrit
  311 root      20   0  2944  604  440 S  0.0  0.1   0:00.14 upstart-udev-br
  314 root      20   0  2996 1212  728 S  0.0  0.1   0:00.09 udevd
  396 root      20   0  2948  636  284 S  0.0  0.1   0:00.00 udevd
  397 root      20   0  2948  700  336 S  0.0  0.1   0:00.00 udevd
  451 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
  496 root      20   0  2824  348  200 S  0.0  0.0   0:00.01 upstart-socket-
  564 root      20   0     0    0    0 S  0.0  0.0   0:00.59 flush-8:0
  585 messageb  20   0  3236  860  624 S  0.0  0.1   0:00.03 dbus-daemon
  592 syslog    20   0 30136 1508 1024 S  0.0  0.2   0:02.34 rsyslogd
  630 root      20   0  2908  760  480 S  0.0  0.1   0:00.00 dhclient3
  653 root      20   0  6660 2248 1820 S  0.0  0.2   0:00.09 sshd
  722 root      20   0  4612  816  696 S  0.0  0.1   0:00.00 getty
  727 root      20   0  4612  816  696 S  0.0  0.1   0:00.00 getty
  738 root      20   0  4612  820  696 S  0.0  0.1   0:00.00 getty
  739 root      20   0  4612  820  696 S  0.0  0.1   0:00.00 getty
  743 root      20   0  4612  812  696 S  0.0  0.1   0:00.00 getty
  746 root      20   0  2156  592  496 S  0.0  0.1   0:00.00 acpid
  757 root      20   0  2600  872  692 S  0.0  0.1   0:00.33 cron

```

---

### Post by CharlesA on 2012-05-02
Does bind always use 99% CPU? That doesn't seem normal.

Here's the output of top on my server - pretty much nothing is using the cpu.

```
top - 14:49:55 up 3 days, 19:08,  1 user,  load average: 0.39, 0.21, 0.19
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.4%sy,  0.0%ni, 99.4%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16287520k total, 10691820k used,  5595700k free,   324260k buffers
Swap: 16624636k total,     3044k used, 16621592k free,  6942416k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
21864 vbox      20   0 1698m 566m 554m S    2  3.6  96:05.91 VBoxHeadless
22004 vbox      20   0 2221m 698m 683m S    2  4.4 104:05.97 VBoxHeadless
 2899 vbox      20   0 2038m 531m 518m S    1  3.3  20:51.49 VBoxHeadless
    1 root      20   0 24328 1420  504 S    0  0.0   0:01.30 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:13.40 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.68 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    9 root      20   0     0    0    0 S    0  0.0   0:07.76 kworker/1:0
   10 root      20   0     0    0    0 S    0  0.0   1:42.20 ksoftirqd/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.68 watchdog/1
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2
   15 root      20   0     0    0    0 S    0  0.0   0:09.10 ksoftirqd/2
   16 root      RT   0     0    0    0 S    0  0.0   0:00.68 watchdog/2
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3
   18 root      20   0     0    0    0 S    0  0.0   0:40.05 kworker/3:0

```

Try restarting bind and see what happens.

---

### Post by jrtboht on 2012-05-02
Thanks for the help

I stopped bind using /etc/init.d/bind9 stop and all websites still seem to be working fine with a system load now averaging about 0.1

So is there a way to stop bind from starting on server reboots or better yet is there a explanation on why bind was using as much of the cpu as it possibly could (it didn't start until after I upgraded to 12.04).

---

### Post by Doug S on 2012-05-02
Please know that reported load averages have been broken for the previous few releases and are now fixed in the release version of 12.04 (the fix barely made the kernel cutoff). Under conditions of a "high" frequency of any CPU going in and out of idle, no matter how short the idle period, the reported load average could have been too low, perhaps massively. By "high" frequency, I mean greater than or equal to 25 hertz, with a proportional effect between 0 and 25 hertz. If this senario applies in your case or not, I do not know. (The screen shot showed 0% idle)
 
References:
[Ubuntu forums thread]("http://ubuntuforums.org/showthread.php?t=1909253").
[Launchpad bug.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811")
[My web notes.]("http://www.smythies.com/~doug/network/load_average/index.html") (the link is safe, although you have no reason to believe me.)

---

### Post by CharlesA on 2012-05-02
> **jrtboht said:**
> Thanks for the help

I stopped bind using /etc/init.d/bind9 stop and all websites still seem to be working fine with a system load now averaging about 0.1

So is there a way to stop bind from starting on server reboots or better yet is there a explanation on why bind was using as much of the cpu as it possibly could (it didn't start until after I upgraded to 12.04).

I'm not sure why it's using that much CPU, does it stay that high after you restart it?

> **Doug S said:**
> [My web notes.]("http://www.smythies.com/~doug/network/load_average/index.html") (the link is safe, although you have no reason to believe me.)

I believe you!

---

### Post by jrtboht on 2012-05-02
I did restart bind and it immediately started using all possible cpu cycles after the restart.  I also shutdown and restarted the entire server and bind still took over the cpu.

---

### Post by CharlesA on 2012-05-02
Well, bind it the problem then.

Have you checked any logs to see why BIND is using so much cpu?

---

### Post by jrtboht on 2012-05-02
That was my next question, what logs should I look at?

---

### Post by CharlesA on 2012-05-02
I don't use bind, but the log should be located in /var/log/bind or /var/log/named

---

### Post by Doug S on 2012-05-02
From your top screen shot, bind used 98.66% of your resources for the 1 day 3 hours and 3 minutes of uptime, interesting.
Probably Charles is or has replied also, but check /var/log/syslog and perhaps others for "named" entries. I.E.```
grep named /var/log/syslog
```By the way, I run bind without issue on one of my test computers, but I can not recall if I initially upgraded from 11.10 or started from a fresh install from a beta ISO.
Is your DNS public facing or only for your internal network inquires.

---

### Post by Doug S on 2012-05-02
Perhaps also post your bind configuration files. From /etc/bind.
The two files mainly of interest would be your domain file and your reverse file. Example (for my case):```
-rw-r--r-- 1 root root  601 2010-08-04 13:50 bind.keys
-rw-r--r-- 1 root root  237 2010-08-04 13:50 db.0
-rw-r--r-- 1 root root  271 2010-08-04 13:50 db.127
-rw-r--r-- 1 root bind  891 2012-03-10 21:07 [COLOR=red]db.192[/COLOR]
-rw-r--r-- 1 root root  237 2010-08-04 13:50 db.255
-rw-r--r-- 1 root root  353 2010-08-04 13:50 db.empty
-rw-r--r-- 1 root root  270 2010-08-04 13:50 db.local
-rw-r--r-- 1 root root 2994 2010-08-04 13:50 db.root
-rw-r--r-- 1 root bind  936 2012-03-10 21:08 [COLOR=red]db.smythies.com[/COLOR]
-rw-r--r-- 1 root bind  463 2010-08-04 13:50 named.conf
-rw-r--r-- 1 root bind  490 2010-08-04 13:50 named.conf.default-zones
-rw-r--r-- 1 root bind 3538 2011-12-02 15:48 named.conf.local
-rw-r--r-- 1 root bind  761 2012-04-11 19:28 named.conf.options
-rw-r----- 1 bind bind   77 2010-12-10 08:22 rndc.key
-rw-r--r-- 1 root root 1317 2010-08-04 13:50 zones.rfc1918
```
 
Charles: I don't think there is a specific "named" or "bind" log file by default.

---

### Post by jrtboht on 2012-05-02
Doug is correct about not having a default bind or named log file.  Here are a couple snippets I took from the syslog file


```
May  2 19:20:28 webserver named[828]: starting BIND 9.8.1-P1 -u bind
May  2 19:20:28 webserver named[828]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
May  2 19:20:28 webserver named[828]: adjusted limit on open files from 4096 to 1048576
May  2 19:20:28 webserver named[828]: found 1 CPU, using 1 worker thread
May  2 19:20:28 webserver named[828]: using up to 4096 sockets
May  2 19:20:28 webserver named[828]: loading configuration from '/etc/bind/named.conf'
May  2 19:20:28 webserver named[828]: reading built-in trusted keys from file '/etc/bind/bind.keys'
May  2 19:20:28 webserver named[828]: using default UDP/IPv4 port range: [1024, 65535]
May  2 19:20:28 webserver named[828]: using default UDP/IPv6 port range: [1024, 65535]
May  2 19:20:28 webserver named[828]: listening on IPv6 interfaces, port 53
May  2 19:20:28 webserver named[828]: listening on IPv4 interface lo, 127.0.0.1#53
May  2 19:20:28 webserver named[828]: listening on IPv4 interface eth0, 192.168.1.43#53
May  2 19:20:28 webserver named[828]: generating session key for dynamic DNS
May  2 19:20:28 webserver named[828]: sizing zone task pool based on 5 zones
May  2 19:20:28 webserver named[828]: using built-in root key for view _default
May  2 19:20:28 webserver named[828]: set up managed keys zone for view _default, file 'managed-keys.bind'
May  2 19:20:28 webserver named[828]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
May  2 19:20:28 webserver named[828]: automatic empty zone: 254.169.IN-ADDR.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: D.F.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 8.E.F.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 9.E.F.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: A.E.F.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: B.E.F.IP6.ARPA
May  2 19:20:28 webserver named[828]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
May  2 19:20:28 webserver named[828]: command channel listening on 127.0.0.1#953
May  2 19:20:28 webserver named[828]: command channel listening on ::1#953
May  2 19:20:28 webserver named[828]: the working directory is not writable
May  2 19:20:28 webserver named[828]: zone 0.in-addr.arpa/IN: loaded serial 1
May  2 19:20:28 webserver named[828]: zone 127.in-addr.arpa/IN: loaded serial 1
May  2 19:20:28 webserver named[828]: zone 255.in-addr.arpa/IN: loaded serial 1
May  2 19:20:28 webserver named[828]: zone localhost/IN: loaded serial 2
May  2 19:20:28 webserver named[828]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
May  2 19:20:28 webserver named[828]: managed-keys.bind.jnl: create: permission denied
May  2 19:20:28 webserver named[828]: managed-keys-zone ./IN: sync_keyzone:dns_journal_open -> unexpected error
May  2 19:20:28 webserver named[828]: running
May  2 19:20:29 webserver named[828]: error (network unreachable) resolving 'c.ntpns.org/A/IN': 2001:500:f::1#53
May  2 19:20:29 webserver named[828]: error (network unreachable) resolving 'c.ntpns.org/AAAA/IN': 2001:500:f::1#53
```

```
May  2 19:20:30 webserver named[828]: error (network unreachable) resolving 'ns2.p20.dynect.net/A/IN': 2001:500:94::100#53
May  2 19:20:30 webserver named[828]: error (network unreachable) resolving 'ntp.org/DS/IN': 2001:500:c::1#53
May  2 19:20:30 webserver named[828]: error (network unreachable) resolving 'org/DNSKEY/IN': 2001:500:40::1#53
May  2 19:20:30 webserver named[828]: error (network unreachable) resolving 'org/DNSKEY/IN': 2001:500:48::1#53
May  2 19:20:30 webserver named[828]: error (network unreachable) resolving 'com/DS/IN': 2001:503:ba3e::2:30#53
May  2 19:20:31 webserver named[828]: error (network unreachable) resolving 'net/DNSKEY/IN': 2001:503:231d::2:30#53
May  2 19:20:31 webserver named[828]: error (network unreachable) resolving '0.ubuntu.pool.ntp.org/A/IN': 2620:101:d007::42#53
```

```
May  2 19:20:39 webserver named[828]: error (network unreachable) resolving 'in-addr.arpa/DS/IN': 2001:500:2f::f#53
May  2 19:20:39 webserver named[828]: error (network unreachable) resolving 'in-addr.arpa/DS/IN': 2001:500:1::803f:235#53
May  2 19:20:40 webserver named[828]: error (network unreachable) resolving '102.50.in-addr.arpa/DS/IN': 2001:470:1a::2#53
May  2 19:20:40 webserver named[828]: error (network unreachable) resolving '50.in-addr.arpa/DNSKEY/IN': 2001:500:14:6050:ad::1#53
May  2 19:20:40 webserver named[828]: error (network unreachable) resolving '50-102-206-28.ekht.in.frontiernet.net/A/IN': 2001:503:a83e::2:30#53
May  2 19:21:26 webserver named[828]: received control channel command 'stop -p'
May  2 19:21:26 webserver named[828]: shutting down: flushing changes
May  2 19:21:26 webserver named[828]: stopping command channel on 127.0.0.1#953
May  2 19:21:26 webserver named[828]: stopping command channel on ::1#953
May  2 19:21:26 webserver named[828]: no longer listening on ::#53
May  2 19:21:26 webserver named[828]: no longer listening on 127.0.0.1#53
May  2 19:21:26 webserver named[828]: no longer listening on 192.168.1.43#53
May  2 19:21:26 webserver named[828]: exiting
```


Here is what I have in /etc/bind

```
total 52
-rw-r--r-- 1 root root 2389 Apr 13 16:31 bind.keys
-rw-r--r-- 1 root root  237 Nov 30  2010 db.0
-rw-r--r-- 1 root root  271 Nov 30  2010 db.127
-rw-r--r-- 1 root root  237 Nov 30  2010 db.255
-rw-r--r-- 1 root root  353 Nov 30  2010 db.empty
-rw-r--r-- 1 root root  270 Nov 30  2010 db.local
-rw-r--r-- 1 root root 2994 Nov 30  2010 db.root
-rw-r--r-- 1 root bind  463 Nov 30  2010 named.conf
-rw-r--r-- 1 root bind  490 Nov 30  2010 named.conf.default-zones
-rw-r--r-- 1 root bind  165 Nov 30  2010 named.conf.local
-rw-r--r-- 1 root bind  890 May  1 13:49 named.conf.options
-rw-r----- 1 bind bind   77 Feb  1  2011 rndc.key
-rw-r--r-- 1 root root 1317 Nov 30  2010 zones.rfc1918
```

---

### Post by CharlesA on 2012-05-02
> **Doug S said:**
> 
Charles: I don't think there is a specific "named" or "bind" log file by default.

I wasn't sure if there was one or not cuz I don't run bind and googling didn't seem to show anything. :D

I wonder if those "network unreachable" errors are what is causing bind to freak out.

---

### Post by Doug S on 2012-05-02
It looks as though you are just using a default installation of bind, and have not implemented a DNS for the internel side of your own domain.
As it turns out, I have the same conditions on one of my test computers. I compared syslog entries during startup between what you listed and what I have (I have IPV6 disabled, so there are some differences). I do not know if this is "the" culprit, but it is at least one problem```
May  2 19:20:28 webserver named[828]: the working directory is not writable
```I'll think about this one some more ...

---

### Post by Leonard Stefanescu on 2012-05-03
I had exactly the same problem. After some googling I found a solution somewhere.
You just have to delete de empty file /var/cache/bind/managed-keys.bind
You will have an error in syslog when bind will start but the load will be ok.

---

### Post by jrtboht on 2012-05-03
The first think I noticed was also all the network unreachable errors and after some searching I found a site that recommending turning off IPv6 by putting

```
# run resolvconf?
RESOLVCONF=yes
# startup options for the server
OPTIONS="-4 -u bind"
```

in /etc/default/bind9

I restarted bind but still have cpu around 100 (although the network unreachable errors seem to have stopped).
---------------------
I don't have a managed-keys.bind file in /var/cache/bind so I can't delete that :)
---------------------
I'm not exactly sure which directory it is talking about being as not being writable and what I should change it to
---------------------
Since I'm not using bind (as far as I can tell I'm not since everything still works when I stop it) would it be safe to uninstall bind9 and then reinstall?

---

### Post by CharlesA on 2012-05-03
I found a couple different answers to the:

```
webserver named[828]: the working directory is not writable
```

[http://forums.freebsd.org/showthread.php?t=1920](http://forums.freebsd.org/showthread.php?t=1920)
[http://slaptijack.com/system-administration/dnsbind-issue-named-the-working-directory-is-not-writable/](http://slaptijack.com/system-administration/dnsbind-issue-named-the-working-directory-is-not-writable/)

---

### Post by jrtboht on 2012-05-03
Thanks for the links, maybe I did this wrong but I ran 

```
sudo chmod g+w named
```

on /var/run/named (I guess I technically ran it in the /var/run directory but you get my point).  Then restarted bind9 and still got

```
May  3 10:03:26 webserver named[12363]: starting BIND 9.8.1-P1 -4 -u bind
May  3 10:03:26 webserver named[12363]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
May  3 10:03:26 webserver named[12363]: adjusted limit on open files from 4096 to 1048576
May  3 10:03:26 webserver named[12363]: found 1 CPU, using 1 worker thread
May  3 10:03:26 webserver named[12363]: using up to 4096 sockets
May  3 10:03:26 webserver named[12363]: loading configuration from '/etc/bind/named.conf'
May  3 10:03:26 webserver named[12363]: reading built-in trusted keys from file '/etc/bind/bind.keys'
May  3 10:03:26 webserver named[12363]: using default UDP/IPv4 port range: [1024, 65535]
May  3 10:03:26 webserver named[12363]: using default UDP/IPv6 port range: [1024, 65535]
May  3 10:03:26 webserver named[12363]: no IPv6 interfaces found
May  3 10:03:26 webserver named[12363]: listening on IPv4 interface lo, 127.0.0.1#53
May  3 10:03:26 webserver named[12363]: listening on IPv4 interface eth0, 192.168.1.43#53
May  3 10:03:26 webserver named[12363]: generating session key for dynamic DNS
May  3 10:03:26 webserver named[12363]: sizing zone task pool based on 5 zones
May  3 10:03:26 webserver named[12363]: using built-in root key for view _default
May  3 10:03:26 webserver named[12363]: set up managed keys zone for view _default, file 'managed-keys.bind'
May  3 10:03:26 webserver named[12363]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
May  3 10:03:26 webserver named[12363]: automatic empty zone: 254.169.IN-ADDR.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: D.F.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 8.E.F.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 9.E.F.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: A.E.F.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: B.E.F.IP6.ARPA
May  3 10:03:26 webserver named[12363]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
May  3 10:03:26 webserver named[12363]: command channel listening on 127.0.0.1#953
May  3 10:03:26 webserver named[12363]: the working directory is not writable
May  3 10:03:26 webserver named[12363]: zone 0.in-addr.arpa/IN: loaded serial 1
May  3 10:03:26 webserver named[12363]: zone 127.in-addr.arpa/IN: loaded serial 1
May  3 10:03:26 webserver named[12363]: zone 255.in-addr.arpa/IN: loaded serial 1
May  3 10:03:26 webserver named[12363]: zone localhost/IN: loaded serial 2
May  3 10:03:26 webserver named[12363]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
May  3 10:03:26 webserver named[12363]: managed-keys.bind.jnl: create: permission denied
May  3 10:03:26 webserver named[12363]: managed-keys-zone ./IN: sync_keyzone:dns_journal_open -> unexpected error
May  3 10:03:26 webserver named[12363]: running
May  3 10:03:42 webserver named[12363]: received control channel command 'stop -p'
May  3 10:03:42 webserver named[12363]: shutting down: flushing changes
May  3 10:03:42 webserver named[12363]: stopping command channel on 127.0.0.1#953
May  3 10:03:42 webserver named[12363]: no longer listening on 127.0.0.1#53
May  3 10:03:42 webserver named[12363]: no longer listening on 192.168.1.43#53
May  3 10:03:42 webserver named[12363]: exiting
```

---

### Post by Doug S on 2012-05-03
I'll list my permissions for you to compare:```
doug@s15:~$ ls -l /var/cache
total 52
drwxr-xr-x  3 www-data www-data 4096 Mar 14 11:54 apache2
drwxr-xr-x  3 root     root     4096 May  3 06:31 apt
drwxr-xr-x  3 root     root     4096 Apr 29 06:47 apt-xapian-index
drwxrwxr-x  2 [COLOR=red]root     bind[/COLOR]     4096 May  2 20:27 [COLOR=red]bind[/COLOR]
drwxr-xr-x  2 root     root     4096 Apr 29 15:43 debconf
drwxr-xr-x  2 root     root     4096 Apr 27 15:37 fontconfig
drwxr-xr-x  2 root     root     4096 Jun 27  2011 fonts
drwxr-xr-x  2 root     root     4096 Apr 10 21:10 git
drwx------  2 root     root     4096 Apr 29 15:43 ldconfig
drwx--x--x  3 root     root     4096 Mar 14 11:55 libvirt
drwxr-sr-x 34 man      root     4096 May  3 06:32 man
drwxr-xr-x  2 root     root     4096 Dec 13 09:11 pppconfig
drwxr-xr-x  3 root     root     4096 May  3 07:41 samba

``````
doug@s15:~$ ls -l /var/cache/bind
total 8
-rw-r--r-- 1 bind bind 698 May  2 10:34 managed-keys.bind
-rw-r--r-- 1 bind bind 512 May  2 10:34 managed-keys.bind.jnl
```> Since I'm not using bind (as far as I can tell I'm not since everything still works when I stop it) would it be safe to uninstall bind9 and then reinstall? I think you could uninstall bind and leave it uninstalled. You don't acutally seem to be using it.

---

### Post by jrtboht on 2012-05-03
for bind permissions I have


```
drwxr-xr-x  2 root     root     4096 Nov 30  2010 bind
```

so where do I change this to match yours?

---

### Post by CharlesA on 2012-05-03
> **jrtboht said:**
> for bind permissions I have


```
drwxr-xr-x  2 root     root     4096 Nov 30  2010 bind
```

so where do I change this to match yours?
Run this:

```
sudo chown root:bind /var/cache/bind
```

---

### Post by jrtboht on 2012-05-03
closer, it's now

```
drwxr-xr-x  2 root     bind     4096 Nov 30  2010 bind
```

sorry, I've never been good with permission (or linux in general;))

---

### Post by CharlesA on 2012-05-03
> **jrtboht said:**
> closer, it's now

```
drwxr-xr-x  2 root     bind     4096 Nov 30  2010 bind
```

sorry, I've never been good with permission (or linux in general;))
Ok, now run this:

```
sudo chmod 775 /var/cache/bind
```

Also check inside that directory to make sure the files inside have the same permissions as Doug's above.

---

### Post by jrtboht on 2012-05-03
I think that did the trick.  I restarted the entire server and bind is nowhere to be found when I run top.

```
 202 root      20   0     0    0    0 S  0.3  0.0   0:00.13 kworker/0:3
 1809 jeremy    20   0  2808 1064  832 R  0.3  0.1   0:00.04 top
    1 root      20   0  3520 1832 1228 S  0.0  0.2   0:00.70 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd
   15 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd
   18 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.24 kworker/u:1
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kswapd0
   23 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd
   24 root      39  19     0    0    0 S  0.0  0.0   0:00.00 khugepaged
   25 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark
   26 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea
   27 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto
   35 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld
   55 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 devfreq_wq
   57 root      20   0     0    0    0 S  0.0  0.0   0:00.14 kworker/0:2
  183 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
  184 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 firewire
  192 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
  193 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  194 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
  195 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kworker/u:3
  217 root      20   0     0    0    0 S  0.0  0.0   0:00.01 jbd2/sda1-8
  218 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-unwrit
  306 root      20   0  2812  604  448 S  0.0  0.1   0:00.16 upstart-udev-br
  310 root      20   0  2952 1132  728 S  0.0  0.1   0:00.10 udevd
  379 root      20   0  2948  584  280 S  0.0  0.1   0:00.00 udevd
  380 root      20   0  2948  584  280 S  0.0  0.1   0:00.00 udevd
  431 messageb  20   0  3236  848  624 S  0.0  0.1   0:00.03 dbus-daemon
  437 syslog    20   0 30016 1244 1016 S  0.0  0.1   0:00.05 rsyslogd
  541 root      20   0  2824  348  204 S  0.0  0.0   0:00.01 upstart-socket-
  675 root      20   0  2908  404  128 S  0.0  0.0   0:00.00 dhclient3
  710 root      20   0  6660 2256 1828 S  0.0  0.2   0:00.00 sshd
  766 root      20   0  4612  808  696 S  0.0  0.1   0:00.00 getty
  771 root      20   0  4612  820  696 S  0.0  0.1   0:00.00 getty
  777 root      20   0  4612  812  696 S  0.0  0.1   0:00.00 getty
  778 root      20   0  4612  812  696 S  0.0  0.1   0:00.00 getty
  781 root      20   0  4612  816  696 S  0.0  0.1   0:00.00 getty
  793 root      20   0  2156  592  496 S  0.0  0.1   0:00.00 acpid
  796 root      20   0  2600  856  680 S  0.0  0.1   0:00.00 cron
  797 daemon    20   0  2448  348  224 S  0.0  0.0   0:00.00 atd
  801 whoopsie  20   0 24448 3536 2700 S  0.0  0.4   0:00.01 whoopsie
  813 mysql     20   0  312m  39m 6492 S  0.0  4.2   0:03.06 mysqld
```


  To be sure that it is in fact running I restarted bind and then checked the logs and got the following


```
May  3 11:51:43 webserver named[832]: received control channel command 'stop -p'
May  3 11:51:43 webserver named[832]: shutting down: flushing changes
May  3 11:51:43 webserver named[832]: stopping command channel on 127.0.0.1#953
May  3 11:51:43 webserver named[832]: no longer listening on 127.0.0.1#53
May  3 11:51:43 webserver named[832]: no longer listening on 192.168.1.43#53
May  3 11:51:43 webserver named[832]: exiting
May  3 11:51:44 webserver named[1689]: starting BIND 9.8.1-P1 -4 -u bind
May  3 11:51:44 webserver named[1689]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
May  3 11:51:44 webserver named[1689]: adjusted limit on open files from 4096 to 1048576
May  3 11:51:44 webserver named[1689]: found 1 CPU, using 1 worker thread
May  3 11:51:44 webserver named[1689]: using up to 4096 sockets
May  3 11:51:44 webserver named[1689]: loading configuration from '/etc/bind/named.conf'
May  3 11:51:44 webserver named[1689]: reading built-in trusted keys from file '/etc/bind/bind.keys'
May  3 11:51:44 webserver named[1689]: using default UDP/IPv4 port range: [1024, 65535]
May  3 11:51:44 webserver named[1689]: using default UDP/IPv6 port range: [1024, 65535]
May  3 11:51:44 webserver named[1689]: no IPv6 interfaces found
May  3 11:51:44 webserver named[1689]: listening on IPv4 interface lo, 127.0.0.1#53
May  3 11:51:44 webserver named[1689]: listening on IPv4 interface eth0, 192.168.1.43#53
May  3 11:51:44 webserver named[1689]: generating session key for dynamic DNS
May  3 11:51:44 webserver named[1689]: sizing zone task pool based on 5 zones
May  3 11:51:44 webserver named[1689]: using built-in root key for view _default
May  3 11:51:44 webserver named[1689]: set up managed keys zone for view _default, file 'managed-keys.bind'
May  3 11:51:44 webserver named[1689]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
May  3 11:51:44 webserver named[1689]: automatic empty zone: 254.169.IN-ADDR.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: D.F.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 8.E.F.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 9.E.F.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: A.E.F.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: B.E.F.IP6.ARPA
May  3 11:51:44 webserver named[1689]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
May  3 11:51:44 webserver named[1689]: command channel listening on 127.0.0.1#953
May  3 11:51:44 webserver named[1689]: zone 0.in-addr.arpa/IN: loaded serial 1
May  3 11:51:44 webserver named[1689]: zone 127.in-addr.arpa/IN: loaded serial 1
May  3 11:51:44 webserver named[1689]: zone 255.in-addr.arpa/IN: loaded serial 1
May  3 11:51:44 webserver named[1689]: zone localhost/IN: loaded serial 2
May  3 11:51:44 webserver named[1689]: managed-keys-zone ./IN: loaded serial 2
May  3 11:51:44 webserver named[1689]: running
```

so it looks like it's running and my server load is still around 0.1

Thanks CharlesA and Doug S for helping me through this

---

### Post by CharlesA on 2012-05-03
Awesome. Funny how such a small thing like permissions can bring a server to its knees.

Glad it's working now. :)

---

### Post by snpz on 2012-12-19
Thanks - that trick worked for me as well :):popcorn:

---

