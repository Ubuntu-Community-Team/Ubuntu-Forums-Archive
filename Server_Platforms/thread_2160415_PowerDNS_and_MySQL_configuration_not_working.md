---
title: "PowerDNS and MySQL configuration not working"
date: 2013-07-07
forum: Server Platforms
---

### Post by basicfreak on 2013-07-07
Before I begin here is my pdns.conf:
```
allow-recursion=127.0.0.1
config-dir=/etc/powerdns
daemon=yes
disable-axfr=yes
guardian=yes
launch=gmysql
gmysql-host=127.0.0.1
gmysql-user=dnsuser
gmysql-password=*******
gmysql-dbname=*******
gmysql-port=3306
gmysql-dnssec=no
lazy-recursion=yes
local-address=0.0.0.0
local-port=53
module-dir=/usr/lib/powerdns
setgid=pdns
setuid=pdns
socket-dir=/var/run
version-string=powerdns
include=/etc/powerdns/pdns.d

```
Running /etc/init.d/pdns monitor
```
Jul 06 23:39:02 Reading random entropy from '/dev/urandom'
Jul 06 23:39:02 This is module gmysqlbackend.so reporting
Jul 06 23:39:02 This is a standalone pdns
Jul 06 23:39:02 It is advised to bind to explicit addresses with the --local-address option
Jul 06 23:39:02 UDP server bound to 0.0.0.0:53
Jul 06 23:39:02 TCP server bound to 0.0.0.0:53
Jul 06 23:39:02 PowerDNS 3.0 (C) 2001-2011 PowerDNS.COM BV (Feb 13 2012, 23:48:17, gcc 4.6.2) starting up
Jul 06 23:39:02 PowerDNS comes with ABSOLUTELY NO WARRANTY. This is free software, and you are welcome to redistribute it according to the terms of the GPL version 2.
Jul 06 23:39:02 Set effective group id to 131
Jul 06 23:39:02 Set effective user id to 124
Jul 06 23:39:02 Creating backend connection for TCP
% Jul 06 23:39:02 gmysql Connection failed: Unable to connect to database: Access denied for user 'root'@'localhost' (using password: NO)
Jul 06 23:39:02 Caught an exception instantiating a backend, cleaning up
Jul 06 23:39:02 TCP server is unable to launch backends - will try again when questions come in: Unable to launch gmysql connection: Unable to connect to database: Access denied for user 'root'@'localhost' (using password: NO)
Jul 06 23:39:02 About to create 3 backend threads for UDP
Jul 06 23:39:02 gmysql Connection failed: Unable to connect to database: Access denied for user 'root'@'localhost' (using password: NO)
Jul 06 23:39:02 Caught an exception instantiating a backend, cleaning up
Jul 06 23:39:02 gmysql Connection failed: Unable to connect to database: Access denied for user 'root'@'localhost' (using password: NO)
Jul 06 23:39:02 Caught an exception instantiating a backend, cleaning up
Jul 06 23:39:02 gmysql Connection failed: Unable to connect to database: Access denied for user 'root'@'localhost' (using password: NO)
Jul 06 23:39:02 Caught an exception instantiating a backend, cleaning up
Jul 06 23:39:02 Done launching threads, ready to distribute questions

```

Output of netstat -tap
without PowerDNS running
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 10.0.0.1:3990           *:*                     LISTEN      16428/chilli    
tcp        0      0 *:ssh                   *:*                     LISTEN      971/sshd        
tcp        0      0 localhost:ipp           *:*                     LISTEN      1128/cupsd      
tcp        0      0 *:https                 *:*                     LISTEN      11100/apache2   
tcp        0      0 localhost:mysql         *:*                     LISTEN      1292/mysqld     
tcp        0      0 *:http                  *:*                     LISTEN      11100/apache2   
tcp        0      0 *:webmin                *:*                     LISTEN      2515/perl       
tcp        0      0 192.168.1.41:ssh        192.168.1.8:57946       ESTABLISHED 4707/2          
tcp        0      0 192.168.1.41:ssh        192.168.1.8:57945       ESTABLISHED 4592/0          
tcp        0      0 192.168.1.41:ssh        192.168.1.8:60212       ESTABLISHED 17225/3         
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      971/sshd        
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      1128/cupsd

