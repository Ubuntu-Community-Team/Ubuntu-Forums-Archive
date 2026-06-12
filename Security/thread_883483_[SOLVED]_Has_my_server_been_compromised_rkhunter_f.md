---
title: "[SOLVED] Has my server been compromised? rkhunter file property warnings"
date: 2008-08-08
forum: Security
---

### Post by FuturePilot on 2008-08-08
I just ran rkhunter on my server and it returned some warnings that have me concerned.
```
[00:46:19] Performing 'shared libraries' checks
[00:46:19] Info: Starting test name 'shared_libs'
[00:46:19] Checking for preloading variables                 [ None found ]
[00:46:20] Checking for preload file                         [ Not found ]
[00:46:20] Info: Starting test name 'shared_libs_path'
[00:46:20] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[00:46:20]
[00:46:20] Performing file properties checks
[00:46:20] Info: Starting test name 'properties'
[00:46:20] Checking for prerequisites                        [ OK ]
[00:46:21] /bin/bash                                         [ OK ]
[00:46:21] /bin/cat                                          [ OK ]
[00:46:21] /bin/chmod                                        [ OK ]
[00:46:22] /bin/chown                                        [ OK ]
[00:46:22] /bin/cp                                           [ OK ]
[00:46:23] /bin/date                                         [ OK ]
[00:46:23] /bin/df                                           [ OK ]
[00:46:24] /bin/dmesg                                        [ OK ]
[00:46:24] /bin/echo                                         [ OK ]
[00:46:25] /bin/ed                                           [ OK ]
[00:46:25] /bin/egrep                                        [ OK ]
[00:46:26] /bin/fgrep                                        [ OK ]
[00:46:26] /bin/grep                                         [ OK ]
[00:46:27] /bin/ip                                           [ Warning ]
[00:46:27] Warning: The file properties have changed:
[00:46:27]          File: /bin/ip
[00:46:27]          Current inode: 951280    Stored inode: 950959
[00:46:27]          Current file modification time: 1215618519
[00:46:27]          Stored file modification time : 1207985171
[00:46:27] /bin/kill                                         [ Warning ]
[00:46:27] Warning: The file properties have changed:
[00:46:27]          File: /bin/kill
[00:46:28]          Current inode: 951436    Stored inode: 950788
[00:46:28]          Current file modification time: 1215682114
[00:46:28]          Stored file modification time : 1205447087
[00:46:28] /bin/login                                        [ OK ]
[00:46:29] /bin/ls                                           [ OK ]
[00:46:29] /bin/lsmod                                        [ OK ]
[00:46:29] /bin/mktemp                                       [ OK ]
[00:46:30] /bin/more                                         [ OK ]
[00:46:30] /bin/mount                                        [ OK ]
[00:46:31] /bin/mv                                           [ OK ]
[00:46:31] /bin/netstat                                      [ OK ]
[00:46:32] /bin/ps                                           [ Warning ]
[00:46:32] Warning: The file properties have changed:
[00:46:32]          File: /bin/ps
[00:46:32]          Current inode: 951723    Stored inode: 950789
[00:46:32]          Current file modification time: 1215682114
[00:46:32]          Stored file modification time : 1205447087
[00:46:32] /bin/pwd                                          [ OK ]
[00:46:33] /bin/readlink                                     [ OK ]
[00:46:33] /bin/sed                                          [ OK ]
[00:46:34] /bin/sh                                           [ OK ]
[00:46:34] /bin/su                                           [ OK ]
[00:46:35] /bin/touch                                        [ OK ]
[00:46:35] /bin/uname                                        [ OK ]
[00:46:36] /bin/which                                        [ OK ]
[00:46:36] /bin/dash                                         [ OK ]
[00:46:37] /usr/bin/awk                                      [ OK ]
[00:46:37] /usr/bin/basename                                 [ OK ]
[00:46:38] /usr/bin/chattr                                   [ OK ]
[00:46:38] /usr/bin/cut                                      [ OK ]
[00:46:39] /usr/bin/diff                                     [ OK ]
[00:46:39] /usr/bin/dirname                                  [ OK ]
[00:46:40] /usr/bin/dpkg                                     [ OK ]
[00:46:40] /usr/bin/dpkg-query                               [ OK ]
[00:46:40] /usr/bin/du                                       [ OK ]
[00:46:41] /usr/bin/env                                      [ OK ]
[00:46:41] /usr/bin/file                                     [ OK ]
[00:46:42] /usr/bin/find                                     [ OK ]
[00:46:42] /usr/bin/GET                                      [ OK ]
[00:46:43] /usr/bin/groups                                   [ OK ]
[00:46:43] /usr/bin/head                                     [ OK ]
[00:46:43] /usr/bin/id                                       [ OK ]
[00:46:44] /usr/bin/killall                                  [ OK ]
[00:46:44] /usr/bin/last                                     [ OK ]
[00:46:45] /usr/bin/lastlog                                  [ OK ]
[00:46:45] /usr/bin/ldd                                      [ OK ]
[00:46:46] /usr/bin/less                                     [ OK ]
[00:46:46] /usr/bin/locate                                   [ OK ]
[00:46:47] /usr/bin/logger                                   [ OK ]
[00:46:47] /usr/bin/lsattr                                   [ OK ]
[00:46:48] /usr/bin/lsof                                     [ OK ]
[00:46:48] /usr/bin/lynx                                     [ Warning ]
[00:46:48] Warning: The file '/usr/bin/lynx' exists on the system, but it is not present in the rkhunter.dat file.
[00:46:48] /usr/bin/mail                                     [ OK ]
[00:46:49] /usr/bin/md5sum                                   [ OK ]
[00:46:49] /usr/bin/mlocate                                  [ OK ]
[00:46:50] /usr/bin/newgrp                                   [ OK ]
[00:46:50] /usr/bin/passwd                                   [ OK ]
[00:46:50] /usr/bin/perl                                     [ OK ]
[00:46:51] /usr/bin/pstree                                   [ OK ]
[00:46:51] /usr/bin/rkhunter                                 [ OK ]
[00:46:52] /usr/bin/runcon                                   [ OK ]
[00:46:52] /usr/bin/sha1sum                                  [ OK ]
[00:46:53] /usr/bin/size                                     [ OK ]
[00:46:53] /usr/bin/sort                                     [ OK ]
[00:46:54] /usr/bin/stat                                     [ OK ]
[00:46:54] /usr/bin/strace                                   [ OK ]
[00:46:55] /usr/bin/strings                                  [ OK ]
[00:46:55] /usr/bin/sudo                                     [ OK ]
[00:46:55] /usr/bin/tail                                     [ OK ]
[00:46:56] /usr/bin/test                                     [ OK ]
[00:46:56] /usr/bin/top                                      [ Warning ]
[00:46:56] Warning: The file properties have changed:
[00:46:56]          File: /usr/bin/top
[00:46:56]          Current inode: 1108439    Stored inode: 1107486
[00:46:57]          Current file modification time: 1215682114
[00:46:57]          Stored file modification time : 1205447087
[00:46:57] /usr/bin/touch                                    [ OK ]
[00:46:57] /usr/bin/tr                                       [ OK ]
[00:46:58] /usr/bin/uniq                                     [ OK ]
[00:46:58] /usr/bin/users                                    [ OK ]
[00:46:59] /usr/bin/vmstat                                   [ Warning ]
[00:46:59] Warning: The file properties have changed:
[00:46:59]          File: /usr/bin/vmstat
[00:46:59]          Current inode: 1108440    Stored inode: 1107487
[00:46:59]          Current file modification time: 1215682114
[00:46:59]          Stored file modification time : 1205447087
[00:46:59] /usr/bin/w                                        [ Warning ]
[00:46:59] Warning: The file properties have changed:
[00:47:00]          File: /usr/bin/w
[00:47:00]          Current hash: fb2819df7d1c7a261311a105100fcae1333b71e7
[00:47:00]          Stored hash : 1afb9e68b386be6926900bf05585f9d8fff4ecf2
[00:47:00] /usr/bin/watch                                    [ Warning ]
[00:47:00] Warning: The file properties have changed:
[00:47:00]          File: /usr/bin/watch
[00:47:00]          Current inode: 1108441    Stored inode: 1107488
[00:47:00]          Current file modification time: 1215682114
[00:47:00]          Stored file modification time : 1205447087
[00:47:01] /usr/bin/wc                                       [ OK ]
[00:47:01] /usr/bin/wget                                     [ OK ]
[00:47:02] /usr/bin/whatis                                   [ OK ]
[00:47:02] /usr/bin/whereis                                  [ OK ]
[00:47:02] /usr/bin/which                                    [ OK ]
[00:47:03] /usr/bin/who                                      [ OK ]
[00:47:03] /usr/bin/whoami                                   [ OK ]
[00:47:04] /usr/bin/mawk                                     [ OK ]
[00:47:04] /usr/bin/lwp-request                              [ OK ]
[00:47:04] /usr/bin/lynx.stable                              [ Warning ]
[00:47:04] Warning: The file '/usr/bin/lynx.stable' exists on the system, but it is not present in the rkhunter.dat file.
[00:47:05] /usr/bin/w.procps                                 [ Warning ]
[00:47:05] Warning: The file properties have changed:
[00:47:05]          File: /usr/bin/w.procps
[00:47:05]          Current inode: 1108447    Stored inode: 1107494
[00:47:05]          Current file modification time: 1215682114
[00:47:05]          Stored file modification time : 1205447087
[00:47:06] /sbin/depmod                                      [ OK ]
[00:47:06] /sbin/ifconfig                                    [ OK ]
[00:47:07] /sbin/ifdown                                      [ OK ]
[00:47:07] /sbin/ifup                                        [ OK ]
[00:47:08] /sbin/init                                        [ OK ]
[00:47:08] /sbin/insmod                                      [ OK ]
[00:47:09] /sbin/ip                                          [ Warning ]
[00:47:09] Warning: The file properties have changed:
[00:47:09]          File: /sbin/ip
[00:47:09]          Current inode: 270477    Stored inode: 270386
[00:47:09]          Current file modification time: 1217720285
[00:47:09]          Stored file modification time : 1215802954
[00:47:09] /sbin/lsmod                                       [ OK ]
[00:47:10] /sbin/modinfo                                     [ OK ]
[00:47:10] /sbin/modprobe                                    [ OK ]
[00:47:11] /sbin/rmmod                                       [ OK ]
[00:47:11] /sbin/runlevel                                    [ OK ]
[00:47:12] /sbin/sulogin                                     [ OK ]
[00:47:12] /sbin/sysctl                                      [ Warning ]
[00:47:13] Warning: The file properties have changed:
[00:47:13]          File: /sbin/sysctl
[00:47:13]          Current inode: 270382    Stored inode: 270345
[00:47:13]          Current file modification time: 1215682114
[00:47:13]          Stored file modification time : 1205447087
[00:47:13] /sbin/syslogd                                     [ OK ]
[00:47:14] /usr/sbin/adduser                                 [ OK ]
[00:47:15] /usr/sbin/chroot                                  [ OK ]
[00:47:15] /usr/sbin/cron                                    [ OK ]
[00:47:16] /usr/sbin/groupadd                                [ OK ]
[00:47:16] /usr/sbin/groupdel                                [ OK ]
[00:47:17] /usr/sbin/groupmod                                [ OK ]
[00:47:17] /usr/sbin/grpck                                   [ OK ]
[00:47:18] /usr/sbin/nologin                                 [ OK ]
[00:47:18] /usr/sbin/pwck                                    [ OK ]
[00:47:19] /usr/sbin/tcpd                                    [ OK ]
[00:47:20] /usr/sbin/useradd                                 [ OK ]
[00:47:20] /usr/sbin/userdel                                 [ OK ]
[00:47:21] /usr/sbin/usermod                                 [ OK ]
[00:47:21] /usr/sbin/vipw                                    [ OK ]
```

I found that those could be false positives caused by an update so I ran rkhunter with the  --pkgmgr dpkg option but it still gave those warnings and I couldn't find anything in my update history that would have updated those files.

The rest of the checks from rkhunter were ok. Anyone know what this might mean?

---

### Post by FuturePilot on 2008-08-08
Ooops, seemed to have jumped the gun. It was an update.
procps 1:3.2.7-5ubuntu3. All the warnings match with the files included in that package. Somehow I missed that one when looking through the updates. ](*,)

So false alarm. Those warnings are scary though. :neutral:

---

### Post by kimda on 2008-11-18
Update the rkhunter file database with the --propupd option so that you wont receive the same error next time. You could also run the package chkrootkit to make sure that the files are not tampered with.

---

