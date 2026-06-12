---
title: "Rkhunter found a lot of warnins"
date: 2010-05-01
forum: Security
---

### Post by xbaez on 2010-05-01
Hello
Rkhunter found a lot of warnings

I have 2 Ubuntu machines

on one it only found the 2 usual warnings

on another machine it found a lot of warnings,

one machine is updated (the one with the warnings)
the other one is not

What should I do?

Here is the log:

[PHP][23:01:30] Performing file properties checks
[23:01:30] Info: Starting test name 'properties'
[23:01:30] Checking for prerequisites                        [ OK ]
[23:01:30] /bin/bash                                         [ OK ]
[23:01:30] /bin/cat                                          [ OK ]
[23:01:30] /bin/chmod                                        [ OK ]
[23:01:31] /bin/chown                                        [ OK ]
[23:01:31] /bin/cp                                           [ OK ]
[23:01:31] /bin/date                                         [ OK ]
[23:01:31] /bin/df                                           [ OK ]
[23:01:31] /bin/dmesg                                        [ OK ]
[23:01:31] /bin/echo                                         [ OK ]
[23:01:31] /bin/ed                                           [ OK ]
[23:01:31] /bin/egrep                                        [ OK ]
[23:01:31] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[23:01:31] /bin/fgrep                                        [ OK ]
[23:01:31] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[23:01:31] /bin/fuser                                        [ OK ]
[23:01:31] /bin/grep                                         [ OK ]
[23:01:32] /bin/ip                                           [ OK ]
[23:01:32] /bin/kill                                         [ OK ]
[23:01:32] /bin/less                                         [ OK ]
[23:01:32] /bin/login                                        [ OK ]
[23:01:32] /bin/ls                                           [ OK ]
[23:01:32] /bin/lsmod                                        [ OK ]
[23:01:32] /bin/mktemp                                       [ OK ]
[23:01:32] /bin/more                                         [ OK ]
[23:01:32] /bin/mount                                        [ OK ]
[23:01:33] /bin/mv                                           [ OK ]
[23:01:33] /bin/netstat                                      [ OK ]
[23:01:33] /bin/ps                                           [ OK ]
[23:01:33] /bin/pwd                                          [ OK ]
[23:01:33] /bin/readlink                                     [ OK ]
[23:01:33] /bin/sed                                          [ OK ]
[23:01:33] /bin/sh                                           [ OK ]
[23:01:33] /bin/su                                           [ OK ]
[23:01:33] /bin/touch                                        [ OK ]
[23:01:33] /bin/uname                                        [ OK ]
[23:01:34] /bin/which                                        [ OK ]
[23:01:34] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[23:01:34] /bin/dash                                         [ OK ]
[23:01:34] /usr/bin/awk                                      [ OK ]
[23:01:34] /usr/bin/basename                                 [ OK ]
[23:01:34] /usr/bin/chattr                                   [ OK ]
[23:01:34] /usr/bin/curl                                     [ OK ]
[23:01:34] /usr/bin/cut                                      [ OK ]
[23:01:34] /usr/bin/diff                                     [ OK ]
[23:01:34] /usr/bin/dirname                                  [ OK ]
[23:01:34] /usr/bin/dpkg                                     [ Warning ]
[23:01:34] Warning: The file properties have changed:
[23:01:35]          File: /usr/bin/dpkg
[23:01:35]          Current hash: 8e820f6ffa1ba84be7c5256a8bd344a49fec7182
[23:01:35]          Stored hash : 7c5ab2420dfddf22f3794a1f2aa4b61243e44a08
[23:01:35]          Current inode: 276583    Stored inode: 9060
[23:01:35]          Current file modification time: 1268271700
[23:01:35]          Stored file modification time : 1253435089
[23:01:35] /usr/bin/dpkg-query                               [ Warning ]
[23:01:35] Warning: The file properties have changed:
[23:01:35]          File: /usr/bin/dpkg-query
[23:01:35]          Current hash: b5a6de09d70cd24592cb59dbdd2d58e9280a7cc0
[23:01:35]          Stored hash : 19539cfbfd8621b4fae64a5f5f8ad80775acbf5d
[23:01:35]          Current inode: 276586    Stored inode: 9063
[23:01:35]          Current file modification time: 1268271700
[23:01:35]          Stored file modification time : 1253435089
[23:01:35] /usr/bin/du                                       [ OK ]
[23:01:35] /usr/bin/elinks                                   [ OK ]
[23:01:35] /usr/bin/env                                      [ OK ]
[23:01:35] /usr/bin/file                                     [ OK ]
[23:01:35] /usr/bin/find                                     [ OK ]
[23:01:35] /usr/bin/GET                                      [ OK ]
[23:01:35] /usr/bin/groups                                   [ OK ]
[23:01:35] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[23:01:36] /usr/bin/head                                     [ OK ]
[23:01:36] /usr/bin/id                                       [ OK ]
[23:01:36] /usr/bin/killall                                  [ OK ]
[23:01:36] /usr/bin/last                                     [ Warning ]
[23:01:36] Warning: The file properties have changed:
[23:01:36]          File: /usr/bin/last
[23:01:36]          Current inode: 9593    Stored inode: 9889
[23:01:36]          Current file modification time: 1257846438
[23:01:36]          Stored file modification time : 1255965924
[23:01:36] /usr/bin/lastlog                                  [ OK ]
[23:01:36] /usr/bin/ldd                                      [ OK ]
[23:01:36] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[23:01:36] /usr/bin/less                                     [ OK ]
[23:01:36] /usr/bin/locate                                   [ OK ]
[23:01:36] /usr/bin/logger                                   [ OK ]
[23:01:36] /usr/bin/lsattr                                   [ OK ]
[23:01:37] /usr/bin/lsof                                     [ OK ]
[23:01:37] /usr/bin/lynx                                     [ OK ]
[23:01:37] /usr/bin/mail                                     [ OK ]
[23:01:37] /usr/bin/md5sum                                   [ OK ]
[23:01:37] /usr/bin/mlocate                                  [ OK ]
[23:01:37] /usr/bin/newgrp                                   [ OK ]
[23:01:37] /usr/bin/passwd                                   [ OK ]
[23:01:37] /usr/bin/perl                                     [ OK ]
[23:01:37] /usr/bin/pstree                                   [ OK ]
[23:01:37] /usr/bin/rkhunter                                 [ OK ]
[23:01:37] /usr/bin/rpm                                      [ Warning ]
[23:01:38] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
[23:01:38] /usr/bin/runcon                                   [ OK ]
[23:01:38] /usr/bin/sha1sum                                  [ OK ]
[23:01:38] /usr/bin/size                                     [ OK ]
[23:01:38] /usr/bin/sort                                     [ OK ]
[23:01:38] /usr/bin/stat                                     [ OK ]
[23:01:38] /usr/bin/strace                                   [ OK ]
[23:01:38] /usr/bin/strings                                  [ OK ]
[23:01:38] /usr/bin/sudo                                     [ Warning ]
[23:01:38] Warning: The file properties have changed:
[23:01:38]          File: /usr/bin/sudo
[23:01:38]          Current hash: f6d3835fd7ad04f7c749b0e1323887fe688af14e
[23:01:38]          Stored hash : db452cb33718b23e8f33d0e27dc5168a25201116
[23:01:38]          Current inode: 12879    Stored inode: 11209
[23:01:38]          Current size: 143736    Stored size: 143656
[23:01:38]          Current file modification time: 1271179860
[23:01:38]          Stored file modification time : 1245687344
[23:01:38] /usr/bin/tail                                     [ OK ]
[23:01:39] /usr/bin/test                                     [ OK ]
[23:01:39] /usr/bin/top                                      [ OK ]
[23:01:39] /usr/bin/touch                                    [ OK ]
[23:01:39] /usr/bin/tr                                       [ OK ]
[23:01:39] /usr/bin/uniq                                     [ OK ]
[23:01:39] /usr/bin/users                                    [ OK ]
[23:01:39] /usr/bin/vmstat                                   [ OK ]
[23:01:39] /usr/bin/w                                        [ OK ]
[23:01:39] /usr/bin/watch                                    [ OK ]
[23:01:39] /usr/bin/wc                                       [ OK ]
[23:01:39] /usr/bin/wget                                     [ OK ]
[23:01:40] /usr/bin/whatis                                   [ OK ]
[23:01:40] /usr/bin/whereis                                  [ OK ]
[23:01:40] /usr/bin/which                                    [ OK ]
[23:01:40] /usr/bin/who                                      [ OK ]
[23:01:40] /usr/bin/whoami                                   [ OK ]
[23:01:40] /usr/bin/gawk                                     [ OK ]
[23:01:40] /usr/bin/lwp-request                              [ OK ]
[23:01:40] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[23:01:40] /usr/bin/lynx.cur                                 [ OK ]
[23:01:40] /usr/bin/w.procps                                 [ OK ]
[23:01:40] /sbin/depmod                                      [ OK ]
[23:01:41] /sbin/ifconfig                                    [ OK ]
[23:01:41] /sbin/ifdown                                      [ Warning ]
[23:01:41] Warning: The file properties have changed:
[23:01:41]          File: /sbin/ifdown
[23:01:41]          Current hash: a233b8eee20b09926816606d3c8cd85ee95d2ed0
[23:01:41]          Stored hash : 4bee75d37d635cd8eb11b4725a3bee26b9547b81
[23:01:41]          Current inode: 209271    Stored inode: 209302
[23:01:41]          Current file modification time: 1266883140
[23:01:41]          Stored file modification time : 1253662472
[23:01:41] /sbin/ifup                                        [ Warning ]
[23:01:41] Warning: The file properties have changed:
[23:01:41]          File: /sbin/ifup
[23:01:41]          Current hash: a233b8eee20b09926816606d3c8cd85ee95d2ed0
[23:01:41]          Stored hash : 4bee75d37d635cd8eb11b4725a3bee26b9547b81
[23:01:41]          Current inode: 209271    Stored inode: 209302
[23:01:41]          Current file modification time: 1266883140
[23:01:41]          Stored file modification time : 1253662472
[23:01:41] /sbin/init                                        [ Warning ]
[23:01:41] Warning: The file properties have changed:
[23:01:41]          File: /sbin/init
[23:01:41]          Current inode: 209259    Stored inode: 209269
[23:01:41]          Current file modification time: 1260464455
[23:01:41]          Stored file modification time : 1255634371
[23:01:41] /sbin/insmod                                      [ OK ]
[23:01:41] /sbin/ip                                          [ OK ]
[23:01:42] /sbin/lsmod                                       [ OK ]
[23:01:42] /sbin/modinfo                                     [ OK ]
[23:01:42] /sbin/modprobe                                    [ OK ]
[23:01:42] /sbin/rmmod                                       [ OK ]
[23:01:42] /sbin/runlevel                                    [ Warning ]
[23:01:42] Warning: The file properties have changed:
[23:01:42]          File: /sbin/runlevel
[23:01:42]          Current inode: 210237    Stored inode: 209272
[23:01:42]          Current file modification time: 1260464455
[23:01:42]          Stored file modification time : 1255634371
[23:01:42] /sbin/sulogin                                     [ Warning ]
[23:01:42] Warning: The file properties have changed:
[23:01:42]          File: /sbin/sulogin
[23:01:42]          Current inode: 210232    Stored inode: 209265
[23:01:42]          Current file modification time: 1257846438
[23:01:42]          Stored file modification time : 1255965924
[23:01:43] /sbin/sysctl                                      [ OK ]
[23:01:43] /usr/sbin/adduser                                 [ Warning ]
[23:01:43] Warning: The file properties have changed:
[23:01:43]          File: /usr/sbin/adduser
[23:01:43]          Current hash: ae9336d2700a0d02fa50900f9f9e7a568a0897a5
[23:01:43]          Stored hash : 3b23a07e11395e782cab2d20d71af5f1dc7bb9e9
[23:01:43]          Current inode: 127    Stored inode: 10095
[23:01:43]          Current file modification time: 1257763340
[23:01:43]          Stored file modification time : 1249313589
[23:01:43] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[23:01:43] /usr/sbin/chroot                                  [ OK ]
[23:01:43] /usr/sbin/cron                                    [ OK ]
[23:01:43] /usr/sbin/groupadd                                [ OK ]
[23:01:43] /usr/sbin/groupdel                                [ OK ]
[23:01:43] /usr/sbin/groupmod                                [ OK ]
[23:01:44] /usr/sbin/grpck                                   [ OK ]
[23:01:44] /usr/sbin/nologin                                 [ OK ]
[23:01:44] /usr/sbin/pwck                                    [ OK ]
[23:01:44] /usr/sbin/rsyslogd                                [ Warning ]
[23:01:44] Warning: The file properties have changed:
[23:01:44]          File: /usr/sbin/rsyslogd
[23:01:44]          Current inode: 10819    Stored inode: 11198
[23:01:44]          Current file modification time: 1257421054
[23:01:44]          Stored file modification time : 1255581770
[23:01:44] /usr/sbin/tcpd                                    [ OK ]
[23:01:44] /usr/sbin/unhide                                  [ Warning ]
[23:01:44] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[23:01:45] /usr/sbin/useradd                                 [ OK ]
[23:01:45] /usr/sbin/userdel                                 [ OK ]
[23:01:45] /usr/sbin/usermod                                 [ OK ]
[23:01:45] /usr/sbin/vipw                                    [ OK ]
[23:01:45] /usr/sbin/unhide-linux26                          [ Warning ]
[23:01:45] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[23:02:58][/PHP]

