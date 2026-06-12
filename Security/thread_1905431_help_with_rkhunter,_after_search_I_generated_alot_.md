---
title: "help with rkhunter, after search I generated alot of warnings"
date: 2012-01-06
forum: Security
---

### Post by euclid1219 on 2012-01-06
System checks summary
=====================

File properties checks...
    Required commands check failed
    Files checked: 138
    Suspect files: 88

Rootkit checks...
    Rootkits checked : 245
    Possible rootkits: 0

this was my results
I wanted to know if the file properties check which came up with 88 suspect files is serious and if so how do I fix it?

also what is the terminal commands for running rkhunter and chkrootkit as regular sudo

I only know how to run it in root 
what are they?

---

### Post by Dangertux on 2012-01-06
> **euclid1219 said:**
> System checks summary
=====================

File properties checks...
    Required commands check failed
    Files checked: 138
    Suspect files: 88

Rootkit checks...
    Rootkits checked : 245
    Possible rootkits: 0

this was my results
I wanted to know if the file properties check which came up with 88 suspect files is serious and if so how do I fix it?

also what is the terminal commands for running rkhunter and chkrootkit as regular sudo

I only know how to run it in root 
what are they?

Can you post the contents of /var/log/rkhunter.log

also to run rkhunter as root with sudo simply

```

sudo rkhunter --check

```

---

### Post by euclid1219 on 2012-01-06
here is a portion
Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ Warning ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ Warning ]
    /usr/sbin/groupadd                                       [ Warning ]
    /usr/sbin/groupdel                                       [ Warning ]
    /usr/sbin/groupmod                                       [ Warning ]
    /usr/sbin/grpck                                          [ Warning ]
    /usr/sbin/inetd                                          [ Warning ]
    /usr/sbin/nologin                                        [ Warning ]
    /usr/sbin/pwck                                           [ Warning ]
    /usr/sbin/rsyslogd                                       [ Warning ]
    /usr/sbin/tcpd                                           [ Warning ]
    /usr/sbin/useradd                                        [ Warning ]
    /usr/sbin/userdel                                        [ Warning ]
    /usr/sbin/usermod                                        [ Warning ]
    /usr/sbin/vipw                                           [ Warning ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/unhide-tcp                                     [ Warning ]
    /usr/sbin/unhide-linux26                                 [ Warning ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/curl                                            [ Warning ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ Warning ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ Warning ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ Warning ]
    /usr/bin/last                                            [ Warning ]
    /usr/bin/lastlog                                         [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ Warning ]
    /usr/bin/locate                                          [ Warning ]
    /usr/bin/logger                                          [ Warning ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ Warning ]
    /usr/bin/newgrp                                          [ Warning ]
    /usr/bin/passwd                                          [ Warning ]
    /usr/bin/perl                                            [ Warning ]
    /usr/bin/pgrep                                           [ Warning ]
    /usr/bin/pstree                                          [ Warning ]
    /usr/bin/rkhunter                                        [ Warning ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ Warning ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ Warning ]
    /usr/bin/strings                                         [ Warning ]
    /usr/bin/sudo                                            [ Warning ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ Warning ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ Warning ]
    /usr/bin/w                                               [ Warning ]
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ Warning ]
    /usr/bin/whatis                                          [ Warning ]
    /usr/bin/whereis                                         [ Warning ]
    /usr/bin/which                                           [ Warning ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/w.procps                                        [ Warning ]
    /sbin/depmod                                             [ Warning ]
    /sbin/fsck                                               [ Warning ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ Warning ]
    /sbin/ifup                                               [ Warning ]
    /sbin/init                                               [ Warning ]
    /sbin/insmod                                             [ Warning ]
    /sbin/ip                                                 [ Warning ]
    /sbin/lsmod                                              [ Warning ]
    /sbin/modinfo                                            [ Warning ]
    /sbin/modprobe                                           [ Warning ]
    /sbin/rmmod                                              [ Warning ]
    /sbin/route                                              [ Warning ]
    /sbin/runlevel                                           [ Warning ]
    /sbin/sulogin                                            [ Warning ]
    /sbin/sysctl                                             [ Warning ]
    /bin/bash                                                [ Warning ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ Warning ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ Warning ]
    /bin/fgrep                                               [ Warning ]
    /bin/fuser                                               [ Warning ]
    /bin/grep                                                [ Warning ]
    /bin/ip                                                  [ Warning ]
    /bin/kill                                                [ Warning ]
    /bin/less                                                [ Warning ]
    /bin/login                                               [ Warning ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ Warning ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ Warning ]
    /bin/mount                                               [ Warning ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ Warning ]
    /bin/sh                                                  [ Warning ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ Warning ]
    /bin/dash                                                [ Warning ]
    /usr/bin/mawk                                            [ Warning ]

---

### Post by Dangertux on 2012-01-06
Hmm.. Not to jump to conclusions. But there is definitely SOMETHING wrong. Not saying you're compromised but a common method for 'rooting' a system is to wrap certain system files. Those would be good examples of what would be wrapped.

Is this the first run of rkhunter? If not did you perform a major update, or possible a distro upgrade since the last time you ran it? 

If not... Well your system may be compromised, again not jumping to conclusions without further info. Also, do  you have tripwire installed or maybe a hostbased IDS. Those will sometimes trigger warnings like that as well.

Hope this helps.

---

### Post by euclid1219 on 2012-01-07
I have run rkhunter many times in 11.04, I did upgrade from 11.04 to 11.10
so do I need to update rkhunter are something?

---

### Post by euclid1219 on 2012-01-07
I fixed some of the problem
I update rkhunter with sudo rkhunter --update
it eliminated all but 1 suspicious file

when I run chkrootkit the file also pops-up as suspicious 
 
how do I fix this problem and also how do I update chkrootkit
what is the command code?

---

### Post by Soul-Sing on 2012-01-07
:[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)
naise wiki for rkhunter and prob. avoid panic.
```
sudo rkhunter --propupd
```
is great to start with.

---

### Post by euclid1219 on 2012-01-07
thanks alot guys

---

