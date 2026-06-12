---
title: "Is there any strange process or port ?"
date: 2006-09-19
forum: Server Platforms
---

### Post by mulysa on 2006-09-19
I had been ask to suspend the server for a while due to bandwidth issue. They claimed that there are a lot of incoming and outgoing traffics. However, up to this moment I don't know what wrong with my server. 
I don't have any process to download anything at all.
So, I curious whether my server was hacked or not?
And here is the result of top:

```
  1 root      16   0  1568  528  460 S  0.0  0.1   0:01.87 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.14 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  105 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  106 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  108 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  107 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  696 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
 1810 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1923 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 2083 root      18  -4  2104  548  368 S  0.0  0.1   0:00.92 udevd
 2911 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 2973 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3388 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3389 root      15   0     0    0    0 S  0.0  0.0   0:00.06 kjournald
 3390 root      15   0     0    0    0 S  0.0  0.0   0:00.11 kjournald
 3693 syslog    16   0  1764  664  548 S  0.0  0.1   0:00.04 syslogd
 3710 root      16   0  1680  496  412 S  0.0  0.1   0:00.03 dd
 3712 klog      17   0  2388 1312  388 S  0.0  0.3   0:00.11 klogd
 3737 bind      18   0 29932 2772 1888 S  0.0  0.5   0:00.29 named
 3760 root      16   0  4760 1052  756 S  0.0  0.2   0:00.00 sshd
 3779 root      16   0  1624  296  232 S  0.0  0.1   0:00.00 mdadm
 3792 daemon    16   0  1796  392  296 S  0.0  0.1   0:00.00 atd
 3802 root      16   0  2120  732  600 S  0.0  0.1   0:00.00 cron
 3838 root      16   0 21888  11m 5224 S  0.0  2.4   0:00.51 httpd
 3862 root      24   0  2620 1304 1064 S  0.0  0.3   0:00.03 mysqld_safe
 3865 nobody    16   0  5392 1528  688 S  0.0  0.3   0:00.00 proftpd
 3880 nobody    15   0 20740 8804 2656 S  0.0  1.7   0:00.00 httpd
 3912 root      16   0  1560  492  424 S  0.0  0.1   0:00.01 getty
 3913 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 3914 root      16   0  1560  492  424 S  0.0  0.1   0:00.01 getty
 3915 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 3916 root      16   0  1564  496  424 S  0.0  0.1   0:00.01 getty
```

Just need your suggestion whether is there any strange process or not?
And here is the result of netstat -an

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp        0      0 <myip>:53        0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:444             0.0.0.0:*               LISTEN
tcp        0      0 <myip>:80        72.30.129.159:35790     TIME_WAIT
tcp        0      0 <myip>:80        72.14.199.1:41963       TIME_WAIT
tcp6       0      0 ::1:953                 :::*                    LISTEN
tcp6       0      0 :::443                  :::*                    LISTEN
tcp6       0    416 ::ffff:<myip>:443 ::ffff:10.7.1.50:1082  ESTABLISHED
tcp6       0  0 ::ffff:<myip>:443 ::ffff:192.165.213.18:9452 ESTABLISHED
udp        0      0 0.0.0.0:32768           0.0.0.0:*
udp        0      0 <myip>:53        0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp6       0      0 :::32769                :::*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    4840     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     8716     /opt/lampp/logs/cgisock.3838
unix  2      [ ACC ]     STREAM     LISTENING     8810     /opt/lampp/var/mysql/mysql.sock
unix  2      [ ]         DGRAM                    8368     /var/lib/named/dev/log
unix  6      [ ]         DGRAM                    8366     /dev/log
unix  2      [ ]         DGRAM                    12631
unix  3      [ ]         STREAM     CONNECTED     12628
unix  3      [ ]         STREAM     CONNECTED     12627
unix  2      [ ]         DGRAM                    9008
unix  3      [ ]         STREAM     CONNECTED     9005
unix  3      [ ]         STREAM     CONNECTED     9004
unix  2      [ ]         DGRAM                    8442
unix  2      [ ]         DGRAM                    8411
```

If you need anything to investigate please feel free to ask me.
Thank you in advance.

---

### Post by Jussi Kukkonen on 2006-09-19
Check out *chkrootkit* and *rkhunter*, they might help...

Also, I'm not a apache expert, but should you really have two instances running with one of them owned by root and one by nobody? It may well be normal, I'm just asking...

---

### Post by skymt on 2006-09-19
Try running "netstat -anp". That'll show you what process is listening on each port.

---

### Post by unless on 2006-12-01
> Also, I'm not a apache expert, but should you really have two instances running with one of them owned by root and one by nobody? It may well be normal, I'm just asking...


Yep, two apache instances is normal. I'm not an expert either, but I think this is the reasoning: 

The UN*X standard is not to allow any process to bind to ports below 1024 unless the owner of the process is root. So, since apache likely listens on tcp port 80 (and maybe 443), apache must be instantiated by root.

On the other hand, you don't want your web server to have root privileges, because when/if your installation has a security hole, the black hat weenie that exploits it will be able to leverage the root privileges of the process and potentially walk all over your system.

So the trick is for apache to start as root, then instantiate child processes of itself, with the user www-data or apache or nobody as owner of the children. The child processes are the ones that actually do the interacting with the clients.

That being said, it probably would've been a good idea to check the apache logs to see if apache was bandwidth hog.

---

