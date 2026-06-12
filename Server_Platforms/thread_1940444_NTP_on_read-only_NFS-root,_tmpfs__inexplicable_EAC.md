---
title: "NTP on read-only NFS-root, tmpfs : inexplicable EACCES"
date: 2012-03-13
forum: Server Platforms
---

### Post by chaz572 on 2012-03-13
Hi.  I'm trying to set up an ubuntu server as a grid compute master, serving PXE boot and NFS root to numerous diskless client nodes.  I'm trying to use NTP to keep time synchronized across the grid.  ntpd on the grid master is working fine.  I can't get ntpd on the compute nodes to work properly -- it keeps getting EACCES while trying to read its config file, and write its pid file.  Both reside in a tmpfs mounted on /var/run.

Here's the specialized /var/run setup code:
```

    # Create the NTP environment
    mkdir -m 3775 /var/run/ntp
    chgrp ntp /var/run/ntp
    echo "0.000" > /var/run/ntp/drift
    chown ntp /var/run/ntp/drift
    echo "driftfile /var/run/ntp/drift" > /var/run/ntp/conf
    echo "disable monitor" >> /var/run/ntp/conf
    echo "disable stats" >> /var/run/ntp/conf
    echo "enable ntp" >> /var/run/ntp/conf
    echo "restrict -4 default kod notrap nomodify nopeer noquery" >> /var/run/ntp/conf
    echo "restrict -6 default kod notrap nomodify nopeer noquery" >> /var/run/ntp/conf
    echo "restrict 127.0.0.1" >> /var/run/ntp/conf
    echo "restrict ::1" >> /var/run/ntp/conf
    ifconfig -a | sed -re 's/ *inet addr:(192\.168\.[0-9]+)\.[0-9]+ .*/server \1.1/' -e t -e d >> /var/run/ntp/conf
    ifconfig -a | sed -re 's/ *inet addr:(192\.168\.[0-9]+)\.[0-9]+ .*/restrict \1.1 kod notrap nopeer/' -e t -e d >>  /var/run/ntp/conf

```

Here's what that all looks like when I log into a running compute node:
```

Script started on Tue Mar 13 05:16:25 2012
root@vanadium:~# ls -ld /
drwxr-xr-x 21 root root 4096 Mar  9 18:00 /
root@vanadium:~# ls -ld /etc
drwxr-xr-x 72 root root 4096 Mar 12 17:02 /etc
root@vanadium:~# ls -la /etc/ntp.conf
lrwxrwxrwx 1 root root 17 Mar 12 16:05 /etc/ntp.conf -> /var/run/ntp/conf
root@vanadium:~# ls -ld /var
drwxr-xr-x 13 root root 4096 Mar  7 14:36 /var
root@vanadium:~# ls -ld /var/run
drwxr-xr-x 7 root root 440 Mar 13 05:15 /var/run
root@vanadium:~# ls -la /var/run/ntp
total 8
drwxrwsr-t 2 root ntp   80 Mar 13 05:14 .
drwxr-xr-x 7 root root 440 Mar 13 05:15 ..
-rw-r--r-- 1 root ntp  274 Mar 13 05:14 conf
-rw-r--r-- 1 ntp  ntp    6 Mar 13 05:14 drift
root@vanadium:~# cat /etc/ntp.conf
driftfile /var/run/ntp/drift
disable monitor
disable stats
enable ntp
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
restrict 127.0.0.1
restrict ::1
server 192.168.112.1
restrict 192.168.112.1 kod notrap nopeer
root@vanadium:~# touch /var/run/ntp/pid
root@vanadium:~# ls -l /var/run/ntp/pid
-rw-r--r-- 1 root ntp 0 Mar 13 05:17 /var/run/ntp/pid
root@vanadium:~# rm /var/run/ntp/pid
root@vanadium:~# su -s /bin/sh -c "cat /etc/ntp.conf" ntp
driftfile /var/run/ntp/drift
disable monitor
disable stats
enable ntp
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
restrict 127.0.0.1
restrict ::1
server 192.168.112.1
restrict 192.168.112.1 kod notrap nopeer
root@vanadium:~# su -s /bin/sh -c "touch /var/run/ntp/pid" ntp
root@vanadium:~# ls -l /var/run/ntp/pid
-rw-r--r-- 1 ntp ntp 0 Mar 13 05:19 /var/run/ntp/pid
root@vanadium:~# su -s /bin/sh -c "rm /var/run/ntp/pid" ntp
root@vanadium:~# ls -l /var/run/ntp/pid
ls: cannot access /var/run/ntp/pid: No such file or directory
root@vanadium:~# strace -v -o /tmp/ntp.trace /usr/sbin/ntpd -p /var/run/ntp/pid -g -u 104:106 -l /tmp/ntp.log -dd -n
ntpd 4.2.6p2@1.2194-o Thu Mar 10 21:16:06 UTC 2011 (1)
addto_syslog: logging to file /tmp/ntp.log
addto_syslog: set_process_priority: Leave priority alone: priority_done is <2>

addto_syslog: proto: precision = 0.102 usec

loop_config: item 1 freq 0.000000
event at 0 0.0.0.0 c01d 0d kern kernel time sync enabled
addto_syslog: pid file /var/run/ntp/pid: Permission denied

addto_syslog: getconfig: Couldn't open </etc/ntp.conf>

create_sockets(123)
addto_syslog: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16

addto_syslog: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123

created interface #0: fd=16, bfd=-1, name=v4wildcard, flags=0x89, scope=0, sin=0.0.0.0, bcast=0.0.0.0, mask=255.255.255.255, Disabled:
addto_syslog: Listen and drop on 1 v6wildcard :: UDP 123

created interface #1: fd=17, bfd=-1, name=v6wildcard, flags=0x81, scope=0, sin=::, Disabled:
create_interface(127.0.0.1#123)
addto_syslog: Listen normally on 2 lo 127.0.0.1 UDP 123

restrict: op 1 addr 127.0.0.1 mask 255.255.255.255 mflags 00003000 flags 00000001
created interface #2: fd=18, bfd=-1, name=lo, flags=0x5, scope=0, sin=127.0.0.1, mask=255.0.0.0, Enabled:
create_interface(192.168.112.23#123)
addto_syslog: Listen normally on 3 eth1 192.168.112.23 UDP 123

restrict: op 1 addr 192.168.112.23 mask 255.255.255.255 mflags 00003000 flags 00000001
created interface #3: fd=19, bfd=-1, name=eth1, flags=0x19, scope=0, sin=192.168.112.23, bcast=192.168.112.255, mask=255.255.255.0, Enabled:
create_interface(fe80::21d:9ff:fe6b:b2a8#123)
addto_syslog: Listen normally on 4 eth1 fe80::21d:9ff:fe6b:b2a8 UDP 123

restrict: op 1 addr fe80::21d:9ff:fe6b:b2a8 mask ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff mflags 00003000 flags 00000001
created interface #4: fd=20, bfd=-1, name=eth1, flags=0x11, scope=3, sin=fe80::21d:9ff:fe6b:b2a8, Enabled:
create_interface(::1#123)
addto_syslog: Listen normally on 5 lo ::1 UDP 123

restrict: op 1 addr ::1 mask ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff mflags 00003000 flags 00000001
created interface #5: fd=21, bfd=-1, name=lo, flags=0x5, scope=0, sin=::1, Enabled:
create_sockets: Total interfaces = 6
event at 0 0.0.0.0 c016 06 restart
loop_config: item 2 freq 1000000000.000000
event at 0 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
local_clock: mu 0 state 1 poll 3 count 0
event at 0 0.0.0.0 c011 01 freq_not_set
auth_agekeys: at 1 keys 0 expired 0
timer: interface update
^Caddto_syslog: ntpd exiting on signal 2

root@vanadium:~# exit
exit

Script done on Tue Mar 13 05:22:05 2012

```