---

### Post by unspawn on 2010-05-01
> **xbaez said:**
> ```

[23:01:34] Warning: The file properties have changed:
[23:01:35]          File: /usr/bin/dpkg
[23:01:35]          Current hash: 8e820f6ffa1ba84be7c5256a8bd344a49fec7182
[23:01:35]          Stored hash : 7c5ab2420dfddf22f3794a1f2aa4b61243e44a08
[23:01:35]          Current inode: 276583    Stored inode: 9060
[23:01:35]          Current file modification time: 1268271700
[23:01:35]          Stored file modification time : 1253435089

```
Might be due to package updates without running 'rkhunter --propupd' afterwards. Check if packages are actually updated first.


> **xbaez said:**
> ```

[23:01:37] /usr/bin/rpm                                      [ Warning ]
[23:01:38] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
(..)
[23:01:45] /usr/sbin/unhide-linux26                          [ Warning ]
[23:01:45] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[23:02:58]
```
The "not present in the rkhunter.dat file" message will disappear after running "propupd".


* For efficiency sake please note most common questions are already answered in the documentation and FAQ RKH comes with and in the rkhunter-users mailing list archives.

---

### Post by xbaez on 2010-05-03
What about the Warning: The file properties have changed errors?

Will they all go away running the rkhunter --propupd command as well?

---

