---
title: "rkhunter warnings - should I be afraid?"
date: 2011-03-24
forum: Security
---

### Post by ericus on 2011-03-24
EDIT: Sorry! Seems like I've somehow made two threads about the same problem, here is the correct one: [http://ubuntuforums.org/showthread.php?t=1713787](http://ubuntuforums.org/showthread.php?t=1713787)

---

### Post by ericus on 2011-03-24
From the log:
```
20:35:03] [B]/bin/login                                        [ Warning ]
[20:35:03] Warning: The file properties have changed:
[20:35:03]          File: /bin/login
[20:35:03]          Current hash: xxx
[20:35:03]          Stored hash : yyy
[20:35:03]          Current inode: 22405136    Stored inode: 6201356
[20:35:03]          Current file modification time: 1297721482 (14-Feb-2011 23:11:22)
[20:35:03]          Stored file modification time : 1264525785 (26-Jan-2010 18:09:45)[/B]
[20:35:03] /bin/ls                                           [ OK ]
[20:35:03] /bin/lsmod                                        [ OK ]
[20:35:03] /bin/mktemp                                       [ OK ]
[20:35:03] /bin/more                                         [ OK ]
[20:35:03] /bin/mount                                        [ OK ]
[20:35:03] /bin/mv                                           [ OK ]
[20:35:03] /bin/netstat                                      [ OK ]
[20:35:03] /bin/ps                                           [ OK ]
[20:35:04] /bin/pwd                                          [ OK ]
[20:35:04] /bin/readlink                                     [ OK ]
[20:35:04] /bin/sed                                          [ OK ]
[20:35:04] /bin/sh                                           [ OK ]
[20:35:04] /bin/su                                           [ Warning ]
[B][20:35:04] Warning: The file properties have changed:
[20:35:04]          File: /bin/su
[20:35:04]          Current hash: xxx
[20:35:04]          Stored hash : yyy
[20:35:04]          Current inode: 22405137    Stored inode: 6201357
[20:35:04]          Current file modification time: 1297721482 (14-Feb-2011 23:11:22)
[20:35:04]          Stored file modification time : 1264525785 [/B](26-Jan-2010 18:09:45)
[20:35:04] /bin/touch                                        [ OK ]
[20:35:04] /bin/uname                                        [ OK ]
[20:35:04] /bin/which                                        [ OK ]
[20:35:04] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[20:35:04] /bin/dash                                         [ OK ]
[20:35:04] /usr/bin/awk                                      [ OK ]
[20:35:04] /usr/bin/basename                                 [ OK ]
[20:35:04] /usr/bin/chattr                                   [ OK ]
[20:35:05] /usr/bin/curl                                     [ OK ]
[20:35:05] /usr/bin/cut                                      [ OK ]
[20:35:05] /usr/bin/diff                                     [ OK ]
[20:35:05] /usr/bin/dirname                                  [ OK ]
[20:35:05] /usr/bin/dpkg                                     [ OK ]
[20:35:05] /usr/bin/dpkg-query                               [ OK ]
[20:35:05] /usr/bin/du                                       [ OK ]
[20:35:05] /usr/bin/env                                      [ OK ]
[20:35:05] /usr/bin/file                                     [ OK ]
[20:35:05] /usr/bin/find                                     [ OK ]
[20:35:05] /usr/bin/GET                                      [ OK ]
[20:35:05] /usr/bin/groups                                   [ OK ]
[20:35:05] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[20:35:05] /usr/bin/head                                     [ OK ]
[20:35:05] /usr/bin/id                                       [ OK ]
[20:35:05] /usr/bin/killall                                  [ OK ]
[20:35:06] /usr/bin/last                                     [ OK ]
[B][20:35:06] /usr/bin/lastlog                                  [ Warning ]
[20:35:06] Warning: The file properties have changed:
[20:35:06]          File: /usr/bin/lastlog
[20:35:06]          Current hash: xxx
[20:35:06]          Stored hash : yyy
[20:35:06]          Current inode: 27186428    Stored inode: 22291038
[20:35:06]          Current file modification time: 1297721482 (14-Feb-2011 23:11:22)
[20:35:06]          Stored file modification time : 1264525785 (26-Jan-2010 18:09:45)[/B]
[20:35:06] /usr/bin/ldd                                      [ OK ]
[20:35:06] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[20:35:06] /usr/bin/less                                     [ OK ]
[20:35:06] /usr/bin/locate                                   [ OK ]
[20:35:06] /usr/bin/logger                                   [ OK ]
[20:35:06] /usr/bin/lsattr                                   [ OK ]
[20:35:06] /usr/bin/lsof                                     [ OK ]
[20:35:06] /usr/bin/mail                                     [ OK ]
[20:35:06] /usr/bin/md5sum                                   [ OK ]
[20:35:06] /usr/bin/mlocate                                  [ OK ]
[B][20:35:06] /usr/bin/newgrp                                   [ Warning ]
[20:35:06] Warning: The file properties have changed:
[20:35:06]          File: /usr/bin/newgrp
[20:35:06]          Current hash: xxx
[20:35:06]          Stored hash : yyy
[20:35:06]          Current inode: 27186429    Stored inode: 22291039
[20:35:06]          Current file modification time: 1297721482 (14-Feb-2011 23:11:22)
[20:35:06]          Stored file modification time : 1264525785 (26-Jan-2010 18:09:45)
[20:35:06] /usr/bin/passwd                                   [ Warning ]
[20:35:06] Warning: The file properties have changed:
[20:35:06]          File: /usr/bin/passwd
[20:35:06]          Current hash: xxx
[20:35:06]          Stored hash : yyy
[20:35:06]          Current inode: 22405142    Stored inode: 27189046
[20:35:07]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:07]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)[/B]
[20:35:07] /usr/bin/perl                                     [ OK ]
[20:35:07] /usr/bin/pgrep                                    [ OK ]
[20:35:07] /usr/bin/pstree                                   [ OK ]
[20:35:07] /usr/bin/rkhunter                                 [ OK ]
[20:35:07] /usr/bin/runcon                                   [ OK ]
[20:35:07] /usr/bin/sha1sum                                  [ OK ]
[20:35:07] /usr/bin/sha224sum                                [ OK ]
[20:35:07] /usr/bin/sha256sum                                [ OK ]
[20:35:07] /usr/bin/sha384sum                                [ OK ]
[20:35:07] /usr/bin/sha512sum                                [ OK ]
[B][20:35:07] /usr/bin/size                                     [ Warning ]
[20:35:07] Warning: The file properties have changed:
[20:35:07]          File: /usr/bin/size
[20:35:07]          Current inode: 27187550    Stored inode: 22290854
[20:35:07]          Current file modification time: 1299208925 (04-Mar-2011 04:22:05)
[20:35:07]          Stored file modification time : 1282315301 (20-Aug-2010 16:41:41)[/B]
[20:35:07] /usr/bin/sort                                     [ OK ]
[20:35:07] /usr/bin/stat                                     [ OK ]
[20:35:07] /usr/bin/strace                                   [ OK ]
[B][20:35:08] /usr/bin/strings                                  [ Warning ]
[20:35:08] Warning: The file properties have changed:
[20:35:08]          File: /usr/bin/strings
[20:35:08]          Current inode: 27188584    Stored inode: 22291223
[20:35:08]          Current file modification time: 1299208925 (04-Mar-2011 04:22:05)
[20:35:08]          Stored file modification time : 1282315301 (20-Aug-2010 16:41:41)[/B]
[20:35:08] /usr/bin/sudo                                     [ OK ]
[20:35:08] /usr/bin/tail                                     [ OK ]
[20:35:08] /usr/bin/test                                     [ OK ]
[20:35:08] /usr/bin/top                                      [ OK ]
[20:35:08] /usr/bin/touch                                    [ OK ]
[20:35:08] /usr/bin/tr                                       [ OK ]
[20:35:08] /usr/bin/uniq                                     [ OK ]
[20:35:08] /usr/bin/users                                    [ OK ]
[20:35:08] /usr/bin/vmstat                                   [ OK ]
[20:35:08] /usr/bin/w                                        [ OK ]
[20:35:08] /usr/bin/watch                                    [ OK ]
[20:35:08] /usr/bin/wc                                       [ OK ]
[20:35:08] /usr/bin/wget                                     [ OK ]
[20:35:08] /usr/bin/whatis                                   [ OK ]
[20:35:08] /usr/bin/whereis                                  [ OK ]
[20:35:08] /usr/bin/which                                    [ OK ]
[20:35:09] /usr/bin/who                                      [ OK ]
[20:35:09] /usr/bin/whoami                                   [ OK ]
[20:35:09] /usr/bin/gawk                                     [ OK ]
[20:35:09] /usr/bin/lwp-request                              [ OK ]
[20:35:09] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[20:35:09] /usr/bin/bsd-mailx                                [ OK ]
[20:35:09] /usr/bin/w.procps                                 [ OK ]
[20:35:09] /sbin/depmod                                      [ OK ]
[20:35:09] /sbin/ifconfig                                    [ OK ]
[20:35:09] /sbin/ifdown                                      [ OK ]
[20:35:09] /sbin/ifup                                        [ OK ]
[20:35:09] /sbin/init                                        [ OK ]
[20:35:09] /sbin/insmod                                      [ OK ]
[20:35:09] /sbin/ip                                          [ OK ]
[20:35:10] /sbin/lsmod                                       [ OK ]
[20:35:10] /sbin/modinfo                                     [ OK ]
[20:35:10] /sbin/modprobe                                    [ OK ]
[20:35:10] /sbin/rmmod                                       [ OK ]
[20:35:10] /sbin/runlevel                                    [ OK ]
[20:35:10] /sbin/sulogin                                     [ OK ]
[20:35:10] /sbin/sysctl                                      [ OK ]
[20:35:10] /usr/sbin/adduser                                 [ OK ]
[20:35:10] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[20:35:10] /usr/sbin/chroot                                  [ OK ]
[20:35:10] /usr/sbin/cron                                    [ OK ]
[B][20:35:11] /usr/sbin/groupadd                                [ Warning ]
[20:35:11] Warning: The file properties have changed:
[20:35:11]          File: /usr/sbin/groupadd
[20:35:11]          Current hash: xxx
[20:35:11]          Stored hash : yyy
[20:35:11]          Current inode: 22372478    Stored inode: 27189051
[20:35:11]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:11]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:11] /usr/sbin/groupdel                                [ Warning ]
[20:35:11] Warning: The file properties have changed:
[20:35:11]          File: /usr/sbin/groupdel
[20:35:11]          Current hash: xxx
[20:35:11]          Stored hash : yyy
[20:35:11]          Current inode: 22372479    Stored inode: 27189084
[20:35:11]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:11]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:11] /usr/sbin/groupmod                                [ Warning ]
[20:35:11] Warning: The file properties have changed:
[20:35:11]          File: /usr/sbin/groupmod
[20:35:11]          Current hash: xxx
[20:35:11]          Stored hash : yyy
[20:35:11]          Current inode: 22372480    Stored inode: 27189085
[20:35:11]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:11]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:11] /usr/sbin/grpck                                   [ Warning ]
[20:35:11] Warning: The file properties have changed:
[20:35:11]          File: /usr/sbin/grpck
[20:35:11]          Current hash: xxx
[20:35:11]          Stored hash : yyy
[20:35:11]          Current inode: 22372481    Stored inode: 27189185
[20:35:11]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:11]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:11] /usr/sbin/nologin                                 [ Warning ]
[20:35:11] Warning: The file properties have changed:
[20:35:11]          File: /usr/sbin/nologin
[20:35:11]          Current hash: xxx
[20:35:11]          Stored hash : yyy
[20:35:11]          Current inode: 27186426    Stored inode: 22323321
[20:35:11]          Current file modification time: 1297721482 (14-Feb-2011 23:11:22)
[20:35:11]          Stored file modification time : 1264525785 (26-Jan-2010 18:09:45)
[20:35:12] /usr/sbin/pwck                                    [ Warning ]
[20:35:12] Warning: The file properties have changed:
[20:35:12]          File: /usr/sbin/pwck
[20:35:12]          Current hash: xxx
[20:35:12]          Stored hash : yyy
[20:35:12]          Current inode: 22372485    Stored inode: 22323292
[20:35:12]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:12]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)[/B]
[20:35:12] /usr/sbin/rsyslogd                                [ OK ]
[20:35:12] /usr/sbin/tcpd                                    [ OK ]
[B][20:35:12] /usr/sbin/useradd                                 [ Warning ]
[20:35:12] Warning: The file properties have changed:
[20:35:12]          File: /usr/sbin/useradd
[20:35:12]          Current hash: f7c92b5ff4eb606f2b38c2b1d97cf5da7fb2b722
[20:35:12]          Stored hash : c1de7c5992a668a02f307f8444a85a4e6f98a004
[20:35:12]          Current inode: 22372490    Stored inode: 22323344
[20:35:12]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:12]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:12] /usr/sbin/userdel                                 [ Warning ]
[20:35:12] Warning: The file properties have changed:
[20:35:12]          File: /usr/sbin/userdel
[20:35:12]          Current hash: xxx
[20:35:12]          Stored hash : yyy
[20:35:12]          Current inode: 22372491    Stored inode: 22323346
[20:35:12]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:12]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:12] /usr/sbin/usermod                                 [ Warning ]
[20:35:12] Warning: The file properties have changed:
[20:35:12]          File: /usr/sbin/usermod
[20:35:12]          Current hash: xxx
[20:35:12]          Stored hash : yyy
[20:35:12]          Current inode: 22372493    Stored inode: 22323364
[20:35:12]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:12]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)
[20:35:12] /usr/sbin/vipw                                    [ Warning ]
[20:35:12] Warning: The file properties have changed:
[20:35:12]          File: /usr/sbin/vipw
[20:35:12]          Current hash: xxx
[20:35:12]          Stored hash : yyy
[20:35:12]          Current inode: 22372494    Stored inode: 22323403
[20:35:12]          Current file modification time: 1297721480 (14-Feb-2011 23:11:20)
[20:35:13]          Stored file modification time : 1264525783 (26-Jan-2010 18:09:43)[/B]
[20:35:13] /usr/sbin/unhide-linux26                          [ OK ]
```

