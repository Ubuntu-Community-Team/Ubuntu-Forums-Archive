---
title: "Possible system keylogger"
date: 2009-06-13
forum: Security
---

### Post by micdhack on 2009-06-13
My wow account was hacked so im trying to figure out if there could be a keylogger on my system. Also i don't know if it is possible to have viruses running through wine when computer starts its time.
And ways that i can positively confirm that system is clean from trojans and keyloggers.

I got this error from chkrootkit
```
Checking `bindshell'... INFECTED (PORTS:  4369)

```

portsentry is not running

also netstat reports this

```
micdhack@micdhack-laptop:~$ netstat | grep 4369
tcp        0      0 localhost:56100         localhost:4369          SPOJENO    
tcp        0      0 localhost:4369          localhost:56100         SPOJENO    

```

I also used rkhunter but the only errors where

```
micdhack@micdhack-laptop:~$ sudo chkrootkit
[sudo] password for micdhack: 
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not infected
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not infected
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not found
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not infected
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not infected
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/jvm/java-6-sun-1.6.0.13/.systemPrefs /usr/lib/jvm/.java-gcj.jinfo /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/xulrunner/.autoreg /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.1.R321_v20060905/.options /usr/lib/eclipse/plugins/org.eclipse.platform.source_3.2.2.r322_v20070119-CXMbUe9K_WF26uA/src/org.eclipse.ui.intro.universal_3.2.1.R321_v20060905/.options /usr/lib/eclipse/plugins/org.eclipse.platform.source_3.2.2.r322_v20070119-CXMbUe9K_WF26uA/src/org.eclipse.ui.intro_3.2.2.R322_v20061214/.options /usr/lib/eclipse/plugins/org.eclipse.pde.build_3.2.1.r321_v20060823/.options /usr/lib/eclipse/plugins/org.eclipse.help.webapp_3.2.2.R322_v20061114/.options /usr/lib/eclipse/.eclipseproduct /usr/lib/firefox-3.0.10/.autoreg /usr/lib/firefox/.autoreg /usr/lib/xulrunner-1.9.0.10/.autoreg /lib/init/rw/.ramfs /lib/modules/2.6.28-11-generic/volatile/.mounted /lib/modules/2.6.27-7-generic/volatile/.mounted

Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             nothing found
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for anomalies in shell history files...           Warning: `//home/micdhack/.kino-history' is linked to another file
Checking `asp'...                                           not infected
Checking `bindshell'...                                     INFECTED (PORTS:  4369)
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[4178])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            chklastlog: nothing deleted


micdhack@micdhack-laptop:~$ sudo rkhunter --update
[ Rootkit Hunter version 1.3.2 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ Updated ]
  Checking file i18n/en                                      [ No update ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zh.utf8                                 [ No update ]
micdhack@micdhack-laptop:~$ sudo rkhunter --checkall
[ Rootkit Hunter version 1.3.2 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
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
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
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
    /usr/bin/lynx                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/rpm                                             [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
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
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/lynx.cur                                        [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
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
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
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
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for Apache backdoor                             [ Not found ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]


Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
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
    Checking for hidden files and directories                [ None found ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ OK ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]
    Checking version of PHP                                  [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 131
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 112
    Possible rootkits: 0

Applications checks...
    Applications checked: 4
    Suspect applications: 0

The system checks took: 1 minute and 38 seconds
```

---

### Post by albinootje on 2009-06-13
Install rkhunter, and run a test :
```

sudo rkhunter -c

```

And see what rkhunter says. And check "lsof|grep 4369" yourself.

---

### Post by iponeverything on 2009-06-13
It could be false positive. 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309386](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309386)

---

### Post by micdhack on 2009-06-13
rkhunter output. i read the warnings from the logs and its not anything serious
```

micdhack@micdhack-laptop:~$ sudo rkhunter -c
[ Rootkit Hunter version 1.3.2 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
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
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
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
    /usr/bin/lynx                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/rpm                                             [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
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
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/lynx.cur                                        [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
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
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
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
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for Apache backdoor                             [ Not found ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
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
    Checking for hidden files and directories                [ None found ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ OK ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]
    Checking version of PHP                                  [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 131
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 112
    Possible rootkits: 0

Applications checks...
    Applications checked: 4
    Suspect applications: 0

The system checks took: 2 minutes and 8 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

```

