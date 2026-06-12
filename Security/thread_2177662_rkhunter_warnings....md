---
title: "rkhunter warnings..."
date: 2013-09-29
forum: Security
---

### Post by CCgirl6690 on 2013-09-29
Hello everyone
i just ran rkhunter and it gave me lots of warnings so it got me all worried and im not sure what to do . any suggestion please?
and im on ubuntu 13.4 and here is my log , thank you 
```
 
Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ Warning ]
    /usr/sbin/adduser                                        [ Warning ]
    /usr/sbin/chroot                                         [ Warning ]
    /usr/sbin/cron                                           [ Warning ]
    /usr/sbin/groupadd                                       [ Warning ]
    /usr/sbin/groupdel                                       [ Warning ]
    /usr/sbin/groupmod                                       [ Warning ]
    /usr/sbin/grpck                                          [ Warning ]
    /usr/sbin/nologin                                        [ Warning ]
    /usr/sbin/pwck                                           [ Warning ]
    /usr/sbin/rsyslogd                                       [ Warning ]
    /usr/sbin/tcpd                                           [ Warning ]
    /usr/sbin/useradd                                        [ Warning ]
    /usr/sbin/userdel                                        [ Warning ]
    /usr/sbin/usermod                                        [ Warning ]
    /usr/sbin/vipw                                           [ Warning ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/basename                                        [ Warning ]
    /usr/bin/chattr                                          [ Warning ]
    /usr/bin/curl                                            [ Warning ]
    /usr/bin/cut                                             [ Warning ]
    /usr/bin/diff                                            [ Warning ]
    /usr/bin/dirname                                         [ Warning ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ Warning ]
    /usr/bin/env                                             [ Warning ]
    /usr/bin/file                                            [ Warning ]
    /usr/bin/find                                            [ Warning ]
    /usr/bin/GET                                             [ Warning ]
    /usr/bin/groups                                          [ Warning ]
    /usr/bin/head                                            [ Warning ]
    /usr/bin/id                                              [ Warning ]
    /usr/bin/killall                                         [ Warning ]
    /usr/bin/last                                            [ Warning ]
    /usr/bin/lastlog                                         [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ Warning ]
    /usr/bin/locate                                          [ Warning ]
    /usr/bin/logger                                          [ Warning ]
    /usr/bin/lsattr                                          [ Warning ]
    /usr/bin/lsof                                            [ Warning ]
    /usr/bin/md5sum                                          [ Warning ]
    /usr/bin/mlocate                                         [ Warning ]
    /usr/bin/newgrp                                          [ Warning ]
    /usr/bin/passwd                                          [ Warning ]
    /usr/bin/perl                                            [ Warning ]
    /usr/bin/pgrep                                           [ Warning ]
    /usr/bin/pkill                                           [ Warning ]
    /usr/bin/pstree                                          [ Warning ]
    /usr/bin/rkhunter                                        [ Warning ]
    /usr/bin/runcon                                          [ Warning ]
    /usr/bin/sha1sum                                         [ Warning ]
    /usr/bin/sha224sum                                       [ Warning ]
    /usr/bin/sha256sum                                       [ Warning ]
    /usr/bin/sha384sum                                       [ Warning ]
    /usr/bin/sha512sum                                       [ Warning ]
    /usr/bin/size                                            [ Warning ]
    /usr/bin/sort                                            [ Warning ]
    /usr/bin/stat                                            [ Warning ]
    /usr/bin/strace                                          [ Warning ]
    /usr/bin/strings                                         [ Warning ]
    /usr/bin/sudo                                            [ Warning ]
    /usr/bin/tail                                            [ Warning ]
    /usr/bin/test                                            [ Warning ]
    /usr/bin/top                                             [ Warning ]
    /usr/bin/touch                                           [ Warning ]
    /usr/bin/tr                                              [ Warning ]
    /usr/bin/uniq                                            [ Warning ]
    /usr/bin/users                                           [ Warning ]
    /usr/bin/vmstat                                          [ Warning ]
    /usr/bin/w                                               [ Warning ]
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              [ Warning ]
    /usr/bin/wget                                            [ Warning ]
    /usr/bin/whatis                                          [ Warning ]
    /usr/bin/whereis                                         [ Warning ]
    /usr/bin/which                                           [ Warning ]
    /usr/bin/who                                             [ Warning ]
    /usr/bin/whoami                                          [ Warning ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/w.procps                                        [ Warning ]
    /sbin/depmod                                             [ Warning ]
    /sbin/fsck                                               [ Warning ]
    /sbin/ifconfig                                           [ Warning ]
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
    /bin/cat                                                 [ Warning ]
    /bin/chmod                                               [ Warning ]
    /bin/chown                                               [ Warning ]
    /bin/cp                                                  [ Warning ]
    /bin/date                                                [ Warning ]
    /bin/df                                                  [ Warning ]
    /bin/dmesg                                               [ Warning ]
    /bin/echo                                                [ Warning ]
    /bin/ed                                                  [ Warning ]
    /bin/egrep                                               [ Warning ]
    /bin/fgrep                                               [ Warning ]
    /bin/fuser                                               [ Warning ]
    /bin/grep                                                [ Warning ]
    /bin/ip                                                  [ Warning ]
    /bin/kill                                                [ Warning ]
    /bin/less                                                [ Warning ]
    /bin/login                                               [ Warning ]
    /bin/ls                                                  [ Warning ]
    /bin/lsmod                                               [ Warning ]
    /bin/mktemp                                              [ Warning ]
    /bin/more                                                [ Warning ]
    /bin/mount                                               [ Warning ]
    /bin/mv                                                  [ Warning ]
    /bin/netstat                                             [ Warning ]
    /bin/ping                                                [ Warning ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ Warning ]
    /bin/readlink                                            [ Warning ]
    /bin/sed                                                 [ Warning ]
    /bin/sh                                                  [ Warning ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ Warning ]
    /bin/uname                                               [ Warning ]
    /bin/which                                               [ Warning ]
    /bin/kmod                                                [ Warning ]
    /bin/dash                                                [ Warning ]
    /usr/bin/mawk                                            [ Warning ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Jynx Rootkit                                             [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

[Press <ENTER> to continue]


  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Required commands check failed
    Files checked: 137
    Suspect files: 137

Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 9 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log) 
```

---

### Post by deadflowr on 2013-09-29
Been a while since I've used rkhunter, but I think you need to run
```
sudo rkhunter --propupd
```

Which updates the file properties database.
```
rkhunter -h
```
for more

---

### Post by CCgirl6690 on 2013-09-30
thank you  deadflowr . it helped now i only get 3 warnings , notsure whats that but still better than all warning LOL . i mark this as solved but plz if anyone else know  what is these 3 warnings i get plz lemme know thanks again .....
here is my new log 
```
none@None:~$ sudo rkhunter -c
[ Rootkit Hunter version 1.4.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/curl                                            [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pkill                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/fsck                                               [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/route                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ping                                                [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/kmod                                                [ OK ]
    /bin/dash                                                [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Jynx Rootkit                                             [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

[Press <ENTER> to continue]


  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 136
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 4 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log) 
```

---

### Post by sandyd on 2013-09-30
> **CCgirl6690 said:**
> thank you  deadflowr . it helped now i only get 3 warnings , notsure whats that but still better than all warning LOL . i mark this as solved but plz if anyone else know  what is these 3 warnings i get plz lemme know thanks again .....
here is my new log 
```
none@None:~$ sudo rkhunter -c
[ Rootkit Hunter version 1.4.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/curl                                            [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pkill                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/fsck                                               [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/route                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ping                                                [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/kmod                                                [ OK ]
    /bin/dash                                                [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Jynx Rootkit                                             [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

[Press <ENTER> to continue]


  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 136
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 4 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log) 
```

Might want to take a look at /var/log/rkhunter.log

---

