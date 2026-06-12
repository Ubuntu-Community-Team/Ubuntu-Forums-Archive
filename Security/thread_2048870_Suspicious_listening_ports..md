---
title: "Suspicious listening ports."
date: 2012-08-27
forum: Security
---

### Post by NilPointer on 2012-08-27
Today I checked my LAN with nmap and found something strange with my machine:

```
PORT     STATE SERVICE    VERSION
80/tcp   open  http       Apache httpd 2.2.14 ((Ubuntu))
|_ html-title: Site doesn't have a title (text/html).
```

Why is there apache running? I never ran a web server and it wasn't here before. When going to localhost in browser, it shows "It works!" page. There are 4 apache2 processes in RAM. apache2 package is installed (perhaps, was a dependency for something?). Is that suspicious?

Also, I'm worried that there are much more warnings in rkhunter than before, and all these changed files are sensitive, such as sudo, ps, etc. I know it's just warnings and could be false positives, but take a look anyway, please.

```
[19:52:05] Performing file properties checks
[19:52:05] Info: Starting test name 'properties'
[19:52:05] Checking for prerequisites                        [ OK ]
[19:52:05] /bin/bash                                         [ OK ]
[19:52:06] /bin/cat                                          [ OK ]
[19:52:06] /bin/chmod                                        [ OK ]
[19:52:06] /bin/chown                                        [ OK ]
[19:52:06] /bin/cp                                           [ OK ]
[19:52:06] /bin/csh                                          [ Warning ]
[19:52:06] Warning: The file '/bin/csh' exists on the system, but it is not present in the rkhunter.dat file.
[19:52:06] /bin/date                                         [ OK ]
[19:52:06] /bin/df                                           [ OK ]
[19:52:07] /bin/dmesg                                        [ OK ]
[19:52:07] /bin/echo                                         [ OK ]
[19:52:07] /bin/ed                                           [ OK ]
[19:52:07] /bin/egrep                                        [ OK ]
[19:52:07] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[19:52:07] /bin/fgrep                                        [ OK ]
[19:52:07] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[19:52:07] /bin/fuser                                        [ OK ]
[19:52:07] /bin/grep                                         [ OK ]
[19:52:08] /bin/ip                                           [ OK ]
[19:52:08] /bin/kill                                         [ Warning ]
[19:52:08] Warning: The file properties have changed:
[19:52:08]          File: /bin/kill
[19:52:08]          Current hash: cfb465a12b8631d37bcedaf1666190981b313c1d
[19:52:08]          Stored hash : bdd9bd3bb26e82bcaa4dff7b3a801b68754d9f01
[19:52:08]          Current inode: 5505084    Stored inode: 5505057
[19:52:08]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:08]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:08] /bin/less                                         [ OK ]
[19:52:08] /bin/login                                        [ OK ]
[19:52:09] /bin/ls                                           [ OK ]
[19:52:09] /bin/lsmod                                        [ OK ]
[19:52:09] /bin/mktemp                                       [ OK ]
[19:52:09] /bin/more                                         [ OK ]
[19:52:09] /bin/mount                                        [ OK ]
[19:52:09] /bin/mv                                           [ OK ]
[19:52:09] /bin/netstat                                      [ OK ]
[19:52:10] /bin/ps                                           [ Warning ]
[19:52:10] Warning: The file properties have changed:
[19:52:10]          File: /bin/ps
[19:52:10]          Current hash: cb1a06cdbecabf6c7949791cd45a3be08a4f17ac
[19:52:10]          Stored hash : f22991ec93ae966c856d367f42fc3d8a484bd827
[19:52:10]          Current inode: 5505102    Stored inode: 5505075
[19:52:10]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:10]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:10] /bin/pwd                                          [ OK ]
[19:52:10] /bin/readlink                                     [ OK ]
[19:52:10] /bin/sed                                          [ OK ]
[19:52:10] /bin/sh                                           [ OK ]
[19:52:11] /bin/su                                           [ OK ]
[19:52:11] /bin/touch                                        [ OK ]
[19:52:11] /bin/uname                                        [ OK ]
[19:52:12] /bin/which                                        [ OK ]
[19:52:12] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[19:52:12] /bin/tcsh                                         [ Warning ]
[19:52:12] Warning: The file '/bin/tcsh' exists on the system, but it is not present in the rkhunter.dat file.
[19:52:12] /bin/dash                                         [ OK ]
[19:52:12] /usr/bin/awk                                      [ OK ]
[19:52:12] /usr/bin/basename                                 [ OK ]
[19:52:12] /usr/bin/chattr                                   [ OK ]
[19:52:13] /usr/bin/curl                                     [ OK ]
[19:52:13] /usr/bin/cut                                      [ OK ]
[19:52:13] /usr/bin/diff                                     [ OK ]
[19:52:13] /usr/bin/dirname                                  [ OK ]
[19:52:13] /usr/bin/dpkg                                     [ OK ]
[19:52:14] /usr/bin/dpkg-query                               [ OK ]
[19:52:14] /usr/bin/du                                       [ OK ]
[19:52:14] /usr/bin/elinks                                   [ OK ]
[19:52:14] /usr/bin/env                                      [ OK ]
[19:52:14] /usr/bin/file                                     [ OK ]
[19:52:14] /usr/bin/find                                     [ OK ]
[19:52:15] /usr/bin/GET                                      [ OK ]
[19:52:15] /usr/bin/groups                                   [ OK ]
[19:52:15] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[19:52:15] /usr/bin/head                                     [ OK ]
[19:52:15] /usr/bin/id                                       [ OK ]
[19:52:15] /usr/bin/killall                                  [ OK ]
[19:52:16] /usr/bin/last                                     [ OK ]
[19:52:16] /usr/bin/lastlog                                  [ OK ]
[19:52:16] /usr/bin/ldd                                      [ OK ]
[19:52:16] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[19:52:16] /usr/bin/less                                     [ OK ]
[19:52:16] /usr/bin/links                                    [ OK ]
[19:52:16] /usr/bin/locate                                   [ OK ]
[19:52:16] /usr/bin/logger                                   [ OK ]
[19:52:17] /usr/bin/lsattr                                   [ OK ]
[19:52:17] /usr/bin/lsof                                     [ OK ]
[19:52:17] /usr/bin/lynx                                     [ OK ]
[19:52:17] /usr/bin/mail                                     [ OK ]
[19:52:17] /usr/bin/md5sum                                   [ OK ]
[19:52:17] /usr/bin/mlocate                                  [ OK ]
[19:52:18] /usr/bin/newgrp                                   [ OK ]
[19:52:18] /usr/bin/passwd                                   [ OK ]
[19:52:18] /usr/bin/perl                                     [ OK ]
[19:52:18] /usr/bin/pgrep                                    [ Warning ]
[19:52:18] Warning: The file properties have changed:
[19:52:18]          File: /usr/bin/pgrep
[19:52:18]          Current hash: c79882a961dbb040b7644ea09f78c7e4b8f9ea18
[19:52:18]          Stored hash : 3eada9a96760f3e2c9111cfe32901d1432813c1d
[19:52:18]          Current inode: 531314    Stored inode: 532079
[19:52:18]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:18]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:19] /usr/bin/pstree                                   [ OK ]
[19:52:19] /usr/bin/rkhunter                                 [ OK ]
[19:52:19] /usr/bin/rpm                                      [ Warning ]
[19:52:19] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
[19:52:19] /usr/bin/runcon                                   [ OK ]
[19:52:19] /usr/bin/sha1sum                                  [ OK ]
[19:52:19] /usr/bin/sha224sum                                [ OK ]
[19:52:20] /usr/bin/sha256sum                                [ OK ]
[19:52:20] /usr/bin/sha384sum                                [ OK ]
[19:52:20] /usr/bin/sha512sum                                [ OK ]
[19:52:20] /usr/bin/size                                     [ OK ]
[19:52:20] /usr/bin/sort                                     [ OK ]
[19:52:20] /usr/bin/stat                                     [ OK ]
[19:52:21] /usr/bin/strace                                   [ OK ]
[19:52:21] /usr/bin/strings                                  [ OK ]
[19:52:21] /usr/bin/sudo                                     [ Warning ]
[19:52:21] Warning: The file properties have changed:
[19:52:21]          File: /usr/bin/sudo
[19:52:21]          Current hash: 4ed0b135dcbd930c6ab713ccf288329782769fd9
[19:52:21]          Stored hash : e708e94892e607fbb0b52318dc94845cb45a1205
[19:52:21]          Current inode: 532695    Stored inode: 525262
[19:52:21]          Current file modification time: 1337145936 (16-&#1052;&#1072;&#1081;-2012 09:25:36)
[19:52:21]          Stored file modification time : 1295460070 (19-&#1071;&#1085;&#1074;-2011 21:01:10)
[19:52:21] /usr/bin/tail                                     [ OK ]
[19:52:22] /usr/bin/test                                     [ OK ]
[19:52:22] /usr/bin/top                                      [ Warning ]
[19:52:22] Warning: The file properties have changed:
[19:52:22]          File: /usr/bin/top
[19:52:22]          Current hash: fd3f600bc1cc692661f9a9ed4c34ceeb68ae5b98
[19:52:22]          Stored hash : 6be13737d8b0950cea2f1ae3a46d4af713dbe971
[19:52:22]          Current inode: 537109    Stored inode: 529122
[19:52:22]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:22]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:22] /usr/bin/touch                                    [ OK ]
[19:52:22] /usr/bin/tr                                       [ OK ]
[19:52:22] /usr/bin/uniq                                     [ OK ]
[19:52:23] /usr/bin/users                                    [ OK ]
[19:52:23] /usr/bin/vmstat                                   [ Warning ]
[19:52:23] Warning: The file properties have changed:
[19:52:23]          File: /usr/bin/vmstat
[19:52:23]          Current hash: d3c3ad4900948f5800d55e3570abf932c11f8879
[19:52:23]          Stored hash : cde33e9ecb7eefd1480cd01ca64afebd5b312571
[19:52:23]          Current inode: 537107    Stored inode: 529123
[19:52:23]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:23]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:23] /usr/bin/w                                        [ Warning ]
[19:52:23] Warning: The file properties have changed:
[19:52:23]          File: /usr/bin/w
[19:52:23]          Current hash: 6dd252a13a48e14b7d853af8784b18ae645a88b9
[19:52:23]          Stored hash : 646c28e95a9159fbd5feb644c30ad7ea8e25f47a
[19:52:23] /usr/bin/watch                                    [ Warning ]
[19:52:23] Warning: The file properties have changed:
[19:52:23]          File: /usr/bin/watch
[19:52:23]          Current hash: 3fd8cb14018adcdf1c00403074ef589e520762fe
[19:52:24]          Stored hash : 97c2a1b127f9a33e9e11d8e1555e3e740cef5478
[19:52:24]          Current inode: 527640    Stored inode: 529124
[19:52:24]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:24]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:24] /usr/bin/wc                                       [ OK ]
[19:52:24] /usr/bin/wget                                     [ OK ]
[19:52:24] /usr/bin/whatis                                   [ OK ]
[19:52:24] /usr/bin/whereis                                  [ OK ]
[19:52:24] /usr/bin/which                                    [ OK ]
[19:52:25] /usr/bin/who                                      [ OK ]
[19:52:25] /usr/bin/whoami                                   [ OK ]
[19:52:25] /usr/bin/tcsh                                     [ Warning ]
[19:52:25] Warning: The file '/usr/bin/tcsh' exists on the system, but it is not present in the rkhunter.dat file.
[19:52:25] /usr/bin/gawk                                     [ OK ]
[19:52:25] /usr/bin/lwp-request                              [ OK ]
[19:52:25] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[19:52:25] /usr/bin/lynx.cur                                 [ OK ]
[19:52:25] /usr/bin/bsd-mailx                                [ OK ]
[19:52:26] /usr/bin/w.procps                                 [ Warning ]
[19:52:26] Warning: The file properties have changed:
[19:52:26]          File: /usr/bin/w.procps
[19:52:26]          Current hash: 6dd252a13a48e14b7d853af8784b18ae645a88b9
[19:52:26]          Stored hash : 646c28e95a9159fbd5feb644c30ad7ea8e25f47a
[19:52:26]          Current inode: 537113    Stored inode: 536810
[19:52:26]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:26]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:26] /sbin/depmod                                      [ OK ]
[19:52:27] /sbin/ifconfig                                    [ OK ]
[19:52:27] /sbin/ifdown                                      [ OK ]
[19:52:27] /sbin/ifup                                        [ OK ]
[19:52:27] /sbin/init                                        [ OK ]
[19:52:27] /sbin/insmod                                      [ OK ]
[19:52:27] /sbin/ip                                          [ OK ]
[19:52:28] /sbin/lsmod                                       [ OK ]
[19:52:28] /sbin/modinfo                                     [ OK ]
[19:52:28] /sbin/modprobe                                    [ OK ]
[19:52:29] /sbin/rmmod                                       [ OK ]
[19:52:29] /sbin/runlevel                                    [ OK ]
[19:52:29] /sbin/sulogin                                     [ OK ]
[19:52:29] /sbin/sysctl                                      [ Warning ]
[19:52:29] Warning: The file properties have changed:
[19:52:29]          File: /sbin/sysctl
[19:52:30]          Current hash: 670072340c870f79aac37a8aac331721e5453475
[19:52:30]          Stored hash : 5093a158551619cad7cf9fa216fdab2486e424e2
[19:52:30]          Current inode: 2621465    Stored inode: 2621458
[19:52:30]          Current file modification time: 1342492315 (17-&#1048;&#1102;&#1083;-2012 06:31:55)
[19:52:30]          Stored file modification time : 1324307913 (19-&#1044;&#1077;&#1082;-2011 19:18:33)
[19:52:30] /usr/sbin/adduser                                 [ OK ]
[19:52:30] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[19:52:30] /usr/sbin/chroot                                  [ OK ]
[19:52:31] /usr/sbin/cron                                    [ Warning ]
[19:52:31] Warning: The file properties have changed:
[19:52:31]          File: /usr/sbin/cron
[19:52:31]          Current hash: fce8bd98e91938397b3c2224ff519d43c12fccc6
[19:52:31]          Stored hash : e783ca973f970aa8a4bf5edc670e690b33914c3d
[19:52:31]          Current inode: 526161    Stored inode: 525900
[19:52:31]          Current file modification time: 1342492671 (17-&#1048;&#1102;&#1083;-2012 06:37:51)
[19:52:31]          Stored file modification time : 1330965568 (05-&#1052;&#1072;&#1088;-2012 20:39:28)
[19:52:31] /usr/sbin/groupadd                                [ OK ]
[19:52:31] /usr/sbin/groupdel                                [ OK ]
[19:52:32] /usr/sbin/groupmod                                [ OK ]
[19:52:32] /usr/sbin/grpck                                   [ OK ]
[19:52:33] /usr/sbin/nologin                                 [ OK ]
[19:52:33] /usr/sbin/pwck                                    [ OK ]
[19:52:33] /usr/sbin/rsyslogd                                [ OK ]
[19:52:33] /usr/sbin/tcpd                                    [ OK ]
[19:52:34] /usr/sbin/useradd                                 [ OK ]
[19:52:34] /usr/sbin/userdel                                 [ OK ]
[19:52:34] /usr/sbin/usermod                                 [ OK ]
[19:52:34] /usr/sbin/vipw                                    [ OK ]
[19:52:34] /usr/sbin/unhide-linux26                          [ OK ]
```