here is the lsof|grep 4369. Although i don't understand what it is and if it is bad
```

micdhack@micdhack-laptop:~$ lsof|grep 4369
seahorse-  4369    micdhack  cwd       DIR        8,3     12288   163841 /tmp
seahorse-  4369    micdhack  rtd       DIR        8,3      4096        2 /
seahorse-  4369    micdhack  txt       REG        8,3    126324   425755 /usr/bin/seahorse-agent
seahorse-  4369    micdhack  mem       REG        8,3     34284   557096 /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
seahorse-  4369    micdhack  DEL       REG        0,9              32769 /SYSV00000000
seahorse-  4369    micdhack  mem       REG        8,3     80280   394104 /usr/lib/libgvfscommon.so.0.0.0
seahorse-  4369    micdhack  mem       REG        8,3    104868   623935 /usr/share/mime/mime.cache
seahorse-  4369    micdhack  mem       REG        8,3    108940   557450 /usr/lib/gio/modules/libgvfsdbus.so
seahorse-  4369    micdhack  mem       REG        8,3     30104   418983 /usr/lib/libltdl.so.7.2.0
seahorse-  4369    micdhack  mem       REG        8,3     50596   418985 /usr/lib/libtdb.so.1.1.3
seahorse-  4369    micdhack  mem       REG        8,3     17628   393882 /usr/lib/libogg.so.0.5.3
seahorse-  4369    micdhack  mem       REG        8,3    167772    98361 /usr/lib/libvorbis.so.0.4.0
seahorse-  4369    micdhack  mem       REG        8,3     30164    98365 /usr/lib/libvorbisfile.so.3.2.0
seahorse-  4369    micdhack  mem       REG        8,3     63308   557448 /usr/lib/gio/modules/libgioremote-volume-monitor.so
seahorse-  4369    micdhack  mem       REG        8,3     39883   295521 /usr/share/locale-langpack/cs/LC_MESSAGES/glib20.mo
seahorse-  4369    micdhack  mem       REG        8,3    153648   295578 /usr/share/locale-langpack/cs/LC_MESSAGES/gtk20-properties.mo
seahorse-  4369    micdhack  mem       REG        8,3     42504   434331 /lib/tls/i686/cmov/libnss_files-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     38444   434333 /lib/tls/i686/cmov/libnss_nis-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     87804   434304 /lib/tls/i686/cmov/libnsl-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     30436   434305 /lib/tls/i686/cmov/libnss_compat-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     58964   423640 /usr/lib/libcanberra.so.0.1.4
seahorse-  4369    micdhack  mem       REG        8,3     13688   418390 /usr/lib/libcanberra-gtk.so.0.0.4
seahorse-  4369    micdhack  mem       REG        8,3     17924   557208 /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
seahorse-  4369    micdhack  mem       REG        8,3     63355   295538 /usr/share/locale-langpack/cs/LC_MESSAGES/gtk20.mo
seahorse-  4369    micdhack  mem       REG        8,3    256316   672374 /usr/lib/locale/cs_CZ.utf8/LC_CTYPE
seahorse-  4369    micdhack  mem       REG        8,3    111970   568969 /usr/lib/locale/cs_CZ.utf8/LC_COLLATE
seahorse-  4369    micdhack  mem       REG        8,3     16628   278732 /usr/lib/libXdmcp.so.6.0.0
seahorse-  4369    micdhack  mem       REG        8,3      9508   421052 /usr/lib/libXau.so.6.0.0
seahorse-  4369    micdhack  mem       REG        8,3    152908   294999 /usr/lib/libexpat.so.1.5.2
seahorse-  4369    micdhack  mem       REG        8,3     99768   421058 /usr/lib/libxcb.so.1.1.0
seahorse-  4369    micdhack  mem       REG        8,3     25876   419887 /usr/lib/libxcb-render.so.0.0.0
seahorse-  4369    micdhack  mem       REG        8,3     13648   419891 /usr/lib/libxcb-render-util.so.0.0.0
seahorse-  4369    micdhack  mem       REG        8,3    149288   419573 /usr/lib/libpng12.so.0.27.0
seahorse-  4369    micdhack  mem       REG        8,3     79736   421043 /usr/lib/libdirect-1.0.so.0.1.0
seahorse-  4369    micdhack  mem       REG        8,3     30020   421045 /usr/lib/libfusion-1.0.so.0.1.0
seahorse-  4369    micdhack  mem       REG        8,3    412840   421044 /usr/lib/libdirectfb-1.0.so.0.1.0
seahorse-  4369    micdhack  mem       REG        8,3    268508   419883 /usr/lib/libpixman-1.so.0.13.2
seahorse-  4369    micdhack  mem       REG        8,3     99972   426003 /lib/libselinux.so.1
seahorse-  4369    micdhack  mem       REG        8,3    197892   427641 /lib/libpcre.so.3.12.1
seahorse-  4369    micdhack  mem       REG        8,3      9676   434301 /lib/tls/i686/cmov/libdl-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     83552   607332 /lib/libz.so.1.2.3.3
seahorse-  4369    micdhack  mem       REG        8,3     14128   278742 /usr/lib/libXfixes.so.3.1.0
seahorse-  4369    micdhack  mem       REG        8,3      6260   278728 /usr/lib/libXdamage.so.1.1.0
seahorse-  4369    micdhack  mem       REG        8,3      9452   278722 /usr/lib/libXcomposite.so.1.0.0
seahorse-  4369    micdhack  mem       REG        8,3    971436   418017 /usr/lib/libX11.so.6.2.0
seahorse-  4369    micdhack  mem       REG        8,3     33152   278726 /usr/lib/libXcursor.so.1.0.2
seahorse-  4369    micdhack  mem       REG        8,3     30008   420757 /usr/lib/libXrandr.so.2.2.0
seahorse-  4369    micdhack  mem       REG        8,3     34232   420753 /usr/lib/libXi.so.6.0.0
seahorse-  4369    micdhack  mem       REG        8,3      6528   278756 /usr/lib/libXinerama.so.1.0.0
seahorse-  4369    micdhack  mem       REG        8,3     34352   278776 /usr/lib/libXrender.so.1.3.0
seahorse-  4369    micdhack  mem       REG        8,3     59964   418048 /usr/lib/libXext.so.6.4.0
seahorse-  4369    micdhack  mem       REG        8,3     30624   434394 /lib/tls/i686/cmov/librt-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3     17880   418822 /usr/lib/libgthread-2.0.so.0.2000.1
seahorse-  4369    micdhack  mem       REG        8,3    338056   420312 /usr/lib/libORBit-2.so.0.1.0
seahorse-  4369    micdhack  mem       REG        8,3    222816   607335 /lib/libdbus-1.so.3.4.0
seahorse-  4369    micdhack  mem       REG        8,3     11468   426066 /lib/libgpg-error.so.0.3.0
seahorse-  4369    micdhack  mem       REG        8,3     13644   418331 /usr/lib/libgmodule-2.0.so.0.2000.1
seahorse-  4369    micdhack  mem       REG        8,3    179024   421038 /usr/lib/libfontconfig.so.1.3.0
seahorse-  4369    micdhack  mem       REG        8,3    480644   418758 /usr/lib/libfreetype.so.6.3.20
seahorse-  4369    micdhack  mem       REG        8,3    494036   419896 /usr/lib/libcairo.so.2.10800.6
seahorse-  4369    micdhack  mem       REG        8,3     42812   420747 /usr/lib/libpangocairo-1.0.so.0.2400.1
seahorse-  4369    micdhack  mem       REG        8,3    149328   434302 /lib/tls/i686/cmov/libm-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3    100068   420839 /usr/lib/libgdk_pixbuf-2.0.so.0.1600.1
seahorse-  4369    micdhack  mem       REG        8,3    161876   420748 /usr/lib/libpangoft2-1.0.so.0.2400.1
seahorse-  4369    micdhack  mem       REG        8,3    108140   419470 /usr/lib/libatk-1.0.so.0.2609.1
seahorse-  4369    micdhack  mem       REG        8,3   1286600   419365 /usr/lib/libxml2.so.2.6.32
seahorse-  4369    micdhack  mem       REG        8,3   1442180   434298 /lib/tls/i686/cmov/libc-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3    116405   434336 /lib/tls/i686/cmov/libpthread-2.9.so
seahorse-  4369    micdhack  mem       REG        8,3    747948   418330 /usr/lib/libglib-2.0.so.0.2000.1
seahorse-  4369    micdhack  mem       REG        8,3    247728   418821 /usr/lib/libgobject-2.0.so.0.2000.1
seahorse-  4369    micdhack  mem       REG        8,3    268288   420746 /usr/lib/libpango-1.0.so.0.2400.1
seahorse-  4369    micdhack  mem       REG        8,3    445320   418329 /usr/lib/libgio-2.0.so.0.2000.1
seahorse-  4369    micdhack  mem       REG        8,3    573224   418396 /usr/lib/libgdk-x11-2.0.so.0.1600.1
seahorse-  4369    micdhack  mem       REG        8,3    117092   420278 /usr/lib/libdbus-glib-1.so.2.1.0
seahorse-  4369    micdhack  mem       REG        8,3   3858824   418336 /usr/lib/libgtk-x11-2.0.so.0.1600.1
seahorse-  4369    micdhack  mem       REG        8,3    198756   418414 /usr/lib/libgconf-2.so.4.1.5
seahorse-  4369    micdhack  mem       REG        8,3     71468   421385 /usr/lib/libgnome-keyring.so.0.1.1
seahorse-  4369    micdhack  mem       REG        8,3    175712   295233 /usr/lib/libgpgme.so.11.6.6
seahorse-  4369    micdhack  mem       REG        8,3     93012   421288 /usr/lib/libglade-2.0.so.0.0.7
seahorse-  4369    micdhack  mem       REG        8,3       620   262286 /usr/local/share/mime/mime.cache
seahorse-  4369    micdhack  mem       REG        8,6       464  7779520 /home/micdhack/.local/share/mime/mime.cache
seahorse-  4369    micdhack  mem       REG        8,3     22140   295577 /usr/share/locale-langpack/cs/LC_MESSAGES/seahorse-plugins.mo
seahorse-  4369    micdhack  mem       REG        8,3        54   566490 /usr/lib/locale/cs_CZ.utf8/LC_NUMERIC
seahorse-  4369    micdhack  mem       REG        8,3      2446   568968 /usr/lib/locale/cs_CZ.utf8/LC_TIME
seahorse-  4369    micdhack  mem       REG        8,3       294   568970 /usr/lib/locale/cs_CZ.utf8/LC_MONETARY
seahorse-  4369    micdhack  mem       REG        8,3        59   568971 /usr/lib/locale/cs_CZ.utf8/LC_MESSAGES/SYS_LC_MESSAGES
seahorse-  4369    micdhack  mem       REG        8,3        34   566314 /usr/lib/locale/cs_CZ.utf8/LC_PAPER
seahorse-  4369    micdhack  mem       REG        8,3        82   568972 /usr/lib/locale/cs_CZ.utf8/LC_NAME
seahorse-  4369    micdhack  mem       REG        8,3       164   568973 /usr/lib/locale/cs_CZ.utf8/LC_ADDRESS
seahorse-  4369    micdhack  mem       REG        8,3        60   568974 /usr/lib/locale/cs_CZ.utf8/LC_TELEPHONE
seahorse-  4369    micdhack  mem       REG        8,3        23   566310 /usr/lib/locale/cs_CZ.utf8/LC_MEASUREMENT
seahorse-  4369    micdhack  mem       REG        8,3     26048   542910 /usr/lib/gconv/gconv-modules.cache
seahorse-  4369    micdhack  mem       REG        8,3       391   568975 /usr/lib/locale/cs_CZ.utf8/LC_IDENTIFICATION
seahorse-  4369    micdhack  mem       REG        8,3    117348   426087 /lib/ld-2.9.so
seahorse-  4369    micdhack    0r      CHR        1,3               3389 /dev/null
seahorse-  4369    micdhack    1w      CHR        1,3               3389 /dev/null
seahorse-  4369    micdhack    2w      CHR        1,3               3389 /dev/null
seahorse-  4369    micdhack    3u     unix 0xf46bfa40              11021 socket
seahorse-  4369    micdhack    4u     unix 0xf46be380              11042 /tmp/seahorse-XVBFLH/S.gpg-agent
seahorse-  4369    micdhack    5w     FIFO        0,6               9407 pipe
seahorse-  4369    micdhack    6r     FIFO        0,6              11044 pipe
seahorse-  4369    micdhack    7r     FIFO        0,6               9411 pipe
seahorse-  4369    micdhack    8w     FIFO        0,6              11044 pipe
seahorse-  4369    micdhack    9u     unix 0xf6001a40              11100 socket
seahorse-  4369    micdhack   10u     unix 0xf44561c0              11163 socket
seahorse-  4369    micdhack   11r     FIFO        0,6              11165 pipe
seahorse-  4369    micdhack   12w     FIFO        0,6              11165 pipe
seahorse-  4369    micdhack   13r     FIFO        0,6              11166 pipe
seahorse-  4369    micdhack   14w     FIFO        0,6              11166 pipe
seahorse-  4369    micdhack   15r     FIFO        0,6              11167 pipe
seahorse-  4369    micdhack   16w     FIFO        0,6              11167 pipe
seahorse-  4369    micdhack   17u     unix 0xf44568c0              11168 socket
seahorse-  4369    micdhack   18u     unix 0xf44d6fc0              11170 /tmp/orbit-micdhack/linc-1111-0-3f5a45d2c7ce2
seahorse-  4369    micdhack   19u     unix 0xf44d7340              11173 /tmp/orbit-micdhack/linc-1111-0-3f5a45d2c7ce2
micdhack@micdhack-laptop:~$ 

```

UPDATE: actually the bindshell port was mapped by epmd which was erlang port mapper. after i uninstalled it the chkroot didnt print such error again.

So my next question is. If the system is clean from viruses and i have verified that with clamav, ckrootkit, rkhunter and avast, is there any other way (maybe through wine) that someone could steal my password? Also the seahorse application is the keyring application. Could it be compromised?

---

### Post by zuerston on 2009-06-13
Mine said port 46 

also

