---
title: "Hidden Process and other warning from roof kit tests"
date: 2011-02-11
forum: Security
---

### Post by themanfromdelmonte on 2011-02-11
Sorry about the long post. Hopefully I can get some advice.ian@ian-HP-G62-Notebook-PC:~$ rkhunter

```
Usage: rkhunter {--check | --unlock | --update | --versioncheck |
                 --propupd [{filename | directory | package name},...] |
                 --list [{tests | {lang | languages} | rootkits}] |
                 --version | --help} [options]
file:///home/ian/Desktop/RKhunts
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
         --hash {MD5 | SHA1 | SHA224 | SHA256 | SHA384 | SHA512 |
                 NONE | <command>}     Use the specified file hash function
                                       (Default is SHA1, then MD5)
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
         --propupd [file | directory | Update the entire file properties database,
                    package]...        or just for the specified entries
     -q, --quiet                       Quiet mode (no output at all)
  --rwo, --report-warnings-only        Show only warning messages
     -r, --rootdir <directory>         Use the specified root directory
   --sk, --skip-keypress               Don't wait for a keypress after each test
         --summary                     Show the summary of system check results
                                       (This is the default)
         --syslog [facility.priority]  Log the check start and finish times to syslog
                                       (Default level is authpriv.notice)
         --tmpdir <directory>          Use the specified temporary directory
         --unlock                      Unlock (remove) the lock file
         --update                      Check for updates to database files
   --vl, --verbose-logging             Use verbose logging (on by default)
     -V, --version                     Display the version number, then exit
         --versioncheck                Check for latest version of program
     -x, --autox                       Automatically detect if X is in use
     -X, --no-autox                    Do not automatically detect if X is in use
```

```
ian@ian-HP-G62-Notebook-PC:~$ rkhunter -c
You must be the root user to run this program.
ian@ian-HP-G62-Notebook-PC:~$ sudo rkhunter -c
[sudo] password for ian: 
Sorry, try again.
[sudo] password for ian: 
[ Rootkit Hunter version 1.3.6 ]
```

