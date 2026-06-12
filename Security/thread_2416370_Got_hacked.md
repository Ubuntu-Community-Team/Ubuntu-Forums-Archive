---
title: "Got hacked"
date: 2019-04-09
forum: Security
---

### Post by buksa on 2019-04-09
Hi everyone. 
If there's exising posts about this subject that I dind't find, please forward me to it.

The abuse-team of my box provider have challenged me on a ongoing port scan towards a range of RFC1918 IPs (LAN IPs within subnets etc. i.e. 192.168.x.x, 10.0.0.0, 172.x.x.x etc.)
They say that they have received complaints from IT-dep. in various companies about security threats. 

This have led me to first of all, close down all outgoing trafic from my Ubuntu 16.04 server with ufw-rules that denies all outgoing on all ports except for chosen whitelisted IPs both at home and at work. 
Now this gives me time to figure out what is happening. I am new to this kind of threat. After some digging and attemts to set up an activity log etc. I gave up and trying here. 

Is this a typical security breach known amongst hackers? Just to put me in the right direction, I'd appreciate any help. 
I am afraid to open my firewall without fixing the service or user that is running malicious activities. 

I don't know what kind of information to supply you with until further replies, but as a start, here's my active PIDs. If anything suspicious, please point it out. 
I also have a netstat running in a root screen, writing a log-fil. But netstat didn't run when the attack happened or when the port scanning was happening.

My usage is: Plex server, apache server w/ MySQL and certbot/SSL, SSH, Tautulli-app for Plex. I had for a short time, Samba and regular FTPd (proftpd but not running as system services). 

SO FAR I HAVE: 
- Deleted all inactive users.
- Root user is disabled for SSH (allways was). 
- Ran a few malware and rootkit scanner software that gave me some recommandations for actions towards vulnerable subjects. But didn't find anything specific as I could see. 
- Tried to install Graylog but stalled so far due to versions compability issues agains ElastiSearch  (still looking at this matter). 