---

### Post by Ms. Daisy on 2012-08-27
If you've got apache running without wanting to, then remove it!
Use the --purge switch to remove config files and everything related to apache.
 
Once you purge apache run rkhunter again, it may report fewer problems.
 
Are you behind a NAT router?  If so, then you'll probably be fine if you didn't forward port 80.  But if a default configuration of apache has been exposed to the internet for any length of time, I would be concerned about compromise personally.  Look at your logs for indications, here's a guide if you don't know what to look for:
 
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by NilPointer on 2012-08-28
> **Ms. Daisy said:**
> If you've got apache running without wanting to, then remove it!
Use the --purge switch to remove config files and everything related to apache.
 
Once you purge apache run rkhunter again, it may report fewer problems.
 
Are you behind a NAT router?  If so, then you'll probably be fine if you didn't forward port 80.  But if a default configuration of apache has been exposed to the internet for any length of time, I would be concerned about compromise personally.  Look at your logs for indications, here's a guide if you don't know what to look for:
 
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

Yes, I'm behind NAT and never forwarded port 80. I even block ICMP pings. But according to this article, there is indeed something suspicious. It says that even 5 unaccounted minutes is suspicious, but I have really large missing timeframes in syslog, such as these:

> Aug 26 16:17:01 localhost CRON[19786]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 26 17:17:01 localhost CRON[19800]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 26 18:17:01 localhost CRON[19890]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 26 19:17:01 localhost CRON[19901]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 26 20:17:01 localhost CRON[20110]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