```
Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
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
    /bin/less                                                [ OK ]
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
    /usr/bin/awk                                             [ Warning ]
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
    /usr/bin/mail                                            [ Warning ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
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
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ OK ]
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
    /usr/sbin/unhide-linux26                                 [ OK ]

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
    FreeBSD Rootkit                                          [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    iLLogiC Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
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
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
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
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

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

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


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
    Checking root account shell history files                [ None found ]

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
    Files checked: 130
    Suspect files: 3

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 23 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

ian@ian-HP-G62-Notebook-PC:~$ 


ian@ian-HP-G62-Notebook-PC:~$ sudo chkrootkit
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
Checking `inetdconf'...                                     not found
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
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
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
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.13/.autoreg /usr/lib/firefox-3.6.13/.autoreg

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
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user ian deleted or never logged from lastlog!
user carol deleted or never logged from lastlog!
Checking `chkutmp'...                                       chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
ian@ian-HP-G62-Notebook-PC:~$ 

ian@ian-HP-G62-Notebook-PC:~$ sudo roothide
sudo: roothide: command not found
ian@ian-HP-G62-Notebook-PC:~$ sudo unhide
Unhide 20100201
[http://www.security-projects.com/?Unhide](http://www.security-projects.com/?Unhide)


usage: unhide proc | sys | brute

ian@ian-HP-G62-Notebook-PC:~$ unhide proc
Unhide 20100201
[http://www.security-projects.com/?Unhide](http://www.security-projects.com/?Unhide)
[*]Searching for Hidden processes through /proc scanning

ian@ian-HP-G62-Notebook-PC:~$ unhide proc
Unhide 20100201
[http://www.security-projects.com/?Unhide](http://www.security-projects.com/?Unhide)
[*]Searching for Hidden processes through /proc scanning



ian@ian-HP-G62-Notebook-PC:~$ 
ian@ian-HP-G62-Notebook-PC:~$ 
ian@ian-HP-G62-Notebook-PC:~$ unhide sys
Unhide 20100201
[http://www.security-projects.com/?Unhide](http://www.security-projects.com/?Unhide)
[*]Searching for Hidden processes through kill(..,0) scanning
[*]Searching for Hidden processes through  comparison of results of system calls

Found HIDDEN PID: 1
Found HIDDEN PID: 2
Found HIDDEN PID: 3
Found HIDDEN PID: 4
Found HIDDEN PID: 5
Found HIDDEN PID: 6
Found HIDDEN PID: 7
Found HIDDEN PID: 8
Found HIDDEN PID: 9
Found HIDDEN PID: 10
Found HIDDEN PID: 11
Found HIDDEN PID: 12
Found HIDDEN PID: 13
Found HIDDEN PID: 14
Found HIDDEN PID: 15
Found HIDDEN PID: 16
Found HIDDEN PID: 17
Found HIDDEN PID: 18
Found HIDDEN PID: 19
Found HIDDEN PID: 20
Found HIDDEN PID: 21
Found HIDDEN PID: 22
Found HIDDEN PID: 23
Found HIDDEN PID: 25
Found HIDDEN PID: 26
Found HIDDEN PID: 27
Found HIDDEN PID: 28
Found HIDDEN PID: 29
Found HIDDEN PID: 30
Found HIDDEN PID: 31
Found HIDDEN PID: 32
Found HIDDEN PID: 33
Found HIDDEN PID: 34
Found HIDDEN PID: 35
Found HIDDEN PID: 36
Found HIDDEN PID: 37
Found HIDDEN PID: 38
Found HIDDEN PID: 39
Found HIDDEN PID: 40
Found HIDDEN PID: 41
Found HIDDEN PID: 42
Found HIDDEN PID: 43
Found HIDDEN PID: 44
Found HIDDEN PID: 45
Found HIDDEN PID: 46
Found HIDDEN PID: 47
Found HIDDEN PID: 48
Found HIDDEN PID: 49
Found HIDDEN PID: 50
Found HIDDEN PID: 51
Found HIDDEN PID: 52
Found HIDDEN PID: 53
Found HIDDEN PID: 54
Found HIDDEN PID: 55
Found HIDDEN PID: 56
Found HIDDEN PID: 57
Found HIDDEN PID: 63
Found HIDDEN PID: 64
Found HIDDEN PID: 65
Found HIDDEN PID: 66
Found HIDDEN PID: 67
Found HIDDEN PID: 68
Found HIDDEN PID: 69
Found HIDDEN PID: 70
Found HIDDEN PID: 71
Found HIDDEN PID: 72
Found HIDDEN PID: 73
Found HIDDEN PID: 74
Found HIDDEN PID: 75
Found HIDDEN PID: 76
Found HIDDEN PID: 77
Found HIDDEN PID: 270
Found HIDDEN PID: 278
Found HIDDEN PID: 288
Found HIDDEN PID: 289
Found HIDDEN PID: 317
Found HIDDEN PID: 318
Found HIDDEN PID: 323
Found HIDDEN PID: 324
Found HIDDEN PID: 325
Found HIDDEN PID: 326
Found HIDDEN PID: 327
Found HIDDEN PID: 362
Found HIDDEN PID: 390
Found HIDDEN PID: 393
Found HIDDEN PID: 689
Found HIDDEN PID: 897
Found HIDDEN PID: 1089
Found HIDDEN PID: 1090
Found HIDDEN PID: 1096
Found HIDDEN PID: 1158
Found HIDDEN PID: 1172
Found HIDDEN PID: 1179
Found HIDDEN PID: 1181
Found HIDDEN PID: 1183
Found HIDDEN PID: 1188
Found HIDDEN PID: 1190
Found HIDDEN PID: 1192
Found HIDDEN PID: 1193
Found HIDDEN PID: 1195
Found HIDDEN PID: 1196
Found HIDDEN PID: 1197
Found HIDDEN PID: 1198
Found HIDDEN PID: 1199
Found HIDDEN PID: 1202
Found HIDDEN PID: 1203
Found HIDDEN PID: 1204
Found HIDDEN PID: 1205
Found HIDDEN PID: 1206
Found HIDDEN PID: 1207
Found HIDDEN PID: 1208
Found HIDDEN PID: 1209
Found HIDDEN PID: 1210
Found HIDDEN PID: 1211
Found HIDDEN PID: 1212
Found HIDDEN PID: 1213
Found HIDDEN PID: 1214
Found HIDDEN PID: 1215
Found HIDDEN PID: 1216
Found HIDDEN PID: 1217
Found HIDDEN PID: 1218
Found HIDDEN PID: 1219
Found HIDDEN PID: 1220
Found HIDDEN PID: 1221
Found HIDDEN PID: 1222
Found HIDDEN PID: 1223
Found HIDDEN PID: 1224
Found HIDDEN PID: 1225
Found HIDDEN PID: 1226
Found HIDDEN PID: 1227
Found HIDDEN PID: 1228
Found HIDDEN PID: 1229
Found HIDDEN PID: 1230
Found HIDDEN PID: 1231
Found HIDDEN PID: 1232
Found HIDDEN PID: 1233
Found HIDDEN PID: 1234
Found HIDDEN PID: 1235
Found HIDDEN PID: 1236
Found HIDDEN PID: 1237
Found HIDDEN PID: 1238
Found HIDDEN PID: 1239
Found HIDDEN PID: 1240
Found HIDDEN PID: 1241
Found HIDDEN PID: 1242
Found HIDDEN PID: 1243
Found HIDDEN PID: 1244
Found HIDDEN PID: 1245
Found HIDDEN PID: 1246
Found HIDDEN PID: 1247
Found HIDDEN PID: 1248
Found HIDDEN PID: 1249
Found HIDDEN PID: 1250
Found HIDDEN PID: 1251
Found HIDDEN PID: 1252
Found HIDDEN PID: 1253
Found HIDDEN PID: 1254
Found HIDDEN PID: 1255
Found HIDDEN PID: 1285
Found HIDDEN PID: 1294
Found HIDDEN PID: 1296
Found HIDDEN PID: 1305
Found HIDDEN PID: 1306
Found HIDDEN PID: 1398
Found HIDDEN PID: 1422
Found HIDDEN PID: 1439
Found HIDDEN PID: 1440
Found HIDDEN PID: 1442
Found HIDDEN PID: 1445
Found HIDDEN PID: 1452
Found HIDDEN PID: 1454
Found HIDDEN PID: 1457
Found HIDDEN PID: 1462
Found HIDDEN PID: 1463
Found HIDDEN PID: 1474
Found HIDDEN PID: 1475
Found HIDDEN PID: 1477
Found HIDDEN PID: 1589
Found HIDDEN PID: 1678
Found HIDDEN PID: 1713
Found HIDDEN PID: 1740
Found HIDDEN PID: 1742
Found HIDDEN PID: 1743
Found HIDDEN PID: 1744
Found HIDDEN PID: 1746
Found HIDDEN PID: 1907
Found HIDDEN PID: 2060
Found HIDDEN PID: 10922
Found HIDDEN PID: 10924
Found HIDDEN PID: 12881
Found HIDDEN PID: 12885
Found HIDDEN PID: 12889
Found HIDDEN PID: 12890
Found HIDDEN PID: 12908
Found HIDDEN PID: 12909
Found HIDDEN PID: 12940
Found HIDDEN PID: 12943
Found HIDDEN PID: 12944
Found HIDDEN PID: 12947
Found HIDDEN PID: 12949
Found HIDDEN PID: 12951
Found HIDDEN PID: 12952
Found HIDDEN PID: 12955
Found HIDDEN PID: 12958
Found HIDDEN PID: 12959
Found HIDDEN PID: 12960
Found HIDDEN PID: 12962
Found HIDDEN PID: 12967
Found HIDDEN PID: 12968
Found HIDDEN PID: 12969
Found HIDDEN PID: 12970
Found HIDDEN PID: 12972
Found HIDDEN PID: 12974
Found HIDDEN PID: 12975
Found HIDDEN PID: 12976
Found HIDDEN PID: 12977
Found HIDDEN PID: 12980
Found HIDDEN PID: 12982
Found HIDDEN PID: 12985
Found HIDDEN PID: 12993
Found HIDDEN PID: 12995
Found HIDDEN PID: 12997
Found HIDDEN PID: 12998
Found HIDDEN PID: 13028
Found HIDDEN PID: 13029
Found HIDDEN PID: 13030
Found HIDDEN PID: 13031
Found HIDDEN PID: 13032
Found HIDDEN PID: 13034
Found HIDDEN PID: 13036
Found HIDDEN PID: 13037
Found HIDDEN PID: 13039
Found HIDDEN PID: 13040
Found HIDDEN PID: 13041
Found HIDDEN PID: 13042
Found HIDDEN PID: 13045
Found HIDDEN PID: 13047
Found HIDDEN PID: 13051
Found HIDDEN PID: 13057
Found HIDDEN PID: 13058
Found HIDDEN PID: 13060
Found HIDDEN PID: 13061
Found HIDDEN PID: 13063
Found HIDDEN PID: 13066
Found HIDDEN PID: 13067
Found HIDDEN PID: 13068
Found HIDDEN PID: 13070
Found HIDDEN PID: 13074
Found HIDDEN PID: 13076
Found HIDDEN PID: 13077
Found HIDDEN PID: 13078
Found HIDDEN PID: 13079
Found HIDDEN PID: 13080
Found HIDDEN PID: 13081
Found HIDDEN PID: 13082
Found HIDDEN PID: 13087
Found HIDDEN PID: 13089
Found HIDDEN PID: 13090
Found HIDDEN PID: 13092
Found HIDDEN PID: 13094
Found HIDDEN PID: 13095
Found HIDDEN PID: 13098
Found HIDDEN PID: 13100
Found HIDDEN PID: 13102
Found HIDDEN PID: 13104
Found HIDDEN PID: 13107
Found HIDDEN PID: 13113
Found HIDDEN PID: 13115
Found HIDDEN PID: 13120
Found HIDDEN PID: 13174
Found HIDDEN PID: 13503
Found HIDDEN PID: 13506
Found HIDDEN PID: 13562
Found HIDDEN PID: 13563
Found HIDDEN PID: 13565
Found HIDDEN PID: 13567
Found HIDDEN PID: 13596
Found HIDDEN PID: 13655
Found HIDDEN PID: 13657
Found HIDDEN PID: 13658
Found HIDDEN PID: 13659
Found HIDDEN PID: 13679
Found HIDDEN PID: 13699
Found HIDDEN PID: 13739
Found HIDDEN PID: 14047
Found HIDDEN PID: 14048
Found HIDDEN PID: 14632
Found HIDDEN PID: 14634
Found HIDDEN PID: 15052
Found HIDDEN PID: 15053
Found HIDDEN PID: 15059
Found HIDDEN PID: 25761
Found HIDDEN PID: 25763
[*]Searching for Hidden processes through getpriority() scanning
[*]Searching for Hidden processes through getpgid() scanning
[*]Searching for Hidden processes through getsid() scanning
[*]Searching for Hidden processes through sched_getaffinity() scanning
[*]Searching for Hidden processes through sched_getparam() scanning
[*]Searching for Hidden processes through sched_getscheduler() scanning
[*]Searching for Hidden processes through sched_rr_get_interval() scanning
[*]Searching for Hidden processes through sysinfo() scanning

HIDDEN Processes Found: 1
ian@ian-HP-G62-Notebook-PC:~$ 

ian@ian-HP-G62-Notebook-PC:~$ klamav
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout
ian@ian-HP-G62-Notebook-PC:~$ QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
ICE default IO error handler doing an exit(), pid = 3449, errno = 11
```


Thanks for any help

---

### Post by cariboo on 2011-02-11
Why did you run rkhunter, and what was the expected result. Running rkhunter is usually a waste of time due to false positives.

I'd suggest reading the man pages, before running it.

---

### Post by mlnease on 2011-05-17
Hello,

I ran unhide and received the following: HIDDEN Processes Found: 1
I take your point about rkhunter; is this something to worry about in uhide?

Thanks in Advance,

mike

---

### Post by Soul-Sing on 2011-05-18
```
ps -e
```
gives you the number and processes "behind" them.
init has something to do with the bootproces imo.

you could do a reboot a see if its still there.

---

### Post by Soul-Sing on 2011-05-18
> **leoquant said:**
> ```
ps -e
```
gives you the number and processes "behind" them.
init has something to do with the bootproces imo.

you could do a reboot a see if its still there.

> is this something to worry about

as far as my knowledge goes: no.

---

### Post by mlnease on 2011-05-18
> **leoquant said:**
> as far as my knowledge goes: no.
Quite cool, thanks very much.

mike

---