```

Output of ps aux
Again without PowerDNS running
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3568  2092 ?        Ss   Jul04   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Jul04   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Jul04   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Jul04   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    Jul04   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    Jul04   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    Jul04   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    Jul04   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    Jul04   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    Jul04   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    Jul04   0:01 [events/0]
root        16  0.0  0.0      0     0 ?        S    Jul04   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S    Jul04   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S    Jul04   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S    Jul04   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S    Jul04   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S    Jul04   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S    Jul04   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S    Jul04   0:00 [pm]
root        25  0.0  0.0      0     0 ?        S    Jul04   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    Jul04   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S    Jul04   0:00 [kintegrityd/0]
root        28  0.0  0.0      0     0 ?        S    Jul04   0:00 [kintegrityd/1]
root        29  0.0  0.0      0     0 ?        S    Jul04   0:00 [kintegrityd/2]
root        30  0.0  0.0      0     0 ?        S    Jul04   0:00 [kintegrityd/3]
root        31  0.0  0.0      0     0 ?        S    Jul04   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S    Jul04   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S    Jul04   0:00 [kblockd/2]
root        34  0.0  0.0      0     0 ?        S    Jul04   0:00 [kblockd/3]
root        35  0.0  0.0      0     0 ?        S    Jul04   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    Jul04   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    Jul04   0:00 [kacpi_hotplug]
root        38  0.0  0.0      0     0 ?        S    Jul04   0:00 [ata/0]
root        39  0.0  0.0      0     0 ?        S    Jul04   0:00 [ata/1]
root        40  0.0  0.0      0     0 ?        S    Jul04   0:00 [ata/2]
root        41  0.0  0.0      0     0 ?        S    Jul04   0:00 [ata/3]
root        42  0.0  0.0      0     0 ?        S    Jul04   0:00 [ata_aux]
root        43  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksuspend_usbd]
root        44  0.0  0.0      0     0 ?        S    Jul04   0:00 [khubd]
root        45  0.0  0.0      0     0 ?        S    Jul04   0:00 [kseriod]
root        46  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmmcd]
root        51  0.0  0.0      0     0 ?        S    Jul04   0:00 [khungtaskd]
root        52  0.0  0.0      0     0 ?        S    Jul04   0:00 [kswapd0]
root        53  0.0  0.0      0     0 ?        SN   Jul04   0:00 [ksmd]
root        54  0.0  0.0      0     0 ?        S    Jul04   0:00 [aio/0]
root        55  0.0  0.0      0     0 ?        S    Jul04   0:00 [aio/1]
root        56  0.0  0.0      0     0 ?        S    Jul04   0:00 [aio/2]
root        57  0.0  0.0      0     0 ?        S    Jul04   0:00 [aio/3]
root        58  0.0  0.0      0     0 ?        S    Jul04   0:00 [ecryptfs-kthrea]
root        59  0.0  0.0      0     0 ?        S    Jul04   0:00 [crypto/0]
root        60  0.0  0.0      0     0 ?        S    Jul04   0:00 [crypto/1]
root        61  0.0  0.0      0     0 ?        S    Jul04   0:00 [crypto/2]
root        62  0.0  0.0      0     0 ?        S    Jul04   0:00 [crypto/3]
root        66  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_0]
root        67  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_1]
root        70  0.0  0.0      0     0 ?        S    Jul04   0:00 [kstriped]
root        71  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmpathd/0]
root        72  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmpathd/1]
root        73  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmpathd/2]
root        74  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmpathd/3]
root        75  0.0  0.0      0     0 ?        S    Jul04   0:00 [kmpath_handlerd]
root        76  0.0  0.0      0     0 ?        S    Jul04   0:00 [ksnapd]
root        77  0.0  0.0      0     0 ?        S    Jul04   0:06 [kondemand/0]
root        78  0.0  0.0      0     0 ?        S    Jul04   0:05 [kondemand/1]
root        79  0.0  0.0      0     0 ?        S    Jul04   0:04 [kondemand/2]
root        80  0.0  0.0      0     0 ?        S    Jul04   0:03 [kondemand/3]
root        81  0.0  0.0      0     0 ?        S    Jul04   0:00 [kconservative/0]
root        82  0.0  0.0      0     0 ?        S    Jul04   0:00 [kconservative/1]
root        83  0.0  0.0      0     0 ?        S    Jul04   0:00 [kconservative/2]
root        84  0.0  0.0      0     0 ?        S    Jul04   0:00 [kconservative/3]
root       263  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_2]
root       265  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_3]
root       269  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_4]
root       274  0.0  0.0      0     0 ?        S    Jul04   0:00 [scsi_eh_5]
root       286  0.0  0.0      0     0 ?        S    Jul04   0:00 [i915]
root       343  0.0  0.0      0     0 ?        S    Jul04   0:00 [jbd2/sda4-8]
root       344  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       345  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       346  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       347  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       431  0.0  0.0   2784   816 ?        S    Jul04   0:00 upstart-udev-bridge --daemon
root       433  0.0  0.0   3312  1540 ?        Ss   Jul04   0:00 /sbin/udevd --daemon
root       633  0.0  0.0   3308  1140 ?        S    Jul04   0:00 /sbin/udevd --daemon
root       699  0.0  0.0      0     0 ?        S    Jul04   0:00 [kpsmoused]
root       720  0.0  0.0      0     0 ?        S    Jul04   0:00 [iwlagn]
root       721  0.0  0.0      0     0 ?        S    Jul04   0:00 [phy0]
root       796  0.0  0.0      0     0 ?        S    Jul04   0:00 [hd-audio0]
root       878  0.0  0.0   2796   524 ?        S    Jul04   0:00 upstart-socket-bridge --daemon
root       884  0.0  0.0      0     0 ?        S    Jul04   0:02 [jbd2/sda3-8]
root       885  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       886  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       887  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       888  0.0  0.0      0     0 ?        S    Jul04   0:00 [ext4-dio-unwrit]
root       971  0.0  0.1   6632  2324 ?        Ss   Jul04   0:00 /usr/sbin/sshd -D
syslog    1022  0.0  0.0  37156  1848 ?        Sl   Jul04   0:47 rsyslogd -c5
108       1056  0.0  0.0   3860  1636 ?        Ss   Jul04   0:06 dbus-daemon --system --fork --activation=upstart
root      1092  0.0  0.1   7092  2808 ?        Ss   Jul04   0:00 /usr/sbin/modem-manager
root      1121  0.0  0.0   4692  1660 ?        Ss   Jul04   0:00 /usr/sbin/bluetoothd
root      1128  0.0  0.1   8184  3508 ?        Ss   Jul04   0:00 /usr/sbin/cupsd -F
root      1139  0.0  0.0      0     0 ?        S    Jul04   0:00 [bluetooth]
root      1158  0.0  0.0      0     0 ?        S<   Jul04   0:00 [krfcommd]
avahi     1160  0.0  0.0   3488  1732 ?        S    Jul04   0:00 avahi-daemon: running [drltcom1.local]
avahi     1161  0.0  0.0   3368   536 ?        Ss   Jul04   0:00 avahi-daemon: chroot helper
root      1191  0.0  0.2  25060  5884 ?        Ssl  Jul04   0:04 NetworkManager
root      1197  0.0  0.1  29252  3804 ?        Sl   Jul04   0:03 /usr/lib/policykit-1/polkitd --no-debug
root      1211  0.0  0.0   4400   824 tty4     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty4
root      1215  0.0  0.0   4400   824 tty5     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty5
root      1241  0.0  0.0   4400   824 tty2     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty2
root      1242  0.0  0.0   4400   832 tty3     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty3
root      1245  0.0  0.0   4400   832 tty6     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty6
root      1254  0.0  0.0   2124   704 ?        Ss   Jul04   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1261  0.0  0.0   2568   908 ?        Ss   Jul04   0:00 cron
daemon    1262  0.0  0.0   2420   436 ?        Ss   Jul04   0:00 atd
root      1263  0.0  0.1  19824  2632 ?        Ssl  Jul04   0:00 gdm-binary
root      1271  0.0  0.0   3308  1124 ?        S    Jul04   0:00 /sbin/udevd --daemon
mysql     1292  0.0  2.0 355108 42656 ?        Ssl  Jul04   2:37 /usr/sbin/mysqld
root      1294  0.0  0.1  21504  3396 ?        Sl   Jul04   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1304  0.0  0.4  17688  8296 tty7     Ss+  Jul04   0:09 /usr/bin/Xorg :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-vBSJ1e/database -nolisten tcp vt7
root      1456  0.0  0.1  38340  3932 ?        Sl   Jul04   0:09 /usr/sbin/console-kit-daemon --no-daemon
gdm       1553  0.0  0.0   3584  1084 ?        Ss   Jul04   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
gdm       1587  0.0  0.3  54536  7356 ?        Ssl  Jul04   0:00 /usr/bin/gnome-session --session gdm --autostart=/usr/share/gdm/autostart/LoginWindow/
gdm       1636  0.0  0.1  10008  3612 ?        S    Jul04   0:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
gdm       1654  0.0  0.6 209720 13036 ?        Sl   Jul04   0:08 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root      1683  0.0  0.1  32436  3788 ?        Sl   Jul04   0:03 /usr/lib/upower/upowerd
gdm       1766  0.0  0.0   8116  2036 ?        S    Jul04   0:00 /usr/lib/gvfs/gvfsd
gdm       2076  0.0  0.5 173712 10536 ?        Sl   Jul04   0:03 metacity
gdm       2132  0.0  0.2 103504  5012 ?        S<l  Jul04   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     2139  0.0  0.0  25376  1320 ?        SNl  Jul04   0:02 /usr/lib/rtkit/rtkit-daemon
gdm       2367  0.0  0.1  14188  2900 ?        S    Jul04   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
gdm       2378  0.0  0.6 106640 12764 ?        Sl   Jul04   0:13 /usr/lib/gdm/gdm-simple-greeter
root      2387  0.0  0.1   8464  2420 ?        S    Jul04   0:00 /usr/lib/gdm/gdm-session-worker
root      2389  0.0  0.1  17804  3388 ?        Sl   Jul04   0:03 /usr/lib/accountsservice/accounts-daemon
root      2515  0.0  0.6  19064 14036 ?        Ss   Jul04   0:06 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      2518  0.0  0.0   4400   828 tty1     Ss+  Jul04   0:00 /sbin/getty -8 38400 tty1
ntp       3592  0.0  0.0   4968  1436 ?        Ss   Jul04   0:10 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 116:125
root      3700  0.0  0.0   4968  1072 ?        S    Jul04   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 116:125
root      4592  0.0  0.1  11804  3760 ?        Ss   15:37   0:00 sshd: root@pts/0    
root      4643  0.0  0.2   7640  4108 pts/0    Ss   15:37   0:00 -bash
freerad   4705  0.0  0.2  19876  5240 pts/0    S+   15:37   0:00 freeradius -X
root      4707  0.0  0.1  11804  3760 ?        Rs   15:37   0:01 sshd: root@pts/2    
root      4759  0.0  0.2   7700  4208 pts/2    Ss   15:38   0:01 -bash
root     11100  0.0  0.2  39500  4392 ?        S    18:56   0:00 /usr/sbin/apache2 -k start
root     11177  0.0  0.2  39500  4392 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
root     13445  0.0  0.0      0     0 ?        S    21:14   0:00 [flush-8:0]
root     16060  0.0  0.2  39500  4392 ?        S    22:06   0:00 /usr/sbin/apache2 -k start
root     16150  0.0  0.2  39500  4392 ?        S    22:06   0:00 /usr/sbin/apache2 -k start
root     16378  0.0  0.2  39500  4392 ?        S    22:07   0:00 /usr/sbin/apache2 -k start
root     16428  0.2 22.6 794536 463872 ?       Ss   22:08   0:12 /usr/sbin/chilli --conf /etc/chilli.conf
root     16570  0.0  0.2  39500  4392 ?        S    22:10   0:00 /usr/sbin/apache2 -k start
root     16572  0.0  0.2  39500  4392 ?        S    22:10   0:00 /usr/sbin/apache2 -k start
root     16573  0.0  0.2  39500  4392 ?        S    22:10   0:00 /usr/sbin/apache2 -k start
root     16621  0.0  0.2  39500  4392 ?        S    22:10   0:00 /usr/sbin/apache2 -k start
root     17225  0.0  0.1  11804  3744 ?        Ss   22:25   0:00 sshd: root@pts/3    
root     17385  0.0  0.2   7684  4184 pts/3    Ss+  22:25   0:00 -bash
root     17546  0.0  0.2  39500  4332 ?        S    22:33   0:00 /usr/sbin/apache2 -k start
root     18299  0.0  0.0   4896  1168 pts/2    R+   23:46   0:00 ps aux
root     21694  0.0  0.4  39476  8716 ?        Ss   03:01   0:03 /usr/sbin/apache2 -k start

```I can't figure out why it is trying root@localhost with no password when I clearly have it set for dnsuser@127.0.0.1 with a password.

Sorry for so much information up there, rather have too much than too little - just let me know if you need anything else

I've tried google with no success all I could find was install tutorials which I followed threw step by step.



Any help is appreciated,

BASICFreak

---

### Post by basicfreak on 2013-07-08
BUMP

Anyone have any ideas, I can't at all figure this out.

What am I doing wrong...

---

### Post by DJ_Max on 2013-07-09
How did you install PowerDNS? Did you restart pdns?

---

### Post by basicfreak on 2013-07-09
> **DJ_Max said:**
> How did you install PowerDNS? Did you restart pdns?
I installed it the lazy way
```
apt-get install pdns-server pdns-backend-mysql
```

And I stopped the service and ran the debug command many times ```
[COLOR=#000000]/etc/init.d/pdns monitor[/COLOR]
```

---

### Post by bluexmas on 2013-07-11
check powerdns config folder (/etc/powerdns) . As far as I remember, in 12.04 (I suppose you use this version) there is a default config file created for mysql connection. this file might override your mysql settings from pdns.conf.

---

