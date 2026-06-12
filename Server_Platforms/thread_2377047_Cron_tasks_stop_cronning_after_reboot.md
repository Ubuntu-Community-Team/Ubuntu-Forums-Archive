---
title: "Cron tasks stop cronning after reboot"
date: 2017-11-08
forum: Server Platforms
---

### Post by rethinkab on 2017-11-08
I have a server whose cron jobs stop after each reboot. I seem to be able to fix this by editing and saving the /etc/crontab file, but this is horrible. I don't usually connect to this server, and I've thus far only been made aware of the error by someone asking me what's wrong.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty

$ date; uptime
Wed Nov  8 14:40:11 EST 2017
 14:40:11 up 4 days, 14:03,  3 users,  load average: 0.00, 0.03, 0.05

$ dpkg --list | grep cron
ii  cron                                 3.0pl1-124ubuntu2                          amd64        process scheduling daemon

```


Anyway, prior to a reboot, many cron tasks happen happily. (Please note the one-hour time change.)
```
# grep CRON /var/log/syslog
Nov  3 23:34:02 myserver CRON[23841]: (root) CMD (find /users/serviceuser/data/JoData -maxdepth 3 -type f \! -perm -0666 -exec chmod -R a+rwX '{}' +)
Nov  3 23:40:01 myserver CRON[24091]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 00:00:01 myserver CRON[24896]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 00:17:01 myserver CRON[25552]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  4 00:20:01 myserver CRON[25712]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 00:34:01 myserver CRON[26282]: (root) CMD (find /users/serviceuser/data/JoData -maxdepth 3 -type f \! -perm -0666 -exec chmod -R a+rwX '{}' +)
Nov  4 00:40:01 myserver CRON[26529]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 00:44:02 myserver CRON[26703]: (serviceuser) CMD (cd /users/serviceuser; mountpoint /mnt/remote_data &>/dev/null && rsync --delete -rlt data/ /mnt/remote_data/)
Nov  4 00:45:01 myserver CRON[26710]: (serviceuser) CMD (/bin/bash /users/serviceuser/clean3/production/src/reporting.sh 2>&1 > /tmp/grab.log | tee /tmp/grab.err)
Nov  4 00:55:02 myserver CRON[27767]: (serviceuser) CMD (/bin/bash /users/serviceuser/ins-grab/get-ins-data 2>&1 > /tmp/ins-grab.log | cat - > /tmp/ins-grab.err)
Nov  4 01:00:02 myserver CRON[28351]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 01:17:02 myserver CRON[28740]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  4 01:20:01 myserver CRON[28749]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 01:34:01 myserver CRON[28803]: (root) CMD (find /users/serviceuser/data/JoData -maxdepth 3 -type f \! -perm -0666 -exec chmod -R a+rwX '{}' +)
Nov  4 01:37:11 myserver cron[930]: (CRON) INFO (pidfile fd = 3)
Nov  4 01:37:11 myserver cron[993]: (CRON) STARTUP (fork ok)
Nov  4 01:37:11 myserver cron[993]: (CRON) INFO (Running @reboot jobs)
Nov  4 01:40:02 myserver CRON[1556]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 02:00:01 myserver CRON[2357]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 02:20:01 myserver CRON[3163]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 02:40:01 myserver CRON[3976]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov  4 03:00:01 myserver CRON[4786]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

```

From that point on, the _only_ cron command to have run over the next four days is the sendmail check command. All of the other cron commands ... don't show up in the log files, and don't generate any output -- they flatly don't run. Does anyone know why this might be?

```
$ ls -l /etc/cron*
-rw-r--r-- 1 root root 2807 Oct 31 16:47 /etc/crontab

/etc/cron.d:
total 4
-rw-r--r-- 1 root root 2320 Dec  9  2015 sendmail