Here's the generated log file:

```

13 Mar 05:21:33 ntpd[955]: set_process_priority: Leave priority alone: priority_done is <2>
13 Mar 05:21:33 ntpd[955]: proto: precision = 0.102 usec
13 Mar 05:21:33 ntpd[955]: pid file /var/run/ntp/pid: Permission denied
13 Mar 05:21:33 ntpd[955]: getconfig: Couldn't open </etc/ntp.conf>
13 Mar 05:21:33 ntpd[955]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
13 Mar 05:21:33 ntpd[955]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
13 Mar 05:21:33 ntpd[955]: Listen and drop on 1 v6wildcard :: UDP 123
13 Mar 05:21:33 ntpd[955]: Listen normally on 2 lo 127.0.0.1 UDP 123
13 Mar 05:21:33 ntpd[955]: Listen normally on 3 eth1 192.168.112.23 UDP 123
13 Mar 05:21:33 ntpd[955]: Listen normally on 4 eth1 fe80::21d:9ff:fe6b:b2a8 UDP 123
13 Mar 05:21:33 ntpd[955]: Listen normally on 5 lo ::1 UDP 123

```

You'll notice it's complained about both the conf file and the pid file.

I'm attaching the full strace output, as it's rather large to inline.  But here's the two relevant lines from it:

```

...
open("/var/run/ntp/pid", O_WRONLY|O_CREAT|O_TRUNC, 0666) = -1 EACCES (Permission denied)
...
open("/etc/ntp.conf", O_RDONLY)         = -1 EACCES (Permission denied)
...

```

It all goes down the same way whether ntpd is started automatically at boot time, or started manually after verifying everything looks good.  Logging or no logging, debug or no debug, ntpd gets EACCES on its conf and pid file that I can read and write just fine from the command line, either as root, or as user ntp.

I don't get it.  I'm tearing my hair out over this one.  Has anybody seen this kind of behavior before?

---

### Post by chaz572 on 2012-03-13
Finally got it.  Just needed another set of eyes.  Simple answer: apparmor.

Somebody else was looking at my work and said, "Hey, what's that in the log about apparmor and ntp?  Is that relevant?"  Bingo.  Added the appropriate /var/run/ntp/* config entries to the local/usr.sbin.ntpd apparmor profile, and all is well.  Happy time-synced compute nodes.

Thanks to anyone who at least read the prior post, scratched their head, and went, "Well dang, that's weird." :)

---