```
 &#65279;[11:39:51] Running Rootkit Hunter version 1.3.2 on xaaxa-laptop
[11:39:51]
[11:39:51] Info: Start date is Sat Jun 13 11:39:51 EDT 2009
[11:39:51]
[11:39:51] Checking configuration file and command-line options...
[11:39:51] Info: Detected operating system is 'Linux'
[11:39:51] Info: Found O/S name: Ubuntu 9.04
[11:39:51] Info: Command line is /usr/bin/rkhunter -c
[11:39:51] Info: Environment shell is /bin/bash; rkhunter is using dash
[11:39:51] Info: Using configuration file '/etc/rkhunter.conf'
[11:39:51] Info: Installation directory is '/usr'
[11:39:51] Info: Using language 'en'
[11:39:51] Info: Using '/var/lib/rkhunter/db' as the database directory
[11:39:51] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[11:39:51] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[11:39:51] Info: Using '/' as the root directory
[11:39:51] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[11:39:51] Info: No mail-on-warning address configured
[11:39:51] Info: X will be automatically detected
[11:39:51] Info: Using second color set
[11:39:51] Info: Found the 'diff' command: /usr/bin/diff
[11:39:51] Info: Found the 'file' command: /usr/bin/file
[11:39:51] Info: Found the 'find' command: /usr/bin/find
[11:39:51] Info: Found the 'ifconfig' command: /sbin/ifconfig
[11:39:51] Info: Found the 'ip' command: /sbin/ip
[11:39:51] Info: Found the 'ldd' command: /usr/bin/ldd
[11:39:51] Info: Found the 'lsattr' command: /usr/bin/lsattr
[11:39:51] Info: Found the 'lsmod' command: /sbin/lsmod
[11:39:51] Info: Found the 'lsof' command: /usr/bin/lsof
[11:39:51] Info: Found the 'mktemp' command: /bin/mktemp
[11:39:51] Info: Found the 'netstat' command: /bin/netstat
[11:39:51] Info: Found the 'perl' command: /usr/bin/perl
[11:39:51] Info: Found the 'ps' command: /bin/ps
[11:39:51] Info: Found the 'pwd' command: /bin/pwd
[11:39:51] Info: Found the 'readlink' command: /bin/readlink
[11:39:52] Info: Found the 'sort' command: /usr/bin/sort
[11:39:52] Info: Found the 'stat' command: /usr/bin/stat
[11:39:52] Info: Found the 'strings' command: /usr/bin/strings
[11:39:52] Info: Found the 'uniq' command: /usr/bin/uniq
[11:39:52] Info: System is not using prelinking
[11:39:52] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[11:39:52] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[11:39:52] Info: Stored hash values did not use a package manager
[11:39:52] Info: The hash function field index is set to 1
[11:39:52] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[11:39:52] Info: Previous file attributes were stored
[11:39:52] Info: Enabled tests are: all
[11:39:52] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[11:39:52] Info: Found ksym file '/proc/kallsyms'
[11:39:52]
[11:39:52] Checking if the O/S has changed since last time...
[11:39:52] Info: Nothing seems to have changed
[11:39:52]
[11:39:52] Starting system checks...
[11:39:52]
[11:39:52] Checking system commands...
[11:39:52] Info: Starting test name 'system_commands'
[11:39:52]
[11:39:52] Performing 'strings' command checks
[11:39:52] Info: Starting test name 'strings'
[11:39:52] Scanning for string /usr/sbin/ntpsx               [ OK ]
[11:39:52] Scanning for string /usr/lib/.../ls               [ OK ]
[11:39:52] Scanning for string /usr/lib/.../netstat          [ OK ]
[11:39:52] Scanning for string /usr/lib/.../lsof             [ OK ]
[11:39:52] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[11:39:52] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[11:39:52] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[11:39:52] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[11:39:52] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[11:39:52] Scanning for string /usr/lib/.../psr              [ OK ]
[11:39:52] Scanning for string /usr/lib/.../find             [ OK ]
[11:39:52] Scanning for string /usr/lib/.../pstree           [ OK ]
[11:39:52] Scanning for string /usr/lib/.../slocate          [ OK ]
[11:39:52] Scanning for string /usr/lib/.../du               [ OK ]
[11:39:52] Scanning for string /usr/lib/.../top              [ OK ]
[11:39:53] Scanning for string /usr/lib/...                  [ OK ]
[11:39:53] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[11:39:53] Scanning for string /usr/lib/.bkit-               [ OK ]
[11:39:53] Scanning for string /tmp/.bkp                     [ OK ]
[11:39:53] Scanning for string /tmp/.cinik                   [ OK ]
[11:39:53] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[11:39:53] Scanning for string /lib/.sso                     [ OK ]
[11:39:53] Scanning for string /lib/.so                      [ OK ]
[11:39:53] Scanning for string /var/run/...dica/clean        [ OK ]
[11:39:53] Scanning for string /var/run/...dica/xl           [ OK ]
[11:39:53] Scanning for string /var/run/...dica/xdr          [ OK ]
[11:39:53] Scanning for string /var/run/...dica/psg          [ OK ]
[11:39:53] Scanning for string /var/run/...dica/secure       [ OK ]
[11:39:53] Scanning for string /var/run/...dica/rdx          [ OK ]
[11:39:53] Scanning for string /var/run/...dica/va           [ OK ]
[11:39:53] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[11:39:53] Scanning for string /usr/bin/.etc                 [ OK ]
[11:39:53] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[11:39:53] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[11:39:53] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[11:39:53] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[11:39:53] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[11:39:53] Scanning for string /bin/sysback                  [ OK ]
[11:39:53] Scanning for string /usr/local/bin/sysback        [ OK ]
[11:39:53] Scanning for string /usr/lib/.tbd                 [ OK ]
[11:39:53] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[11:39:53] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[11:39:53] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[11:39:54] Scanning for string /usr/info/.torn/sh*           [ OK ]
[11:39:54] Scanning for string /usr/src/.****/.1addr         [ OK ]
[11:39:54] Scanning for string /usr/src/.****/.1file         [ OK ]
[11:39:54] Scanning for string /usr/src/.****/.1proc         [ OK ]
[11:39:54] Scanning for string /usr/src/.****/.1logz         [ OK ]
[11:39:54] Scanning for string /usr/info/.t0rn               [ OK ]
[11:39:54] Scanning for string /dev/.lib                     [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib                 [ OK ]
[11:39:54] Scanning for string /dev/.lib/lib/lib             [ OK ]
[11:39:55] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[11:39:55] Scanning for string /dev/.lib/lib/scan            [ OK ]
[11:39:55] Scanning for string /usr/src/.****                [ OK ]
[11:39:55] Scanning for string /usr/man/man1/man1            [ OK ]
[11:39:55] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[11:39:55] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[11:39:55] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[11:39:55]
[11:39:55] Performing 'shared libraries' checks
[11:39:55] Info: Starting test name 'shared_libs'
[11:39:55] Checking for preloading variables                 [ None found ]
[11:39:55] Checking for preload file                         [ Not found ]
[11:39:55] Info: Starting test name 'shared_libs_path'
[11:39:55] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[11:39:55]
[11:39:55] Performing file properties checks
[11:39:55] Info: Starting test name 'properties'
[11:39:55] Checking for prerequisites                        [ OK ]
[11:39:55] /bin/bash                                         [ OK ]
[11:39:55] /bin/cat                                          [ OK ]
[11:39:56] /bin/chmod                                        [ OK ]
[11:39:56] /bin/chown                                        [ OK ]
[11:39:56] /bin/cp                                           [ OK ]
[11:39:56] /bin/date                                         [ OK ]
[11:39:56] /bin/df                                           [ OK ]
[11:39:56] /bin/dmesg                                        [ OK ]
[11:39:56] /bin/echo                                         [ OK ]
[11:39:56] /bin/ed                                           [ OK ]
[11:39:57] /bin/egrep                                        [ OK ]
[11:39:57] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[11:39:57] /bin/fgrep                                        [ OK ]
[11:39:57] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[11:39:57] /bin/fuser                                        [ OK ]
[11:39:57] /bin/grep                                         [ OK ]
[11:39:57] /bin/ip                                           [ OK ]
[11:39:57] /bin/kill                                         [ OK ]
[11:39:57] /bin/login                                        [ OK ]
[11:39:57] /bin/ls                                           [ OK ]
[11:39:58] /bin/lsmod                                        [ OK ]
[11:39:58] /bin/mktemp                                       [ OK ]
[11:39:58] /bin/more                                         [ OK ]
[11:39:58] /bin/mount                                        [ OK ]
[11:39:58] /bin/mv                                           [ OK ]
[11:39:58] /bin/netstat                                      [ OK ]
[11:39:58] /bin/ps                                           [ OK ]
[11:39:58] /bin/pwd                                          [ OK ]
[11:39:59] /bin/readlink                                     [ OK ]
[11:39:59] /bin/sed                                          [ OK ]
[11:39:59] /bin/sh                                           [ OK ]
[11:39:59] /bin/su                                           [ OK ]
[11:39:59] /bin/touch                                        [ OK ]
[11:39:59] /bin/uname                                        [ OK ]
[11:39:59] /bin/which                                        [ OK ]
[11:39:59] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[11:40:00] /bin/dash                                         [ OK ]
[11:40:00] /usr/bin/awk                                      [ OK ]
[11:40:00] /usr/bin/basename                                 [ OK ]
[11:40:00] /usr/bin/chattr                                   [ OK ]
[11:40:00] /usr/bin/cut                                      [ OK ]
[11:40:00] /usr/bin/diff                                     [ OK ]
[11:40:00] /usr/bin/dirname                                  [ OK ]
[11:40:01] /usr/bin/dpkg                                     [ OK ]
[11:40:01] /usr/bin/dpkg-query                               [ OK ]
[11:40:01] /usr/bin/du                                       [ OK ]
[11:40:01] /usr/bin/env                                      [ OK ]
[11:40:01] /usr/bin/file                                     [ OK ]
[11:40:01] /usr/bin/find                                     [ OK ]
[11:40:01] /usr/bin/GET                                      [ OK ]
[11:40:01] /usr/bin/groups                                   [ OK ]
[11:40:02] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[11:40:02] /usr/bin/head                                     [ OK ]
[11:40:02] /usr/bin/id                                       [ OK ]
[11:40:02] /usr/bin/killall                                  [ OK ]
[11:40:02] /usr/bin/last                                     [ OK ]
[11:40:02] /usr/bin/lastlog                                  [ OK ]
[11:40:02] /usr/bin/ldd                                      [ OK ]
[11:40:02] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[11:40:02] /usr/bin/less                                     [ OK ]
[11:40:02] /usr/bin/locate                                   [ OK ]
[11:40:03] /usr/bin/logger                                   [ OK ]
[11:40:03] /usr/bin/lsattr                                   [ OK ]
[11:40:03] /usr/bin/lsof                                     [ OK ]
[11:40:03] /usr/bin/mail                                     [ OK ]
[11:40:03] /usr/bin/md5sum                                   [ OK ]
[11:40:03] /usr/bin/mlocate                                  [ OK ]
[11:40:03] /usr/bin/newgrp                                   [ OK ]
[11:40:03] /usr/bin/passwd                                   [ OK ]
[11:40:04] /usr/bin/perl                                     [ OK ]
[11:40:04] /usr/bin/pstree                                   [ OK ]
[11:40:04] /usr/bin/rkhunter                                 [ OK ]
[11:40:04] /usr/bin/runcon                                   [ OK ]
[11:40:04] /usr/bin/sha1sum                                  [ OK ]
[11:40:04] /usr/bin/size                                     [ OK ]
[11:40:04] /usr/bin/sort                                     [ OK ]
[11:40:04] /usr/bin/stat                                     [ OK ]
[11:40:04] /usr/bin/strace                                   [ OK ]
[11:40:05] /usr/bin/strings                                  [ OK ]
[11:40:05] /usr/bin/sudo                                     [ OK ]
[11:40:05] /usr/bin/tail                                     [ OK ]
[11:40:05] /usr/bin/test                                     [ OK ]
[11:40:05] /usr/bin/top                                      [ OK ]
[11:40:05] /usr/bin/touch                                    [ OK ]
[11:40:05] /usr/bin/tr                                       [ OK ]
[11:40:05] /usr/bin/uniq                                     [ OK ]
[11:40:06] /usr/bin/users                                    [ OK ]
[11:40:06] /usr/bin/vmstat                                   [ OK ]
[11:40:06] /usr/bin/w                                        [ OK ]
[11:40:06] /usr/bin/watch                                    [ OK ]
[11:40:06] /usr/bin/wc                                       [ OK ]
[11:40:06] /usr/bin/wget                                     [ OK ]
[11:40:06] /usr/bin/whatis                                   [ OK ]
[11:40:06] /usr/bin/whereis                                  [ OK ]
[11:40:06] /usr/bin/which                                    [ OK ]
[11:40:07] /usr/bin/who                                      [ OK ]
[11:40:07] /usr/bin/whoami                                   [ OK ]
[11:40:07] /usr/bin/gawk                                     [ OK ]
[11:40:07] /usr/bin/lwp-request                              [ OK ]
[11:40:07] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[11:40:07] /usr/bin/bsd-mailx                                [ OK ]
[11:40:07] /usr/bin/w.procps                                 [ OK ]
[11:40:07] /sbin/depmod                                      [ OK ]
[11:40:08] /sbin/ifconfig                                    [ OK ]
[11:40:08] /sbin/ifdown                                      [ OK ]
[11:40:08] /sbin/ifup                                        [ OK ]
[11:40:08] /sbin/init                                        [ OK ]
[11:40:08] /sbin/insmod                                      [ OK ]
[11:40:08] /sbin/ip                                          [ OK ]
[11:40:08] /sbin/lsmod                                       [ OK ]
[11:40:09] /sbin/modinfo                                     [ OK ]
[11:40:09] /sbin/modprobe                                    [ OK ]
[11:40:09] /sbin/rmmod                                       [ OK ]
[11:40:09] /sbin/runlevel                                    [ OK ]
[11:40:09] /sbin/sulogin                                     [ OK ]
[11:40:09] /sbin/sysctl                                      [ OK ]
[11:40:09] /sbin/syslogd                                     [ OK ]
[11:40:10] /usr/sbin/adduser                                 [ OK ]
[11:40:10] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[11:40:10] /usr/sbin/chroot                                  [ OK ]
[11:40:10] /usr/sbin/cron                                    [ OK ]
[11:40:10] /usr/sbin/groupadd                                [ OK ]
[11:40:10] /usr/sbin/groupdel                                [ OK ]
[11:40:10] /usr/sbin/groupmod                                [ OK ]
[11:40:11] /usr/sbin/grpck                                   [ OK ]
[11:40:11] /usr/sbin/nologin                                 [ OK ]
[11:40:11] /usr/sbin/pwck                                    [ OK ]
[11:40:11] /usr/sbin/tcpd                                    [ OK ]
[11:40:11] /usr/sbin/unhide                                  [ Warning ]
[11:40:11] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[11:40:12] /usr/sbin/useradd                                 [ OK ]
[11:40:12] /usr/sbin/userdel                                 [ OK ]
[11:40:12] /usr/sbin/usermod                                 [ OK ]
[11:40:12] /usr/sbin/vipw                                    [ OK ]
[11:40:12] /usr/sbin/unhide-linux26                          [ Warning ]
[11:40:12] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[11:41:32]
[11:41:32] Checking for rootkits...
[11:41:32] Info: Starting test name 'rootkits'
[11:41:32]
[11:41:32] Performing check of known rootkit files and directories
[11:41:32] Info: Starting test name 'known_rkts'
[11:41:32]
[11:41:32] Checking for 55808 Trojan - Variant A...
[11:41:32]   Checking for file '/tmp/.../r'                  [ Not found ]
[11:41:32]   Checking for file '/tmp/.../a'                  [ Not found ]
[11:41:32] 55808 Trojan - Variant A                          [ Not found ]
[11:41:32]
[11:41:32] Checking for ADM Worm...
[11:41:32]   Checking for string 'w0rm'                      [ Not found ]
[11:41:32] ADM Worm                                          [ Not found ]
[11:41:32]
[11:41:32] Checking for AjaKit Rootkit...
[11:41:32]   Checking for file '/dev/tux/.addr'              [ Not found ]
[11:41:32]   Checking for file '/dev/tux/.proc'              [ Not found ]
[11:41:32]   Checking for file '/dev/tux/.file'              [ Not found ]
[11:41:32]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[11:41:32]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[11:41:32]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[11:41:32]   Checking for directory '/dev/tux'               [ Not found ]
[11:41:32]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[11:41:32] AjaKit Rootkit                                    [ Not found ]
[11:41:32]
[11:41:32] Checking for aPa Kit...
[11:41:32]   Checking for file '/usr/share/.aPa'             [ Not found ]
[11:41:32] aPa Kit                                           [ Not found ]
[11:41:32]
[11:41:32] Checking for Apache Worm...
[11:41:32]   Checking for file '/bin/.log'                   [ Not found ]
[11:41:32] Apache Worm                                       [ Not found ]
[11:41:33]
[11:41:33] Checking for Ambient (ark) Rootkit...
[11:41:33]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[11:41:33]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[11:41:33]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[11:41:33]   Checking for directory '/dev/ptyxx'             [ Not found ]
[11:41:33] Ambient (ark) Rootkit                             [ Not found ]
[11:41:33]
[11:41:33] Checking for Balaur Rootkit...
[11:41:33]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[11:41:33]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[11:41:33]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[11:41:33]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[11:41:33] Balaur Rootkit                                    [ Not found ]
[11:41:33]
[11:41:33] Checking for BeastKit Rootkit...
[11:41:33]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[11:41:33]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[11:41:33]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[11:41:33]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[11:41:33] BeastKit Rootkit                                  [ Not found ]
[11:41:33]
[11:41:33] Checking for beX2 Rootkit...
[11:41:33]   Checking for directory '/usr/include/bex'       [ Not found ]
[11:41:33] beX2 Rootkit                                      [ Not found ]
[11:41:33]
[11:41:33] Checking for BOBKit Rootkit...
[11:41:33]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[11:41:33]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../find'           [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../du'             [ Not found ]
[11:41:34]   Checking for file '/usr/lib/.../top'            [ Not found ]
[11:41:34]   Checking for directory '/usr/lib/...'           [ Not found ]
[11:41:34]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[11:41:34]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[11:41:34]   Checking for directory '/tmp/.bkp'              [ Not found ]
[11:41:34] BOBKit Rootkit                                    [ Not found ]
[11:41:34]
[11:41:34] Checking for CiNIK Worm (Slapper.B variant)...
[11:41:34]   Checking for file '/tmp/.cinik'                 [ Not found ]
[11:41:34]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[11:41:34] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[11:41:34]
[11:41:34] Checking for Danny-Boy's Abuse Kit...
[11:41:34]   Checking for file '/dev/mdev'                   [ Not found ]
[11:41:34]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[11:41:34] Danny-Boy's Abuse Kit                             [ Not found ]
[11:41:34]
[11:41:34] Checking for Devil RootKit...
[11:41:34]   Checking for file '/var/lib/games/.src'         [ Not found ]
[11:41:34]   Checking for file '/dev/dsx'                    [ Not found ]
[11:41:35]   Checking for file '/dev/caca'                   [ Not found ]
[11:41:35] Devil RootKit                                     [ Not found ]
[11:41:35]
[11:41:35] Checking for Dica-Kit Rootkit...
[11:41:35]   Checking for file '/lib/.sso'                   [ Not found ]
[11:41:35]   Checking for file '/lib/.so'                    [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/va'         [ Not found ]
[11:41:35]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[11:41:35]   Checking for file '/usr/bin/.etc'               [ Not found ]
[11:41:35]   Checking for directory '/var/run/...dica'       [ Not found ]
[11:41:35]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[11:41:35]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[11:41:35] Dica-Kit Rootkit                                  [ Not found ]
[11:41:35]
[11:41:35] Checking for Dreams Rootkit...
[11:41:35]   Checking for file '/dev/ttyoa'                  [ Not found ]
[11:41:35]   Checking for file '/dev/ttyof'                  [ Not found ]
[11:41:35]   Checking for file '/dev/ttyop'                  [ Not found ]
[11:41:35]   Checking for file '/usr/bin/sense'              [ Not found ]
[11:41:35]   Checking for file '/usr/bin/sl2'                [ Not found ]
[11:41:35]   Checking for file '/usr/bin/logclear'           [ Not found ]
[11:41:35]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[11:41:35]   Checking for file '/usr/bin/snfs'               [ Not found ]
[11:41:35]   Checking for file '/usr/lib/libsss'             [ Not found ]
[11:41:35]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[11:41:36] Dreams Rootkit                                    [ Not found ]
[11:41:36]
[11:41:36] Checking for Duarawkz Rootkit...
[11:41:36]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[11:41:36]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[11:41:36] Duarawkz Rootkit                                  [ Not found ]
[11:41:36]
[11:41:36] Checking for Enye LKM...
[11:41:36]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[11:41:36] Enye LKM                                          [ Not found ]
[11:41:36]
[11:41:36] Checking for Flea Linux Rootkit...
[11:41:36]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:41:36]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[11:41:36]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[11:41:36]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[11:41:36]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[11:41:36]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[11:41:36]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[11:41:36]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[11:41:36]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[11:41:36]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[11:41:36]   Checking for directory '/dev/..0'               [ Not found ]
[11:41:36]   Checking for directory '/dev/..0/backup'        [ Not found ]
[11:41:36] Flea Linux Rootkit                                [ Not found ]
[11:41:36]
[11:41:36] Checking for FreeBSD Rootkit...
[11:41:36]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[11:41:36]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[11:41:36]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[11:41:36]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[11:41:36]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[11:41:36]   Checking for file '/bin/sysback'                [ Not found ]
[11:41:36]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[11:41:37]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[11:41:37]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[11:41:37] FreeBSD Rootkit                                   [ Not found ]
[11:41:37]
[11:41:37] Checking for ****`it Rootkit...
[11:41:37]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[11:41:37]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[11:41:37] ****`it Rootkit                                   [ Not found ]
[11:41:37]
[11:41:37] Checking for GasKit Rootkit...
[11:41:37]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[11:41:37]   Checking for directory '/dev/dev'               [ Not found ]
[11:41:37]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[11:41:37]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[11:41:37] GasKit Rootkit                                    [ Not found ]
[11:41:37]
[11:41:37] Checking for Heroin LKM...
[11:41:37]   Checking for kernel symbol 'heroin'             [ Not found ]
[11:41:37] Heroin LKM                                        [ Not found ]
[11:41:37]
[11:41:37] Checking for HjC Kit...
[11:41:37]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[11:41:37] HjC Kit                                           [ Not found ]
[11:41:37]
[11:41:37] Checking for ignoKit Rootkit...
[11:41:37]   Checking for file '/lib/defs/p'                 [ Not found ]
[11:41:37]   Checking for file '/lib/defs/q'                 [ Not found ]
[11:41:38]   Checking for file '/lib/defs/r'                 [ Not found ]
[11:41:38]   Checking for file '/lib/defs/s'                 [ Not found ]
[11:41:38]   Checking for file '/lib/defs/t'                 [ Not found ]
[11:41:38]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[11:41:38]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[11:41:38]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[11:41:38]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[11:41:38]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[11:41:38]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[11:41:38]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[11:41:38]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[11:41:38]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[11:41:38] ignoKit Rootkit                                   [ Not found ]
[11:41:38]
[11:41:38] Checking for ImperalsS-FBRK Rootkit...
[11:41:38]   Checking for directory '/dev/fd/.88'            [ Not found ]
[11:41:38]   Checking for directory '/dev/fd/.99'            [ Not found ]
[11:41:38] ImperalsS-FBRK Rootkit                            [ Not found ]
[11:41:38]
[11:41:38] Checking for Irix Rootkit...
[11:41:38]   Checking for directory '/dev/pts/01'            [ Not found ]
[11:41:38]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[11:41:38]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[11:41:38]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[11:41:38] Irix Rootkit                                      [ Not found ]
[11:41:38]
[11:41:38] Checking for Kitko Rootkit...
[11:41:38]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[11:41:38] Kitko Rootkit                                     [ Not found ]
[11:41:38]
[11:41:38] Checking for Knark Rootkit...
[11:41:38]   Checking for file '/proc/knark/pids'            [ Not found ]
[11:41:38]   Checking for directory '/proc/knark'            [ Not found ]
[11:41:39] Knark Rootkit                                     [ Not found ]
[11:41:39]
[11:41:39] Checking for Li0n Worm...
[11:41:39]   Checking for file '/bin/in.telnetd'             [ Not found ]
[11:41:39]   Checking for file '/bin/mjy'                    [ Not found ]
[11:41:39]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[11:41:39]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[11:41:39]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[11:41:39]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[11:41:39] Li0n Worm                                         [ Not found ]
[11:41:39]
[11:41:39] Checking for Lockit / LJK2 Rootkit...
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[11:41:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[11:41:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[11:41:40]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[11:41:40] Lockit / LJK2 Rootkit                             [ Not found ]
[11:41:40]
[11:41:40] Checking for Mood-NT Rootkit...
[11:41:40]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[11:41:41]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[11:41:41]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[11:41:41]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[11:41:41]   Checking for directory '/_cthulhu'              [ Not found ]
[11:41:41] Mood-NT Rootkit                                   [ Not found ]
[11:41:41]
[11:41:41] Checking for MRK Rootkit...
[11:41:41]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[11:41:41]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[11:41:41]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[11:41:41]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[11:41:41]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[11:41:41]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[11:41:41] MRK Rootkit                                       [ Not found ]
[11:41:41]
[11:41:41] Checking for Ni0 Rootkit...
[11:41:41]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[11:41:41]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[11:41:41]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[11:41:41]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[11:41:41]   Checking for directory '/tmp/waza'              [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[11:41:41]   Checking for directory '/usr/sbin/es'           [ Not found ]
[11:41:41] Ni0 Rootkit                                       [ Not found ]
[11:41:41]
[11:41:41] Checking for Ohhara Rootkit...
[11:41:41]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[11:41:41]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[11:41:42] Ohhara Rootkit                                    [ Not found ]
[11:41:42]
[11:41:42] Checking for Optic Kit (Tux) Worm...
[11:41:42]   Checking for directory '/dev/tux'               [ Not found ]
[11:41:42]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[11:41:42]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[11:41:42]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[11:41:42] Optic Kit (Tux) Worm                              [ Not found ]
[11:41:42]
[11:41:42] Checking for Oz Rootkit...
[11:41:42]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[11:41:42]   Checking for directory '/dev/.oz'               [ Not found ]
[11:41:42] Oz Rootkit                                        [ Not found ]
[11:41:42]
[11:41:42] Checking for Phalanx Rootkit...
[11:41:42]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[11:41:42]   Checking for file '/etc/host.ph1'               [ Not found ]
[11:41:42]   Checking for file '/bin/host.ph1'               [ Not found ]
[11:41:42]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[11:41:42]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[11:41:42] Phalanx Rootkit                                   [ Not found ]
[11:41:42]
[11:41:42] Checking for Phalanx Rootkit (strings)...
[11:41:42]   Checking for string 'phalanx'                   [ Not found ]
[11:41:42] Phalanx Rootkit (strings)                         [ Not found ]
[11:41:42]
[11:41:42] Checking for Portacelo Rootkit...
[11:41:42]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../.p'             [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../getty'          [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[11:41:42]   Checking for file '/var/lib/.../show'           [ Not found ]
[11:41:43]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[11:41:43]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[11:41:43]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[11:41:43]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[11:41:43]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[11:41:43]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[11:41:43] Portacelo Rootkit                                 [ Not found ]
[11:41:43]
[11:41:43] Checking for R3dstorm Toolkit...
[11:41:43]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[11:41:43]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[11:41:43]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[11:41:43]   Checking for file '/bin/.../see_all'            [ Not found ]
[11:41:43]   Checking for directory '/var/log/tk02'          [ Not found ]
[11:41:43]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[11:41:43]   Checking for directory '/bin/...'               [ Not found ]
[11:41:43] R3dstorm Toolkit                                  [ Not found ]
[11:41:43]
[11:41:43] Checking for RH-Sharpe's Rootkit...
[11:41:43]   Checking for file '/bin/lps'                    [ Not found ]
[11:41:43]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[11:41:43]   Checking for file '/usr/bin/ltop'               [ Not found ]
[11:41:43]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[11:41:43]   Checking for file '/usr/bin/ldu'                [ Not found ]
[11:41:43]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[11:41:43]   Checking for file '/usr/bin/wp'                 [ Not found ]
[11:41:43]   Checking for file '/usr/bin/shad'               [ Not found ]
[11:41:43]   Checking for file '/usr/bin/vadim'              [ Not found ]
[11:41:43]   Checking for file '/usr/bin/slice'              [ Not found ]
[11:41:43]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[11:41:43]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[11:41:43] RH-Sharpe's Rootkit                               [ Not found ]
[11:41:44]
[11:41:44] Checking for RSHA's Rootkit...
[11:41:44]   Checking for file '/bin/kr4p'                   [ Not found ]
[11:41:44]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[11:41:44]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[11:41:44]   Checking for file '/usr/bin/slice2'             [ Not found ]
[11:41:44]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[11:41:44]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[11:41:44]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[11:41:44]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[11:41:44] RSHA's Rootkit                                    [ Not found ]
[11:41:44]
[11:41:44] Checking for Scalper Worm...
[11:41:44]   Checking for file '/tmp/.a'                     [ Not found ]
[11:41:44]   Checking for file '/tmp/.uua'                   [ Not found ]
[11:41:44] Scalper Worm                                      [ Not found ]
[11:41:44]
[11:41:44] Checking for Sebek LKM...
[11:41:44]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[11:41:44] Sebek LKM                                         [ Not found ]
[11:41:45]
[11:41:45] Checking for Shutdown Rootkit...
[11:41:45]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[11:41:45]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[11:41:45]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[11:41:45]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[11:41:45]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[11:41:45]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[11:41:45]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[11:41:45]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[11:41:45] Shutdown Rootkit                                  [ Not found ]
[11:41:45]
[11:41:45] Checking for SHV4 Rootkit...
[11:41:45]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:41:45]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[11:41:45]   Checking for file '/lib/lidps1.so'              [ Not found ]
[11:41:45]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[11:41:45]   Checking for directory '/lib/security/.config'  [ Not found ]
[11:41:45]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[11:41:45] SHV4 Rootkit                                      [ Not found ]
[11:41:45]
[11:41:45] Checking for SHV5 Rootkit...
[11:41:45]   Checking for file '/etc/sh.conf'                [ Not found ]
[11:41:45]   Checking for file '/dev/srd0'                   [ Not found ]
[11:41:45]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[11:41:45] SHV5 Rootkit                                      [ Not found ]
[11:41:45]
[11:41:45] Checking for Sin Rootkit...
[11:41:45]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[11:41:45]   Checking for file '/dev/ttyoa'                  [ Not found ]
[11:41:45]   Checking for file '/dev/ttyof'                  [ Not found ]
[11:41:45]   Checking for file '/dev/ttyop'                  [ Not found ]
[11:41:45]   Checking for file '/dev/ttyos'                  [ Not found ]
[11:41:46]   Checking for file '/usr/lib/.lib'               [ Not found ]
[11:41:46]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[11:41:46]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[11:41:46]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[11:41:46]   Checking for file '/usr/man/man1/...'           [ Not found ]
[11:41:46]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[11:41:46]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[11:41:46]   Checking for directory '/usr/lib/sn'            [ Not found ]
[11:41:46]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[11:41:46]   Checking for directory '/dev/.haos'             [ Not found ]
[11:41:46] Sin Rootkit                                       [ Not found ]
[11:41:46]
[11:41:46] Checking for Slapper Worm...
[11:41:46]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[11:41:46]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[11:41:46]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[11:41:46]   Checking for file '/tmp/httpd'                  [ Not found ]
[11:41:46]   Checking for file '/tmp/.unlock'                [ Not found ]
[11:41:46]   Checking for file '/tmp/update'                 [ Not found ]
[11:41:46]   Checking for file '/tmp/.cinik'                 [ Not found ]
[11:41:46]   Checking for file '/tmp/.b'                     [ Not found ]
[11:41:46] Slapper Worm                                      [ Not found ]
[11:41:46]
[11:41:46] Checking for Sneakin Rootkit...
[11:41:46]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[11:41:46] Sneakin Rootkit                                   [ Not found ]
[11:41:46]
[11:41:46] Checking for Suckit Rootkit...
[11:41:46]   Checking for file '/sbin/initsk12'              [ Not found ]
[11:41:46]   Checking for file '/sbin/initxrk'               [ Not found ]
[11:41:46]   Checking for file '/usr/bin/null'               [ Not found ]
[11:41:46]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[11:41:46]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[11:41:47]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[11:41:47]   Checking for directory '/etc/.MG'               [ Not found ]
[11:41:47]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[11:41:47]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[11:41:47] Suckit Rootkit                                    [ Not found ]
[11:41:47]
[11:41:47] Checking for SunOS Rootkit...
[11:41:47]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:41:47]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[11:41:47]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[11:41:47]   Checking for file '/bin/xlogin'                 [ Not found ]
[11:41:47]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[11:41:47]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[11:41:47]   Checking for file '/sbin/login'                 [ Not found ]
[11:41:47]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[11:41:47]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[11:41:47]   Checking for file '/dev/kmod'                   [ Not found ]
[11:41:47]   Checking for file '/dev/dos'                    [ Not found ]
[11:41:47] SunOS Rootkit                                     [ Not found ]
[11:41:47]
[11:41:47] Checking for SunOS / NSDAP Rootkit...
[11:41:47]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[11:41:47]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[11:41:47]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[11:41:47]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[11:41:47]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[11:41:48]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[11:41:48]   Checking for file '/usr/lib/lpset'              [ Not found ]
[11:41:48]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[11:41:48] SunOS / NSDAP Rootkit                             [ Not found ]
[11:41:48]
[11:41:48] Checking for Superkit Rootkit...
[11:41:48]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[11:41:48] Superkit Rootkit                                  [ Not found ]
[11:41:48]
[11:41:48] Checking for TBD (Telnet BackDoor)...
[11:41:48]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[11:41:48] TBD (Telnet BackDoor)                             [ Not found ]
[11:41:48]
[11:41:48] Checking for TeLeKiT Rootkit...
[11:41:48]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[11:41:48]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[11:41:48]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[11:41:48]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[11:41:48]   Checking for file '/dev/ptyr'                   [ Not found ]
[11:41:48]   Checking for file '/dev/ptyp'                   [ Not found ]
[11:41:48]   Checking for file '/dev/ptyq'                   [ Not found ]
[11:41:48]   Checking for file '/dev/hda06'                  [ Not found ]
[11:41:48]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[11:41:48]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[11:41:48]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[11:41:48]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[11:41:48] TeLeKiT Rootkit                                   [ Not found ]
[11:41:48]
[11:41:48] Checking for T0rn Rootkit...
[11:41:49]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[11:41:49]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[11:41:49]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[11:41:49]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[11:41:49]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[11:41:49]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[11:41:49]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[11:41:49]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[11:41:49]   Checking for directory '/dev/.lib'              [ Not found ]
[11:41:49]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[11:41:50]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[11:41:50]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[11:41:50]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[11:41:50]   Checking for directory '/usr/src/.****'         [ Not found ]
[11:41:50]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[11:41:50]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[11:41:50]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[11:41:50]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[11:41:50] T0rn Rootkit                                      [ Not found ]
[11:41:50]
[11:41:50] Checking for Trojanit Kit...
[11:41:50]   Checking for file '/bin/.ls'                    [ Not found ]
[11:41:50]   Checking for file '/bin/.ps'                    [ Not found ]
[11:41:50]   Checking for file '/bin/.netstat'               [ Not found ]
[11:41:50]   Checking for file '/usr/bin/.nop'               [ Not found ]
[11:41:50]   Checking for file '/usr/bin/.who'               [ Not found ]
[11:41:50] Trojanit Kit                                      [ Not found ]
[11:41:50]
[11:41:50] Checking for Tuxtendo Rootkit...
[11:41:50]   Checking for file '/dev/tux/.addr'              [ Not found ]
[11:41:50]   Checking for file '/dev/tux/.cron'              [ Not found ]
[11:41:50]   Checking for file '/dev/tux/.file'              [ Not found ]
[11:41:50]   Checking for file '/dev/tux/.log'               [ Not found ]
[11:41:50]   Checking for file '/dev/tux/.proc'              [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[11:41:50]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[11:41:51]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[11:41:51]   Checking for directory '/dev/tux'               [ Not found ]
[11:41:51]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[11:41:51]   Checking for directory '/dev/tux/backup'        [ Not found ]
[11:41:51] Tuxtendo Rootkit                                  [ Not found ]
[11:41:51]
[11:41:51] Checking for URK Rootkit...
[11:41:51]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[11:41:51]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[11:41:51]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[11:41:51]   Checking for file '/tmp/conf.inf'               [ Not found ]
[11:41:51]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[11:41:51] URK Rootkit                                       [ Not found ]
[11:41:51]
[11:41:51] Checking for VcKit Rootkit...
[11:41:51]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[11:41:51]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[11:41:51] VcKit Rootkit                                     [ Not found ]
[11:41:51]
[11:41:51] Checking for Volc Rootkit...
[11:41:51]   Checking for directory '/var/spool/.recent'     [ Not found ]
[11:41:51]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[11:41:51]   Checking for directory '/usr/lib/volc'          [ Not found ]
[11:41:51]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[11:41:51] Volc Rootkit                                      [ Not found ]
[11:41:51]
[11:41:51] Checking for X-Org SunOS Rootkit...
[11:41:51]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[11:41:51]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[11:41:52]   Checking for file '/usr/bin/srload'             [ Not found ]
[11:41:52]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[11:41:52]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[11:41:52]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[11:41:52]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[11:41:52]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[11:41:52]   Checking for directory '/usr/share/man...'      [ Not found ]
[11:41:52] X-Org SunOS Rootkit                               [ Not found ]
[11:41:52]
[11:41:52] Checking for zaRwT.KiT Rootkit...
[11:41:52]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[11:41:52]   Checking for file '/dev/ttyf'                   [ Not found ]
[11:41:52]   Checking for file '/dev/ttyp'                   [ Not found ]
[11:41:52]   Checking for file '/dev/ttyn'                   [ Not found ]
[11:41:52]   Checking for file '/rk/tulz'                    [ Not found ]
[11:41:52]   Checking for directory '/rk'                    [ Not found ]
[11:41:52]   Checking for directory '/dev/rd/s'              [ Not found ]
[11:41:52] zaRwT.KiT Rootkit                                 [ Not found ]
[11:41:52]
[11:41:52] Performing additional rootkit checks
[11:41:52] Info: Starting test name 'additional_rkts'
[11:41:52]
[11:41:52]   Performing Suckit Rookit additional checks
[11:41:52]     Checking /sbin/init link count                [ OK ]
[11:41:52]     Checking for hidden file extensions           [ None found ]
[11:41:52]     Running skdet command                         [ Skipped ]
[11:41:52] Info: Unable to find the 'skdet' command
[11:41:52]   Suckit Rookit additional checks                 [ OK ]
[11:41:52]
[11:41:52]   Performing check of possible rootkit files and directories
[11:41:52] Info: Starting test name 'possible_rkt_files'
[11:41:52]     Checking for file '/dev/sdr0'                 [ Not found ]
[11:41:52]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[11:41:53]     Checking for file '/tmp/.bash_history'        [ Not found ]
[11:41:53]     Checking for file '/usr/info/.clib'           [ Not found ]
[11:41:53]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[11:41:53]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[11:41:53]     Checking for file '/sbin/create'              [ Not found ]
[11:41:53]     Checking for file '/dev/ttypz'                [ Not found ]
[11:41:53]     Checking for directory '/usr/bin/take'        [ Not found ]
[11:41:53]     Checking for directory '/usr/src/.lib'        [ Not found ]
[11:41:53]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[11:41:53]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[11:41:53]     Checking for directory '/usr/sbin/...'        [ Not found ]
[11:41:53]     Checking for directory '/usr/share/.gun'      [ Not found ]
[11:41:53]   Checking for possible rootkit files and directories [ None found ]
[11:41:53]
[11:41:53]   Performing check for possible rootkit strings
[11:41:53] Info: Starting test name 'possible_rkt_strings'
[11:41:53] Info: Found local startup file: /etc/rc.local
[11:41:53]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[11:41:53]     Checking for string '****'                    [ Not found ]
[11:41:53]     Checking for string 'backdoor'                [ Not found ]
[11:41:53]     Checking for string 'vt200'                   [ Not found ]
[11:41:53]     Checking for string '/usr/bin/xstat'          [ Not found ]
[11:41:53]     Checking for string '/bin/envpc'              [ Not found ]
[11:41:53]     Checking for string 'L4m3r0x'                 [ Not found ]
[11:41:53]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:41:54]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[11:41:54]     Checking for string '/dev/sgk'                [ Not found ]
[11:41:54]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:41:54]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:41:54]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[11:41:54]     Checking for string '/lib/.sso'               [ Not found ]
[11:41:54]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:41:54]     Checking for string '/dev/caca'               [ Not found ]
[11:41:54]     Checking for string '/dev/ttyoa'              [ Not found ]
[11:41:54]     Checking for string 'syg'                     [ Not found ]
[11:41:54]     Checking for string '/dev/pts/01'             [ Not found ]
[11:41:54]     Checking for string 'tw33dl3'                 [ Not found ]
[11:41:54]     Checking for string 'psniff'                  [ Not found ]
[11:41:54]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:41:54]     Checking for string 'promiscuous'             [ Not found ]
[11:41:54]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:41:54]     Checking for string '/dev/xdta'               [ Not found ]
[11:41:54]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:41:55]     Checking for string 'in.inetd'                [ Not found ]
[11:41:55]     Checking for string '#<HIDE_.*>'              [ Not found ]
[11:41:55]     Checking for string 'bin/xchk'                [ Not found ]
[11:41:55]     Checking for string 'bin/xsf'                 [ Not found ]
[11:41:55]   Checking for possible rootkit strings           [ None found ]
[11:41:55]
[11:41:55] Performing malware checks
[11:41:55] Info: Starting test name 'malware'
[11:41:55]
[11:41:55] Info: Test 'deleted_files' disabled at users request.
[11:41:55] Info: Starting test name 'running_procs'
[11:41:55]   Checking running processes for suspicious files [ None found ]
[11:41:55]
[11:41:55] Info: Test 'hidden_procs' disabled at users request.
[11:41:55]
[11:41:55] Info: Test 'suspscan' disabled at users request.
[11:41:55]
[11:41:55]   Performing check for login backdoors
[11:41:55] Info: Starting test name 'other_malware'
[11:41:55]     Checking for '/bin/.login'                    [ Not found ]
[11:41:55]     Checking for '/sbin/.login'                   [ Not found ]
[11:41:55]   Checking for login backdoors                    [ None found ]
[11:41:55]
[11:41:55]   Performing check for suspicious directories
[11:41:55]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[11:41:56]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[11:41:56]   Checking for suspicious directories             [ None found ]
[11:41:56]
[11:41:56]   Checking for software intrusions                [ Skipped ]
[11:41:56] Info: Check skipped - tripwire not installed
[11:41:56]
[11:41:56]   Performing check for sniffer log files
[11:41:56]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[11:41:56]   Checking for sniffer log files                  [ None found ]
[11:41:56]
[11:41:56] Performing trojan specific checks
[11:41:56] Info: Starting test name 'trojans'
[11:41:56] Info: Using inetd configuration file '/etc/inetd.conf'
[11:41:56]   Checking for enabled inetd services             [ OK ]
[11:41:56]
[11:41:56]   Performing check for enabled xinetd services
[11:41:56]   Checking for enabled xinetd services            [ Skipped ]
[11:41:56] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[11:41:56]   Checking for Apache backdoor                    [ Not found ]
[11:41:56]
[11:41:56] Performing Linux specific checks
[11:41:56] Info: Starting test name 'os_specific'
[11:41:56]   Checking kernel module commands                 [ OK ]
[11:41:56] Info: Using modules pathname of '/lib/modules/2.6.28-11-generic'
[11:41:56]   Checking kernel module names                    [ OK ]
[11:42:00]
[11:42:00] Checking the network...
[11:42:01] Info: Starting test name 'network'
[11:42:01] Info: Starting test name 'ports'
[11:42:01]
[11:42:01] Performing check for backdoor ports
[11:42:01]   Checking for UDP port 2001                      [ Not found ]
[11:42:01]   Checking for TCP port 2006                      [ Not found ]
[11:42:01]   Checking for TCP port 2128                      [ Not found ]
[11:42:01]   Checking for TCP port 14856                     [ Not found ]
[11:42:01]   Checking for TCP port 47107                     [ Not found ]
[11:42:01]   Checking for TCP port 60922                     [ Not found ]
[11:42:01]
[11:42:01] Performing checks on the network interfaces
[11:42:01] Info: Starting test name 'promisc'
[11:42:01]   Checking for promiscuous interfaces             [ None found ]
[11:42:01]
[11:42:01] Info: Test 'packet_cap_apps' disabled at users request.
[11:42:03]
[11:42:03] Checking the local host...
[11:42:03] Info: Starting test name 'local_host'
[11:42:03]
[11:42:03] Performing system boot checks
[11:42:03] Info: Starting test name 'startup_files'
[11:42:03]   Checking for local host name                    [ Found ]
[11:42:03] Info: Starting test name 'startup_malware'
[11:42:03] Info: Found local startup file: /etc/rc.local
[11:42:03]   Checking for local startup files                [ Found ]
[11:42:04]   Checking local startup files for malware        [ None found ]
[11:42:04] Info: Found system startup directory: /etc/init.d
[11:42:05]   Checking system startup files for malware       [ None found ]
[11:42:05]
[11:42:05] Performing group and account checks
[11:42:05] Info: Starting test name 'group_accounts'
[11:42:05]   Checking for passwd file                        [ Found ]
[11:42:05] Info: Found password file: /etc/passwd
[11:42:05]   Checking for root equivalent (UID 0) accounts   [ None found ]
[11:42:05] Info: Found shadow file: /etc/shadow
[11:42:05]   Checking for passwordless accounts              [ None found ]
[11:42:05] Info: Starting test name 'passwd_changes'
[11:42:05]   Checking for passwd file changes                [ None found ]
[11:42:05] Info: Starting test name 'group_changes'
[11:42:05]   Checking for group file changes                 [ None found ]
[11:42:05]   Checking root account shell history files       [ None found ]
[11:42:05]
[11:42:05] Performing system configuration file checks
[11:42:05] Info: Starting test name 'system_configs'
[11:42:06]   Checking for SSH configuration file             [ Not found ]
[11:42:06]   Checking for running syslog daemon              [ Warning ]
[11:42:06] Warning: The syslog daemon is not running.
[11:42:06]   Checking for syslog configuration file          [ Found ]
[11:42:06] Info: Found syslog configuration file: /etc/syslog.conf
[11:42:06]   Checking if syslog remote logging is allowed    [ Not allowed ]
[11:42:06]
[11:42:06] Performing filesystem checks
[11:42:06] Info: Starting test name 'filesystem'
[11:42:06] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:42:06]   Checking /dev for suspicious file types         [ Warning ]
[11:42:06] Warning: Suspicious file types found in /dev:
[11:42:06]          /dev/shm/pulse-shm-1165159497: data
[11:42:06]   Checking for hidden files and directories       [ None found ]
[11:42:18]
[11:42:18] Checking application versions...
[11:42:18] Info: Starting test name 'apps'
[11:42:18] Info: Application 'exim' not found.
[11:42:18]   Checking version of GnuPG                       [ OK ]
[11:42:18] Info: Application 'gpg' version '1.4.9' found.
[11:42:18] Info: Application 'httpd' not found.
[11:42:18] Info: Application 'named' not found.
[11:42:18]   Checking version of OpenSSL                     [ OK ]
[11:42:18] Info: Application 'openssl' version '0.9.8g' found.
[11:42:18] Info: Application 'php' not found.
[11:42:18] Info: Application 'procmail' not found.
[11:42:18] Info: Application 'proftpd' not found.
[11:42:18] Info: Application 'sshd' not found.
[11:42:18] Info: Applications checked: 2 out of 9
[11:42:18]
[11:42:18] System checks summary
[11:42:18] =====================
[11:42:19]
[11:42:19] File properties checks...
[11:42:19] Files checked: 127
[11:42:19] Suspect files: 2
[11:42:19]
[11:42:19] Rootkit checks...
[11:42:19] Rootkits checked : 109
[11:42:19] Possible rootkits: 0
[11:42:19]
[11:42:19] Applications checks...
[11:42:19] Applications checked: 2
[11:42:19] Suspect applications: 0
[11:42:19]
[11:42:19] The system checks took: 2 minutes and 26 seconds
[11:42:19]
[11:42:19] Info: End date is Sat Jun 13 11:42:19 EDT 2009
```