### Post by CCgirl6690 on 2013-09-30
hello sandyd here is that log file , now what?
thanks
```
[23:32:29] Running Rootkit Hunter version 1.4.0 on None
[23:32:29]
[23:32:29] Info: Start date is Sun Sep 29 23:32:29 PDT 2013
[23:32:29]
[23:32:29] Checking configuration file and command-line options...
[23:32:29] Info: Detected operating system is 'Linux'
[23:32:29] Info: Found O/S name: Ubuntu 13.04
[23:32:29] Info: Command line is /usr/bin/rkhunter -c
[23:32:29] Info: Environment shell is /bin/bash; rkhunter is using dash
[23:32:29] Info: Using configuration file '/etc/rkhunter.conf'
[23:32:29] Info: Installation directory is '/usr'
[23:32:29] Info: Using language 'en'
[23:32:29] Info: Using '/var/lib/rkhunter/db' as the database directory
[23:32:29] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[23:32:29] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin' as the command directories
[23:32:29] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[23:32:29] Info: No mail-on-warning address configured
[23:32:29] Info: X will be automatically detected
[23:32:29] Info: Using second color set
[23:32:29] Info: Found the 'basename' command: /usr/bin/basename
[23:32:29] Info: Found the 'diff' command: /usr/bin/diff
[23:32:29] Info: Found the 'dirname' command: /usr/bin/dirname
[23:32:29] Info: Found the 'file' command: /usr/bin/file
[23:32:29] Info: Found the 'find' command: /usr/bin/find
[23:32:29] Info: Found the 'ifconfig' command: /sbin/ifconfig
[23:32:29] Info: Found the 'ip' command: /sbin/ip
[23:32:29] Info: Found the 'ldd' command: /usr/bin/ldd
[23:32:29] Info: Found the 'lsattr' command: /usr/bin/lsattr
[23:32:29] Info: Found the 'lsmod' command: /sbin/lsmod
[23:32:29] Info: Found the 'lsof' command: /usr/bin/lsof
[23:32:29] Info: Found the 'mktemp' command: /bin/mktemp
[23:32:29] Info: Found the 'netstat' command: /bin/netstat
[23:32:29] Info: Found the 'perl' command: /usr/bin/perl
[23:32:29] Info: Found the 'pgrep' command: /usr/bin/pgrep
[23:32:29] Info: Found the 'ps' command: /bin/ps
[23:32:30] Info: Found the 'pwd' command: /bin/pwd
[23:32:30] Info: Found the 'readlink' command: /bin/readlink
[23:32:30] Info: Found the 'stat' command: /usr/bin/stat
[23:32:30] Info: Found the 'strings' command: /usr/bin/strings
[23:32:30] Info: System is not using prelinking
[23:32:30] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[23:32:30] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[23:32:30] Info: Stored hash values did not use a package manager
[23:32:30] Info: The hash function field index is set to 1
[23:32:30] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[23:32:30] Info: Previous file attributes were stored
[23:32:30] Info: Enabled tests are: all
[23:32:30] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[23:32:30] Info: Found ksym file '/proc/kallsyms'
[23:32:30] Info: Using 'date' to process epoch second times.
[23:32:30]
[23:32:30] Checking if the O/S has changed since last time...
[23:32:30] Info: Nothing seems to have changed.
[23:32:30] Info: Locking is not being used
[23:32:30]
[23:32:30] Starting system checks...
[23:32:30]
[23:32:30] Info: Starting test name 'system_commands'
[23:32:30] Checking system commands...
[23:32:30]
[23:32:30] Info: Starting test name 'strings'
[23:32:30] Performing 'strings' command checks
[23:32:30]   Scanning for string /usr/sbin/ntpsx             [ OK ]
[23:32:30]   Scanning for string /usr/sbin/.../bkit-ava      [ OK ]
[23:32:30]   Scanning for string /usr/sbin/.../bkit-d        [ OK ]
[23:32:30]   Scanning for string /usr/sbin/.../bkit-shd      [ OK ]
[23:32:30]   Scanning for string /usr/sbin/.../bkit-f        [ OK ]
[23:32:30]   Scanning for string /usr/include/.../proc.h     [ OK ]
[23:32:30]   Scanning for string /usr/include/.../.bash_history [ OK ]
[23:32:30]   Scanning for string /usr/include/.../bkit-get   [ OK ]
[23:32:30]   Scanning for string /usr/include/.../bkit-dl    [ OK ]
[23:32:30]   Scanning for string /usr/include/.../bkit-screen [ OK ]
[23:32:30]   Scanning for string /usr/include/.../bkit-sleep [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-adore.o   [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../ls             [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../netstat        [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../lsof           [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../uconf.inv      [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../psr            [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../find           [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../pstree         [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../slocate        [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../du             [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../top            [ OK ]
[23:32:30]   Scanning for string /usr/sbin/...               [ OK ]
[23:32:30]   Scanning for string /usr/include/...            [ OK ]
[23:32:30]   Scanning for string /usr/include/.../.tmp       [ OK ]
[23:32:30]   Scanning for string /usr/lib/...                [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../.ssh           [ OK ]
[23:32:30]   Scanning for string /usr/lib/.../bkit-ssh       [ OK ]
[23:32:30]   Scanning for string /usr/lib/.bkit-             [ OK ]
[23:32:30]   Scanning for string /tmp/.bkp                   [ OK ]
[23:32:30]   Scanning for string /tmp/.cinik                 [ OK ]
[23:32:30]   Scanning for string /tmp/.font-unix/.cinik      [ OK ]
[23:32:30]   Scanning for string /lib/.sso                   [ OK ]
[23:32:30]   Scanning for string /lib/.so                    [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/clean      [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/dxr        [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/read       [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/write      [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/lf         [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/xl         [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/xdr        [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/psg        [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/secure     [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/rdx        [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/va         [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/cl.sh      [ OK ]
[23:32:30]   Scanning for string /var/run/...dica/last.log   [ OK ]
[23:32:30]   Scanning for string /usr/bin/.etc               [ OK ]
[23:32:31]   Scanning for string /etc/sshd_config            [ OK ]
[23:32:31]   Scanning for string /etc/ssh_host_key           [ OK ]
[23:32:31]   Scanning for string /etc/ssh_random_seed        [ OK ]
[23:32:31]   Scanning for string /dev/ptyp                   [ OK ]
[23:32:31]   Scanning for string /dev/ptyq                   [ OK ]
[23:32:31]   Scanning for string /dev/ptyr                   [ OK ]
[23:32:31]   Scanning for string /dev/ptys                   [ OK ]
[23:32:31]   Scanning for string /dev/ptyt                   [ OK ]
[23:32:31]   Scanning for string /dev/fd/.88/freshb-bsd      [ OK ]
[23:32:31]   Scanning for string /dev/fd/.88/fresht          [ OK ]
[23:32:31]   Scanning for string /dev/fd/.88/zxsniff         [ OK ]
[23:32:31]   Scanning for string /dev/fd/.88/zxsniff.log     [ OK ]
[23:32:31]   Scanning for string /dev/fd/.99/.ttyf00         [ OK ]
[23:32:31]   Scanning for string /dev/fd/.99/.ttyp00         [ OK ]
[23:32:31]   Scanning for string /dev/fd/.99/.ttyq00         [ OK ]
[23:32:31]   Scanning for string /dev/fd/.99/.ttys00         [ OK ]
[23:32:31]   Scanning for string /dev/fd/.99/.pwsx00         [ OK ]
[23:32:31]   Scanning for string /etc/.acid                  [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/sched_host.2   [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/random_d.2     [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/set_pid.2      [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/setrgrp.2      [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/TOHIDE         [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/cons.saver     [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/adore/ava/ava  [ OK ]
[23:32:31]   Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[23:32:31]   Scanning for string /bin/sysback                [ OK ]
[23:32:31]   Scanning for string /usr/local/bin/sysback      [ OK ]
[23:32:31]   Scanning for string /usr/lib/.tbd               [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/t0rns     [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/du        [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/ls        [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/t0rnsb    [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/ps        [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/t0rnp     [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/find      [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/ifconfig  [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/pg        [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/ssh.tgz   [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/top       [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/sz        [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/login     [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/in.fingerd [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/1i0n.sh   [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/pstree    [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/in.telnetd [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/mjy       [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/sush      [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/tfn       [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/name      [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/getip.sh  [ OK ]
[23:32:31]   Scanning for string /usr/info/.torn/sh*         [ OK ]
[23:32:31]   Scanning for string /usr/src/.puta/.1addr       [ OK ]
[23:32:31]   Scanning for string /usr/src/.puta/.1file       [ OK ]
[23:32:31]   Scanning for string /usr/src/.puta/.1proc       [ OK ]
[23:32:31]   Scanning for string /usr/src/.puta/.1logz       [ OK ]
[23:32:31]   Scanning for string /usr/info/.t0rn             [ OK ]
[23:32:31]   Scanning for string /dev/.lib                   [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib               [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib           [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/lib/dev       [ OK ]
[23:32:31]   Scanning for string /dev/.lib/lib/scan          [ OK ]
[23:32:31]   Scanning for string /usr/src/.puta              [ OK ]
[23:32:31]   Scanning for string /usr/man/man1/man1          [ OK ]
[23:32:31]   Scanning for string /usr/man/man1/man1/lib      [ OK ]
[23:32:32]   Scanning for string /usr/man/man1/man1/lib/.lib [ OK ]
[23:32:32]   Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[23:32:32]
[23:32:32] Info: Starting test name 'shared_libs'
[23:32:32] Performing 'shared libraries' checks
[23:32:32]   Checking for preloading variables               [ None found ]
[23:32:32]   Checking for preloaded libraries                [ None found ]
[23:32:32]
[23:32:32] Info: Starting test name 'shared_libs_path'
[23:32:32]   Checking LD_LIBRARY_PATH variable               [ Not found ]
[23:32:32]
[23:32:32] Info: Starting test name 'properties'
[23:32:32] Performing file properties checks
[23:32:32]   Checking for prerequisites                      [ OK ]
[23:32:33]   /usr/sbin/adduser                               [ OK ]
[23:32:33] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[23:32:33]   /usr/sbin/chroot                                [ OK ]
[23:32:33]   /usr/sbin/cron                                  [ OK ]
[23:32:34]   /usr/sbin/groupadd                              [ OK ]
[23:32:34]   /usr/sbin/groupdel                              [ OK ]
[23:32:34]   /usr/sbin/groupmod                              [ OK ]
[23:32:34]   /usr/sbin/grpck                                 [ OK ]
[23:32:34]   /usr/sbin/nologin                               [ OK ]
[23:32:34]   /usr/sbin/pwck                                  [ OK ]
[23:32:34]   /usr/sbin/rsyslogd                              [ OK ]
[23:32:34]   /usr/sbin/tcpd                                  [ OK ]
[23:32:35]   /usr/sbin/useradd                               [ OK ]
[23:32:35]   /usr/sbin/userdel                               [ OK ]
[23:32:35]   /usr/sbin/usermod                               [ OK ]
[23:32:35]   /usr/sbin/vipw                                  [ OK ]
[23:32:35]   /usr/bin/awk                                    [ OK ]
[23:32:35]   /usr/bin/basename                               [ OK ]
[23:32:35]   /usr/bin/chattr                                 [ OK ]
[23:32:35]   /usr/bin/curl                                   [ OK ]
[23:32:35]   /usr/bin/cut                                    [ OK ]
[23:32:35]   /usr/bin/diff                                   [ OK ]
[23:32:35]   /usr/bin/dirname                                [ OK ]
[23:32:35]   /usr/bin/dpkg                                   [ OK ]
[23:32:35]   /usr/bin/dpkg-query                             [ OK ]
[23:32:35]   /usr/bin/du                                     [ OK ]
[23:32:35]   /usr/bin/env                                    [ OK ]
[23:32:35]   /usr/bin/file                                   [ OK ]
[23:32:35]   /usr/bin/find                                   [ OK ]
[23:32:36]   /usr/bin/GET                                    [ OK ]
[23:32:36]   /usr/bin/groups                                 [ OK ]
[23:32:36] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[23:32:36]   /usr/bin/head                                   [ OK ]
[23:32:36]   /usr/bin/id                                     [ OK ]
[23:32:36]   /usr/bin/killall                                [ OK ]
[23:32:36]   /usr/bin/last                                   [ OK ]
[23:32:36]   /usr/bin/lastlog                                [ OK ]
[23:32:36]   /usr/bin/ldd                                    [ OK ]
[23:32:36] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[23:32:36]   /usr/bin/less                                   [ OK ]
[23:32:36]   /usr/bin/locate                                 [ OK ]
[23:32:36]   /usr/bin/logger                                 [ OK ]
[23:32:36]   /usr/bin/lsattr                                 [ OK ]
[23:32:36]   /usr/bin/lsof                                   [ OK ]
[23:32:36]   /usr/bin/md5sum                                 [ OK ]
[23:32:36]   /usr/bin/mlocate                                [ OK ]
[23:32:36]   /usr/bin/newgrp                                 [ OK ]
[23:32:36]   /usr/bin/passwd                                 [ OK ]
[23:32:36]   /usr/bin/perl                                   [ OK ]
[23:32:36]   /usr/bin/pgrep                                  [ OK ]
[23:32:37]   /usr/bin/pkill                                  [ OK ]
[23:32:37]   /usr/bin/pstree                                 [ OK ]
[23:32:37]   /usr/bin/rkhunter                               [ OK ]
[23:32:37]   /usr/bin/runcon                                 [ OK ]
[23:32:37]   /usr/bin/sha1sum                                [ OK ]
[23:32:37]   /usr/bin/sha224sum                              [ OK ]
[23:32:37]   /usr/bin/sha256sum                              [ OK ]
[23:32:37]   /usr/bin/sha384sum                              [ OK ]
[23:32:37]   /usr/bin/sha512sum                              [ OK ]
[23:32:37]   /usr/bin/size                                   [ OK ]
[23:32:37]   /usr/bin/sort                                   [ OK ]
[23:32:37]   /usr/bin/stat                                   [ OK ]
[23:32:37]   /usr/bin/strace                                 [ OK ]
[23:32:37]   /usr/bin/strings                                [ OK ]
[23:32:37]   /usr/bin/sudo                                   [ OK ]
[23:32:37]   /usr/bin/tail                                   [ OK ]
[23:32:37]   /usr/bin/test                                   [ OK ]
[23:32:37]   /usr/bin/top                                    [ OK ]
[23:32:37]   /usr/bin/touch                                  [ OK ]
[23:32:38]   /usr/bin/tr                                     [ OK ]
[23:32:38]   /usr/bin/uniq                                   [ OK ]
[23:32:38]   /usr/bin/users                                  [ OK ]
[23:32:38]   /usr/bin/vmstat                                 [ OK ]
[23:32:38]   /usr/bin/w                                      [ OK ]
[23:32:38]   /usr/bin/watch                                  [ OK ]
[23:32:38]   /usr/bin/wc                                     [ OK ]
[23:32:38]   /usr/bin/wget                                   [ OK ]
[23:32:38]   /usr/bin/whatis                                 [ OK ]
[23:32:38]   /usr/bin/whereis                                [ OK ]
[23:32:38]   /usr/bin/which                                  [ OK ]
[23:32:38]   /usr/bin/who                                    [ OK ]
[23:32:38]   /usr/bin/whoami                                 [ OK ]
[23:32:38]   /usr/bin/unhide.rb                              [ Warning ]
[23:32:38] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[23:32:38]   /usr/bin/gawk                                   [ OK ]
[23:32:38]   /usr/bin/lwp-request                            [ OK ]
[23:32:38] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[23:32:38]   /usr/bin/w.procps                               [ OK ]
[23:32:38]   /sbin/depmod                                    [ OK ]
[23:32:38]   /sbin/fsck                                      [ OK ]
[23:32:39]   /sbin/ifconfig                                  [ OK ]
[23:32:39]   /sbin/ifdown                                    [ OK ]
[23:32:39]   /sbin/ifup                                      [ OK ]
[23:32:39]   /sbin/init                                      [ OK ]
[23:32:39]   /sbin/insmod                                    [ OK ]
[23:32:39]   /sbin/ip                                        [ OK ]
[23:32:39]   /sbin/lsmod                                     [ OK ]
[23:32:39]   /sbin/modinfo                                   [ OK ]
[23:32:39]   /sbin/modprobe                                  [ OK ]
[23:32:39]   /sbin/rmmod                                     [ OK ]
[23:32:39]   /sbin/route                                     [ OK ]
[23:32:39]   /sbin/runlevel                                  [ OK ]
[23:32:39]   /sbin/sulogin                                   [ OK ]
[23:32:40]   /sbin/sysctl                                    [ OK ]
[23:32:40]   /bin/bash                                       [ OK ]
[23:32:40]   /bin/cat                                        [ OK ]
[23:32:40]   /bin/chmod                                      [ OK ]
[23:32:40]   /bin/chown                                      [ OK ]
[23:32:40]   /bin/cp                                         [ OK ]
[23:32:40]   /bin/date                                       [ OK ]
[23:32:40]   /bin/df                                         [ OK ]
[23:32:40]   /bin/dmesg                                      [ OK ]
[23:32:40]   /bin/echo                                       [ OK ]
[23:32:40]   /bin/ed                                         [ OK ]
[23:32:40]   /bin/egrep                                      [ OK ]
[23:32:40] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[23:32:40]   /bin/fgrep                                      [ OK ]
[23:32:40] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[23:32:40]   /bin/fuser                                      [ OK ]
[23:32:40]   /bin/grep                                       [ OK ]
[23:32:41]   /bin/ip                                         [ OK ]
[23:32:41]   /bin/kill                                       [ OK ]
[23:32:41]   /bin/less                                       [ OK ]
[23:32:41]   /bin/login                                      [ OK ]
[23:32:41]   /bin/ls                                         [ OK ]
[23:32:41]   /bin/lsmod                                      [ OK ]
[23:32:41]   /bin/mktemp                                     [ OK ]
[23:32:41]   /bin/more                                       [ OK ]
[23:32:41]   /bin/mount                                      [ OK ]
[23:32:41]   /bin/mv                                         [ OK ]
[23:32:41]   /bin/netstat                                    [ OK ]
[23:32:41]   /bin/ping                                       [ OK ]
[23:32:41]   /bin/ps                                         [ OK ]
[23:32:41]   /bin/pwd                                        [ OK ]
[23:32:41]   /bin/readlink                                   [ OK ]
[23:32:41]   /bin/sed                                        [ OK ]
[23:32:41]   /bin/sh                                         [ OK ]
[23:32:42]   /bin/su                                         [ OK ]
[23:32:42]   /bin/touch                                      [ OK ]
[23:32:42]   /bin/uname                                      [ OK ]
[23:32:42]   /bin/which                                      [ OK ]
[23:32:42] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[23:32:42]   /bin/kmod                                       [ OK ]
[23:32:42]   /bin/dash                                       [ OK ]
[23:32:47]
[23:32:47] Info: Starting test name 'rootkits'
[23:32:47] Checking for rootkits...
[23:32:47]
[23:32:47] Info: Starting test name 'known_rkts'
[23:32:47] Performing check of known rootkit files and directories
[23:32:47]
[23:32:47] Checking for 55808 Trojan - Variant A...
[23:32:47]   Checking for file '/tmp/.../r'                  [ Not found ]
[23:32:47]   Checking for file '/tmp/.../a'                  [ Not found ]
[23:32:47] 55808 Trojan - Variant A                          [ Not found ]
[23:32:47]
[23:32:47] Checking for ADM Worm...
[23:32:47]   Checking for string 'w0rm'                      [ Not found ]
[23:32:47] ADM Worm                                          [ Not found ]
[23:32:47]
[23:32:47] Checking for AjaKit Rootkit...
[23:32:47]   Checking for file '/dev/tux/.addr'              [ Not found ]
[23:32:47]   Checking for file '/dev/tux/.proc'              [ Not found ]
[23:32:47]   Checking for file '/dev/tux/.file'              [ Not found ]
[23:32:47]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[23:32:47]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[23:32:47]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[23:32:47]   Checking for directory '/dev/tux'               [ Not found ]
[23:32:47]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[23:32:47] AjaKit Rootkit                                    [ Not found ]
[23:32:47]
[23:32:47] Checking for Adore Rootkit...
[23:32:47]   Checking for file '/usr/secure'                 [ Not found ]
[23:32:47]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[23:32:47]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[23:32:47]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[23:32:47]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[23:32:47]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[23:32:47]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[23:32:47]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[23:32:47]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[23:32:47]   Checking for file '/var/log/ssh/old'            [ Not found ]
[23:32:47]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/kern'          [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/backup'        [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[23:32:47]   Checking for directory '/lib/backup'            [ Not found ]
[23:32:47]   Checking for directory '/lib/backup/txt'        [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/work'          [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/sys'           [ Not found ]
[23:32:47]   Checking for directory '/var/log/ssh'           [ Not found ]
[23:32:47]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[23:32:47]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[23:32:47] Adore Rootkit                                     [ Not found ]
[23:32:47]
[23:32:47] Checking for aPa Kit...
[23:32:47]   Checking for file '/usr/share/.aPa'             [ Not found ]
[23:32:47] aPa Kit                                           [ Not found ]
[23:32:47]
[23:32:47] Checking for Apache Worm...
[23:32:47]   Checking for file '/bin/.log'                   [ Not found ]
[23:32:47] Apache Worm                                       [ Not found ]
[23:32:47]
[23:32:47] Checking for Ambient (ark) Rootkit...
[23:32:47]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[23:32:47]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[23:32:47]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[23:32:47]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[23:32:47]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[23:32:47]   Checking for directory '/dev/ptyxx'             [ Not found ]
[23:32:47] Ambient (ark) Rootkit                             [ Not found ]
[23:32:47]
[23:32:47] Checking for Balaur Rootkit...
[23:32:48]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[23:32:48] Balaur Rootkit                                    [ Not found ]
[23:32:48]
[23:32:48] Checking for BeastKit Rootkit...
[23:32:48]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[23:32:48]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[23:32:48]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[23:32:48] BeastKit Rootkit                                  [ Not found ]
[23:32:48]
[23:32:48] Checking for beX2 Rootkit...
[23:32:48]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[23:32:48]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[23:32:48]   Checking for directory '/usr/include/bex'       [ Not found ]
[23:32:48] beX2 Rootkit                                      [ Not found ]
[23:32:48]
[23:32:48] Checking for BOBKit Rootkit...
[23:32:48]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[23:32:48]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[23:32:48]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[23:32:48]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[23:32:48]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[23:32:48]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../find'           [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../du'             [ Not found ]
[23:32:48]   Checking for file '/usr/lib/.../top'            [ Not found ]
[23:32:48]   Checking for directory '/usr/sbin/...'          [ Not found ]
[23:32:48]   Checking for directory '/usr/include/...'       [ Not found ]
[23:32:48]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/...'           [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[23:32:48]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[23:32:48]   Checking for directory '/tmp/.bkp'              [ Not found ]
[23:32:48] BOBKit Rootkit                                    [ Not found ]
[23:32:48]
[23:32:48] Checking for cb Rootkit...
[23:32:48]   Checking for file '/dev/srd0'                   [ Not found ]
[23:32:48]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[23:32:48]   Checking for file '/dev/mounnt'                 [ Not found ]
[23:32:48]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /cl'       [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /.x.tgz'   [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /statdx'   [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /wted'     [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /write'    [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /scan'     [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /sc'       [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /sl2'      [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /wroot'    [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /wscan'    [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /wu'       [ Not found ]
[23:32:48]   Checking for file '/usr/bin/.zeen/.. /v'        [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.zeen/.. /read'     [ Not found ]
[23:32:49]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[23:32:49]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[23:32:49]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[23:32:49]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[23:32:49]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[23:32:49]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[23:32:49]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[23:32:49]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.system/.. /tcp.log' [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.zeen/.. /curatare/attrib' [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.zeen/.. /curatare/chattr' [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.zeen/.. /curatare/ps' [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.zeen/.. /curatare/pstree' [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.system/.. /.x/xC.o' [ Not found ]
[23:32:49]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[23:32:49]   Checking for directory '/usr/bin/.zeen/.. /curatare' [ Not found ]
[23:32:49]   Checking for directory '/usr/bin/.zeen/.. /scan' [ Not found ]
[23:32:49]   Checking for directory '/usr/bin/.system/.. '   [ Not found ]
[23:32:49] cb Rootkit                                        [ Not found ]
[23:32:49]
[23:32:49] Checking for CiNIK Worm (Slapper.B variant)...
[23:32:49]   Checking for file '/tmp/.cinik'                 [ Not found ]
[23:32:49]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[23:32:49] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[23:32:49]
[23:32:49] Checking for Danny-Boy's Abuse Kit...
[23:32:49]   Checking for file '/dev/mdev'                   [ Not found ]
[23:32:49]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[23:32:49] Danny-Boy's Abuse Kit                             [ Not found ]
[23:32:49]
[23:32:49] Checking for Devil RootKit...
[23:32:49]   Checking for file '/var/lib/games/.src'         [ Not found ]
[23:32:49]   Checking for file '/dev/dsx'                    [ Not found ]
[23:32:49]   Checking for file '/dev/caca'                   [ Not found ]
[23:32:49]   Checking for file '/dev/pro'                    [ Not found ]
[23:32:49]   Checking for file '/bin/bye'                    [ Not found ]
[23:32:49]   Checking for file '/bin/homedir'                [ Not found ]
[23:32:49]   Checking for file '/usr/bin/xfss'               [ Not found ]
[23:32:49]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[23:32:49]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[23:32:49]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[23:32:49] Devil RootKit                                     [ Not found ]
[23:32:49]
[23:32:49] Checking for Dica-Kit Rootkit...
[23:32:49]   Checking for file '/lib/.sso'                   [ Not found ]
[23:32:49]   Checking for file '/lib/.so'                    [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/read'       [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/write'      [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/va'         [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[23:32:49]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[23:32:49]   Checking for file '/usr/bin/.etc'               [ Not found ]
[23:32:49]   Checking for file '/etc/sshd_config'            [ Not found ]
[23:32:49]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[23:32:50]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[23:32:50]   Checking for directory '/var/run/...dica'       [ Not found ]
[23:32:50]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[23:32:50]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[23:32:50] Dica-Kit Rootkit                                  [ Not found ]
[23:32:50]
[23:32:50] Checking for Dreams Rootkit...
[23:32:50]   Checking for file '/dev/ttyoa'                  [ Not found ]
[23:32:50]   Checking for file '/dev/ttyof'                  [ Not found ]
[23:32:50]   Checking for file '/dev/ttyop'                  [ Not found ]
[23:32:50]   Checking for file '/usr/bin/sense'              [ Not found ]
[23:32:50]   Checking for file '/usr/bin/sl2'                [ Not found ]
[23:32:50]   Checking for file '/usr/bin/logclear'           [ Not found ]
[23:32:50]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[23:32:50]   Checking for file '/usr/bin/initrd'             [ Not found ]
[23:32:50]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[23:32:50]   Checking for file '/usr/bin/snfs'               [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libsss'             [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[23:32:50]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[23:32:50]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[23:32:50]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[23:32:50]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[23:32:50]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[23:32:50]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[23:32:50]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[23:32:50]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[23:32:50]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[23:32:50]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[23:32:50]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[23:32:50] Dreams Rootkit                                    [ Not found ]
[23:32:50]
[23:32:50] Checking for Duarawkz Rootkit...
[23:32:50]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[23:32:50]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[23:32:50] Duarawkz Rootkit                                  [ Not found ]
[23:32:50]
[23:32:50] Checking for Enye LKM...
[23:32:50]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[23:32:50]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[23:32:50] Enye LKM                                          [ Not found ]
[23:32:50]
[23:32:50] Checking for Flea Linux Rootkit...
[23:32:50]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[23:32:50]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[23:32:50]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[23:32:50]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[23:32:50]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[23:32:50]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[23:32:50]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[23:32:50]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[23:32:50]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[23:32:50]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[23:32:50]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[23:32:50]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[23:32:50]   Checking for directory '/dev/..0'               [ Not found ]
[23:32:50]   Checking for directory '/dev/..0/backup'        [ Not found ]
[23:32:50] Flea Linux Rootkit                                [ Not found ]
[23:32:50]
[23:32:50] Checking for Fu Rootkit...
[23:32:50]   Checking for file '/sbin/xc'                    [ Not found ]
[23:32:50]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[23:32:50]   Checking for file '/bin/.lib'                   [ Not found ]
[23:32:50] Fu Rootkit                                        [ Not found ]
[23:32:50]
[23:32:50] Checking for ****`it Rootkit...
[23:32:50]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[23:32:50]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[23:32:50]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[23:32:50]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/hax0r'      [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/hax0rshell' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/config/lports' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/config/rports' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/config/rkconf' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/config/password' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/config/progs' [ Not found ]
[23:32:50]   Checking for file '/dev/proc/****it/system-bins/init' [ Not found ]
[23:32:51]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[23:32:51]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[23:32:51]   Checking for directory '/dev/proc'              [ Not found ]
[23:32:51]   Checking for directory '/dev/proc/****it'       [ Not found ]
[23:32:51]   Checking for directory '/dev/proc/****it/system-bins' [ Not found ]
[23:32:51]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[23:32:51] ****`it Rootkit                                   [ Not found ]
[23:32:51]
[23:32:51] Checking for GasKit Rootkit...
[23:32:51]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[23:32:51]   Checking for directory '/dev/dev'               [ Not found ]
[23:32:51]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[23:32:51]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[23:32:51] GasKit Rootkit                                    [ Not found ]
[23:32:51]
[23:32:51] Checking for Heroin LKM...
[23:32:51]   Checking for kernel symbol 'heroin'             [ Not found ]
[23:32:51] Heroin LKM                                        [ Not found ]
[23:32:51]
[23:32:51] Checking for HjC Kit...
[23:32:51]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[23:32:51] HjC Kit                                           [ Not found ]
[23:32:51]
[23:32:51] Checking for ignoKit Rootkit...
[23:32:51]   Checking for file '/lib/defs/p'                 [ Not found ]
[23:32:51]   Checking for file '/lib/defs/q'                 [ Not found ]
[23:32:51]   Checking for file '/lib/defs/r'                 [ Not found ]
[23:32:51]   Checking for file '/lib/defs/s'                 [ Not found ]
[23:32:51]   Checking for file '/lib/defs/t'                 [ Not found ]
[23:32:51]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[23:32:51]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[23:32:51]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[23:32:51]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[23:32:51]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[23:32:51]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[23:32:51]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[23:32:51]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[23:32:51]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[23:32:51] ignoKit Rootkit                                   [ Not found ]
[23:32:51]
[23:32:51] Checking for IntoXonia-NG Rootkit...
[23:32:51]   Checking for kernel symbol 'funces'             [ Not found ]
[23:32:51]   Checking for kernel symbol 'ixinit'             [ Not found ]
[23:32:51]   Checking for kernel symbol 'tricks'             [ Not found ]
[23:32:51]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[23:32:51]   Checking for kernel symbol 'rootme'             [ Not found ]
[23:32:51]   Checking for kernel symbol 'hide_module'        [ Not found ]
[23:32:52]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[23:32:52] IntoXonia-NG Rootkit                              [ Not found ]
[23:32:52]
[23:32:52] Checking for Irix Rootkit...
[23:32:52]   Checking for directory '/dev/pts/01'            [ Not found ]
[23:32:52]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[23:32:52]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[23:32:52]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[23:32:52] Irix Rootkit                                      [ Not found ]
[23:32:52]
[23:32:52] Checking for Jynx Rootkit...
[23:32:52]   Checking for file '/xochikit/bc'                [ Not found ]
[23:32:52]   Checking for file '/xochikit/ld_poison.so'      [ Not found ]
[23:32:52]   Checking for file '/omgxochi/bc'                [ Not found ]
[23:32:52]   Checking for file '/omgxochi/ld_poison.so'      [ Not found ]
[23:32:52]   Checking for directory '/xochikit'              [ Not found ]
[23:32:52]   Checking for directory '/omgxochi'              [ Not found ]
[23:32:52] Jynx Rootkit                                      [ Not found ]
[23:32:52]
[23:32:52] Checking for KBeast Rootkit...
[23:32:52]   Checking for file '/usr/_h4x_/ipsecs-kbeast-v1.ko' [ Not found ]
[23:32:52]   Checking for file '/usr/_h4x_/_h4x_bd'          [ Not found ]
[23:32:52]   Checking for file '/usr/_h4x_/acctlog'          [ Not found ]
[23:32:52]   Checking for directory '/usr/_h4x_'             [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_delete_module'  [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_getdents64'     [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_kill'           [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_open'           [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_read'           [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_rename'         [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_rmdir'          [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_tcp4_seq_show'  [ Not found ]
[23:32:52]   Checking for kernel symbol 'h4x_write'          [ Not found ]
[23:32:52] KBeast Rootkit                                    [ Not found ]
[23:32:52]
[23:32:52] Checking for Kitko Rootkit...
[23:32:52]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[23:32:52] Kitko Rootkit                                     [ Not found ]
[23:32:52]
[23:32:52] Checking for Knark Rootkit...
[23:32:52]   Checking for file '/proc/knark/pids'            [ Not found ]
[23:32:52]   Checking for directory '/proc/knark'            [ Not found ]
[23:32:52] Knark Rootkit                                     [ Not found ]
[23:32:53]
[23:32:53] Checking for ld-linuxv.so Rootkit...
[23:32:53]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[23:32:53]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[23:32:53]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[23:32:53]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[23:32:53] ld-linuxv.so Rootkit                              [ Not found ]
[23:32:53]
[23:32:53] Checking for Li0n Worm...
[23:32:53]   Checking for file '/bin/in.telnetd'             [ Not found ]
[23:32:53]   Checking for file '/bin/mjy'                    [ Not found ]
[23:32:53]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[23:32:53]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[23:32:53]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[23:32:53]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[23:32:53] Li0n Worm                                         [ Not found ]
[23:32:53]
[23:32:53] Checking for Lockit / LJK2 Rootkit...
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[23:32:53]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[23:32:53]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[23:32:53] Lockit / LJK2 Rootkit                             [ Not found ]
[23:32:53]
[23:32:53] Checking for Mood-NT Rootkit...
[23:32:53]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[23:32:53]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[23:32:53]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[23:32:53]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[23:32:53]   Checking for directory '/_cthulhu'              [ Not found ]
[23:32:53] Mood-NT Rootkit                                   [ Not found ]
[23:32:53]
[23:32:53] Checking for MRK Rootkit...
[23:32:53]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[23:32:53]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[23:32:53]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[23:32:53]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[23:32:53]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[23:32:54]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[23:32:54] MRK Rootkit                                       [ Not found ]
[23:32:54]
[23:32:54] Checking for Ni0 Rootkit...
[23:32:54]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[23:32:54]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[23:32:54]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[23:32:54]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[23:32:54]   Checking for directory '/tmp/waza'              [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[23:32:54]   Checking for directory '/usr/sbin/es'           [ Not found ]
[23:32:54] Ni0 Rootkit                                       [ Not found ]
[23:32:54]
[23:32:54] Checking for Ohhara Rootkit...
[23:32:54]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[23:32:54]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[23:32:54] Ohhara Rootkit                                    [ Not found ]
[23:32:54]
[23:32:54] Checking for Optic Kit (Tux) Worm...
[23:32:54]   Checking for directory '/dev/tux'               [ Not found ]
[23:32:54]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[23:32:54]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[23:32:54]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[23:32:54] Optic Kit (Tux) Worm                              [ Not found ]
[23:32:54]
[23:32:54] Checking for Oz Rootkit...
[23:32:54]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[23:32:54]   Checking for directory '/dev/.oz'               [ Not found ]
[23:32:54] Oz Rootkit                                        [ Not found ]
[23:32:54]
[23:32:54] Checking for Phalanx Rootkit...
[23:32:54]   Checking for file '/uNFuNF'                     [ Not found ]
[23:32:54]   Checking for file '/etc/host.ph1'               [ Not found ]
[23:32:54]   Checking for file '/bin/host.ph1'               [ Not found ]
[23:32:54]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[23:32:54]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[23:32:54]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[23:32:54]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[23:32:54]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[23:32:54] Phalanx Rootkit                                   [ Not found ]
[23:32:54]
[23:32:54] Checking for Phalanx2 Rootkit...
[23:32:54]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[23:32:54]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[23:32:54]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[23:32:54]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[23:32:54]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[23:32:54]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[23:32:54]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[23:32:54]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[23:32:54]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[23:32:54]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[23:32:54]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[23:32:54]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[23:32:54]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[23:32:54]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[23:32:54] Phalanx2 Rootkit                                  [ Not found ]
[23:32:54]
[23:32:54] Checking for Phalanx2 Rootkit (extended tests)...
[23:32:54]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[23:32:54]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[23:32:54]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[23:32:54] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[23:32:54]
[23:32:54] Checking for Portacelo Rootkit...
[23:32:54]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../.p'             [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../getty'          [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../show'           [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[23:32:54]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[23:32:55]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[23:32:55]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[23:32:55] Portacelo Rootkit                                 [ Not found ]
[23:32:55]
[23:32:55] Checking for R3dstorm Toolkit...
[23:32:55]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[23:32:55]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[23:32:55]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[23:32:55]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[23:32:55]   Checking for file '/bin/.../see_all'            [ Not found ]
[23:32:55]   Checking for directory '/var/log/tk02'          [ Not found ]
[23:32:55]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[23:32:55]   Checking for directory '/bin/...'               [ Not found ]
[23:32:55] R3dstorm Toolkit                                  [ Not found ]
[23:32:55]
[23:32:55] Checking for RH-Sharpe's Rootkit...
[23:32:55]   Checking for file '/bin/lps'                    [ Not found ]
[23:32:55]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[23:32:55]   Checking for file '/usr/bin/ltop'               [ Not found ]
[23:32:55]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[23:32:55]   Checking for file '/usr/bin/ldu'                [ Not found ]
[23:32:55]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[23:32:55]   Checking for file '/usr/bin/wp'                 [ Not found ]
[23:32:55]   Checking for file '/usr/bin/shad'               [ Not found ]
[23:32:55]   Checking for file '/usr/bin/vadim'              [ Not found ]
[23:32:55]   Checking for file '/usr/bin/slice'              [ Not found ]
[23:32:55]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[23:32:55]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[23:32:55] RH-Sharpe's Rootkit                               [ Not found ]
[23:32:55]
[23:32:55] Checking for RSHA's Rootkit...
[23:32:55]   Checking for file '/bin/kr4p'                   [ Not found ]
[23:32:55]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[23:32:55]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[23:32:55]   Checking for file '/usr/bin/slice2'             [ Not found ]
[23:32:55]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[23:32:55]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[23:32:55]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[23:32:55]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[23:32:55] RSHA's Rootkit                                    [ Not found ]
[23:32:55]
[23:32:55] Checking for Scalper Worm...
[23:32:55]   Checking for file '/tmp/.a'                     [ Not found ]
[23:32:55]   Checking for file '/tmp/.uua'                   [ Not found ]
[23:32:55] Scalper Worm                                      [ Not found ]
[23:32:55]
[23:32:55] Checking for Sebek LKM...
[23:32:55]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[23:32:55] Sebek LKM                                         [ Not found ]
[23:32:56]
[23:32:56] Checking for Shutdown Rootkit...
[23:32:56]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[23:32:56]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[23:32:56]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[23:32:56]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[23:32:56]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[23:32:56]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[23:32:56]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[23:32:56]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[23:32:56] Shutdown Rootkit                                  [ Not found ]
[23:32:56]
[23:32:56] Checking for SHV4 Rootkit...
[23:32:56]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[23:32:56]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[23:32:56]   Checking for file '/lib/lidps1.so'              [ Not found ]
[23:32:56]   Checking for file '/lib/libproc.a'              [ Not found ]
[23:32:56]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[23:32:56]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[23:32:56]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[23:32:56]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[23:32:56]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[23:32:56]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[23:32:56]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[23:32:56]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[23:32:56]   Checking for file '/usr/include/file.h'         [ Not found ]
[23:32:56]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[23:32:56]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[23:32:56]   Checking for file '/usr/include/log.h'          [ Not found ]
[23:32:56]   Checking for file '/usr/include/proc.h'         [ Not found ]
[23:32:56]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[23:32:56]   Checking for file '/dev/srd0'                   [ Not found ]
[23:32:56]   Checking for directory '/lib/ldd.so'            [ Not found ]
[23:32:56]   Checking for directory '/lib/security/.config'  [ Not found ]
[23:32:56]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[23:32:56] SHV4 Rootkit                                      [ Not found ]
[23:32:56]
[23:32:56] Checking for SHV5 Rootkit...
[23:32:56]   Checking for file '/etc/sh.conf'                [ Not found ]
[23:32:56]   Checking for file '/lib/libproc.a'              [ Not found ]
[23:32:56]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[23:32:56]   Checking for file '/lib/lidps1.so'              [ Not found ]
[23:32:56]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[23:32:56]   Checking for file '/usr/include/file.h'         [ Not found ]
[23:32:56]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[23:32:56]   Checking for file '/usr/include/log.h'          [ Not found ]
[23:32:56]   Checking for file '/usr/include/proc.h'         [ Not found ]
[23:32:56]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[23:32:56]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[23:32:56]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[23:32:56]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[23:32:56]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[23:32:56]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[23:32:56]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[23:32:56]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[23:32:56]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[23:32:56]   Checking for file '/dev/srd0'                   [ Not found ]
[23:32:56]   Checking for directory '/lib/libsh.so'          [ Not found ]
[23:32:56]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[23:32:56]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[23:32:56]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[23:32:56] SHV5 Rootkit                                      [ Not found ]
[23:32:56]
[23:32:56] Checking for Sin Rootkit...
[23:32:56]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[23:32:56]   Checking for file '/dev/ttyoa'                  [ Not found ]
[23:32:56]   Checking for file '/dev/ttyof'                  [ Not found ]
[23:32:56]   Checking for file '/dev/ttyop'                  [ Not found ]
[23:32:56]   Checking for file '/dev/ttyos'                  [ Not found ]
[23:32:56]   Checking for file '/usr/lib/.lib'               [ Not found ]
[23:32:56]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[23:32:56]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[23:32:56]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[23:32:56]   Checking for file '/usr/man/man1/...'           [ Not found ]
[23:32:56]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[23:32:56]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[23:32:56]   Checking for directory '/usr/lib/sn'            [ Not found ]
[23:32:57]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[23:32:57]   Checking for directory '/dev/.haos'             [ Not found ]
[23:32:57] Sin Rootkit                                       [ Not found ]
[23:32:57]
[23:32:57] Checking for Slapper Worm...
[23:32:57]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[23:32:57]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[23:32:57]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[23:32:57]   Checking for file '/tmp/httpd'                  [ Not found ]
[23:32:57]   Checking for file '/tmp/.unlock'                [ Not found ]
[23:32:57]   Checking for file '/tmp/update'                 [ Not found ]
[23:32:57]   Checking for file '/tmp/.cinik'                 [ Not found ]
[23:32:57]   Checking for file '/tmp/.b'                     [ Not found ]
[23:32:57] Slapper Worm                                      [ Not found ]
[23:32:57]
[23:32:57] Checking for Sneakin Rootkit...
[23:32:57]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[23:32:57] Sneakin Rootkit                                   [ Not found ]
[23:32:57]
[23:32:57] Checking for 'Spanish' Rootkit...
[23:32:57]   Checking for file '/dev/ptyq'                   [ Not found ]
[23:32:57]   Checking for file '/bin/ad'                     [ Not found ]
[23:32:57]   Checking for file '/bin/ava'                    [ Not found ]
[23:32:57]   Checking for file '/bin/server'                 [ Not found ]
[23:32:57]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[23:32:57]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[23:32:57]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[23:32:57]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[23:32:57]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[23:32:57]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[23:32:57]   Checking for directory '/usr/share/...'         [ Not found ]
[23:32:57] 'Spanish' Rootkit                                 [ Not found ]
[23:32:57]
[23:32:57] Checking for Suckit Rootkit...
[23:32:57]   Checking for file '/sbin/initsk12'              [ Not found ]
[23:32:57]   Checking for file '/sbin/initxrk'               [ Not found ]
[23:32:57]   Checking for file '/usr/bin/null'               [ Not found ]
[23:32:57]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[23:32:57]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[23:32:57]   Checking for directory '/etc/.MG'               [ Not found ]
[23:32:57]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[23:32:57]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[23:32:57] Suckit Rootkit                                    [ Not found ]
[23:32:57]
[23:32:57] Checking for Superkit Rootkit...
[23:32:57]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[23:32:57]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[23:32:57]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[23:32:57]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[23:32:57]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[23:32:57] Superkit Rootkit                                  [ Not found ]
[23:32:57]
[23:32:57] Checking for TBD (Telnet BackDoor)...
[23:32:57]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[23:32:57] TBD (Telnet BackDoor)                             [ Not found ]
[23:32:57]
[23:32:57] Checking for TeLeKiT Rootkit...
[23:32:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[23:32:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[23:32:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[23:32:57]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[23:32:57]   Checking for file '/dev/ptyr'                   [ Not found ]
[23:32:57]   Checking for file '/dev/ptyp'                   [ Not found ]
[23:32:57]   Checking for file '/dev/ptyq'                   [ Not found ]
[23:32:57]   Checking for file '/dev/hda06'                  [ Not found ]
[23:32:57]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[23:32:57]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[23:32:57]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[23:32:57]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[23:32:57] TeLeKiT Rootkit                                   [ Not found ]
[23:32:58]
[23:32:58] Checking for T0rn Rootkit...
[23:32:58]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[23:32:58]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[23:32:58]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[23:32:58]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[23:32:58]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[23:32:58]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[23:32:58]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[23:32:58]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[23:32:58]   Checking for directory '/dev/.lib'              [ Not found ]
[23:32:58]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[23:32:58]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[23:32:58]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[23:32:58]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[23:32:58]   Checking for directory '/usr/src/.puta'         [ Not found ]
[23:32:58]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[23:32:58]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[23:32:58]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[23:32:58]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[23:32:58] T0rn Rootkit                                      [ Not found ]
[23:32:58]
[23:32:58] Checking for trNkit Rootkit...
[23:32:58]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[23:32:58]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[23:32:58]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[23:32:58] trNkit Rootkit                                    [ Not found ]
[23:32:58]
[23:32:58] Checking for Trojanit Kit...
[23:32:58]   Checking for file '/bin/.ls'                    [ Not found ]
[23:32:58]   Checking for file '/bin/.ps'                    [ Not found ]
[23:32:58]   Checking for file '/bin/.netstat'               [ Not found ]
[23:32:58]   Checking for file '/usr/bin/.nop'               [ Not found ]
[23:32:58]   Checking for file '/usr/bin/.who'               [ Not found ]
[23:32:58] Trojanit Kit                                      [ Not found ]
[23:32:58]
[23:32:58] Checking for Tuxtendo Rootkit...
[23:32:58]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[23:32:58]   Checking for file '/usr/bin/xchk'               [ Not found ]
[23:32:58]   Checking for file '/usr/bin/xsf'                [ Not found ]
[23:32:58]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.addr'              [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.cron'              [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.file'              [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.log'               [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.proc'              [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.iface'             [ Not found ]
[23:32:58]   Checking for file '/dev/tux/.pw'                [ Not found ]
[23:32:59]   Checking for file '/dev/tux/.df'                [ Not found ]
[23:32:59]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[23:32:59]   Checking for file '/dev/tux/.tux'               [ Not found ]
[23:32:59]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[23:32:59]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[23:32:59]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[23:32:59]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[23:32:59]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[23:32:59]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[23:32:59]   Checking for directory '/dev/tux'               [ Not found ]
[23:32:59]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[23:32:59]   Checking for directory '/dev/tux/backup'        [ Not found ]
[23:32:59] Tuxtendo Rootkit                                  [ Not found ]
[23:32:59]
[23:32:59] Checking for URK Rootkit...
[23:32:59]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[23:32:59]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[23:32:59]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[23:32:59]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[23:32:59]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[23:32:59]   Checking for file '/tmp/conf.inv'               [ Not found ]
[23:32:59]   Checking for directory '/dev/prom'              [ Not found ]
[23:32:59]   Checking for directory '/dev/pts/01'            [ Not found ]
[23:32:59]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[23:32:59]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[23:32:59] URK Rootkit                                       [ Not found ]
[23:32:59]
[23:32:59] Checking for Vampire Rootkit...
[23:32:59]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[23:32:59]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[23:33:00]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[23:33:00]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[23:33:00] Vampire Rootkit                                   [ Not found ]
[23:33:00]
[23:33:00] Checking for VcKit Rootkit...
[23:33:00]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[23:33:00]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[23:33:00] VcKit Rootkit                                     [ Not found ]
[23:33:00]
[23:33:00] Checking for Volc Rootkit...
[23:33:00]   Checking for file '/usr/bin/volc'               [ Not found ]
[23:33:00]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[23:33:00]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[23:33:00]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[23:33:00]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[23:33:00]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[23:33:00]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[23:33:00]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[23:33:00]   Checking for directory '/var/spool/.recent'     [ Not found ]
[23:33:00]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[23:33:00]   Checking for directory '/usr/lib/volc'          [ Not found ]
[23:33:00]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[23:33:00] Volc Rootkit                                      [ Not found ]
[23:33:00]
[23:33:00] Checking for Xzibit Rootkit...
[23:33:00]   Checking for file '/dev/dsx'                    [ Not found ]
[23:33:00]   Checking for file '/dev/caca'                   [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[23:33:00]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[23:33:00]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[23:33:00]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[23:33:00]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[23:33:00]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[23:33:00]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[23:33:00]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[23:33:00] Xzibit Rootkit                                    [ Not found ]
[23:33:00]
[23:33:00] Checking for zaRwT.KiT Rootkit...
[23:33:00]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[23:33:00]   Checking for file '/dev/ttyf'                   [ Not found ]
[23:33:00]   Checking for file '/dev/ttyp'                   [ Not found ]
[23:33:00]   Checking for file '/dev/ttyn'                   [ Not found ]
[23:33:00]   Checking for file '/rk/tulz'                    [ Not found ]
[23:33:00]   Checking for directory '/rk'                    [ Not found ]
[23:33:00]   Checking for directory '/dev/rd/s'              [ Not found ]
[23:33:00] zaRwT.KiT Rootkit                                 [ Not found ]
[23:33:00]
[23:33:00] Checking for ZK Rootkit...
[23:33:00]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[23:33:00]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[23:33:00]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[23:33:00]   Checking for file '/etc/1ssue.net'              [ Not found ]
[23:33:00]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[23:33:00]   Checking for directory '/usr/share/.zk'         [ Not found ]
[23:33:00]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[23:33:00] ZK Rootkit                                        [ Not found ]
[23:33:02]
[23:33:02] Info: Starting test name 'additional_rkts'
[23:33:02] Performing additional rootkit checks
[23:33:02]
[23:33:02]   Performing Suckit Rookit additional checks
[23:33:02]     Checking hard link count on '/sbin/init'      [ OK ]
[23:33:02]     Checking for hidden file extensions           [ None found ]
[23:33:02]     Running skdet command                         [ Skipped ]
[23:33:02] Info: Unable to find the 'skdet' command
[23:33:02]   Suckit Rookit additional checks                 [ OK ]
[23:33:02]
[23:33:02] Info: Starting test name 'possible_rkt_files'
[23:33:02]   Performing check of possible rootkit files and directories
[23:33:02]     Checking for file '/dev/sdr0'                 [ Not found ]
[23:33:02]     Checking for file '/dev/pisu'                 [ Not found ]
[23:33:02]     Checking for file '/dev/xdta'                 [ Not found ]
[23:33:02]     Checking for file '/dev/saux'                 [ Not found ]
[23:33:02]     Checking for file '/dev/hdx'                  [ Not found ]
[23:33:02]     Checking for file '/dev/hdx1'                 [ Not found ]
[23:33:02]     Checking for file '/dev/hdx2'                 [ Not found ]
[23:33:02]     Checking for file '/dev/ptyy'                 [ Not found ]
[23:33:02]     Checking for file '/dev/ptyu'                 [ Not found ]
[23:33:02]     Checking for file '/dev/ptyv'                 [ Not found ]
[23:33:02]     Checking for file '/dev/hdbb'                 [ Not found ]
[23:33:02]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[23:33:02]     Checking for file '/tmp/.bash_history'        [ Not found ]
[23:33:02]     Checking for file '/usr/info/.clib'           [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[23:33:03]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[23:33:03]     Checking for file '/sbin/create'              [ Not found ]
[23:33:03]     Checking for file '/dev/ttypz'                [ Not found ]
[23:33:03]     Checking for file '/var/log/tcp.log'          [ Not found ]
[23:33:03]     Checking for file '/usr/include/audit.h'      [ Not found ]
[23:33:03]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[23:33:03]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[23:33:03]     Checking for file '/dev/xmx'                  [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[23:33:03]     Checking for file '/bin/vobiscum'             [ Not found ]
[23:33:03]     Checking for file '/bin/psr'                  [ Not found ]
[23:33:03]     Checking for file '/dev/kdx'                  [ Not found ]
[23:33:03]     Checking for file '/dev/dkx'                  [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[23:33:03]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[23:33:03]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[23:33:03]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[23:33:03]     Checking for file '/tmp/.ush'                 [ Not found ]
[23:33:03]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[23:33:03]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[23:33:03]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[23:33:03]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[23:33:03]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[23:33:03]     Checking for file '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:03]     Checking for file '/etc/init.d/xfs3'          [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/t.txt'           [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/change'          [ Not found ]
[23:33:03]     Checking for file '/usr/sbin/s'               [ Not found ]
[23:33:03]     Checking for file '/bin/f'                    [ Not found ]
[23:33:03]     Checking for file '/bin/i'                    [ Not found ]
[23:33:03]     Checking for file '/lib/libncom.so.4.0.1'     [ Not found ]
[23:33:03]     Checking for file '/sbin/zinit'               [ Not found ]
[23:33:03]     Checking for file '/tmp/pass_ssh.log'         [ Not found ]
[23:33:03]     Checking for file '/usr/include/gpm2.h'       [ Not found ]
[23:33:03]     Checking for file '/etc/ssh/.sshd_auth'       [ Not found ]
[23:33:03]     Checking for file '/usr/lib/.sshd.h'          [ Not found ]
[23:33:03]     Checking for file '/var/run/.defunct'         [ Not found ]
[23:33:03]     Checking for file '/etc/httpd/run/.defunct'   [ Not found ]
[23:33:03]     Checking for file '/usr/share/pci.r'          [ Not found ]
[23:33:03]     Checking for file '/etc/cron.daily/dnsquery'  [ Not found ]
[23:33:03]     Checking for file '/usr/lib/libutil1.2.1.2.so' [ Not found ]
[23:33:03]     Checking for file '/bin/ceva'                 [ Not found ]
[23:33:03]     Checking for file '/sbin/syslogd '            [ Not found ]
[23:33:03]     Checking for file '/usr/include/shup.h'       [ Not found ]
[23:33:03]     Checking for file '/etc/rpm/sshdOLD'          [ Not found ]
[23:33:03]     Checking for file '/etc/rpm/sshOLD'           [ Not found ]
[23:33:04]     Checking for file '/usr/share/passwd.h'       [ Not found ]
[23:33:04]     Checking for file '/lib/.xsyslog'             [ Not found ]
[23:33:04]     Checking for file '/etc/.xsyslog'             [ Not found ]
[23:33:04]     Checking for file '/lib/.ssyslog'             [ Not found ]
[23:33:04]     Checking for file '/tmp/.sendmail'            [ Not found ]
[23:33:04]     Checking for file '/usr/share/sshd.sync'      [ Not found ]
[23:33:04]     Checking for file '/bin/zcut'                 [ Not found ]
[23:33:04]     Checking for file '/usr/bin/zmuie'            [ Not found ]
[23:33:04]     Checking for directory '/dev/ptyas'           [ Not found ]
[23:33:04]     Checking for directory '/usr/bin/take'        [ Not found ]
[23:33:04]     Checking for directory '/usr/src/.lib'        [ Not found ]
[23:33:04]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[23:33:04]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[23:33:04]     Checking for directory '/usr/sbin/...'        [ Not found ]
[23:33:04]     Checking for directory '/usr/share/.gun'      [ Not found ]
[23:33:04]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[23:33:04]     Checking for directory '/usr/man/man1/..  /.dir' [ Not found ]
[23:33:04]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[23:33:04]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[23:33:04]     Checking for directory '/tmp/.sys'            [ Not found ]
[23:33:04]     Checking for directory '/tmp/''               [ Not found ]
[23:33:04]     Checking for directory '/tmp/.,'              [ Not found ]
[23:33:04]     Checking for directory '/tmp/,.,'             [ Not found ]
[23:33:04]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[23:33:04]     Checking for directory '/var/tmp/.log'        [ Not found ]
[23:33:04]     Checking for directory '/tmp/zmeu/... '       [ Not found ]
[23:33:04]     Checking for directory '/var/log/ssh'         [ Not found ]
[23:33:04]     Checking for directory '/dev/ida'             [ Not found ]
[23:33:04]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[23:33:04]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[23:33:04]     Checking for directory '/usr/src/.poop'       [ Not found ]
[23:33:04]     Checking for directory '/dev/wd4'             [ Not found ]
[23:33:04]     Checking for directory '/var/run/.tmp'        [ Not found ]
[23:33:04]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[23:33:04]     Checking for directory '/dev/portd'           [ Not found ]
[23:33:04]     Checking for directory '/dev/...'             [ Not found ]
[23:33:04]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[23:33:04]     Checking for directory '/lib/.so'             [ Not found ]
[23:33:04]     Checking for directory '/lib/.sso'            [ Not found ]
[23:33:04]     Checking for directory '/usr/include/sslv3'   [ Not found ]
[23:33:04]     Checking for directory '/dev/shm/sshd'        [ Not found ]
[23:33:04]     Checking for directory '/usr/share/locale/mk/.dev/sk' [ Not found ]
[23:33:04]     Checking for directory '/usr/share/locale/mk/.dev' [ Not found ]
[23:33:04]     Checking for directory '/usr/include/netda.h' [ Not found ]
[23:33:04]     Checking for directory '/usr/include/.ssh'    [ Not found ]
[23:33:04]     Checking for directory '/usr/share/locale/jp/. ' [ Not found ]
[23:33:04]     Checking for directory '/usr/share/.sqe'      [ Not found ]
[23:33:04]   Checking for possible rootkit files and directories [ None found ]
[23:33:04]
[23:33:04] Info: Starting test name 'possible_rkt_strings'
[23:33:04]   Performing check for possible rootkit strings
[23:33:04] Info: Using system startup paths: /etc/rc.local /etc/init.d
[23:33:04]     Checking for string 'phalanx'                 [ Not found ]
[23:33:05]     Checking for string '/dev/proc/****it'        [ Not found ]
[23:33:05]     Checking for string '****'                    [ Not found ]
[23:33:05]     Checking for string 'backdoor'                [ Not found ]
[23:33:05]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[23:33:05]     Checking for string '/usr/sbin/login'         [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[23:33:05]     Checking for string 'vt200'                   [ Not found ]
[23:33:05]     Checking for string '/usr/bin/xstat'          [ Not found ]
[23:33:05]     Checking for string '/bin/envpc'              [ Not found ]
[23:33:05]     Checking for string 'L4m3r0x'                 [ Not found ]
[23:33:05]     Checking for string '/lib/libext'             [ Not found ]
[23:33:05]     Checking for string '/usr/sbin/login'         [ Not found ]
[23:33:05]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:33:05]     Checking for string 'sendmail'                [ Not found ]
[23:33:05]     Checking for string 'cocacola'                [ Not found ]
[23:33:05]     Checking for string 'joao'                    [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[23:33:05]     Checking for string '/dev/sgk'                [ Not found ]
[23:33:05]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:33:05]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:33:05]     Checking for string '/dev/proc/****it'        [ Not found ]
[23:33:05]     Checking for string '/lib/.sso'               [ Not found ]
[23:33:05]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:33:05]     Checking for string '/dev/caca'               [ Not found ]
[23:33:05]     Checking for string '/dev/ttyoa'              [ Not found ]
[23:33:05]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[23:33:05]     Checking for string 'syg'                     [ Not found ]
[23:33:05]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:33:05]     Checking for string '/dev/pts/01'             [ Not found ]
[23:33:05]     Checking for string 'tw33dl3'                 [ Not found ]
[23:33:05]     Checking for string 'psniff'                  [ Not found ]
[23:33:05]     Checking for string 'uconf.inv'               [ Not found ]
[23:33:05]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[23:33:05]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[23:33:05]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[23:33:05]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[23:33:05]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:05]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:05]     Checking for string '/bin/bash'               [ Not found ]
[23:33:06]     Checking for string '/dev/xdta'               [ Not found ]
[23:33:06]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:33:06]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[23:33:06]     Checking for string 'in.inetd'                [ Not found ]
[23:33:06]     Checking for string '#<HIDE_.*>'              [ Not found ]
[23:33:06]     Checking for string 'bin/xchk'                [ Not found ]
[23:33:06]     Checking for string 'bin/xsf'                 [ Not found ]
[23:33:06]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[23:33:07]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[23:33:07]     Checking for string 'ttyload'                 [ Not found ]
[23:33:07]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[23:33:07]     Checking for string 'usr/bin/xfss'            [ Not found ]
[23:33:07]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[23:33:07]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[23:33:07]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[23:33:08]     Checking for string '/ssh2d'                  [ Not found ]
[23:33:08]     Checking for string '/dev/kmod'               [ Not found ]
[23:33:08]     Checking for string '/crth.o'                 [ Not found ]
[23:33:08]     Checking for string '/crtz.o'                 [ Not found ]
[23:33:08]     Checking for string '/dev/dos'                [ Not found ]
[23:33:08]     Checking for string '/lpq'                    [ Not found ]
[23:33:08]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[23:33:08]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[23:33:09]     Checking for string '/volc'                   [ Not found ]
[23:33:09]     Checking for string 'sourcemask'              [ Not found ]
[23:33:09]     Checking for string '/bin/vobiscum'           [ Not found ]
[23:33:09]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[23:33:09]     Checking for string '/usr/bin/hdparm?-t1?-X53?-p' [ Not found ]
[23:33:09]     Checking for string '/lib/.xsyslog'           [ Not found ]
[23:33:09]     Checking for string '/etc/.xsyslog'           [ Not found ]
[23:33:09]     Checking for string '/lib/.ssyslog'           [ Not found ]
[23:33:10]     Checking for string '/tmp/.sendmail'          [ Not found ]
[23:33:10]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[23:33:10]     Checking for string 't0rnkit'                 [ Not found ]
[23:33:10]     Checking for string '/dev/proc/****it'        [ Not found ]
[23:33:10]     Checking for string 'backdoor.h'              [ Not found ]
[23:33:10]     Checking for string 'backdoor_active'         [ Not found ]
[23:33:10]     Checking for string 'magic_pass_active'       [ Not found ]
[23:33:10]     Checking for string '/usr/include/gpm2.h'     [ Not found ]
[23:33:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:10]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[23:33:10]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[23:33:10]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[23:33:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[23:33:10]     Checking for string '/dev/ida/.inet'          [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[23:33:10]     Checking for string 'backconnect'             [ Not found ]
[23:33:10]     Checking for string 'magic?packet?received'   [ Not found ]
[23:33:10]   Checking for possible rootkit strings           [ None found ]
[23:33:10]
[23:33:10] Info: Starting test name 'malware'
[23:33:10] Performing malware checks
[23:33:10]
[23:33:10] Info: Test 'deleted_files' disabled at users request.
[23:33:10]
[23:33:10] Info: Starting test name 'running_procs'
[23:33:12]   Checking running processes for suspicious files [ None found ]
[23:33:12]
[23:33:12] Info: Test 'hidden_procs' disabled at users request.
[23:33:12]
[23:33:12] Info: Test 'suspscan' disabled at users request.
[23:33:12]
[23:33:12] Info: Starting test name 'other_malware'
[23:33:12]   Performing check for login backdoors
[23:33:13]     Checking for '/bin/.login'                    [ Not found ]
[23:33:13]     Checking for '/sbin/.login'                   [ Not found ]
[23:33:13]   Checking for login backdoors                    [ None found ]
[23:33:13]
[23:33:13]   Performing check for suspicious directories
[23:33:13]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[23:33:13]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[23:33:13]   Checking for suspicious directories             [ None found ]
[23:33:13]
[23:33:13]   Checking for software intrusions                [ Skipped ]
[23:33:13] Info: Check skipped - tripwire not installed
[23:33:13]
[23:33:13]   Performing check for sniffer log files
[23:33:13]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[23:33:13]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[23:33:13]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[23:33:13]   Checking for sniffer log files                  [ None found ]
[23:33:13]
[23:33:13] Info: Starting test name 'trojans'
[23:33:13] Performing trojan specific checks
[23:33:13]   Checking for enabled inetd services             [ Skipped ]
[23:33:13] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[23:33:13]
[23:33:13]   Performing check for enabled xinetd services
[23:33:13]   Checking for enabled xinetd services            [ Skipped ]
[23:33:13] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[23:33:13] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[23:33:13]
[23:33:13] Info: Starting test name 'os_specific'
[23:33:13] Performing Linux specific checks
[23:33:13]   Checking loaded kernel modules                  [ OK ]
[23:33:13] Info: Using modules pathname of '/lib/modules/3.8.0-31-generic'
[23:33:13]   Checking kernel module names                    [ OK ]
[23:33:28]
[23:33:28] Info: Starting test name 'network'
[23:33:29] Checking the network...
[23:33:29]
[23:33:29] Performing checks on the network ports
[23:33:29] Info: Starting test name 'ports'
[23:33:29]   Performing check for backdoor ports
[23:33:29]     Checking for TCP port 1524                    [ Not found ]
[23:33:29]     Checking for TCP port 1984                    [ Not found ]
[23:33:29]     Checking for UDP port 2001                    [ Not found ]
[23:33:29]     Checking for TCP port 2006                    [ Not found ]
[23:33:29]     Checking for TCP port 2128                    [ Not found ]
[23:33:29]     Checking for TCP port 6666                    [ Not found ]
[23:33:29]     Checking for TCP port 6667                    [ Not found ]
[23:33:29]     Checking for TCP port 6668                    [ Not found ]
[23:33:29]     Checking for TCP port 6669                    [ Not found ]
[23:33:29]     Checking for TCP port 7000                    [ Not found ]
[23:33:29]     Checking for TCP port 13000                   [ Not found ]
[23:33:29]     Checking for TCP port 14856                   [ Not found ]
[23:33:29]     Checking for TCP port 25000                   [ Not found ]
[23:33:29]     Checking for TCP port 29812                   [ Not found ]
[23:33:29]     Checking for TCP port 31337                   [ Not found ]
[23:33:30]     Checking for TCP port 32982                   [ Not found ]
[23:33:30]     Checking for TCP port 33369                   [ Not found ]
[23:33:30]     Checking for TCP port 47107                   [ Not found ]
[23:33:30]     Checking for TCP port 47018                   [ Not found ]
[23:33:30]     Checking for TCP port 60922                   [ Not found ]
[23:33:30]     Checking for TCP port 62883                   [ Not found ]
[23:33:30]     Checking for TCP port 65535                   [ Not found ]
[23:33:30]   Checking for backdoor ports                     [ None found ]
[23:33:30]
[23:33:30] Info: Starting test name 'hidden_ports'
[23:33:30] Checking for hidden ports                         [ Skipped ]
[23:33:30] Info: Unable to find the 'unhide-tcp' command
[23:33:30]
[23:33:30] Performing checks on the network interfaces
[23:33:30] Info: Starting test name 'promisc'
[23:33:30]   Checking for promiscuous interfaces             [ None found ]
[23:33:30]
[23:33:30] Info: Test 'packet_cap_apps' disabled at users request.
[23:33:30]
[23:33:30] Info: Starting test name 'local_host'
[23:33:30] Checking the local host...
[23:33:30]
[23:33:30] Info: Starting test name 'startup_files'
[23:33:30] Performing system boot checks
[23:33:30]   Checking for local host name                    [ Found ]
[23:33:30]
[23:33:30] Info: Starting test name 'startup_malware'
[23:33:30]   Checking for system startup files               [ Found ]
[23:33:31]   Checking system startup files for malware       [ None found ]
[23:33:31]
[23:33:31] Info: Starting test name 'group_accounts'
[23:33:31] Performing group and account checks
[23:33:31]   Checking for passwd file                        [ Found ]
[23:33:31] Info: Found password file: /etc/passwd
[23:33:31]   Checking for root equivalent (UID 0) accounts   [ None found ]
[23:33:31] Info: Found shadow file: /etc/shadow
[23:33:31]   Checking for passwordless accounts              [ None found ]
[23:33:31]
[23:33:31] Info: Starting test name 'passwd_changes'
[23:33:31]   Checking for passwd file changes                [ None found ]
[23:33:31]
[23:33:31] Info: Starting test name 'group_changes'
[23:33:31]   Checking for group file changes                 [ None found ]
[23:33:31]   Checking root account shell history files       [ OK ]
[23:33:31]
[23:33:31] Info: Starting test name 'system_configs'
[23:33:31] Performing system configuration file checks
[23:33:31]   Checking for SSH configuration file             [ Not found ]
[23:33:31]   Checking for running syslog daemon              [ Found ]
[23:33:31] Info: Found rsyslog configuration file: /etc/rsyslog.conf
[23:33:31]   Checking for syslog configuration file          [ Found ]
[23:33:31]   Checking if syslog remote logging is allowed    [ Not allowed ]
[23:33:31]
[23:33:31] Info: Starting test name 'filesystem'
[23:33:31] Performing filesystem checks
[23:33:31] Info: SCAN_MODE_DEV set to 'THOROUGH'
[23:33:31]   Checking /dev for suspicious file types         [ Warning ]
[23:33:31] Warning: Suspicious file types found in /dev:
[23:33:31]          /dev/.udev/rules.d/root.rules: ASCII text
[23:33:31]   Checking for hidden files and directories       [ Warning ]
[23:33:31] Warning: Hidden directory found: '/etc/.java'
[23:33:31] Warning: Hidden directory found: '/dev/.udev'
[23:33:31] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[23:33:34]
[23:33:34] Info: Test 'apps' disabled at users request.
[23:33:34]
[23:33:34] System checks summary
[23:33:34] =====================
[23:33:34]
[23:33:34] File properties checks...
[23:33:34] Files checked: 136
[23:33:34] Suspect files: 1
[23:33:34]
[23:33:34] Rootkit checks...
[23:33:34] Rootkits checked : 292
[23:33:34] Possible rootkits: 0
[23:33:34]
[23:33:34] Applications checks...
[23:33:34] All checks skipped
[23:33:34]
[23:33:34] The system checks took: 1 minute and 4 seconds
[23:33:34]
[23:33:34] Info: End date is Sun Sep 29 23:33:34 PDT 2013 
```

