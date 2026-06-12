---
title: "Strange  Problems..."
date: 2010-01-16
forum: Security
---

### Post by experienced on 2010-01-16
Good day, everyone.

I have been experiencing some odd problems and behavior from my computer.  First, I use rkhunter (rkhunter.sf.net) and have received a number of errors from it.  The file errors are not new, but the root kit error seems to have emerged since I upgraded to Karmic.
Second, I have a (usually) 3 megabyte per second FIOS Internet connection; however, when I was downloading some updates, the speed slowly deteriorated to 500 or so kilobytes per second (using the US Server).  Also, after downloading the tzdata update, I received an error that the hash was incorrect, though when I downloaded it again, I did not receive an error, and the installation proceeded as usual.  Below are the rkhunter logs.  I hope someone can help me confirm whether my computer and/or network has been compromised.  Thank you in advance.

(I have WPA Personal wireless with a strong password.)  

```
[ Rootkit Hunter version 1.3.6 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
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
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ Warning ]
    /bin/readlink                                            [ Warning ]
    /bin/sed                                                 [ Warning ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ Warning ]
    /bin/uname                                               [ Warning ]
    /bin/which                                               [ Warning ]
    /bin/dash                                                [ Warning ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ Warning ]
    /usr/bin/chattr                                          [ Warning ]
    /usr/bin/cut                                             [ Warning ]
    /usr/bin/diff                                            [ Warning ]
    /usr/bin/dirname                                         [ Warning ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ Warning ]
    /usr/bin/env                                             [ Warning ]
    /usr/bin/file                                            [ Warning ]
    /usr/bin/find                                            [ Warning ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ Warning ]
    /usr/bin/head                                            [ Warning ]
    /usr/bin/id                                              [ Warning ]
    /usr/bin/killall                                         [ Warning ]
    /usr/bin/last                                            [ Warning ]
    /usr/bin/lastlog                                         [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ Warning ]
    /usr/bin/lsattr                                          [ Warning ]
    /usr/bin/lsof                                            [ Warning ]
    /usr/bin/md5sum                                          [ Warning ]
    /usr/bin/mlocate                                         [ Warning ]
    /usr/bin/newgrp                                          [ Warning ]
    /usr/bin/passwd                                          [ Warning ]
    /usr/bin/perl                                            [ Warning ]
    /usr/bin/pgrep                                           [ Warning ]
    /usr/bin/pstree                                          [ Warning ]
    /usr/bin/runcon                                          [ Warning ]
    /usr/bin/sha1sum                                         [ Warning ]
    /usr/bin/sha224sum                                       [ Warning ]
    /usr/bin/sha256sum                                       [ Warning ]
    /usr/bin/sha384sum                                       [ Warning ]
    /usr/bin/sha512sum                                       [ Warning ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ Warning ]
    /usr/bin/stat                                            [ Warning ]
    /usr/bin/strace                                          [ Warning ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ Warning ]
    /usr/bin/tail                                            [ Warning ]
    /usr/bin/test                                            [ Warning ]
    /usr/bin/top                                             [ Warning ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ Warning ]
    /usr/bin/uniq                                            [ Warning ]
    /usr/bin/users                                           [ Warning ]
    /usr/bin/vmstat                                          [ Warning ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              [ Warning ]
    /usr/bin/wget                                            [ Warning ]
    /usr/bin/whatis                                          [ Warning ]
    /usr/bin/whereis                                         [ Warning ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ Warning ]
    /usr/bin/whoami                                          [ Warning ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/w.procps                                        [ Warning ]
    /sbin/depmod                                             [ Warning ]
    /sbin/ifconfig                                           [ Warning ]
    /sbin/ifdown                                             [ Warning ]
    /sbin/ifup                                               [ Warning ]
    /sbin/init                                               [ Warning ]
    /sbin/insmod                                             [ Warning ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ Warning ]
    /sbin/modprobe                                           [ Warning ]
    /sbin/rmmod                                              [ Warning ]
    /sbin/runlevel                                           [ Warning ]
    /sbin/sulogin                                            [ Warning ]
    /sbin/sysctl                                             [ Warning ]
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
    /root/rkhunter-1.3.6/files/rkhunter                      [ OK ]
    /root/rkhunter-1.3.6/files/rkhunter.conf                 [ OK ]

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
    Checking for possible rootkit strings                    [ Warning ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

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

Checking application versions...

    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]


System checks summary
=====================

File properties checks...
    Files checked: 130
    Suspect files: 115

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 1
    Rootkit names    : Xzibit Rootkit

Applications checks...
    Applications checked: 2
    Suspect applications: 2

The system checks took: 1 minute and 10 seconds

All results have been written to the log file (/root/rkhunter-1.3.6/files/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/root/rkhunter-1.3.6/files/rkhunter.log)

THE RELEVANT PARTS OF THE LOG FILE:



13:31:45] Checking application versions...
[13:31:45] Info: Starting test name 'apps'
[13:31:45] Info: Application 'exim' not found.
[13:31:45]   Checking version of GnuPG                       [ Warning ]
[13:31:45] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
[13:31:45] Info: Application 'httpd' not found.
[13:31:45] Info: Application 'named' not found.
[13:31:45]   Checking version of OpenSSL                     [ Warning ]
[13:31:45] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
[13:31:45] Info: Application 'php' not found.
[13:31:45] Info: Application 'procmail' not found.
[13:31:45] Info: Application 'proftpd' not found.
[13:31:45] Info: Application 'sshd' not found.
[13:31:45] Info: Applications checked: 2 out of 9

[13:31:44] Performing filesystem checks
[13:31:44] Info: Starting test name 'filesystem'
[13:31:44] Info: SCAN_MODE_DEV set to 'THOROUGH'
[13:31:44]   Checking /dev for suspicious file types         [ Warning ]
[13:31:44] Warning: Suspicious file types found in /dev:
[13:31:44]          /dev/shm/pulse-shm-1006653492: data
[13:31:44]          /dev/shm/pulse-shm-3946530129: data
[13:31:44]          /dev/shm/pulse-shm-727430837: data
[13:31:44]          /dev/shm/pulse-shm-512410362: AmigaOS bitmap font
[13:31:44]          /dev/shm/pulse-shm-321593724: data
[13:31:45]   Checking for hidden files and directories       [ Warning ]
[13:31:45] Warning: Hidden directory found: /dev/.udev
[13:31:45] Warning: Hidden directory found: /dev/.initramfs

[13:31:33]   Performing check for possible rootkit strings
[13:31:33] Info: Starting test name 'possible_rkt_strings'
[13:31:33] Info: Using system startup paths: /etc/rc.local /etc/init.d
[13:31:33]     Checking for string 'phalanx'                 [ Not found ]
[13:31:33]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:31:33]     Checking for string '****'                    [ Not found ]
[13:31:33]     Checking for string 'backdoor'                [ Not found ]
[13:31:33]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[13:31:33]     Checking for string '/usr/sbin/login'         [ Not found ]
[13:31:33]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:31:33]     Checking for string 'vt200'                   [ Not found ]
[13:31:33]     Checking for string '/usr/bin/xstat'          [ Not found ]
[13:31:33]     Checking for string '/bin/envpc'              [ Not found ]
[13:31:33]     Checking for string 'L4m3r0x'                 [ Not found ]
[13:31:33]     Checking for string '/lib/libext'             [ Not found ]
[13:31:33]     Checking for string '/usr/sbin/login'         [ Not found ]
[13:31:33]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:31:33]     Checking for string 'sendmail'                [ Not found ]
[13:31:34]     Checking for string 'cocacola'                [ Not found ]
[13:31:34]     Checking for string 'joao'                    [ Not found ]
[13:31:34]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:31:34]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:31:34]     Checking for string '/dev/sgk'                [ Not found ]
[13:31:34]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:31:34]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:31:34]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:31:34]     Checking for string '/lib/.sso'               [ Not found ]
[13:31:34]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:31:34]     Checking for string '/dev/caca'               [ Not found ]
[13:31:34]     Checking for string '/dev/ttyoa'              [ Not found ]
[13:31:34]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[13:31:34]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[13:31:34]     Checking for string 'syg'                     [ Not found ]
[13:31:34]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:31:34]     Checking for string '/dev/pts/01'             [ Not found ]
[13:31:34]     Checking for string 'tw33dl3'                 [ Not found ]
[13:31:34]     Checking for string 'psniff'                  [ Not found ]
[13:31:34]     Checking for string 'uconf.inv'               [ Not found ]
[13:31:34]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[13:31:34]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[13:31:34]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:31:34]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:35]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:31:35]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:31:35]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:35]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:35]     Checking for string '/bin/bash'               [ Not found ]
[13:31:35]     Checking for string '/dev/xdta'               [ Not found ]
[13:31:35]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:31:35]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:31:35]     Checking for string 'in.inetd'                [ Not found ]
[13:31:35]     Checking for string '#<HIDE_.*>'              [ Not found ]
[13:31:35]     Checking for string 'bin/xchk'                [ Not found ]
[13:31:36]     Checking for string 'bin/xsf'                 [ Not found ]
[13:31:36]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[13:31:36]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[13:31:36]     Checking for string 'ttyload'                 [ Not found ]
[13:31:36]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[13:31:36]     Checking for string 'usr/bin/xfss'            [ Not found ]
[13:31:37]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[13:31:37]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[13:31:37]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[13:31:37]     Checking for string '/ssh2d'                  [ Not found ]
[13:31:37]     Checking for string '/dev/kmod'               [ Not found ]
[13:31:37]     Checking for string '/crth.o'                 [ Not found ]
[13:31:38]     Checking for string '/crtz.o'                 [ Not found ]
[13:31:38]     Checking for string '/dev/dos'                [ Not found ]
[13:31:38]     Checking for string '/lpq'                    [ Not found ]
[13:31:38]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[13:31:38]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[13:31:38]     Checking for string '/volc'                   [ Not found ]
[13:31:38]     Checking for string 'sourcemask'              [ Not found ]
[13:31:39]     Checking for string '/bin/vobiscum'           [ Not found ]
[13:31:39]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[13:31:39]     Checking for string 'hdparm'                  [ Warning ]
[13:31:39]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[13:31:39]     Checking for string 't0rnkit'                 [ Not found ]
[13:31:39]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:31:39]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:39]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:39]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:39]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[13:31:39]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[13:31:39]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:31:39]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:31:39]     Checking for string '/dev/ida/.inet'          [ Not found ]
[13:31:39] Warning: Checking for possible rootkit strings    [ Warning ]
[13:31:39]          Found string 'hdparm' in file '/etc/init.d/bootlogd'. Possible rootkit: Xzibit Rootkit
```