Four hours and only cron appears there once in a hour. There is similar thing in log for next day, but it's only three hours.

Log is only thing that seems off. No suspicious connections, no new users or cron jobs.

After removing apache there is still same number of suspect files in rkhunter. Also, unlike rkhunter, chkrootkit comes up without any warnings (besides list of not really suspicious dirs).

---

### Post by wirelessmonkey on 2012-08-28
The thing with rkhunter, is that you must build an original database as a baseline for it to compare against, otherwise its database is defined by settings on the build system, which is most likely not the same as yours.

When you are relatively sure that your system is clean (reinstall?), run:

```

rkhunter --propupd

```
This establishes your system baseline, updates the root kit and detection databases, and makes sure the rkhunter binary is up to date.

This way, any future runs of rkhunter will check against your baseline, giving better answers with fewer false positives.

---

Now to directly address your issues:

My syslogs also just show CRON entries, and this appears to be entirely normal behavior.  

I think key in this particular instance, is to take a look at the apache connection and error logs.

```
 
cat /var/log/apache2/access.log
cat /var/log/apache2/error.log

```

This will help you see what has been connected to, i.e. hidden sites, as well as IP addresses of those who have connected to those sites. Now, if someone has taken full control of your system, be aware that logs could have been edited. But if not, this will tell you if you have something installed that uses apache2 as a dependancy and show what directories it accesses.