```
PID USER      PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
    1 root       20   0  181M  5528  3504 S  0.0  0.0  0:16.54 /sbin/init
  385 root       20   0  100M  1008   824 S  0.0  0.0  0:00.00 /sbin/lvmetad -f
  405 root       20   0 12204  4596  1472 S  0.0  0.0  1:14.83 /usr/sbin/haveged --Foreground --verbose=1 -w 1024
  406 root       20   0 52124 17280 14772 S  0.0  0.1  0:24.83 /lib/systemd/systemd-journald
  413 root       20   0 46928  5564  2888 S  0.0  0.0  0:01.90 /lib/systemd/systemd-udevd
  513 www-data   20   0  448M 11404  1840 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
  767 systemd-t  20   0   99M  2452  2236 S  0.0  0.0  0:02.66 /lib/systemd/systemd-timesyncd
  773 systemd-t  20   0   99M  2452  2236 S  0.0  0.0  0:00.98 /lib/systemd/systemd-timesyncd
  870 daemon     20   0 26044  2132  1932 S  0.0  0.0  0:00.01 /usr/sbin/atd -f
  890 root       20   0  382M  5016  4140 S  0.0  0.0  0:33.12 /usr/lib/accountsservice/accounts-daemon
  891 root       20   0 28996  3348  2548 S  0.0  0.0  0:02.02 /lib/systemd/systemd-logind
  896 avahi      20   0 44908  3000  2624 S  0.0  0.0  0:00.05 avahi-daemon: running [Ubuntu-1604-xenial-64-minimal.local]
  897 root       20   0  141M  2528  2244 S  0.0  0.0  0:07.33 /usr/sbin/cron -f
  898 messagebu  20   0 43692  4212  3012 S  0.0  0.0  0:03.79 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
  915 root       20   0  382M  5016  4140 S  0.0  0.0  0:32.62 /usr/lib/accountsservice/accounts-daemon
  937 avahi      20   0 44784   320     0 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
  983 root       20   0  382M  5016  4140 S  0.0  0.0  0:00.12 /usr/lib/accountsservice/accounts-daemon
  984 root       20   0  551M  7864  5468 S  0.0  0.0  0:01.45 /usr/sbin/NetworkManager --no-daemon
 1027 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.25 /usr/lib/plexmediaserver/Plex Media Server
 1028 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.18 /usr/lib/plexmediaserver/Plex Media Server
 1029 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.27 /usr/lib/plexmediaserver/Plex Media Server
 1033 root       20   0 13688  1996  1608 S  0.0  0.0  0:00.50 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan --syslog
 1115 syslog     20   0  250M  3188  2776 S  0.0  0.0  0:00.03 /usr/sbin/rsyslogd -n
 1116 syslog     20   0  250M  3188  2776 S  0.0  0.0  0:00.00 /usr/sbin/rsyslogd -n
 1117 syslog     20   0  250M  3188  2776 S  0.0  0.0  0:00.00 /usr/sbin/rsyslogd -n
 1118 syslog     20   0  250M  3188  2776 S  0.0  0.0  0:00.02 /usr/sbin/rsyslogd -n
 1164 root       20   0  551M  7864  5468 S  0.0  0.0  0:00.00 /usr/sbin/NetworkManager --no-daemon
 1166 root       20   0  551M  7864  5468 S  0.0  0.0  0:00.51 /usr/sbin/NetworkManager --no-daemon
 1455 deluge     20   0  461M  110M  9764 S  0.0  0.7  4h13:27 /usr/bin/python /usr/bin/deluged -d
 1459 deluge     20   0  239M 62256  7272 S  0.0  0.4  8:50.11 deluge-web
 1473 root       20   0 94928  6948  6008 S  0.0  0.0  0:00.01 sshd: buksa [priv]
 1490 buksa      20   0 94928  4468  3504 S  0.0  0.0  0:00.23 sshd: buksa@pts/0
 1493 buksa      20   0  135M  5420  3420 S  0.0  0.0  0:00.04 -bash
 1521 root       20   0  128M  1556  1420 S  0.0  0.0  0:00.00 /sbin/agetty --noclear tty1 linux
 1555 root       20   0 65512  5444  4732 S  0.0  0.0  0:00.33 /usr/sbin/sshd -D
 1559 root       20   0  392M  4620  3848 S  0.0  0.0  0:00.01 /usr/sbin/gdm3
 1565 root       20   0  166M  3988  3524 S  0.0  0.0  0:00.00 sudo htop
 1566 root       20   0  392M  4620  3848 S  0.0  0.0  0:00.00 /usr/sbin/gdm3
 1567 root       20   0  392M  4620  3848 S  0.0  0.0  0:00.00 /usr/sbin/gdm3
 1568 root       20   0  140M  5140  3228 R  0.7  0.0  0:13.08 htop
 1569 root       20   0  339M  5424  4344 S  0.0  0.0  0:00.12 gdm-session-worker [pam/gdm-launch-environment]
 1574 root       20   0  339M  5424  4344 S  0.0  0.0  0:00.00 gdm-session-worker [pam/gdm-launch-environment]
 1575 root       20   0  339M  5424  4344 S  0.0  0.0  0:00.06 gdm-session-worker [pam/gdm-launch-environment]
 1613 root       20   0  134M  3108  2676 S  0.0  0.0  0:00.00 /bin/bash /usr/bin/mysqld_safe
 1619 buksa      20   0 45280  4176  3296 S  0.0  0.0  0:00.01 /lib/systemd/systemd --user
 1621 buksa      20   0 63536  2160     0 S  0.0  0.0  0:00.00 (sd-pam)
 1761 gdm        20   0 45280  4088  3208 S  0.0  0.0  0:00.02 /lib/systemd/systemd --user
 1762 gdm        20   0 63536  2160     0 S  0.0  0.0  0:00.00 (sd-pam)
 1791 gdm        20   0  302M  3864  3364 S  0.0  0.0  0:00.00 /usr/lib/gdm3/gdm-x-session /usr/bin/gnome-session --autostart /usr/share/gdm/greeter/autostart
 1806 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.04 /usr/lib/plexmediaserver/Plex Media Server
 1807 gdm        20   0  302M  3864  3364 S  0.0  0.0  0:00.00 /usr/lib/gdm3/gdm-x-session /usr/bin/gnome-session --autostart /usr/share/gdm/greeter/autostart
 1808 root       20   0  357M 20644  7144 S  0.0  0.1  0:08.23 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 1809 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.03 /usr/lib/plexmediaserver/Plex Media Server
 1811 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.00 /usr/lib/plexmediaserver/Plex Media Server
 1838 mysql      20   0  624M  109M  6104 S  0.7  0.7 14:32.53 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1839 root       20   0  138M   956   776 S  0.0  0.0  0:00.00 logger -t mysqld -p daemon error
 1875 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:04.23 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1876 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:03.93 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1877 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:04.28 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1878 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:04.30 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1879 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:04.24 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1880 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:03.56 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1881 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:02.85 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1882 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:03.93 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1883 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:03.68 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1884 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:03.71 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 1899 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:06.97 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2037 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:34.31 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2038 mysql      20   0  624M  109M  6104 S  0.0  0.7  1:01.79 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2039 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:40.10 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2040 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:03.55 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2041 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:07.32 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2042 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:00.32 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2043 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:38.63 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2044 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:35.27 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2047 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:00.00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2062 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:01.25 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2063 root       20   0  443M  8772  6220 S  0.0  0.1  0:07.94 /usr/sbin/smbd -D
 2065 root       20   0  435M  4696  2252 S  0.0  0.0  0:00.00 /usr/sbin/smbd -D
 2069 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:00.00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2074 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2075 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2076 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2077 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2078 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2079 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2080 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2081 root       20   0  357M 20644  7144 S  0.0  0.1  0:00.00 /usr/lib/xorg/Xorg vt7 -displayfd 3 -auth /run/user/124/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2082 root       20   0  443M  5632  3080 S  0.0  0.0  0:04.21 /usr/sbin/smbd -D
 2114 gdm        20   0 42980  3524  2992 S  0.0  0.0  0:00.07 dbus-daemon --print-address 4 --session
 2115 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:03.93 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
 2157 gdm        20   0  302M  3864  3364 S  0.0  0.0  0:00.00 /usr/lib/gdm3/gdm-x-session /usr/bin/gnome-session --autostart /usr/share/gdm/greeter/autostart
 2161 deluge     20   0  461M  110M  9764 S  0.0  0.7  8:04.99 /usr/bin/python /usr/bin/deluged -d
 2162 deluge     20   0  461M  110M  9764 S  0.7  0.7 36:26.13 /usr/bin/python /usr/bin/deluged -d
 2168 gdm        20   0  544M  7052  5272 S  0.0  0.0  0:00.10 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
 2181 deluge     20   0  461M  110M  9764 S  0.0  0.7  0:16.66 /usr/bin/python /usr/bin/deluged -d
 2247 gdm        20   0  330M  3816  3328 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi-bus-launcher
 2248 gdm        20   0  330M  3816  3328 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi-bus-launcher
 2249 gdm        20   0  330M  3816  3328 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi-bus-launcher
 2251 gdm        20   0  330M  3816  3328 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi-bus-launcher
 2252 gdm        20   0 42764  2932  2608 S  0.0  0.0  0:00.00 /usr/bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
 2254 gdm        20   0  202M  4528  3896 S  0.0  0.0  0:00.03 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 2271 gdm        20   0  202M  4528  3896 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 2272 gdm        20   0  202M  4528  3896 S  0.0  0.0  0:00.00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session

 2282 gdm        20   0  544M  7052  5272 S  0.0  0.0  0:00.00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
 2283 gdm        20   0  544M  7052  5272 S  0.0  0.0  0:00.03 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
 2285 gdm        20   0  544M  7052  5272 S  0.0  0.0  0:00.00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
 2287 gdm        20   0  970M 12488  7448 S  0.0  0.1  0:02.39 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2291 gdm        20   0  970M 12488  7448 S  0.0  0.1  0:00.00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2293 gdm        20   0  970M 12488  7448 S  0.0  0.1  0:00.07 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2294 gdm        20   0  970M 12488  7448 S  0.0  0.1  0:00.00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2296 root       20   0  452M  6680  5424 S  0.0  0.0  0:00.06 /usr/lib/upower/upowerd
 2297 root       20   0  452M  6680  5424 S  0.0  0.0  0:00.00 /usr/lib/upower/upowerd
 2298 root       20   0  452M  6680  5424 S  0.0  0.0  0:00.02 /usr/lib/upower/upowerd
 2312 gdm        20   0  970M 12488  7448 S  0.0  0.1  0:00.00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2314 colord     20   0  407M  6756  4140 S  0.0  0.0  0:00.05 /usr/lib/colord/colord
 2317 gdm        20   0 1849M  119M 26636 S  0.0  0.8  7:17.04 gnome-shell --mode=gdm
 2318 colord     20   0  407M  6756  4140 S  0.0  0.0  0:00.00 /usr/lib/colord/colord
 2320 colord     20   0  407M  6756  4140 S  0.0  0.0  0:00.00 /usr/lib/colord/colord
 2323 gdm         9 -11  441M  4276  3100 S  0.0  0.0  0:00.03 /usr/bin/pulseaudio --start --log-target=syslog
 2324 rtkit      21   1  179M  2740  2464 S  0.0  0.0  0:15.06 /usr/lib/rtkit/rtkit-daemon
 2327 rtkit      20   0  179M  2740  2464 S  0.0  0.0  0:08.41 /usr/lib/rtkit/rtkit-daemon
 2328 rtkit      RT   1  179M  2740  2464 S  0.0  0.0  0:06.63 /usr/lib/rtkit/rtkit-daemon
 2333 gdm        20   0  441M  4276  3100 S  0.0  0.0  0:00.00 /usr/bin/pulseaudio --start --log-target=syslog
 2340 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:15.76 gnome-shell --mode=gdm
 2341 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:27.00 gnome-shell --mode=gdm
 2342 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:24.77 gnome-shell --mode=gdm
 2343 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:24.76 gnome-shell --mode=gdm
 2344 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:24.22 gnome-shell --mode=gdm
 2345 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:23.90 gnome-shell --mode=gdm
 2346 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:23.79 gnome-shell --mode=gdm
 2347 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:23.51 gnome-shell --mode=gdm
 2348 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:23.34 gnome-shell --mode=gdm
 2349 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:00.25 gnome-shell --mode=gdm
 2351 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:00.00 gnome-shell --mode=gdm
 2354 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:00.00 gnome-shell --mode=gdm
 2355 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:00.05 gnome-shell --mode=gdm
 2364 gdm        20   0 1849M  119M 26636 S  0.0  0.8  0:00.00 gnome-shell --mode=gdm
 2469 gdm        20   0  450M  4568  3512 S  0.0  0.0  0:00.01 ibus-daemon --xim --panel disable
 2470 gdm        20   0  450M  4568  3512 S  0.0  0.0  0:00.00 ibus-daemon --xim --panel disable
 2472 gdm        20   0  371M  3104  2748 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-dconf
 2473 gdm        20   0  450M  4568  3512 S  0.0  0.0  0:00.00 ibus-daemon --xim --panel disable
 2477 gdm        20   0  452M 10080  6868 S  0.0  0.1  0:00.03 /usr/lib/ibus/ibus-x11 --kill-daemon
 2478 gdm        20   0  371M  3104  2748 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-dconf
 2480 gdm        20   0  371M  3104  2748 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-dconf
 2481 gdm        20   0  371M  3104  2748 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-dconf
 2482 gdm        20   0  452M 10080  6868 S  0.0  0.1  0:00.00 /usr/lib/ibus/ibus-x11 --kill-daemon
 2483 gdm        20   0  452M 10080  6868 S  0.0  0.1  0:00.00 /usr/lib/ibus/ibus-x11 --kill-daemon
 2490 root       20   0 43900  3492  2980 S  0.0  0.0  0:00.00 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
 2508 gdm        20   0  297M  3068  2724 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-engine-simple
 2515 gdm        20   0  297M  3068  2724 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-engine-simple
 2516 gdm        20   0  297M  3068  2724 S  0.0  0.0  0:00.00 /usr/lib/ibus/ibus-engine-simple
 5467 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:17.49 /usr/lib/plexmediaserver/Plex Media Server
 7630 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.09 python Tautulli.py
 7631 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.14 python Tautulli.py
 7632 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.05 python Tautulli.py
 7633 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.12 python Tautulli.py
 7634 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.02 python Tautulli.py
 7635 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.02 python Tautulli.py
 7636 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.11 python Tautulli.py
12665 root       20   0  140M  2796  2028 S  0.0  0.0  4:17.48 SCREEN
12666 root       20   0  134M  3444  2780 S  0.0  0.0  0:00.01 /bin/bash
14443 mysql      20   0  624M  109M  6104 S  0.0  0.7  0:00.09 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --skip-log-error --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/
14747 root       20   0  120M   440   372 S  1.4  0.0  5h47:44 netstat -nputwc
14748 root       20   0  120M   420   352 S  0.0  0.0  1:13.00 tee /home/buksa/network.log
18402 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:13.00 /usr/lib/plexmediaserver/Plex Media Server
18728 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:12.50 /usr/lib/plexmediaserver/Plex Media Server
19926 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:06.81 /usr/lib/plexmediaserver/Plex Media Server
19927 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:06.71 /usr/lib/plexmediaserver/Plex Media Server
20266 root       20   0  139M  2884  2380 S  0.0  0.0  0:01.31 SCREEN
20267 buksa      20   0  135M  5536  3464 S  0.0  0.0  0:00.04 /bin/bash
20280 buksa      20   0 2400M  107M 13744 S  0.0  0.7  6:58.05 python Tautulli.py
20304 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:05.16 python Tautulli.py
20305 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.07 python Tautulli.py
20306 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.08 python Tautulli.py
20307 buksa      20   0 2400M  107M 13744 S  0.0  0.7  1:36.43 python Tautulli.py
20308 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.00 python Tautulli.py
20309 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:11.75 python Tautulli.py
20310 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.69 python Tautulli.py
20311 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.44 python Tautulli.py
20312 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:02.40 python Tautulli.py
20313 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.71 python Tautulli.py
20314 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.62 python Tautulli.py
20315 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.60 python Tautulli.py
20316 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.64 python Tautulli.py
20317 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.81 python Tautulli.py
20318 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.74 python Tautulli.py
20319 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:01.70 python Tautulli.py
20320 buksa      20   0 2400M  107M 13744 S  0.0  0.7  2:12.55 python Tautulli.py
20321 buksa      20   0 25508  4048  3572 S  0.0  0.0  0:00.00 www-browser [http://localhost:8181/](http://localhost:8181/)
20333 buksa      20   0 2400M  107M 13744 S  0.0  0.7  1:15.92 python Tautulli.py
20334 buksa      20   0 2400M  107M 13744 S  0.0  0.7  1:15.98 python Tautulli.py
23842 nobody     20   0 43616  4484  3788 S  0.0  0.0  0:21.63 /usr/sbin/openvpn --daemon ovpn-server --status /run/openvpn/server.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/server.conf --writepid /run/openvpn/
23944 root       20   0  448M 41148 31592 S  0.0  0.3  0:03.73 /usr/sbin/apache2 -k start
24406 root       20   0  388M  8140  5848 S  0.0  0.0  0:00.23 /usr/lib/policykit-1/polkitd --no-debug
24407 root       20   0  388M  8140  5848 S  0.0  0.0  0:00.00 /usr/lib/policykit-1/polkitd --no-debug
24409 root       20   0  388M  8140  5848 S  0.0  0.0  0:00.06 /usr/lib/policykit-1/polkitd --no-debug
24529 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:02.98 /usr/lib/plexmediaserver/Plex Media Server
24530 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:02.86 /usr/lib/plexmediaserver/Plex Media Server
24531 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:02.72 /usr/lib/plexmediaserver/Plex Media Server
24534 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:02.99 /usr/lib/plexmediaserver/Plex Media Server
28689 snmp       20   0  171M  6440  2068 S  0.3  0.0 19:14.44 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux mteTrigger mteTriggerConf -p /run/snmpd.pid
29427 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:01.23 /usr/lib/plexmediaserver/Plex Media Server
30174 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.11 python Tautulli.py
30175 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.18 python Tautulli.py
30176 buksa      20   0 2400M  107M 13744 S  0.0  0.7  0:00.10 python Tautulli.py
30271 plex       20   0  4504   740   668 S  0.0  0.0  0:00.00 /bin/sh -c  PLEX_MEDIA_SERVER_INFO_VENDOR="$(grep ^NAME= /etc/os-release | awk -F= "{print \$2}" | tr -d \" )"  PLEX_MEDIA_SERVER_INFO_DEVICE="PC"  PLEX_MEDIA_SERVER_INFO_MOD
30281 plex       20   0 4656M  819M 25896 S  0.0  5.1  1h32:10 /usr/lib/plexmediaserver/Plex Media Server
30283 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:42.13 /usr/lib/plexmediaserver/Plex Media Server
30284 plex       20   0 4656M  819M 25896 S  0.0  5.1  2:33.54 /usr/lib/plexmediaserver/Plex Media Server
30285 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.42 /usr/lib/plexmediaserver/Plex Media Server
30405 plex       20   0 4656M  819M 25896 S  0.0  5.1  6:46.87 /usr/lib/plexmediaserver/Plex Media Server
30406 plex       20   0 4656M  819M 25896 S  0.0  5.1  6:45.24 /usr/lib/plexmediaserver/Plex Media Server
30442 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:22.05 /usr/lib/plexmediaserver/Plex Media Server
30448 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:10.77 /usr/lib/plexmediaserver/Plex Media Server
30449 plex       35  15 1930M 72884  8944 S  0.0  0.4 14:32.59 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30464 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.00 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30465 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.00 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30466 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.25 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30467 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.05 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30468 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.05 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30469 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.03 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30470 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.03 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30471 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.36 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30475 www-data   20   0  448M 13396  3740 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
30476 www-data   20   0  448M 11404  1840 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
30477 www-data   20   0  448M 11404  1840 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
30478 www-data   20   0  448M 11404  1840 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
30479 www-data   20   0  448M 13396  3740 S  0.0  0.1  0:00.00 /usr/sbin/apache2 -k start
30494 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.00 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30495 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:00.00 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30509 plex       35  15 1930M 72884  8944 S  0.0  0.4  3:28.15 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
30521 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:23.66 /usr/lib/plexmediaserver/Plex Media Server
30524 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.00 /usr/lib/plexmediaserver/Plex Media Server
30527 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:40.78 /usr/lib/plexmediaserver/Plex Media Server
30528 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:18.36 /usr/lib/plexmediaserver/Plex Media Server
30530 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.00 /usr/lib/plexmediaserver/Plex Media Server
30531 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.00 /usr/lib/plexmediaserver/Plex Media Server
30532 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.05 /usr/lib/plexmediaserver/Plex Media Server
30533 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:44.10 /usr/lib/plexmediaserver/Plex DLNA Server
30534 plex       20   0  557M  7548  5988 S  0.0  0.0  3:33.29 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30541 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:00.00 /usr/lib/plexmediaserver/Plex DLNA Server
30542 plex       20   0  557M  7548  5988 S  0.0  0.0  0:00.00 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30543 plex       20   0  557M  7548  5988 S  0.0  0.0  0:10.81 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30544 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.21 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30545 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.38 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30546 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.41 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30547 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.27 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30548 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.30 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30549 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.32 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30550 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.50 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30551 plex       20   0  557M  7548  5988 S  0.0  0.0  0:01.24 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30570 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:11.70 /usr/lib/plexmediaserver/Plex DLNA Server
30571 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:01.91 /usr/lib/plexmediaserver/Plex DLNA Server
30572 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:07.10 /usr/lib/plexmediaserver/Plex DLNA Server
30573 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:03.93 /usr/lib/plexmediaserver/Plex DLNA Server
30574 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:02.93 /usr/lib/plexmediaserver/Plex DLNA Server
30575 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:07.11 /usr/lib/plexmediaserver/Plex DLNA Server
30576 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:01.05 /usr/lib/plexmediaserver/Plex DLNA Server
30577 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:02.35 /usr/lib/plexmediaserver/Plex DLNA Server30578 plex       20   0 1127M 13684 10036 S  0.0  0.1  0:02.36 /usr/lib/plexmediaserver/Plex DLNA Server
30651 plex       20   0 4656M  819M 25896 S  0.0  5.1  0:00.39 /usr/lib/plexmediaserver/Plex Media Server
30907 plex       20   0 4656M  819M 25896 S  0.0  5.1  2:25.36 /usr/lib/plexmediaserver/Plex Media Server
30956 plex       20   0  557M  7548  5988 S  0.0  0.0  3:11.75 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
30957 plex       20   0  557M  7548  5988 S  0.0  0.0  0:00.00 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.15.2.793-782228f99 32600 /waitm
32045 plex       20   0 1930M 72884  8944 S  0.0  0.4  0:05.17 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-782228f99/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.
```