/etc/cron.daily:
total 68
-rwxr-xr-x 1 root root   376 Apr  4  2014 apport
-rwxr-xr-x 1 root root 15481 Apr 10  2014 apt
-rwxr-xr-x 1 root root   314 Feb 17  2014 aptitude
-rwxr-xr-x 1 root root   355 Jun  4  2013 bsdmainutils
-rwxr-xr-x 1 root root   384 Mar 23  2014 cracklib-runtime
-rwxr-xr-x 1 root root   256 Mar  7  2014 dpkg
-rwxr-xr-x 1 root root   372 Jan 22  2014 logrotate
-rwxr-xr-x 1 root root  1261 Sep 23  2014 man-db
-rwxr-xr-x 1 root root   435 Jun 20  2013 mlocate
-rwxr-xr-x 1 root root   249 Feb 16  2014 passwd
-rwxr-xr-x 1 root root  2417 May 13  2013 popularity-contest
-rwxr-xr-x 1 root root  3285 Feb 11  2014 sendmail
-rwxr-xr-x 1 root root   214 Oct  6  2014 update-notifier-common
-rwxr-xr-x 1 root root   328 Jul 18  2014 upstart

/etc/cron.hourly:
total 0

/etc/cron.monthly:
total 0

/etc/cron.weekly:
total 16
-rwxr-xr-x 1 root root 730 Feb 23  2014 apt-xapian-index
-rwxr-xr-x 1 root root 427 Apr 16  2014 fstrim
-rwxr-xr-x 1 root root 771 Sep 23  2014 man-db
-rwxr-xr-x 1 root root 211 Oct  6  2014 update-notifier-common

```

The sendmil cron.d file doesn't have the execute bit set. (Unsure if that is meaningful, but it's the only one.)
```
$ grep -v '^#' /etc/cron.d/sendmail 
MAILTO=root
*/20 *    *    *    *           smmsp   test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp

```

/etc/crontab. I open this and save it, and cron resumes working merrily.
```

$ cat /etc/crontab 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

# serviceuser user isn't available immediately at reboot. Delay start.
#@reboot        serviceuser /users/serviceuser/clean3/production/src/reporting/start_server.sh
#@reboot        serviceuser ( sleep 15 && /users/serviceuser/clean3/production/src/reporting/start_server.sh ) &
#*/5 *  * * *   serviceuser pgrep -f production/src/reporting/server.py &>/dev/null || /users/serviceuser/clean3/production/src/reporting/start_server.sh &
# ^-- server is ded.

# Redirect stdout (> comes second) to grab.log; tee the error stream (2>&1 comes first) to tee.
45 */12 * * *   serviceuser /bin/bash /users/serviceuser/clean3/production/src/reporting/grab.sh 2>&1 > /tmp/grab.log | tee /tmp/grab.err
# This needs to start _after_ the BI grab script, and will wait for it to finish.
# The two use conflicting VPN connections.
55 */12 * * *   serviceuser /bin/bash /users/serviceuser/ins-grab/get-ins-data 2>&1 > /tmp/ins-grab.log | cat - > /tmp/ins-grab.err
# Again, AFTER INS.
55 1,6,12,16 * * 1-5    serviceuser cd /users/serviceuser/fiprt/ && ./master_scp_data.sh 2>/tmp/fiprt-grab.log >> /tmp/fiprt-grab.err
04 16 * * 1-5   serviceuser cd /users/serviceuser/fiprt/ && ./master_scp_data.sh 2>/tmp/fiprt-grab.log >> /tmp/fiprt-grab.err

#55 */12 * * * serviceuser find /users/<truncated>


44 */12 * * * serviceuser cd /users/serviceuser; mountpoint /mnt/remote_data &>/dev/null && rsync --delete -rlt data/ /mnt/remote_data/


# Fix tester permissions
34 * * * * root find /users/serviceuser/data/JoData -maxdepth 3 -type f \! -perm -0666 -exec chmod -R a+rwX '{}' +

```

What's wrong?

---

