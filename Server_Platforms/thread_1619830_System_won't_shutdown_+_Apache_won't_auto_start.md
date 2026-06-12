---
title: "System won't shutdown + Apache won't auto start"
date: 2010-11-12
forum: Server Platforms
---

### Post by OxideCom on 2010-11-12
Hi All,

First post here so I'll do my best to provide the information needed.

First off, thanks for reading, and hopefully helping me out. 

System:

Dell Poweredge R310
Xeon 3460 2.8Ghz
4x2GB ram
4x 160GB Sata 7.2k (RAID 10)
Ubuntu Server 64bit

If I type as root, "reboot" or "shutdown -r now", nothing happenings - except the apache2 process stops + the usual "System is going down for reboot now". If I type "shutdown -h now" the system goes down.

Upon booting the server back up, MySQL starts correctly, but Apache2 does not - I have to run "service apache2 start", and it starts up fine.

I feel the 2 issues are related. I've reinstalled apache2 completely (configs and all) and this didn't help - I used yum to install/reinstall it.

Thanks,

Rob

---

### Post by dapperdanny77 on 2010-11-12
is this a RedHat System ? (because of yum)

---

### Post by OxideCom on 2010-11-12
Ubuntu 10.04.1 

Also I used apt-get not yum, my bad :)

---

### Post by dapperdanny77 on 2010-11-12
maybe some symlinks are missing due to whatever - you can recreate them with update-rc.d

```
>update-rc.d apache2 enable
```


any error entries in /var/log/apache2/error.log ?

---

### Post by OxideCom on 2010-11-12
Cheers, unfortunately that didn't fix it, no errors in the error log either. Looks like I'm missing some arguements?

```
update-rc.d: warning: apache2 start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: apache2 stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 Enabling system startup links for /etc/init.d/apache2 ...
 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2
   /etc/rc1.d/K09apache2
   /etc/rc2.d/S91apache2
   /etc/rc3.d/S91apache2
   /etc/rc4.d/S91apache2
   /etc/rc5.d/S91apache2
   /etc/rc6.d/K09apache2
 Adding system startup for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2 -> ../init.d/apache2
   /etc/rc1.d/K09apache2 -> ../init.d/apache2
   /etc/rc6.d/K09apache2 -> ../init.d/apache2
   /etc/rc2.d/S91apache2 -> ../init.d/apache2
   /etc/rc3.d/S91apache2 -> ../init.d/apache2
   /etc/rc4.d/S91apache2 -> ../init.d/apache2
   /etc/rc5.d/S91apache2 -> ../init.d/apache2
```

---

### Post by dapperdanny77 on 2010-11-12
does your /var/log/apache2/error.log look like this

```
[Fri Nov 12 20:16:19 2010] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Fri Nov 12 20:16:41 2010] [notice] caught SIGTERM, shutting down
```

try to catch a more verbose output of apache startup or shutdown

```
bash -x /etc/init.d/apache2 stop
```

anyway if apache is stopping/starting properly when doing it manually ... we have to look deeper into the startup process

---

### Post by OxideCom on 2010-11-12
Nothing in the error log from after the server starts, only after I start it manually.

Stop:

```
+ ENV='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin'
+ HTCACHECLEAN_RUN=auto
+ HTCACHECLEAN_MODE=daemon
+ HTCACHECLEAN_SIZE=300M
+ HTCACHECLEAN_DAEMON_INTERVAL=120
+ HTCACHECLEAN_PATH=/var/cache/apache2/mod_disk_cache
+ HTCACHECLEAN_OPTIONS=
+ set -e
+ '[' -x /usr/sbin/apache2 ']'
+ HAVE_APACHE2=1
+ . /lib/lsb/init-functions
++ FANCYTTY=
++ '[' -e /etc/lsb-base-logging.sh ']'
++ . /etc/lsb-base-logging.sh
+ test -f /etc/default/rcS
+ . /etc/default/rcS
++ TMPTIME=0
++ SULOGIN=no
++ DELAYLOGIN=no
++ UTC=yes
++ VERBOSE=no
++ FSCKFIX=no
+ test -f /etc/default/apache2
+ . /etc/default/apache2
++ HTCACHECLEAN_RUN=auto
++ HTCACHECLEAN_MODE=daemon
++ HTCACHECLEAN_SIZE=300M
++ HTCACHECLEAN_DAEMON_INTERVAL=120
++ HTCACHECLEAN_PATH=/var/cache/apache2/mod_disk_cache
++ HTCACHECLEAN_OPTIONS=-n
+ APACHE2CTL='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/apache2ctl'
+ HTCACHECLEAN='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/htcacheclean'
++ . /etc/apache2/envvars
+++ export APACHE_RUN_USER=www-data
+++ APACHE_RUN_USER=www-data
+++ export APACHE_RUN_GROUP=www-data
+++ APACHE_RUN_GROUP=www-data
+++ export APACHE_PID_FILE=/var/run/apache2.pid
+++ APACHE_PID_FILE=/var/run/apache2.pid
+++ export LANG=C
+++ LANG=C
+++ export LANG
++ echo /var/run/apache2.pid
+ PIDFILE=/var/run/apache2.pid
+ '[' -z /var/run/apache2.pid ']'
+ case $1 in
+ check_htcacheclean
+ '[' daemon = daemon ']'
+ '[' auto = yes ']'
+ '[' auto = auto -a -e /etc/apache2/mods-enabled/disk_cache.load ']'
+ return 1
+ log_daemon_msg 'Stopping web server' apache2
+ '[' -z 'Stopping web server' ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ '[' -t 1 ']'
+ '[' xxterm '!=' x ']'
+ '[' xxterm '!=' xdumb ']'
+ '[' -x /usr/bin/tput ']'
+ '[' -x /usr/bin/expr ']'
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ '[' -z ']'
+ FANCYTTY=1
+ case "$FANCYTTY" in
+ true
+ /usr/bin/tput xenl
++ /usr/bin/tput cols
+ COLS=157
+ '[' 157 ']'
+ '[' 157 -gt 6 ']'
++ /usr/bin/expr 157 - 7
+ COL=150
+ printf ' * Stopping web server apache2       '
 * Stopping web server apache2       ++ /usr/bin/expr 157 - 1
+ /usr/bin/tput hpa 156
                                                                                                                                                            + printf ' '
 + apache_wait_stop
++ pidof_apache
++ '[' -e /var/run/apache2.pid ']'
++ pidof apache2
++ tr ' ' '\n'
+++ cat /var/run/apache2.pid
++ grep 1109
++ return 0
+ PIDTMP=1109
+ kill -0 1109
+ PID=1109
+ apache_stop
+ env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/apache2ctl configtest
+ env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/apache2ctl stop
+ grep -v 'not running'
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
+ '[' -n 1109 ']'
+ i=0
+ kill -0 1109
+ '[' 0 = 60 ']'
+ '[' 0 = 0 ']'
+ echo -n ' ... waiting '
 ... waiting + i=1
+ sleep 1
+ kill -0 1109
+ log_end_msg 0
+ '[' -z 0 ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ '[' 150 ']'
+ '[' -x /usr/bin/tput ']'
+ printf '\r'
+ /usr/bin/tput hpa 150
                                                                                                                                                      + '[' 0 -eq 0 ']'
+ echo '[ OK ]'
[ OK ]
+ return 0

```