---

### Post by TheFu on 2019-04-09
> My usage is: Plex server, apache server w/ MySQL and certbot/SSL, SSH, Tautulli-app for Plex. I had for a short time, Samba and regular FTPd (proftpd but not running as system services). 

What do the log files show?  Any authentication failures?

Is this at home or in a data center?
Which services do you think are internet available?  Prove it.  Router and local configs, please.
Are the system logs sent to a different machine or have they been locally altered by the attacker, so we cannot trust them?  

BTW, I don't think you can trust anything on this machine, so it needs to be wiped - AFTER you figure out how they got in.  All other devices on the same subnet probably need to be wiped too.

Can you compare what is on the system today with what it had 2 months ago?  Good versioned, backups, would let you do that.

To check out most of these things in an environment that you can trust, you'll need to boot from alternate media and scan the file system without any networking enabled. Can you trust the process table?  On a hacked machine, I wouldn't.

Are you really running a GUI on a server?  Why?  GUIs add 1000x more attack vectors to any system. 

Apache is a little vague. Is there a webapp or are they all static pages?
Why have a plain FTP server at all?  Just use opensftp-server. then authentication via ssh-keys can be used, all password attempts blocked and brute force attacks can be blocked using fail2ban.  Don't use passwords for any network authentication. If you can type the password in, then it isn't complex or long enough.  People never believe me when I say these things, until they get hacked.