---

### Post by sandyd on 2013-09-30
```
[23:32:38] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[23:33:31] Warning: Suspicious file types found in /dev:
[23:33:31]          /dev/.udev/rules.d/root.rules: ASCII text
[23:33:31]   Checking for hidden files and directories       [ Warning ]
[23:33:31] Warning: Hidden directory found: '/etc/.java'
[23:33:31] Warning: Hidden directory found: '/dev/.udev'
[23:33:31] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
```

---

### Post by CCgirl6690 on 2013-09-30
sandy  , yes i noticed that but im a beginner please tell me what to do thanks

---

### Post by Nil_Pointer on 2013-10-01
Yes, beginners seem to be often confused with rkhunter. So, I'll try to explain. First of all, you must understand what rkhunter does and what it doesn't. Yes, rkhunter checks system for several known rootkits. But it's primary purpose is to check system state against previously collected database of properties. So, if any file listed in this database gets changed, rkhunter throws a warning. Most of times it indicates that certain programs were changed as result of installing updates, not malicious actions.

This command just updates properties database with current state of system:

```
sudo rkhunter --propupd
```

If you don't want rkhunter to spit false warnings due to updates, you must do following:

1. Before installing any updates, run a rkhunter check:

```
sudo rkhunter --check
```

2. If there is no warnings on file properties scan phase, there's nothing to worry about. You can install the updates.