Start:

```
+ ENV='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin'
+ HTCACHECLEAN_RUN=auto
+ HTCACHECLEAN_MODE=daemon
+ HTCACHECLEAN_SIZE=300M
+ HTCACHECLEAN_DAEMON_INTERVAL=120
+ HTCACHECLEAN_PATH=/var/cache/apache2/mod_disk_cache
+ HTCACHECLEAN_OPTIONS=
+ set -e
+ '[' -x /usr/sbin/apache2 ']'
+ HAVE_APACHE2=1
+ . /lib/lsb/init-functions
++ FANCYTTY=
++ '[' -e /etc/lsb-base-logging.sh ']'
++ . /etc/lsb-base-logging.sh
+ test -f /etc/default/rcS
+ . /etc/default/rcS
++ TMPTIME=0
++ SULOGIN=no
++ DELAYLOGIN=no
++ UTC=yes
++ VERBOSE=no
++ FSCKFIX=no
+ test -f /etc/default/apache2
+ . /etc/default/apache2
++ HTCACHECLEAN_RUN=auto
++ HTCACHECLEAN_MODE=daemon
++ HTCACHECLEAN_SIZE=300M
++ HTCACHECLEAN_DAEMON_INTERVAL=120
++ HTCACHECLEAN_PATH=/var/cache/apache2/mod_disk_cache
++ HTCACHECLEAN_OPTIONS=-n
+ APACHE2CTL='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/apache2ctl'
+ HTCACHECLEAN='env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/htcacheclean'
++ . /etc/apache2/envvars
+++ export APACHE_RUN_USER=www-data
+++ APACHE_RUN_USER=www-data
+++ export APACHE_RUN_GROUP=www-data
+++ APACHE_RUN_GROUP=www-data
+++ export APACHE_PID_FILE=/var/run/apache2.pid
+++ APACHE_PID_FILE=/var/run/apache2.pid
+++ export LANG=C
+++ LANG=C
+++ export LANG
++ echo /var/run/apache2.pid
+ PIDFILE=/var/run/apache2.pid
+ '[' -z /var/run/apache2.pid ']'
+ case $1 in
+ log_daemon_msg 'Starting web server' apache2
+ '[' -z 'Starting web server' ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ '[' -t 1 ']'
+ '[' xxterm '!=' x ']'
+ '[' xxterm '!=' xdumb ']'
+ '[' -x /usr/bin/tput ']'
+ '[' -x /usr/bin/expr ']'
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ '[' -z ']'
+ FANCYTTY=1
+ case "$FANCYTTY" in
+ true
+ /usr/bin/tput xenl
++ /usr/bin/tput cols
+ COLS=157
+ '[' 157 ']'
+ '[' 157 -gt 6 ']'
++ /usr/bin/expr 157 - 7
+ COL=150
+ printf ' * Starting web server apache2       '
 * Starting web server apache2       ++ /usr/bin/expr 157 - 1
+ /usr/bin/tput hpa 156
                                                                                                                                                            + printf ' '
 + env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin /usr/sbin/apache2ctl start
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
+ check_htcacheclean
+ '[' daemon = daemon ']'
+ '[' auto = yes ']'
+ '[' auto = auto -a -e /etc/apache2/mods-enabled/disk_cache.load ']'
+ return 1
+ log_end_msg 0
+ '[' -z 0 ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ '[' 150 ']'
+ '[' -x /usr/bin/tput ']'
+ printf '\r'
+ /usr/bin/tput hpa 150
                                                                                                                                                      + '[' 0 -eq 0 ']'
+ echo '[ OK ]'
[ OK ]
+ return 0

```

Thanks for your help so far

---

### Post by dapperdanny77 on 2010-11-12
hmm - can't find somthing wrong (nothing obvious)
I don't know exactly how to debug the ubuntu boot process best.

you can try to boot the 'recovery mode' which is the second line in the boot menu. the boot process is more transparent there - try to find when apache ist starting and look out for errors ...

---

### Post by OxideCom on 2010-11-12
Alright thanks,

I'll see if I can get a monitor plugged in to the box up stairs :)

---