Best of Luck, keep us posted.

---

### Post by CharlesA on 2012-08-28
Just wanted to second that those entries for cron are normal.

---

### Post by NilPointer on 2012-08-28
Doesn't rkhunter build it's database on first run? I had it installed for quite a long time and was checking my system with it from time to time. There was less warnings before.

Also, i googled current hashes and it seems some of them match with one from this thread (even dates match - 17-Jul-2012): [http://ubuntuforums.org/showthread.php?t=2036242]("http://ubuntuforums.org/showthread.php?t=2036242")

As for apache logs, they don't exist (probably because I purged apache2 and related packages). I don't think it was possible to access running apache from Internet, since both firewall and NAT blocked connection to port 80.

[QUOTE=CharlesA]Just wanted to second that those entries for cron are normal.[/QUOTE]

Good. Then I have no signs of being hacked at all. But that means that this wiki page is misleading.

> Partially sanitized: If large chunks of time (more than 5 minutes) are unaccounted for in a log file while the machine was running, it is a safe bet something has happened that someone didn't wish to be seen.

---

### Post by CharlesA on 2012-08-28
No, the wiki page is fine. Cron jobs are known to only run every hour which is why it is important to get to know what the normal log files of your system look like, so you can spot discrepancies.

---

### Post by NilPointer on 2012-08-28
> **CharlesA said:**
> No, the wiki page is fine. Cron jobs are known to only run every hour which is why it is important to get to know what the normal log files of your system look like, so you can spot discrepancies.

So does that mean that one-hour gaps between messages in syslog is normal?

---

### Post by CharlesA on 2012-08-28
> **NilPointer said:**
> So does that mean that one-hour gaps between messages in syslog is normal?
For cron, yes.

---

### Post by NilPointer on 2012-08-28
> **CharlesA said:**
> For cron, yes.

But what I posted was single directly copied piece of syslog, not only cron messages. Here is another example (more clear):

> Aug 27 18:00:59 localhost init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory
Aug 27 18:17:01 localhost CRON[19359]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 19:17:01 localhost CRON[19536]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 20:17:01 localhost CRON[28303]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 21:17:01 localhost CRON[28411]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 22:01:39 localhost ntfs-3g[28605]: Version 2010.3.6 external FUSE 28

And as you can see, there is gap between 18:00 and 22:01 with only cron messages.

---

### Post by CharlesA on 2012-08-28
Looks fine. The ufw message is probably due to this:
[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/578628](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/578628)

---