3. Now update properties database with this command to prevent rkhunter from treating newly installed updates as suspicious changes and spitting warnings:

```
sudo rkhunter --propupd
```

Now, about these warnings:

```
[23:32:38] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[23:33:31] Warning: Suspicious file types found in /dev:
[23:33:31]          /dev/.udev/rules.d/root.rules: ASCII text
[23:33:31]   Checking for hidden files and directories       [ Warning ]
[23:33:31] Warning: Hidden directory found: '/etc/.java'
[23:33:31] Warning: Hidden directory found: '/dev/.udev'
[23:33:31] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
```

 First line doesn't look right at all. It must be a bug. Unhide.rb is not a command, it's a ruby script. Probably, rkhunter assumes that everything inside /usr/bin is a binary file. Ergo, there is nothing wrong with unhide.rb. All next lines are just false positives. Three last lines appear on my system, too. And file /dev/.udev/rules.d/root.rules is just result of existence of /dev/.udev.

To sum it up, there's nothing looks off place, looks like your system is safe.

---

### Post by CCgirl6690 on 2013-10-01
> **Nil_Pointer said:**
> Yes, beginners seem to be often confused with rkhunter. So, I'll try to explain. First of all, you must understand what rkhunter does and what it doesn't. Yes, rkhunter checks system for several known rootkits. But it's primary purpose is to check system state against previously collected database of properties. So, if any file listed in this database gets changed, rkhunter throws a warning. Most of times it indicates that certain programs were changed as result of installing updates, not malicious actions.