*(I changed the hash sums to xxx and yyy, don't know if it's good to post them for all to see?)*

So, are these false positives? Many warnings there... Should I be aware? Am I in danger? :(

Please help me sort this out!

---

### Post by bodhi.zazen on 2011-03-24
I merged your two threads. 

Your question is a FAQ, see the security sticky and the man page.

If after reading the stickies you have a specific question please ask, but, asking somebody to go through the output of rkhunter line by line is unrealistic.

---

### Post by ericus on 2011-03-25
> **bodhi.zazen said:**
> I merged your two threads. 

Your question is a FAQ, see the security sticky and the man page.

If after reading the stickies you have a specific question please ask, but, asking somebody to go through the output of rkhunter line by line is unrealistic.

Okay, thanks. The interesting lines are bolded. Will google it later on, but 'til then; does anyone know if this is any bad? I dont get these warnings on my netbook.

---

### Post by cariboo on 2011-03-25
You can check System->Administration-> Synaptic Package Manager->File->History, to see if those files have been updated.

---

### Post by ericus on 2011-03-27
There are no entries for 14th february or 4th mars in synaptic history.. Those are the two dates mentioned several times in the log files.

I found this after searching for login:
```
login (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
openssl (0.9.8k-7ubuntu8.5) to 0.9.8k-7ubuntu8.6
passwd (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
```
But that was three days later, 17th feb.

So, whats next? Has my system been compromised?

---

### Post by Soul-Sing on 2011-03-27
> **ericus said:**
> There are no entries for 14th february or 4th mars in synaptic history.. Those are the two dates mentioned several times in the log files.

I found this after searching for login:
```
login (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
openssl (0.9.8k-7ubuntu8.5) to 0.9.8k-7ubuntu8.6
passwd (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
```
But that was three days later, 17th feb.

So, whats next? Has my system been compromised?

would you please run a
```
sudo rkhunter --propupd
```
and after this a "normal" rkhunter check, if possible after a reboot of your system. And compare the two scans.
It could be interesting to analyse the results.

---

### Post by ericus on 2011-03-27
> **leoquant said:**
> would you please run a
```
sudo rkhunter --propupd
```
and after this a "normal" rkhunter check, if possible after a reboot of your system. And compare the two scans.
It could be interesting to analyse the results.

No warnings after running that.
But, doesn't that mean that IF my computer was altered somehow, I just made it look normal to rkhunter?

---

### Post by Soul-Sing on 2011-03-27
its in the FAQ and readme of rkhunter.

> Before running RKH you will need to fill the file properties database by running the following command And last - do no forget to set rkhunter in sysconfig to run the --propupd every time new software is installed or else you will get "compromised" after every software update (/etc/sysconfig/rkhunter)

I hope you are not "afraid" of these "warnings" anymore!

---

### Post by ericus on 2011-03-27
> **leoquant said:**
> its in the FAQ and readme of rkhunter.



I hope you are not "afraid" of these "warnings" anymore!

Thank you, and all of you others as well for the help!

---