So what think?
:o

---

### Post by zuerston on 2009-06-13
The other info
```
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     INFECTED (PORTS:  465)
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[5591], /sbin/dhclient3[7121])
virbr0: PACKET SNIFFER(/usr/sbin/arpalert[5549])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user xaaxa deleted or never logged from lastlog!
xaaxa@xaaxa-laptop:~$ sudo rkhunter

Usage: rkhunter {--check | --update | --propupd | --versioncheck |
                 --list [tests | languages | rootkits] |
                 --version | --help} [options]

Current options are:
         --append-log                  Append to the logfile, do not overwrite
         --bindir <directory>...       Use the specified command directories
     -c, --check                       Check the local system
  --cs2, --color-set2                  Use the second color set for output
         --configfile <file>           Use the specified configuration file
         --cronjob                     Run as a cron job
                                       (implies -c, --sk and --nocolors options)
         --dbdir <directory>           Use the specified database directory
         --debug                       Debug mode
                                       (Do not use unless asked to do so)
         --disable <test>[,<test>...]  Disable specific tests
                                       (Default is to disable no tests)
         --display-logfile             Display the logfile at the end
         --enable  <test>[,<test>...]  Enable specific tests
                                       (Default is to enable all tests)
         --hash {MD5 | SHA1 | NONE |   Use the specified file hash function
                 <command>}            (Default is SHA1)
     -h, --help                        Display this help menu, then exit
 --lang, --language <language>         Specify the language to use
                                       (Default is English)
         --list [tests | languages |   List the available test names, languages,
                 rootkits]             or checked for rootkits, then exit
     -l, --logfile [file]              Write to a logfile
                                       (Default is /var/log/rkhunter.log)
         --noappend-log                Do not append to the logfile, overwrite it
         --nocolors                    Use black and white output
         --nolog                       Do not write to a logfile
--nomow, --no-mail-on-warning          Do not send a message if warnings occur
   --ns, --nosummary                   Do not show the summary of check results
 --novl, --no-verbose-logging          No verbose logging
         --pkgmgr {RPM | DPKG | BSD |  Use the specified package manager to obtain or
                   NONE}               verify file hash values. (Default is NONE)
         --propupd                     Update the file properties database
     -q, --quiet                       Quiet mode (no output at all)
  --rwo, --report-warnings-only        Show only warning messages
     -r, --rootdir <directory>         Use the specified root directory
   --sk, --skip-keypress               Don't wait for a keypress after each test
         --summary                     Show the summary of system check results
                                       (This is the default)
         --syslog [facility.priority]  Log the check start and finish times to syslog
                                       (Default level is authpriv.notice)
         --tmpdir <directory>          Use the specified temporary directory
         --update                      Check for updates to database files
   --vl, --verbose-logging             Use verbose logging (on by default)
     -V, --version                     Display the version number, then exit
         --versioncheck                Check for latest version of program
     -x, --autox                       Automatically detect if X is in use
     -X, --no-autox                    Do not automatically detect if X is in use

xaaxa@xaaxa-laptop:~$ rkhunter -c
You must be the root user to run this program.
xaaxa@xaaxa-laptop:~$ sudo rkhunter -c
[ Rootkit Hunter version 1.3.2 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
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
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
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
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
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
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
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
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
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
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for Apache backdoor                             [ Not found ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Warning ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ None found ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 127
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 2
    Suspect applications: 0

The system checks took: 2 minutes and 26 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

xaaxa@xaaxa-laptop:~$ gkedit /var/log/rkhunter.log
bash: gkedit: command not found
xaaxa@xaaxa-laptop:~$ sudo dolphin
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xaaxa" is owned by uid 1000 instead of uid 0.
"/usr/bin/dolphin(30620)" Error in thread 3049666304 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(30620)" Error in thread 3049666304 : "QLocalSocket::connectToServer: Invalid name"
dolphin(30620) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/home/xaaxa/.kde/share/apps/nepomuk/socket"
dolphin(30620): Attempt to use QAction "close_tab" with KXMLGUIFactory! 
dolphin(30620): Attempt to use QAction "show_info_panel" with KXMLGUIFactory! 
dolphin(30620): Attempt to use QAction "show_folders_panel" with KXMLGUIFactory! 
dolphin(30620): Attempt to use QAction "show_terminal_panel" with KXMLGUIFactory! 
dolphin(30620): Attempt to use QAction "show_places_panel" with KXMLGUIFactory! 
xaaxa@xaaxa-laptop:~$ Error: "/tmp/ksocket-xaaxa" is owned by uid 1000 instead of uid 0.
dolphin(30620) KToolInvocation::klauncher: klauncher not running... launching kdeinit
Error: "/tmp/kde-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-xaaxa" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xaaxa" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xaaxa" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
WARNING: field 'http://strigi.sf.net/ontologies/0.9#debugParseError' is not defined in any rdfs ontology database.
/usr/lib/strigi/strigila_deb.so
/usr/lib/strigi/strigita_audible.so
/usr/lib/strigi/strigita_avi.so
/usr/lib/strigi/strigila_namespaceharvester.so
/usr/lib/strigi/strigita_dds.so
/usr/lib/strigi/strigila_txt.so
/usr/lib/strigi/strigita_sid.so
/usr/lib/strigi/strigita_wav.so
/usr/lib/strigi/strigila_cpp.so
/usr/lib/strigi/strigita_xbm.so
/usr/lib/strigi/strigita_pcx.so
/usr/lib/strigi/strigita_au.so
/usr/lib/strigi/strigita_mp4.so
/usr/lib/strigi/strigita_ico.so
/usr/lib/strigi/strigita_gif.so
/usr/lib/strigi/strigila_xpm.so
/usr/lib/strigi/strigita_rgb.so
/usr/lib/strigi/strigiea_jpeg.so
WARNING: field 'maxLineLength' is not defined in any rdfs ontology database.
WARNING: field 'line ending format' is not defined in any rdfs ontology database.
WARNING: field 'content.mime_type' is not defined in any rdfs ontology database.
WARNING: field 'audio.title' is not defined in any rdfs ontology database.
WARNING: field 'audio.artist' is not defined in any rdfs ontology database.
WARNING: field 'todo.audio.narrator' is not defined in any rdfs ontology database.
WARNING: field 'media.codec' is not defined in any rdfs ontology database.
WARNING: field 'todo.audible.user_id' is not defined in any rdfs ontology database.
WARNING: field 'todo.audible.user_alias' is not defined in any rdfs ontology database.
WARNING: field 'audio.duration' is not defined in any rdfs ontology database.
WARNING: field 'content.description' is not defined in any rdfs ontology database.
WARNING: field 'content.copyright' is not defined in any rdfs ontology database.
WARNING: field 'content.keyword' is not defined in any rdfs ontology database.
WARNING: field 'content.creation_time' is not defined in any rdfs ontology database.
WARNING: field 'content.maintainer' is not defined in any rdfs ontology database.
WARNING: field 'content.ID' is not defined in any rdfs ontology database.
WARNING: field 'audio.channel_count' is not defined in any rdfs ontology database.
WARNING: field 'dds volume depth' is not defined in any rdfs ontology database.
WARNING: field 'dds mipmap count' is not defined in any rdfs ontology database.
WARNING: field 'dds image type' is not defined in any rdfs ontology database.
WARNING: field 'document.stats.image_count' is not defined in any rdfs ontology database.
WARNING: field 'content.genre' is not defined in any rdfs ontology database.
WARNING: field 'TODO_trackNumber' is not defined in any rdfs ontology database.
WARNING: field 'TODO_discNumber' is not defined in any rdfs ontology database.
WARNING: field 'content.author' is not defined in any rdfs ontology database.
WARNING: field 'content.comment' is not defined in any rdfs ontology database.
WARNING: field 'audio.album' is not defined in any rdfs ontology database.
WARNING: field 'TODO_audio.albumartist' is not defined in any rdfs ontology database.
WARNING: field 'content.links' is not defined in any rdfs ontology database.
WARNING: field 'TODO_content.purchaser' is not defined in any rdfs ontology database.
WARNING: field 'TODO_content.purchasedate' is not defined in any rdfs ontology database.
WARNING: field 'content.generator' is not defined in any rdfs ontology database.
WARNING: field 'media.duration' is not defined in any rdfs ontology database.
WARNING: field 'TODO_video.duration' is not defined in any rdfs ontology database.
WARNING: field 'av.audio_codec' is not defined in any rdfs ontology database.
WARNING: field 'av.video_codec' is not defined in any rdfs ontology database.
WARNING: field 'content.thumbnail' is not defined in any rdfs ontology database.
WARNING: field 'user.rating' is not defined in any rdfs ontology database.
WARNING: field 'image.width' is not defined in any rdfs ontology database.
WARNING: field 'image.height' is not defined in any rdfs ontology database.
WARNING: field 'media.sample_rate' is not defined in any rdfs ontology database.
WARNING: field 'media.sample_format' is not defined in any rdfs ontology database.
WARNING: field 'document.stats.image_name' is not defined in any rdfs ontology database.
WARNING: field 'document.stats.image_shared_rows' is not defined in any rdfs ontology database.
WARNING: field 'ole.category' is not defined in any rdfs ontology database.
WARNING: field 'ole.presentationtarget' is not defined in any rdfs ontology database.
WARNING: field 'ole.manager' is not defined in any rdfs ontology database.
WARNING: field 'ole.company' is not defined in any rdfs ontology database.
WARNING: field 'document.stats.table_count' is not defined in any rdfs ontology database.
WARNING: field 'document.stats.object_count' is not defined in any rdfs ontology database.
WARNING: field 'http://rdf.openmolecules.net/0.9#moleculeCount' is not defined in any rdfs ontology database.
dolphin(30620) KFileMetaInfoPrivate::init: KUrl("file:///var/log/pm-suspend.log")
kdeinit4: preparing to launch 
Error: "/var/tmp/kdecache-xaaxa" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xaaxa" is owned by uid 1000 instead of uid 0.
dolphin(30620) KFileMetaInfoPrivate::init: KUrl("file:///var/log/rkhunter.log")
kdeinit4: preparing to launch /usr/bin/ooffice

** (soffice:30692): WARNING **: unable to get gail version number
dolphin(30620) KFileMetaInfoPrivate::init: KUrl("file:///var/log/rkhunter.log")
dolphin(30620) KFileMetaInfoPrivate::init: KUrl("file:///var/log/rkhunter.log")
error - missing word count in dictionary file
Hash Manager Error : 4
dolphin(30620) KFileMetaInfoPrivate::init: KUrl("file:///var/log/rkhunter.log")
kDebugStream called after destruction (from void KDirWatchPrivate::removeEntry(KDirWatch*, KDirWatchPrivate::Entry*, KDirWatchPrivate::Entry*) file /build/buildd/kde4libs-4.2.2/kio/kio/kdirwatch.cpp line 840)
Cancelled INotify (fd 9, 1) for "/home/xaaxa/.local/share"

 
```
:popcorn:

---

### Post by albinootje on 2009-06-13
> **micdhack said:**
> 
```

micdhack@micdhack-laptop:~$ lsof|grep 4369
seahorse-  4369    micdhack  cwd       DIR        8,3     12288   163841 /tmp

```
4369 is/was the process ID of the seahorse daemon on your machine. That's not related to port 4369.

---

### Post by HermanAB on 2009-06-13
Howdy,

These rootkit things are quite useless.

Your WOW account was likely compromised due to a simple password.

---

### Post by statistic on 2009-06-13
> **HermanAB said:**
> Howdy,

These rootkit things are quite useless.

Your WOW account was likely compromised due to a simple password.


Yeah, the problem with the root-kit detectors, is anyone who knows that it's on the system, can take measures to avoid it, and it's really not that difficult. One can simply change something, then update the system to tell it everything is ok, and rkhunter won't say a word.

---

### Post by micdhack on 2009-06-13
> **HermanAB said:**
> Howdy,

These rootkit things are quite useless.

Your WOW account was likely compromised due to a simple password.

I really dont think thats the case cause its 8 digit and uses numbers and characters and i have it since i first started using the net (10+ back). It doesn't make sense and it has no words in it.
So other than keylogger the only way that someone could find it is seeing me typing it (which i havent used it outside home and i play wow when im alone at home) or by brute forcing all the possible combinations which i thought that blizzard had protection for these kind of staff.