---

### Post by cariboo on 2010-01-16
I would suggest running:

```
 sudo rkhunter --update
```

Then run rkhunter again, and see if you get the same results.

I find that the update speeds are all over the place, at times it can be as high as 1200Mbps and other times it almost comes to a standstill.

---

### Post by experienced on 2010-01-16
Thanks, though I updated rkhunter just before the check.

---

### Post by MarkC502 on 2010-01-16
I would say that all I see is warnigns on everything and at the end it gives one real warning but that is for hdparm ( hard disk low level control ) instance and I am not sure of this reference but I used to use hdparm commands to control disk parking with a init script so I would not say this is in any way proof of a rootkit.

Try running chkrootkit instead as at least it seems to not throw around warnings as willy nilly as rkhunter does.

The chances of being infected with a rootkit via any of the official Ubuntu update servers is like zero/unprecedented so I doubt this would be the case. you could only get a rootkit if you are obtaining source code from 3rd parties and installing it yourself not through the repositories or updates.

Hope that helps and rest easy your safe, your not using Windows.

---

### Post by experienced on 2010-01-17
Thanks a bunch, though I was afraid that the upgrade irregularities could be a symptom of an infection, as opposed to a cause of one.  By the way, is it possible for a (Verizon FIOS) router to be infected?

---

### Post by Sporkman on 2010-01-18
> **experienced said:**
> By the way, is it possible for a (Verizon FIOS) router to be infected?

Possibly - they have the option to allow remote login access, though it's off (disallowed) by default (at least it was off on mine - I also have Verizon FIOS).

---

### Post by fonsi2099 on 2010-04-14
I notice that my labtop becomes sometimes very slow, I run rkhunter and I get the following feedback, what I need to do? 
Thank you for any help, 

Performing group and account checks
    Checking for passwd file                                 [ Found ]
Performing group and account checks
    Checking for passwd file                                 [ Found ]
Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
/usr/sbin/unhide                                         [ Warning 
/usr/sbin/unhide-linux26                                 [ Warning ]

System checks summary
File properties checks...
    Files checked: 129
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 111
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

---

### Post by cariboo on 2010-04-14
If you had searched this sub-forum for rkhunter, you would have come up with quite a few posts with the same problem, that being said, unhide and unhide-linux26, are installed as dependencies of rkhunter, and the other 2 warnings are normal.

---