Stay patched. You don't have to do it daily, but every 2 weeks is too long for internet-facing services.  I patch every Saturday morning - unless travelling.

That's off the top of my head.

My #1 security technique is having automatic, daily, versioned, backups that are "pulled", never pushed. Think about why "pulling" is important from a security standpoint. Should be clear.

---

### Post by buksa on 2019-04-10
[COLOR=#000000]TheFu, thanks for the quick reply. 
Just want to draw a conclusion before answering, then it's optional to read the rest. 
I had hoped that it would exist a better solution to the problem than to wipe the whole box, but as you say, it obviously has to be done. 

Since you took some time to help, I will try to answer your comments and questions as good as I can below. 

> What do the log files show? Any authentication failures?[/COLOR]
Don't know where all my most relevant log files are located, or what to look for. Maybe I'll take some time to configure logging after a fresh install has been set. Any good tuts on setting up a neat logging system, please advice. 

> [COLOR=#000000]Is this at home or in a data center?[/COLOR]
This is a private box that I rent (Hetzner in Germany) but it is placed within a large data center with a large LAN w/routed public IP.

> [COLOR=#000000]Which services do you think are internet available? Prove it. Router and local configs, please.[/COLOR]
[COLOR=#000000]Are the system logs sent to a different machine or have they been locally altered by the attacker, so we cannot trust them? [/COLOR]
My log files are stored locally, and I haven't altered any logging configs after installing Ubuntu. Which I should have done. 
I didn't run a firewall at all, because I thoguht I'd be a needle in a haystack if anyone should've been interested in hacking my IP. Naive thinking, I know. All services/every port range has been available to the internet. 

> [COLOR=#000000]Can you compare what is on the system today with what it had 2 months ago? Good versioned, backups, would let you do that.[/COLOR]
Haven't got any snapshots etc. Nothing to compare with. I will make a snapshot whenever I have restored this time. 

> [COLOR=#000000]Are you really running a GUI on a server? Why? GUIs add 1000x more attack vectors to any system.[/COLOR]
Was playing with VNC, needed it to access some software that I hadn't access to run at work by the time. Shouldn't been left as system service :( And stopped. I will not install any VNC next time. 

> [COLOR=#000000]Apache is a little vague. Is there a webapp or are they all static pages?[/COLOR]
It is all static pages. I've been using LetsEncrypt and Certbot with Apache to route subdomains for plex, Roundcube email web client, etc. But not a major thing. I also use Deluge Torrent client. But on a private tracker with secure connections to the tracker and users. (At least in theory) Since torrents require available ports, I need to have a closer look at which ports I can open and which ones to close without reducing hitrate for leechers.

> [COLOR=#000000]Why have a plain FTP server at all? Just use opensftp-server. then authentication via ssh-keys can be used, all password attempts blocked and brute force attacks can be blocked using fail2ban. Don't use passwords for any network authentication. If you can type the password in, then it isn't complex or long enough. People never believe me when I say these things, until they get hacked.[/COLOR] 
I almost always use SFTP via 22. But I wanted to map a directory in windows as a network drive. I didn't manage to get SFTP/22 working when I tried. Maybe it is possible somehow. Same reason I use smbd, but uncertain if it is a system service or not... I know it's a risk. 

I will CLEARLY take big advantage of your advices when restoring my system. Thanks very much.

---

### Post by TheFu on 2019-04-10
> **buksa said:**
> TheFu, thanks for the quick reply. 
Just want to draw a conclusion before answering, then it's optional to read the rest. 
I had hoped that it would exist a better solution to the problem than to wipe the whole box, but as you say, it obviously has to be done. 
Only open 1 port from the outside. ssh.  Move it to a non-standard port, setup ssh-keys for authentication. DO NOT ALLOW PASSWORDS over the internet.  Setup fail2ban to block brute force attacks.  Also, block all subnets on the internet from places you don't need to provide access.  If you are in Germany, then there isn't any reason to allow anyone in the USA or China to have access. Right?
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has some ideas and settings.
[https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication) - use ssh keys.
Never use plain FTP [https://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](https://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

> **buksa said:**
> 
Since you took some time to help, I will try to answer your comments and questions as good as I can below. 
Never allow access to services to anyone who doesn't need that access.  Period.  
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)  How you setup a server in the beginning matters.
[https://blog.jdpfu.com/2016/10/04/lamp-server-security](https://blog.jdpfu.com/2016/10/04/lamp-server-security) - thoughts on server security.

> **buksa said:**
> 
Don't know where all my most relevant log files are located, or what to look for. Maybe I'll take some time to configure logging after a fresh install has been set. Any good tuts on setting up a neat logging system, please advice. 

All Unix systems store most logs in /var/log/ .  If they aren't there, then YOU, the admin, would know where they were because you did something non-standard.  Google "ubuntu logs" for a tutorial.  This is my main tool for quickly checking logs for issues:
```
egrep -i 'error|warn' /var/log/*g
```
That searches all the current log files for warnings and errors.
Probably want to setup '**logwatch**' to let you know about issues daily too.

> **buksa said:**
> This is a private box that I rent (Hetzner in Germany) but it is placed within a large data center with a large LAN w/routed public IP.
If it is on the internet, inside someone else's building, on someone else's network, then it isn't private.  I know Germany has better privacy laws than in country, but the location **is** an issue if you expect anything on it to be private.

> **buksa said:**
> 
My log files are stored locally, and I haven't altered any logging configs after installing Ubuntu. Which I should have done. 
I didn't run a firewall at all, because I thoguht I'd be a needle in a haystack if anyone should've been interested in hacking my IP. Naive thinking, I know. All services/every port range has been available to the internet. 
It takes less than 8 minutes for every system on the internet using IPv4 to be scanned.  You only need a firewall enabled if you have services open to the world.  Nobody is interested in hacking YOUR specific box (probably), but they are very interested in hacking 1,000,000 Linux systems to use for anything they want.  By default, all inbound traffic needs to be blocked and only allow specific connections, like ssh, from your normal locations at home/work/school/coffee shop/cafes to have access to ssh.  Everyone else should be blocked.  

The firewall in Linux is part of the kernel.  What most people think of as "firewalls" are really just interfaces into the kernel controls. ufw is easy for home needs, but insufficient for servers and definitely insufficient for servers on the internet, with public services running.  Iptables is the tool you need to be using. Don't mix different firewall interfaces on the same machine.  Use one or the other. If you need to switch, be certain to clean up the one you aren't using anymore.

> **buksa said:**
> 
Haven't got any snapshots etc. Nothing to compare with. I will make a snapshot whenever I have restored this time. 
Snapshots are not backups.  You need daily, automatic, versioned, backups. If you cannot compare what is on the system today with what was on it yesterday, 3 days ago, last week, 2.2 weeks ago, last month, then you don't have a backup solution.  You have "hope."

> **buksa said:**
> 
Was playing with VNC, needed it to access some software that I hadn't access to run at work by the time. Shouldn't been left as system service :( And stopped. I will not install any VNC next time. 
Yeah ... nope to VNC.  Don't.  Just don't.  Not on an internet server.  Ok, there might be a need for a remote GUI.  When I need something like that, I use x2go, not VNC.  x2go is based on the NX protocol which uses ssh-tunnels and ssh-authentication.  NX "feels" 2-3x faster than VNC as well.  After people using VNC switch to x2go, they say it is like night vs day.  I don't load x2go on servers, but my primary desktop is a virtual machine, running a lite Ubuntu desktop, with x2go.  This runs on a headless server.  I'm using it right now from a cafe near my home on a cheap chromebook (running a lite Ubuntu desktop).  While I can't watch videos on it, everything else works just like being in the house.  I've used it from 5 different continents while travelling.  Great for security - only a non-standard ssh port is open.

> **buksa said:**
> 
It is all static pages. I've been using LetsEncrypt and Certbot with Apache to route subdomains for plex, Roundcube email web client, etc. But not a major thing. I also use Deluge Torrent client. But on a private tracker with secure connections to the tracker and users. (At least in theory) Since torrents require available ports, I need to have a closer look at which ports I can open and which ones to close without reducing hitrate for leechers. 
HTTPS isn't about security. It is about privacy of that connection.
Roundcube is a webapp. All webapps are dangerous.  Don't downplay the dangers.
I wouldn't run BT on any important server.  Buy a VPS in another country and use that for BT, and only BT, if you must.  Unix has an idea of separation of services.  In the 1990s, we'd put 50 services onto a single machine because we could and they were expensive.  Then we'd get stuck because of inter-dependencies that prevented upgrading 1 service because 3 others needed an older version of some library.  For the last 20 yrs, virtual machines have solved that problem.  1 VM for each similar, related, service.  VMs can be heavy, but a normal $400 desktop can easily run 25 VMs today.  I have a desktop from 2010 running 15 right now.  Those blog links above ... that's hitting a Core i5-750 box with 8GB of RAM.  Tomorrow, it might be on a different machine.  Virtual machines provide all sorts of great abstraction, so the physical hardware usually doesn't matter at all.

> **buksa said:**
> 
I almost always use SFTP via 22. But I wanted to map a directory in windows as a network drive. I didn't manage to get SFTP/22 working when I tried. Maybe it is possible somehow. Same reason I use smbd, but uncertain if it is a system service or not... I know it's a risk. 


Don't use port 22/tcp.  Move to something above 60K/tcp.
WinSCP is a Windows sftp client. When you setup the ssh-server on Linux, you get the sftp and scp servers with it.  All the fail2ban and ssh-keys work - the same ones.
Never use SMB/CIFS over the internet.  Purge that immediately. Only use CIFS on your home LAN and only for Windows machines.  For any Linux/Unix-based OS, there are better choices, IMHO. It is hard to explain how limited Windows is when it comes to network stuff that "just works" - like sshfs or NFS.

I don't understand putting plex inside a data center, but that could be my world view being warped by limited internet bandwidth at home, at least compared to many others.

> **buksa said:**
> 
I will CLEARLY take big advantage of your advices when restoring my system. Thanks very much.

The best way to learn about security is to be hacked, unfortunately.  I've been hacked 3 times.

First time, I was completely unprepared.  Thought I was safe since my IP was on a govt network. They got in over telnet using a well-know root password, the default.  I handed over the HDD to the security officer, never to get it back. It was purely an opportunity hack, long before security was much of a concern. At the time, ssh wasn't widely used anywhere and we where just beginning to deploy tcp-wrappers to protect services.  The hacker changed the root password and deleted my account - WHILE I WAS LOGGED IN!  The error message was this:
> You don't exist. Go away.

Second time, I was allowing DNS to be access over the internet and was 3 months behind on patches. Most of the internet was relatively safe back then. I happened to have a backup of the system that was 7 days old. With that backup, I was able to quickly compare all the current files with all the files in the backup and saw exactly what the hacker had done and was trying to accomplish. It was an automated attack. At the time, I didn't have backup religion. About a year later, I lost 80% of my data due to a failed disk that was part of a single LVM VG with 3 disks.  None of the data on any of those 3 disks was ever recovered. I got more and more backup religion after that.

I don't bring online any primary storage without a reasonable method to back it up. It has been that way the last 20 yrs or so.  A failed HDD is a minor inconvenience here, nothing more.

Last time, I was at a security conference, helping to run a King-of-the-Hill contest.  I wasn't on the attacker network, but someone decided to hack my bluetooth stack. I had a freshly loaded, freshly patched, Ubuntu desktop (running openbox, not Unity/Gnome/or any other DE).  I was prepared to be hacked, that is sorta what happens at security conferences.  I've always kept my cell phone off and never take a smartphone to those places. ;)  Hacking of cell phones is part of the games there.

How good are my backups?  Well, yesterday I added a new SSD to my newest system. It had been running off a 5+ yr old HDD that was previously installed in a 2009 Core i7 machine.  This was pre-UEFI.  I decided it was time for my legacy boot setup to end, so a fresh install of Ubuntu Server with ssh-server was the starting point.  30 minutes later, I had effectively the same virtual machine host as the day before running. Same hostname, same networking, all my script, packages, data, back exactly where they were before, just 50% of it was on the new SSD instead.  My backups are solid, but efficient.

Anyway, I suspect that is enough for now. Don't forget, this stuff is supposed to be fun.

---

### Post by buksa on 2019-04-10
Dear TheFu. 

I sure hope you make a good living out of your knowledge :) 
I've got no further comments here, else than THANK YOU very much for giving me so valuable information on the matter. 
This was above all expectations. You really got me thinking, and I'm looking forward to start setting everything up again. 

And yes, it is very fun and educational indeed. I am working as an IT consultant (not with Linux OS) in a Norwegian organization. Spends some time during the days to learn more networking skills and some Linux. 

By the way, the Plex-thing: There I've got allocated 1 Gbps in/out, and in Norway it's rather normal to have high speed fiber to most housings. I am having a 300 Mbps both ways in my apartment. And the cool thing is that it's not even a star topology, I ALLWAYS have 300 Mbps both ways no matter how much bandwidth is used in my neighborhood/against the same fiber node. And with Plex server with global access gives me options (and gives hackers options as well apparently). 

Well, enough about that. I guess I will be tagging this post as solved, and get to work/write a list of what needs to be done, and in what order I will do it in. :-) 
Thanks again!

---

