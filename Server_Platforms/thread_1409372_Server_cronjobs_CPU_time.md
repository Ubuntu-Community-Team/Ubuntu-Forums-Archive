---
title: "Server cronjobs CPU time?"
date: 2010-02-17
forum: Server Platforms
---

### Post by ThomWilhelm on 2010-02-17
I have a 9.04 server for mysql/apache commands. Mainly does MySQL but runs some cronjobs using apache php scripts.

This week the database server has been using more CPU that normal. I noticed certain cronjobs were not performing as normal, so decided to get a command that would tell me the current usage of CPU. Here is my output:

0.1   -  -5 S 00:00:00 [ksoftirqd/0]
 0.1   -   0 S 00:00:01 /bin/dbus-daemon --system
 0.1   -   0 S 00:00:01 /usr/sbin/console-kit-daemon
 0.1   -   0 S 00:00:01 /sbin/init
 0.1   -  -5 S 00:00:01 [ksoftirqd/1]
 0.1   -   0 S 00:00:01 /usr/sbin/hald
 0.2   -   0 S 00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 0.3   -   0 S 00:00:02 nautilus
 0.3   -   0 S 00:00:02 nm-applet --sm-disable
 0.3   -   0 S 00:00:00 /usr/bin/gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 52428836 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpfUz1hy
 0.4   -   0 S 00:00:03 gnome-panel
 1.4   -   0 S 00:00:11 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 2.0   -  -5 S 00:00:17 [kswapd0]
 5.4   -   0 S 00:00:44 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --log-error=/var/lib/mysql/fileserver.err --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
 2.0   -   0 R 00:00:00 ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu
 8.2   -   0 D 00:00:03 /usr/bin/wget -q --timeout=3600 --ignore-length [http://127.0.0.1/serverScripts/hallOfFame.php](http://127.0.0.1/serverScripts/hallOfFame.php)
 9.0   -   0 D 00:00:03 /usr/bin/wget -q --timeout=3600 --ignore-length [http://127.0.0.1/serverScripts/calendarMinute.php](http://127.0.0.1/serverScripts/calendarMinute.php)
 9.8   -   0 D 00:00:04 /usr/bin/wget -q --timeout=3600 --ignore-length [http://127.0.0.1/serverScripts/transferMinute.php](http://127.0.0.1/serverScripts/transferMinute.php)
10.5   -   0 D 00:00:04 /usr/bin/wget -q --timeout=3600 --ignore-length [http://127.0.0.1/serverScripts/autoCloseCups.php](http://127.0.0.1/serverScripts/autoCloseCups.php)
12.4   -   0 S 00:00:09 /usr/bin/python2.6 /usr/bin/update-manager
22.0   -   0 R 00:00:03 /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 52428836 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpfUz1hy

Lines like this:

10.5   -   0 D 00:00:04 /usr/bin/wget -q --timeout=3600 --ignore-length [http://127.0.0.1/serverScripts/autoCloseCups.php](http://127.0.0.1/serverScripts/autoCloseCups.php)

I do not understand why my calls to wget can be there, I have added die("") statements to the top of all the files to stop them being executed, so how on earth are they taking up 10% CPU???

All the above scripts that use wget calls have such statements to stop execution, so I am stumped as to why CPU usage is so high.

Any ideas??

---

### Post by ThomWilhelm on 2010-02-23
For anyone interested this was fixed by running the scripts through /usr/bin/php rather than using wget calls.

---