This command just updates properties database with current state of system:

```
sudo rkhunter --propupd
```

If you don't want rkhunter to spit false warnings due to updates, you must do following:

1. Before installing any updates, run a rkhunter check:

```
sudo rkhunter --check
```

2. If there is no warnings on file properties scan phase, there's nothing to worry about. You can install the updates.

3. Now update properties database with this command to prevent rkhunter from treating newly installed updates as suspicious changes and spitting warnings:

```
sudo rkhunter --propupd
```

Now, about these warnings:

```
[23:32:38] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[23:33:31] Warning: Suspicious file types found in /dev:
[23:33:31]          /dev/.udev/rules.d/root.rules: ASCII text
[23:33:31]   Checking for hidden files and directories       [ Warning ]
[23:33:31] Warning: Hidden directory found: '/etc/.java'
[23:33:31] Warning: Hidden directory found: '/dev/.udev'
[23:33:31] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
```

 First line doesn't look right at all. It must be a bug. Unhide.rb is not a command, it's a ruby script. Probably, rkhunter assumes that everything inside /usr/bin is a binary file. Ergo, there is nothing wrong with unhide.rb. All next lines are just false positives. Three last lines appear on my system, too. And file /dev/.udev/rules.d/root.rules is just result of existence of /dev/.udev.

To sum it up, there's nothing looks off place, looks like your system is safe.

thank you so much Nil . although you  are a new member but you explained it the best and i understood all  thanks again ......

---

### Post by cariboo on 2013-10-02
> **CCgirl6690 said:**
> thank you so much Nil . although you  are a new member but you explained it the best and i understood all  thanks again ......

Don't be fooled by join dates, since we changed to using SSO to login, many members have decided for whatever reason not to use their original accounts.

---

### Post by Nil_Pointer on 2013-10-04
Indeed, I've originally joined in Aug 2010, but during change to SSO managed to lose my account, since I've forgot email address I used to register on forums, so I've registered a new one.

---

### Post by Elfy on 2013-10-04
> **Nil_Pointer said:**
> Indeed, I've originally joined in Aug 2010, but during change to SSO managed to lose my account, since I've forgot email address I used to register on forums, so I've registered a new one.

As an aside - just because you've forgotten, or might have no access to it now, that does not mean we can't find it. We've had more than one account where a nudge makes people remember. Some alos put their DoB which is hidden by default - we can see it. More than one way to verify accounts. If you want to try and get it back then post in here [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