---

### Post by cariboo on 2009-06-13
The only way a keylogger could be installed, is if your system was hacked, which is doesn't look like, or someone did some social egineering on you, and you installed it yourself. I find it highly unlikely that you have a keylogger installed. 

For more info search google for linux keyloggers.

---

### Post by HermanAB on 2009-06-14
There are brute force programs that can rapidly try bazillions of combinations.  Your passwords should always be longer than 8 characters.  Also, the WOW login is not secure, so your user credentials can be intercepted anywhere along the way to Blizzard.

---

### Post by vociferous666 on 2009-07-24
you are <unwise> for using the same password for everything and not changing it for 10 (TEN!!!) years!!!! what are you thinking?

i change my password every month and dont use the same password on more than two online services.  i also have different degrees of password strength.  for forms and such i use a simple pass, for email i use a very strong pass, and for financial, i use the most secure pass i can think of and change it every week.

call me paranoid, but i like not having to worry about who is getting at my internet accounts.  

and i live with my roomate who knows nothing about computers and my wifi is wpa2 on a linux router so noone has access to my network to arp poison me.

you might reply "oh ive been using the internet for 10 years, im a seasoned professional" but my security laughs at yours.

---

### Post by dragos2 on 2009-07-24
> **vociferous666 said:**
> you are <unwise> for using the same password for everything and not changing it for 10 (TEN!!!) years!!!! what are you thinking?

i change my password every month and dont use the same password on more than two online services.  i also have different degrees of password strength.  for forms and such i use a simple pass, for email i use a very strong pass, and for financial, i use the most secure pass i can think of and change it every week.

call me paranoid, but i like not having to worry about who is getting at my internet accounts.  

and i live with my roomate who knows nothing about computers and my wifi is wpa2 on a linux router so noone has access to my network to arp poison me.

you might reply "oh ive been using the internet for 10 years, im a seasoned professional" but my security laughs at yours.

You pretty much said all that needed to be said.

I would add that maybe someone sniffed it on some site/place then tried it everywhere,
and lucky attacker it worked for the wow account (I would suspect an teenager hacker :D)
and since you have not changed it in 10 years changes are that your mail is being read
since a long time now ;)

---

### Post by niteshifter on 2009-07-25
Hi,

Although vociferous doesn't explictly say he/she using a laptop but ...

10 years same password
+
Connecting through a helpfully provided open WiFi when out & about
=
pwned!

---

