---
title: "CHKRootkit returned a positive, RKHunter did not."
date: 2008-07-30
forum: Security
---

### Post by LeoSolaris on 2008-07-30
I ran a random chkrootkit and it came back with two possible positives. before panicing, I did an rkhunter as well. The rkhunter did not return anything more than warnings. I did a tiger scan, but it uses chkrootkit for it's rootkit scan anyways, so it just returned the same two possible positives.

I have a couple of non-standard repos, they are as follows:

[http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy
[http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

My Hardy install is fully updated to 8.04.1 from the main server.

Here's the chkrootkit scan results:

```
11:54 AM on Wed Jul 30 leo-laptop: ~$ sudo chkrootkit
ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not infected
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.1/.autoreg
/usr/lib/firefox-3.0.1/.autoreg
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/.java-6-openjdk.jinfo
/usr/lib/jvm/java-6-sun-1.6.0.06/.systemPrefs
/lib/linux-restricted-modules/.nvidia_new_installed
/lib/modules/2.6.24-20-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... INFECTED (PORTS:  1524 6667 31337)
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[8501], /sbin/dhclient3[8571])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

```Here is my /var/log/rkhunter.log

```

[11:58:15] Running Rootkit Hunter version 1.3.0 on leo-laptop
[11:58:15]
[11:58:15] Info: Start date is Wed Jul 30 11:58:15 EDT 2008
[11:58:15]
[11:58:15] Checking configuration file and command-line options...
[11:58:15] Info: Detected operating system is 'Linux'
[11:58:15] Info: Found O/S name: Ubuntu 8.04.1
[11:58:15] Info: Command line is /usr/bin/rkhunter -c --sk
[11:58:15] Info: Environment shell is /bin/bash; rkhunter is using dash
[11:58:15] Info: Using configuration file '/etc/rkhunter.conf'
[11:58:15] Info: Installation directory is '/usr'
[11:58:15] Info: Using language 'en'
[11:58:15] Info: Using '/var/lib/rkhunter/db' as the database directory
[11:58:15] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[11:58:15] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[11:58:15] Info: Using '/' as the root directory
[11:58:15] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[11:58:15] Info: No mail-on-warning address configured
[11:58:15] Info: X will automatically be detected
[11:58:15] Info: Using second color set
[11:58:15] Info: Found the 'diff' command: /usr/bin/diff
[11:58:15] Info: Found the 'file' command: /usr/bin/file
[11:58:15] Info: Found the 'find' command: /usr/bin/find
[11:58:15] Info: Found the 'ifconfig' command: /sbin/ifconfig
[11:58:15] Info: Found the 'ip' command: /sbin/ip
[11:58:15] Info: Found the 'ldd' command: /usr/bin/ldd
[11:58:16] Info: Found the 'lsattr' command: /usr/bin/lsattr
[11:58:16] Info: Found the 'lsmod' command: /sbin/lsmod
[11:58:16] Info: Found the 'lsof' command: /usr/bin/lsof
[11:58:16] Info: Found the 'mktemp' command: /bin/mktemp
[11:58:16] Info: Found the 'netstat' command: /bin/netstat
[11:58:16] Info: Found the 'perl' command: /usr/bin/perl
[11:58:16] Info: Found the 'ps' command: /bin/ps
[11:58:16] Info: Found the 'pwd' command: /bin/pwd
[11:58:16] Info: Found the 'readlink' command: /bin/readlink
[11:58:16] Info: Found the 'sort' command: /usr/bin/sort
[11:58:16] Info: Found the 'stat' command: /usr/bin/stat
[11:58:16] Info: Found the 'strings' command: /usr/bin/strings
[11:58:16] Info: Found the 'uniq' command: /usr/bin/uniq
[11:58:16] Info: System is not using prelinking
[11:58:16] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[11:58:16] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[11:58:16] Info: Stored hash values did not use a package manager
[11:58:16] Info: The hash function field index is set to 1
[11:58:16] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[11:58:16] Info: Previous file attributes were stored
[11:58:16] Info: Enabled tests are: all
[11:58:16] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[11:58:16] Info: Found ksym file '/proc/kallsyms'
[11:58:16]
[11:58:16] Checking if the O/S has changed since last time...
[11:58:16] Info: Nothing seems to have changed
[11:58:16]
[11:58:16] Starting system checks...
[11:58:16]
[11:58:16] Checking system commands...
[11:58:16] Info: Starting test name 'system_commands'
[11:58:16]
[11:58:16] Performing 'strings' command checks
[11:58:16] Info: Starting test name 'strings'
[11:58:16] Scanning for string /usr/sbin/ntpsx               [ OK ]
[11:58:16] Scanning for string /usr/lib/.../ls               [ OK ]
[11:58:16] Scanning for string /usr/lib/.../netstat          [ OK ]
[11:58:16] Scanning for string /usr/lib/.../lsof             [ OK ]
[11:58:16] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[11:58:16] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[11:58:16] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[11:58:16] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[11:58:16] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[11:58:16] Scanning for string /usr/lib/.../psr              [ OK ]
[11:58:16] Scanning for string /usr/lib/.../find             [ OK ]
[11:58:16] Scanning for string /usr/lib/.../pstree           [ OK ]
[11:58:16] Scanning for string /usr/lib/.../slocate          [ OK ]
[11:58:17] Scanning for string /usr/lib/.../du               [ OK ]
[11:58:17] Scanning for string /usr/lib/.../top              [ OK ]
[11:58:17] Scanning for string /usr/lib/...                  [ OK ]
[11:58:17] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[11:58:17] Scanning for string /usr/lib/.bkit-               [ OK ]
[11:58:17] Scanning for string /tmp/.bkp                     [ OK ]
[11:58:17] Scanning for string /tmp/.cinik                   [ OK ]
[11:58:17] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[11:58:17] Scanning for string /lib/.sso                     [ OK ]
[11:58:17] Scanning for string /lib/.so                      [ OK ]
[11:58:17] Scanning for string /var/run/...dica/clean        [ OK ]
[11:58:17] Scanning for string /var/run/...dica/xl           [ OK ]
[11:58:17] Scanning for string /var/run/...dica/xdr          [ OK ]
[11:58:17] Scanning for string /var/run/...dica/psg          [ OK ]
[11:58:17] Scanning for string /var/run/...dica/secure       [ OK ]
[11:58:17] Scanning for string /var/run/...dica/rdx          [ OK ]
[11:58:17] Scanning for string /var/run/...dica/va           [ OK ]
[11:58:17] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[11:58:17] Scanning for string /usr/bin/.etc                 [ OK ]
[11:58:17] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[11:58:17] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[11:58:17] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[11:58:17] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[11:58:17] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[11:58:17] Scanning for string /bin/sysback                  [ OK ]
[11:58:17] Scanning for string /usr/local/bin/sysback        [ OK ]
[11:58:17] Scanning for string /usr/lib/.tbd                 [ OK ]
[11:58:17] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[11:58:17] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[11:58:17] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[11:58:17] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[11:58:18] Scanning for string /usr/info/.torn/sh*           [ OK ]
[11:58:18] Scanning for string /usr/src/.****/.1addr         [ OK ]
[11:58:18] Scanning for string /usr/src/.****/.1file         [ OK ]
[11:58:18] Scanning for string /usr/src/.****/.1proc         [ OK ]
[11:58:18] Scanning for string /usr/src/.****/.1logz         [ OK ]
[11:58:18] Scanning for string /usr/info/.t0rn               [ OK ]
[11:58:18] Scanning for string /dev/.lib                     [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib                 [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib             [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[11:58:18] Scanning for string /dev/.lib/lib/scan            [ OK ]
[11:58:18] Scanning for string /usr/src/.****                [ OK ]
[11:58:18] Scanning for string /usr/man/man1/man1            [ OK ]
[11:58:19] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[11:58:19] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[11:58:19] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[11:58:19]
[11:58:19] Performing 'shared libraries' checks
[11:58:19] Info: Starting test name 'shared_libs'
[11:58:19] Checking for preloading variables                 [ None found ]
[11:58:19] Checking for preload file                         [ Not found ]
[11:58:19] Info: Starting test name 'shared_libs_path'
[11:58:19] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[11:58:19]
[11:58:19] Performing file properties checks
[11:58:19] Info: Starting test name 'properties'
[11:58:19] Checking for prerequisites                        [ OK ]
[11:58:19] /bin/bash                                         [ OK ]
[11:58:19] /bin/cat                                          [ OK ]
[11:58:19] /bin/chmod                                        [ OK ]
[11:58:20] /bin/chown                                        [ OK ]
[11:58:20] /bin/cp                                           [ OK ]
[11:58:20] /bin/date                                         [ OK ]
[11:58:20] /bin/df                                           [ OK ]
[11:58:20] /bin/dmesg                                        [ OK ]
[11:58:20] /bin/echo                                         [ OK ]
[11:58:20] /bin/ed                                           [ OK ]
[11:58:20] /bin/egrep                                        [ OK ]
[11:58:20] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[11:58:21] /bin/fgrep                                        [ OK ]
[11:58:21] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[11:58:21] /bin/grep                                         [ OK ]
[11:58:21] /bin/ip                                           [ Warning ]
[11:58:21] Warning: The file properties have changed:
[11:58:21]          File: /bin/ip
[11:58:21]          Current inode: 122464    Stored inode: 122447
[11:58:21]          Current file modification time: 1215621293
[11:58:21]          Stored file modification time : 1207985280
[11:58:21] /bin/kill                                         [ Warning ]
[11:58:21] Warning: The file properties have changed:
[11:58:21]          File: /bin/kill
[11:58:21]          Current hash: 84e9b211a9a8b630da0421714d393fbc849922ea
[11:58:21]          Stored hash : e0baf2e8f195d5f58ba1d6253d152c5da35fea92
[11:58:21]          Current inode: 122447    Stored inode: 122449
[11:58:21]          Current file modification time: 1215682145
[11:58:21]          Stored file modification time : 1205449373
[11:58:21] /bin/login                                        [ OK ]
[11:58:22] /bin/ls                                           [ OK ]
[11:58:22] /bin/lsmod                                        [ OK ]
[11:58:22] /bin/mktemp                                       [ OK ]
[11:58:22] /bin/more                                         [ OK ]
[11:58:22] /bin/mount                                        [ OK ]
[11:58:22] /bin/mv                                           [ OK ]
[11:58:22] /bin/netstat                                      [ OK ]
[11:58:22] /bin/ps                                           [ Warning ]
[11:58:22] Warning: The file properties have changed:
[11:58:22]          File: /bin/ps
[11:58:23]          Current hash: e2a3f61272faa77bcf5560e2d16333f4a960d676
[11:58:23]          Stored hash : 585c1ea7e99a8c0bc5a0701c307b8f6bb7593200
[11:58:23]          Current inode: 122476    Stored inode: 122485
[11:58:23]          Current file modification time: 1215682145
[11:58:23]          Stored file modification time : 1205449373
[11:58:23] /bin/pwd                                          [ OK ]
[11:58:23] /bin/readlink                                     [ OK ]
[11:58:23] /bin/sed                                          [ OK ]
[11:58:23] /bin/sh                                           [ OK ]
[11:58:23] /bin/su                                           [ OK ]
[11:58:23] /bin/touch                                        [ OK ]
[11:58:24] /bin/uname                                        [ OK ]
[11:58:24] /bin/which                                        [ OK ]
[11:58:24] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[11:58:24] /bin/dash                                         [ OK ]
[11:58:24] /usr/bin/awk                                      [ OK ]
[11:58:24] /usr/bin/basename                                 [ OK ]
[11:58:24] /usr/bin/chattr                                   [ OK ]
[11:58:24] /usr/bin/cut                                      [ OK ]
[11:58:25] /usr/bin/diff                                     [ OK ]
[11:58:25] /usr/bin/dirname                                  [ OK ]
[11:58:25] /usr/bin/dpkg                                     [ OK ]
[11:58:25] /usr/bin/dpkg-query                               [ OK ]
[11:58:25] /usr/bin/du                                       [ OK ]
[11:58:25] /usr/bin/env                                      [ OK ]
[11:58:25] /usr/bin/file                                     [ OK ]
[11:58:25] /usr/bin/find                                     [ OK ]
[11:58:26] /usr/bin/GET                                      [ OK ]
[11:58:26] /usr/bin/groups                                   [ OK ]
[11:58:26] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[11:58:26] /usr/bin/head                                     [ OK ]
[11:58:26] /usr/bin/id                                       [ OK ]
[11:58:26] /usr/bin/killall                                  [ OK ]
[11:58:26] /usr/bin/last                                     [ OK ]
[11:58:26] /usr/bin/lastlog                                  [ OK ]
[11:58:26] /usr/bin/ldd                                      [ OK ]
[11:58:26] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[11:58:27] /usr/bin/less                                     [ OK ]
[11:58:27] /usr/bin/locate                                   [ OK ]
[11:58:27] /usr/bin/logger                                   [ OK ]
[11:58:27] /usr/bin/lsattr                                   [ OK ]
[11:58:27] /usr/bin/lsof                                     [ OK ]
[11:58:27] /usr/bin/mail                                     [ OK ]
[11:58:27] /usr/bin/md5sum                                   [ OK ]
[11:58:27] /usr/bin/mlocate                                  [ OK ]
[11:58:28] /usr/bin/newgrp                                   [ OK ]
[11:58:28] /usr/bin/passwd                                   [ OK ]
[11:58:28] /usr/bin/perl                                     [ OK ]
[11:58:28] /usr/bin/pstree                                   [ OK ]
[11:58:28] /usr/bin/rkhunter                                 [ OK ]
[11:58:28] /usr/bin/rpm                                      [ Warning ]
[11:58:28] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
[11:58:28] /usr/bin/runcon                                   [ OK ]
[11:58:29] /usr/bin/sha1sum                                  [ OK ]
[11:58:29] /usr/bin/size                                     [ OK ]
[11:58:29] /usr/bin/sort                                     [ OK ]
[11:58:29] /usr/bin/stat                                     [ OK ]
[11:58:29] /usr/bin/strace                                   [ OK ]
[11:58:29] /usr/bin/strings                                  [ OK ]
[11:58:29] /usr/bin/sudo                                     [ OK ]
[11:58:29] /usr/bin/tail                                     [ OK ]
[11:58:29] /usr/bin/test                                     [ OK ]
[11:58:30] /usr/bin/top                                      [ Warning ]
[11:58:30] Warning: The file properties have changed:
[11:58:30]          File: /usr/bin/top
[11:58:30]          Current hash: b4cf2a58383c07c23bb012a63b2608b82b3d6c40
[11:58:30]          Stored hash : 38c45e2dc5972a8177f364bbb81c6e246817a934
[11:58:30]          Current inode: 294642    Stored inode: 294793
[11:58:30]          Current file modification time: 1215682145
[11:58:30]          Stored file modification time : 1205449373
[11:58:30] /usr/bin/touch                                    [ OK ]
[11:58:30] /usr/bin/tr                                       [ OK ]
[11:58:30] /usr/bin/uniq                                     [ OK ]
[11:58:30] /usr/bin/users                                    [ OK ]
[11:58:30] /usr/bin/vmstat                                   [ Warning ]
[11:58:30] Warning: The file properties have changed:
[11:58:30]          File: /usr/bin/vmstat
[11:58:30]          Current hash: ac7946f2f2021ca52aae91db9844de1c3651e0e4
[11:58:30]          Stored hash : b0ddafbaa624a5a9cce0667ada94a4f084e94a9e
[11:58:30]          Current inode: 294651    Stored inode: 294868
[11:58:30]          Current file modification time: 1215682145
[11:58:30]          Stored file modification time : 1205449373
[11:58:31] /usr/bin/w                                        [ Warning ]
[11:58:31] Warning: The file properties have changed:
[11:58:31]          File: /usr/bin/w
[11:58:31]          Current hash: cacc1a2b6f692350301516a0e380e18ffa901cd9
[11:58:31]          Stored hash : 17aad0b16c5cc7f079784ce8b0436654325de29d
[11:58:31] /usr/bin/watch                                    [ Warning ]
[11:58:31] Warning: The file properties have changed:
[11:58:31]          File: /usr/bin/watch
[11:58:31]          Current hash: 78dfee98aa89089b102a100665c1352b15bedfbf
[11:58:31]          Stored hash : 0c484585d78e62e691adf4d32f55dd877e2f5c7c
[11:58:31]          Current inode: 297982    Stored inode: 294877
[11:58:31]          Current file modification time: 1215682145
[11:58:31]          Stored file modification time : 1205449373
[11:58:31] /usr/bin/wc                                       [ OK ]
[11:58:31] /usr/bin/wget                                     [ OK ]
[11:58:31] /usr/bin/whatis                                   [ OK ]
[11:58:31] /usr/bin/whereis                                  [ OK ]
[11:58:31] /usr/bin/which                                    [ OK ]
[11:58:32] /usr/bin/who                                      [ OK ]
[11:58:32] /usr/bin/whoami                                   [ OK ]
[11:58:32] /usr/bin/mawk                                     [ OK ]
[11:58:32] /usr/bin/lwp-request                              [ OK ]
[11:58:32] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[11:58:32] /usr/bin/w.procps                                 [ Warning ]
[11:58:32] Warning: The file properties have changed:
[11:58:32]          File: /usr/bin/w.procps
[11:58:32]          Current hash: cacc1a2b6f692350301516a0e380e18ffa901cd9
[11:58:32]          Stored hash : 17aad0b16c5cc7f079784ce8b0436654325de29d
[11:58:32]          Current inode: 298376    Stored inode: 294873
[11:58:32]          Current file modification time: 1215682145
[11:58:32]          Stored file modification time : 1205449373
[11:58:33] /sbin/depmod                                      [ OK ]
[11:58:33] /sbin/ifconfig                                    [ OK ]
[11:58:33] /sbin/ifdown                                      [ OK ]
[11:58:33] /sbin/ifup                                        [ OK ]
[11:58:33] /sbin/init                                        [ OK ]
[11:58:33] /sbin/insmod                                      [ OK ]
[11:58:33] /sbin/ip                                          [ Warning ]
[11:58:33] Warning: The file properties have changed:
[11:58:33]          File: /sbin/ip
[11:58:33]          Current inode: 212279    Stored inode: 212217
[11:58:33]          Current file modification time: 1215987445
[11:58:33]          Stored file modification time : 1211357699
[11:58:34] /sbin/lsmod                                       [ OK ]
[11:58:34] /sbin/modinfo                                     [ OK ]
[11:58:34] /sbin/modprobe                                    [ OK ]
[11:58:34] /sbin/rmmod                                       [ OK ]
[11:58:34] /sbin/runlevel                                    [ OK ]
[11:58:34] /sbin/sulogin                                     [ OK ]
[11:58:35] /sbin/sysctl                                      [ Warning ]
[11:58:35] Warning: The file properties have changed:
[11:58:35]          File: /sbin/sysctl
[11:58:35]          Current hash: 9ff13a7b24c9ef73cc8bf3577c97b77a40d3c1d2
[11:58:35]          Stored hash : a490b16d64f78bf8108e50a6b46d0e43d500d6ad
[11:58:35]          Current inode: 212217    Stored inode: 212310
[11:58:35]          Current file modification time: 1215682145
[11:58:35]          Stored file modification time : 1205449373
[11:58:35] /sbin/syslogd                                     [ OK ]
[11:58:35] /usr/sbin/adduser                                 [ OK ]
[11:58:35] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[11:58:35] /usr/sbin/chroot                                  [ OK ]
[11:58:35] /usr/sbin/cron                                    [ OK ]
[11:58:36] /usr/sbin/groupadd                                [ OK ]
[11:58:36] /usr/sbin/groupdel                                [ OK ]
[11:58:36] /usr/sbin/groupmod                                [ OK ]
[11:58:36] /usr/sbin/grpck                                   [ OK ]
[11:58:36] /usr/sbin/nologin                                 [ OK ]
[11:58:36] /usr/sbin/pwck                                    [ OK ]
[11:58:37] /usr/sbin/tcpd                                    [ OK ]
[11:58:37] /usr/sbin/unhide                                  [ OK ]
[11:58:37] /usr/sbin/useradd                                 [ OK ]
[11:58:37] /usr/sbin/userdel                                 [ OK ]
[11:58:37] /usr/sbin/usermod                                 [ OK ]
[11:58:37] /usr/sbin/vipw                                    [ OK ]
[11:58:37] /usr/sbin/unhide-linux26                          [ OK ]
[11:58:39]
[11:58:39] Checking for rootkits...
[11:58:39] Info: Starting test name 'rootkits'
[11:58:39]
[11:58:39] Performing check of known rootkit files and directories
[11:58:39] Info: Starting test name 'known_rkts'
[11:58:39]
[11:58:39] Checking for 55808 Trojan - Variant A...
[11:58:39]   Checking for file '/tmp/.../r'                  [ Not found ]
[11:58:39]   Checking for file '/tmp/.../a'                  [ Not found ]
[11:58:39] 55808 Trojan - Variant A                          [ Not found ]
[11:58:39]
[11:58:39] Checking for ADM Worm...
[11:58:39]   Checking for string 'w0rm'                      [ Not found ]
[11:58:39] ADM Worm                                          [ Not found ]
[11:58:39]
[11:58:39] Checking for AjaKit Rootkit...
[11:58:39]   Checking for file '/dev/tux/.addr'              [ Not found ]
[11:58:39]   Checking for file '/dev/tux/.proc'              [ Not found ]
[11:58:39]   Checking for file '/dev/tux/.file'              [ Not found ]
[11:58:39]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[11:58:40]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[11:58:40]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[11:58:40]   Checking for directory '/dev/tux'               [ Not found ]
[11:58:40]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[11:58:40] AjaKit Rootkit                                    [ Not found ]
[11:58:40]
[11:58:40] Checking for aPa Kit...
[11:58:40]   Checking for file '/usr/share/.aPa'             [ Not found ]
[11:58:40] aPa Kit                                           [ Not found ]
[11:58:40]
[11:58:40] Checking for Apache Worm...
[11:58:40]   Checking for file '/bin/.log'                   [ Not found ]
[11:58:40] Apache Worm                                       [ Not found ]
[11:58:40]
[11:58:40] Checking for Ambient (ark) Rootkit...
[11:58:40]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[11:58:40]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[11:58:40]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[11:58:40]   Checking for directory '/dev/ptyxx'             [ Not found ]
[11:58:40] Ambient (ark) Rootkit                             [ Not found ]
[11:58:40]
[11:58:40] Checking for Balaur Rootkit...
[11:58:40]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[11:58:40]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[11:58:40]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[11:58:40]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[11:58:40] Balaur Rootkit                                    [ Not found ]
[11:58:40]
[11:58:40] Checking for BeastKit Rootkit...
[11:58:40]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[11:58:40]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[11:58:40]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[11:58:40]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[11:58:40]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[11:58:40]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[11:58:40]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[11:58:41]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[11:58:41] BeastKit Rootkit                                  [ Not found ]
[11:58:41]
[11:58:41] Checking for beX2 Rootkit...
[11:58:41]   Checking for directory '/usr/include/bex'       [ Not found ]
[11:58:41] beX2 Rootkit                                      [ Not found ]
[11:58:41]
[11:58:41] Checking for BOBKit Rootkit...
[11:58:41]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../find'           [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../du'             [ Not found ]
[11:58:41]   Checking for file '/usr/lib/.../top'            [ Not found ]
[11:58:41]   Checking for directory '/usr/lib/...'           [ Not found ]
[11:58:41]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[11:58:41]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[11:58:41]   Checking for directory '/tmp/.bkp'              [ Not found ]
[11:58:41] BOBKit Rootkit                                    [ Not found ]
[11:58:41]
[11:58:41] Checking for CiNIK Worm (Slapper.B variant)...
[11:58:41]   Checking for file '/tmp/.cinik'                 [ Not found ]
[11:58:41]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[11:58:42] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[11:58:42]
[11:58:42] Checking for Danny-Boy's Abuse Kit...
[11:58:42]   Checking for file '/dev/mdev'                   [ Not found ]
[11:58:42]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[11:58:42] Danny-Boy's Abuse Kit                             [ Not found ]
[11:58:42]
[11:58:42] Checking for Devil RootKit...
[11:58:42]   Checking for file '/var/lib/games/.src'         [ Not found ]
[11:58:42]   Checking for file '/dev/dsx'                    [ Not found ]
[11:58:42]   Checking for file '/dev/caca'                   [ Not found ]
[11:58:42] Devil RootKit                                     [ Not found ]
[11:58:42]
[11:58:42] Checking for Dica-Kit Rootkit...
[11:58:42]   Checking for file '/lib/.sso'                   [ Not found ]
[11:58:42]   Checking for file '/lib/.so'                    [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/va'         [ Not found ]
[11:58:42]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[11:58:42]   Checking for file '/usr/bin/.etc'               [ Not found ]
[11:58:42]   Checking for directory '/var/run/...dica'       [ Not found ]
[11:58:42]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[11:58:42]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[11:58:42] Dica-Kit Rootkit                                  [ Not found ]
[11:58:42]
[11:58:42] Checking for Dreams Rootkit...
[11:58:42]   Checking for file '/dev/ttyoa'                  [ Not found ]
[11:58:42]   Checking for file '/dev/ttyof'                  [ Not found ]
[11:58:42]   Checking for file '/dev/ttyop'                  [ Not found ]
[11:58:42]   Checking for file '/usr/bin/sense'              [ Not found ]
[11:58:42]   Checking for file '/usr/bin/sl2'                [ Not found ]
[11:58:43]   Checking for file '/usr/bin/logclear'           [ Not found ]
[11:58:43]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[11:58:43]   Checking for file '/usr/bin/snfs'               [ Not found ]
[11:58:43]   Checking for file '/usr/lib/libsss'             [ Not found ]
[11:58:43]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[11:58:43] Dreams Rootkit                                    [ Not found ]
[11:58:43]
[11:58:43] Checking for Duarawkz Rootkit...
[11:58:43]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[11:58:43]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[11:58:43] Duarawkz Rootkit                                  [ Not found ]
[11:58:43]
[11:58:43] Checking for Enye LKM...
[11:58:43]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[11:58:43] Enye LKM                                          [ Not found ]
[11:58:43]
[11:58:43] Checking for Flea Linux Rootkit...
[11:58:43]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:58:43]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[11:58:43]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[11:58:43]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[11:58:43]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[11:58:43]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[11:58:43]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[11:58:43]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[11:58:43]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[11:58:43]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[11:58:43]   Checking for directory '/dev/..0'               [ Not found ]
[11:58:43]   Checking for directory '/dev/..0/backup'        [ Not found ]
[11:58:43] Flea Linux Rootkit                                [ Not found ]
[11:58:43]
[11:58:43] Checking for FreeBSD Rootkit...
[11:58:43]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[11:58:43]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[11:58:44]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[11:58:44]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[11:58:44]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[11:58:44]   Checking for file '/bin/sysback'                [ Not found ]
[11:58:44]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[11:58:44]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[11:58:44]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[11:58:44] FreeBSD Rootkit                                   [ Not found ]
[11:58:44]
[11:58:44] Checking for ****`it Rootkit...
[11:58:44]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[11:58:44]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[11:58:44] ****`it Rootkit                                   [ Not found ]
[11:58:44]
[11:58:44] Checking for GasKit Rootkit...
[11:58:44]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[11:58:44]   Checking for directory '/dev/dev'               [ Not found ]
[11:58:44]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[11:58:44]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[11:58:44] GasKit Rootkit                                    [ Not found ]
[11:58:44]
[11:58:44] Checking for Heroin LKM...
[11:58:44]   Checking for kernel symbol 'heroin'             [ Not found ]
[11:58:44] Heroin LKM                                        [ Not found ]
[11:58:44]
[11:58:44] Checking for HjC Kit...
[11:58:44]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[11:58:44] HjC Kit                                           [ Not found ]
[11:58:45]
[11:58:45] Checking for ignoKit Rootkit...
[11:58:45]   Checking for file '/lib/defs/p'                 [ Not found ]
[11:58:45]   Checking for file '/lib/defs/q'                 [ Not found ]
[11:58:45]   Checking for file '/lib/defs/r'                 [ Not found ]
[11:58:45]   Checking for file '/lib/defs/s'                 [ Not found ]
[11:58:45]   Checking for file '/lib/defs/t'                 [ Not found ]
[11:58:45]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[11:58:45]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[11:58:45]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[11:58:45]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[11:58:45]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[11:58:45]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[11:58:45]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[11:58:45]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[11:58:45]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[11:58:45] ignoKit Rootkit                                   [ Not found ]
[11:58:45]
[11:58:45] Checking for ImperalsS-FBRK Rootkit...
[11:58:45]   Checking for directory '/dev/fd/.88'            [ Not found ]
[11:58:45]   Checking for directory '/dev/fd/.99'            [ Not found ]
[11:58:45] ImperalsS-FBRK Rootkit                            [ Not found ]
[11:58:45]
[11:58:45] Checking for Irix Rootkit...
[11:58:45]   Checking for directory '/dev/pts/01'            [ Not found ]
[11:58:45]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[11:58:45]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[11:58:45]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[11:58:45] Irix Rootkit                                      [ Not found ]
[11:58:45]
[11:58:45] Checking for Kitko Rootkit...
[11:58:45]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[11:58:45] Kitko Rootkit                                     [ Not found ]
[11:58:45]
[11:58:45] Checking for Knark Rootkit...
[11:58:45]   Checking for file '/proc/knark/pids'            [ Not found ]
[11:58:46]   Checking for directory '/proc/knark'            [ Not found ]
[11:58:46] Knark Rootkit                                     [ Not found ]
[11:58:46]
[11:58:46] Checking for Li0n Worm...
[11:58:46]   Checking for file '/bin/in.telnetd'             [ Not found ]
[11:58:46]   Checking for file '/bin/mjy'                    [ Not found ]
[11:58:46]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[11:58:46]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[11:58:46]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[11:58:46]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[11:58:46] Li0n Worm                                         [ Not found ]
[11:58:46]
[11:58:46] Checking for Lockit / LJK2 Rootkit...
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[11:58:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[11:58:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[11:58:47]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[11:58:47] Lockit / LJK2 Rootkit                             [ Not found ]
[11:58:47]
[11:58:47] Checking for Mood-NT Rootkit...
[11:58:47]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[11:58:47]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[11:58:47]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[11:58:47]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[11:58:47]   Checking for directory '/_cthulhu'              [ Not found ]
[11:58:48] Mood-NT Rootkit                                   [ Not found ]
[11:58:48]
[11:58:48] Checking for MRK Rootkit...
[11:58:48]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[11:58:48]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[11:58:48]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[11:58:48]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[11:58:48]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[11:58:48]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[11:58:48] MRK Rootkit                                       [ Not found ]
[11:58:48]
[11:58:48] Checking for Ni0 Rootkit...
[11:58:48]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[11:58:48]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[11:58:48]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[11:58:48]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[11:58:48]   Checking for directory '/tmp/waza'              [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[11:58:48]   Checking for directory '/usr/sbin/es'           [ Not found ]
[11:58:48] Ni0 Rootkit                                       [ Not found ]
[11:58:48]
[11:58:48] Checking for Ohhara Rootkit...
[11:58:48]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[11:58:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[11:58:48] Ohhara Rootkit                                    [ Not found ]
[11:58:48]
[11:58:48] Checking for Optic Kit (Tux) Worm...
[11:58:48]   Checking for directory '/dev/tux'               [ Not found ]
[11:58:48]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[11:58:48]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[11:58:48]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[11:58:48] Optic Kit (Tux) Worm                              [ Not found ]
[11:58:49]
[11:58:49] Checking for Oz Rootkit...
[11:58:49]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[11:58:49]   Checking for directory '/dev/.oz'               [ Not found ]
[11:58:49] Oz Rootkit                                        [ Not found ]
[11:58:49]
[11:58:49] Checking for Phalanx Rootkit...
[11:58:49]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[11:58:49]   Checking for file '/etc/host.ph1'               [ Not found ]
[11:58:49]   Checking for file '/bin/host.ph1'               [ Not found ]
[11:58:49]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[11:58:49]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[11:58:49] Phalanx Rootkit                                   [ Not found ]
[11:58:49]
[11:58:49] Checking for Phalanx Rootkit (strings)...
[11:58:49]   Checking for string 'phalanx'                   [ Not found ]
[11:58:49] Phalanx Rootkit (strings)                         [ Not found ]
[11:58:49]
[11:58:49] Checking for Portacelo Rootkit...
[11:58:49]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../.p'             [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../getty'          [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../show'           [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[11:58:49]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[11:58:49]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[11:58:49] Portacelo Rootkit                                 [ Not found ]
[11:58:49]
[11:58:49] Checking for R3dstorm Toolkit...
[11:58:49]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[11:58:49]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[11:58:50]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[11:58:50]   Checking for file '/bin/.../see_all'            [ Not found ]
[11:58:50]   Checking for directory '/var/log/tk02'          [ Not found ]
[11:58:50]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[11:58:50]   Checking for directory '/bin/...'               [ Not found ]
[11:58:50] R3dstorm Toolkit                                  [ Not found ]
[11:58:50]
[11:58:50] Checking for RH-Sharpe's Rootkit...
[11:58:50]   Checking for file '/bin/lps'                    [ Not found ]
[11:58:50]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[11:58:50]   Checking for file '/usr/bin/ltop'               [ Not found ]
[11:58:50]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[11:58:50]   Checking for file '/usr/bin/ldu'                [ Not found ]
[11:58:50]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[11:58:50]   Checking for file '/usr/bin/wp'                 [ Not found ]
[11:58:50]   Checking for file '/usr/bin/shad'               [ Not found ]
[11:58:50]   Checking for file '/usr/bin/vadim'              [ Not found ]
[11:58:50]   Checking for file '/usr/bin/slice'              [ Not found ]
[11:58:50]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[11:58:50]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[11:58:50] RH-Sharpe's Rootkit                               [ Not found ]
[11:58:50]
[11:58:50] Checking for RSHA's Rootkit...
[11:58:50]   Checking for file '/bin/kr4p'                   [ Not found ]
[11:58:50]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[11:58:50]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[11:58:50]   Checking for file '/usr/bin/slice2'             [ Not found ]
[11:58:50]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[11:58:50]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[11:58:50]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[11:58:50]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[11:58:50] RSHA's Rootkit                                    [ Not found ]
[11:58:50]
[11:58:50] Checking for Scalper Worm...
[11:58:50]   Checking for file '/tmp/.a'                     [ Not found ]
[11:58:51]   Checking for file '/tmp/.uua'                   [ Not found ]
[11:58:51] Scalper Worm                                      [ Not found ]
[11:58:51]
[11:58:51] Checking for Sebek LKM...
[11:58:51]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[11:58:51] Sebek LKM                                         [ Not found ]
[11:58:51]
[11:58:51] Checking for Shutdown Rootkit...
[11:58:51]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[11:58:51]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[11:58:51]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[11:58:51]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[11:58:51]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[11:58:51]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[11:58:51]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[11:58:51]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[11:58:51] Shutdown Rootkit                                  [ Not found ]
[11:58:51]
[11:58:51] Checking for SHV4 Rootkit...
[11:58:52]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:58:52]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[11:58:52]   Checking for file '/lib/lidps1.so'              [ Not found ]
[11:58:52]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[11:58:52]   Checking for directory '/lib/security/.config'  [ Not found ]
[11:58:52]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[11:58:52] SHV4 Rootkit                                      [ Not found ]
[11:58:52]
[11:58:52] Checking for SHV5 Rootkit...
[11:58:52]   Checking for file '/etc/sh.conf'                [ Not found ]
[11:58:52]   Checking for file '/dev/srd0'                   [ Not found ]
[11:58:52]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[11:58:52] SHV5 Rootkit                                      [ Not found ]
[11:58:52]
[11:58:52] Checking for Sin Rootkit...
[11:58:52]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[11:58:52]   Checking for file '/dev/ttyoa'                  [ Not found ]
[11:58:52]   Checking for file '/dev/ttyof'                  [ Not found ]
[11:58:52]   Checking for file '/dev/ttyop'                  [ Not found ]
[11:58:52]   Checking for file '/dev/ttyos'                  [ Not found ]
[11:58:52]   Checking for file '/usr/lib/.lib'               [ Not found ]
[11:58:52]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[11:58:52]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[11:58:52]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[11:58:52]   Checking for file '/usr/man/man1/...'           [ Not found ]
[11:58:52]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[11:58:52]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[11:58:52]   Checking for directory '/usr/lib/sn'            [ Not found ]
[11:58:52]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[11:58:52]   Checking for directory '/dev/.haos'             [ Not found ]
[11:58:52] Sin Rootkit                                       [ Not found ]
[11:58:52]
[11:58:52] Checking for Slapper Worm...
[11:58:52]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[11:58:52]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[11:58:53]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[11:58:53]   Checking for file '/tmp/httpd'                  [ Not found ]
[11:58:53]   Checking for file '/tmp/.unlock'                [ Not found ]
[11:58:53]   Checking for file '/tmp/update'                 [ Not found ]
[11:58:53]   Checking for file '/tmp/.cinik'                 [ Not found ]
[11:58:53]   Checking for file '/tmp/.b'                     [ Not found ]
[11:58:53] Slapper Worm                                      [ Not found ]
[11:58:53]
[11:58:53] Checking for Sneakin Rootkit...
[11:58:53]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[11:58:53] Sneakin Rootkit                                   [ Not found ]
[11:58:53]
[11:58:53] Checking for Suckit Rootkit...
[11:58:53]   Checking for file '/sbin/initsk12'              [ Not found ]
[11:58:53]   Checking for file '/sbin/initxrk'               [ Not found ]
[11:58:53]   Checking for file '/usr/bin/null'               [ Not found ]
[11:58:53]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[11:58:53]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[11:58:53]   Checking for directory '/etc/.MG'               [ Not found ]
[11:58:53]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[11:58:53]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[11:58:53] Suckit Rootkit                                    [ Not found ]
[11:58:53]
[11:58:53] Checking for SunOS Rootkit...
[11:58:53]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[11:58:53]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[11:58:53]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[11:58:53]   Checking for file '/bin/xlogin'                 [ Not found ]
[11:58:54]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[11:58:54]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[11:58:54]   Checking for file '/sbin/login'                 [ Not found ]
[11:58:54]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[11:58:54]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[11:58:54]   Checking for file '/dev/kmod'                   [ Not found ]
[11:58:54]   Checking for file '/dev/dos'                    [ Not found ]
[11:58:54] SunOS Rootkit                                     [ Not found ]
[11:58:54]
[11:58:54] Checking for SunOS / NSDAP Rootkit...
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[11:58:54]   Checking for file '/usr/lib/lpset'              [ Not found ]
[11:58:54]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[11:58:54] SunOS / NSDAP Rootkit                             [ Not found ]
[11:58:54]
[11:58:54] Checking for Superkit Rootkit...
[11:58:54]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[11:58:54] Superkit Rootkit                                  [ Not found ]
[11:58:54]
[11:58:54] Checking for TBD (Telnet BackDoor)...
[11:58:54]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[11:58:54] TBD (Telnet BackDoor)                             [ Not found ]
[11:58:54]
[11:58:54] Checking for TeLeKiT Rootkit...
[11:58:54]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[11:58:54]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[11:58:54]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[11:58:55]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[11:58:55]   Checking for file '/dev/ptyr'                   [ Not found ]
[11:58:55]   Checking for file '/dev/ptyp'                   [ Not found ]
[11:58:55]   Checking for file '/dev/ptyq'                   [ Not found ]
[11:58:55]   Checking for file '/dev/hda06'                  [ Not found ]
[11:58:55]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[11:58:55]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[11:58:55]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[11:58:55]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[11:58:55] TeLeKiT Rootkit                                   [ Not found ]
[11:58:55]
[11:58:55] Checking for T0rn Rootkit...
[11:58:55]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[11:58:55]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[11:58:56]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[11:58:56]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[11:58:56]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[11:58:56]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[11:58:56]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[11:58:56]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[11:58:56]   Checking for directory '/dev/.lib'              [ Not found ]
[11:58:56]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[11:58:56]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[11:58:56]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[11:58:56]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[11:58:56]   Checking for directory '/usr/src/.****'         [ Not found ]
[11:58:56]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[11:58:56]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[11:58:56]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[11:58:56]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[11:58:56] T0rn Rootkit                                      [ Not found ]
[11:58:56]
[11:58:56] Checking for Trojanit Kit...
[11:58:56]   Checking for file '/bin/.ls'                    [ Not found ]
[11:58:56]   Checking for file '/bin/.ps'                    [ Not found ]
[11:58:56]   Checking for file '/bin/.netstat'               [ Not found ]
[11:58:56]   Checking for file '/usr/bin/.nop'               [ Not found ]
[11:58:56]   Checking for file '/usr/bin/.who'               [ Not found ]
[11:58:56] Trojanit Kit                                      [ Not found ]
[11:58:56]
[11:58:56] Checking for Tuxtendo Rootkit...
[11:58:56]   Checking for file '/dev/tux/.addr'              [ Not found ]
[11:58:56]   Checking for file '/dev/tux/.cron'              [ Not found ]
[11:58:56]   Checking for file '/dev/tux/.file'              [ Not found ]
[11:58:56]   Checking for file '/dev/tux/.log'               [ Not found ]
[11:58:56]   Checking for file '/dev/tux/.proc'              [ Not found ]
[11:58:56]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[11:58:57]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[11:58:57]   Checking for directory '/dev/tux'               [ Not found ]
[11:58:57]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[11:58:57]   Checking for directory '/dev/tux/backup'        [ Not found ]
[11:58:57] Tuxtendo Rootkit                                  [ Not found ]
[11:58:57]
[11:58:57] Checking for URK Rootkit...
[11:58:57]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[11:58:57]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[11:58:57]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[11:58:57]   Checking for file '/tmp/conf.inf'               [ Not found ]
[11:58:57]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[11:58:57] URK Rootkit                                       [ Not found ]
[11:58:57]
[11:58:57] Checking for VcKit Rootkit...
[11:58:57]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[11:58:57]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[11:58:57] VcKit Rootkit                                     [ Not found ]
[11:58:57]
[11:58:57] Checking for Volc Rootkit...
[11:58:57]   Checking for directory '/var/spool/.recent'     [ Not found ]
[11:58:58]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[11:58:58]   Checking for directory '/usr/lib/volc'          [ Not found ]
[11:58:58]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[11:58:58] Volc Rootkit                                      [ Not found ]
[11:58:58]
[11:58:58] Checking for X-Org SunOS Rootkit...
[11:58:58]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[11:58:58]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[11:58:58]   Checking for file '/usr/bin/srload'             [ Not found ]
[11:58:58]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[11:58:58]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[11:58:58]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[11:58:58]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[11:58:58]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[11:58:58]   Checking for directory '/usr/share/man...'      [ Not found ]
[11:58:58] X-Org SunOS Rootkit                               [ Not found ]
[11:58:58]
[11:58:58] Checking for zaRwT.KiT Rootkit...
[11:58:58]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[11:58:58]   Checking for file '/dev/ttyf'                   [ Not found ]
[11:58:58]   Checking for file '/dev/ttyp'                   [ Not found ]
[11:58:58]   Checking for file '/dev/ttyn'                   [ Not found ]
[11:58:58]   Checking for file '/rk/tulz'                    [ Not found ]
[11:58:58]   Checking for directory '/rk'                    [ Not found ]
[11:58:58]   Checking for directory '/dev/rd/s'              [ Not found ]
[11:58:58] zaRwT.KiT Rootkit                                 [ Not found ]
[11:58:58]
[11:58:58] Performing additional rootkit checks
[11:58:58] Info: Starting test name 'additional_rkts'
[11:58:58]
[11:58:58]   Performing Suckit Rookit additional checks
[11:58:58]     Checking /sbin/init link count                [ OK ]
[11:58:58]     Checking for hidden file extensions           [ None found ]
[11:58:58]     Running skdet command                         [ Skipped ]
[11:58:59] Info: Unable to find the 'skdet' command
[11:58:59]   Suckit Rookit additional checks                 [ OK ]
[11:58:59]
[11:58:59]   Performing check of possible rootkit files and directories
[11:58:59] Info: Starting test name 'possible_rkt_files'
[11:58:59]     Checking for file '/dev/sdr0'                 [ Not found ]
[11:58:59]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[11:58:59]     Checking for file '/tmp/.bash_history'        [ Not found ]
[11:58:59]     Checking for file '/usr/info/.clib'           [ Not found ]
[11:58:59]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[11:58:59]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[11:58:59]     Checking for file '/sbin/create'              [ Not found ]
[11:58:59]     Checking for file '/dev/ttypz'                [ Not found ]
[11:58:59]     Checking for directory '/usr/bin/take'        [ Not found ]
[11:58:59]     Checking for directory '/usr/src/.lib'        [ Not found ]
[11:58:59]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[11:58:59]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[11:58:59]     Checking for directory '/usr/sbin/...'        [ Not found ]
[11:58:59]     Checking for directory '/usr/share/.gun'      [ Not found ]
[11:58:59]   Checking for possible rootkit files and directories [ None found ]
[11:58:59]
[11:58:59]   Performing check for possible rootkit strings
[11:58:59] Info: Starting test name 'possible_rkt_strings'
[11:58:59] Info: Found local startup file: /etc/rc.local
[11:58:59]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[11:58:59]     Checking for string '****'                    [ Not found ]
[11:58:59]     Checking for string 'backdoor'                [ Not found ]
[11:58:59]     Checking for string 'vt200'                   [ Not found ]
[11:59:00]     Checking for string '/usr/bin/xstat'          [ Not found ]
[11:59:00]     Checking for string '/bin/envpc'              [ Not found ]
[11:59:00]     Checking for string 'L4m3r0x'                 [ Not found ]
[11:59:00]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:59:00]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[11:59:00]     Checking for string '/dev/sgk'                [ Not found ]
[11:59:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:59:00]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:59:00]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[11:59:00]     Checking for string '/lib/.sso'               [ Not found ]
[11:59:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:59:00]     Checking for string '/dev/caca'               [ Not found ]
[11:59:00]     Checking for string '/dev/ttyoa'              [ Not found ]
[11:59:00]     Checking for string 'syg'                     [ Not found ]
[11:59:00]     Checking for string '/dev/pts/01'             [ Not found ]
[11:59:00]     Checking for string 'tw33dl3'                 [ Not found ]
[11:59:00]     Checking for string 'psniff'                  [ Not found ]
[11:59:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[11:59:00]     Checking for string 'promiscuous'             [ Not found ]
[11:59:01]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:59:01]     Checking for string '/dev/xdta'               [ Not found ]
[11:59:01]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[11:59:01]     Checking for string 'in.inetd'                [ Not found ]
[11:59:01]     Checking for string '#<HIDE_.*>'              [ Not found ]
[11:59:01]     Checking for string 'bin/xchk'                [ Not found ]
[11:59:01]     Checking for string 'bin/xsf'                 [ Not found ]
[11:59:01]   Checking for possible rootkit strings           [ None found ]
[11:59:01]
[11:59:01] Performing malware checks
[11:59:01] Info: Starting test name 'malware'
[11:59:01]
[11:59:01] Info: Test 'deleted_files' disabled at users request.
[11:59:01] Info: Starting test name 'running_procs'
[11:59:01]   Checking running processes for suspicious files [ None found ]
[11:59:01]
[11:59:01] Info: Test 'hidden_procs' disabled at users request.
[11:59:01]
[11:59:01] Info: Test 'suspscan' disabled at users request.
[11:59:01]
[11:59:01]   Performing check for login backdoors
[11:59:01] Info: Starting test name 'other_malware'
[11:59:01]     Checking for '/bin/.login'                    [ Not found ]
[11:59:02]     Checking for '/sbin/.login'                   [ Not found ]
[11:59:02]   Checking for login backdoors                    [ None found ]
[11:59:02]
[11:59:02]   Performing check for suspicious directories
[11:59:02]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[11:59:02]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[11:59:02]   Checking for suspicious directories             [ None found ]
[11:59:02]
[11:59:02]   Checking for software intrusions                [ Skipped ]
[11:59:02] Info: Check skipped - tripwire not installed
[11:59:02]
[11:59:02]   Performing check for sniffer log files
[11:59:02]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[11:59:02]   Checking for sniffer log files                  [ None found ]
[11:59:02]
[11:59:02] Performing trojan specific checks
[11:59:02] Info: Starting test name 'trojans'
[11:59:02] Info: Using inetd configuration file '/etc/inetd.conf'
[11:59:02]   Checking for enabled inetd services             [ OK ]
[11:59:02]
[11:59:02]   Performing check for enabled xinetd services
[11:59:02]   Checking for enabled xinetd services            [ Skipped ]
[11:59:02] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[11:59:02] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[11:59:02]
[11:59:02] Performing Linux specific checks
[11:59:02] Info: Starting test name 'os_specific'
[11:59:02]   Checking kernel module commands                 [ OK ]
[11:59:02] Info: Using modules pathname of '/lib/modules/2.6.24-20-generic'
[11:59:02]   Checking kernel module names                    [ OK ]
[11:59:02]
[11:59:02] Checking the network...
[11:59:02] Info: Starting test name 'network'
[11:59:02] Info: Starting test name 'ports'
[11:59:02]
[11:59:02] Performing check for backdoor ports
[11:59:03]   Checking for UDP port 2001                      [ Not found ]
[11:59:03]   Checking for TCP port 2006                      [ Not found ]
[11:59:03]   Checking for TCP port 2128                      [ Not found ]
[11:59:03]   Checking for TCP port 14856                     [ Not found ]
[11:59:03]   Checking for TCP port 47107                     [ Not found ]
[11:59:04]   Checking for TCP port 60922                     [ Not found ]
[11:59:04]
[11:59:04] Performing checks on the network interfaces
[11:59:04] Info: Starting test name 'promisc'
[11:59:04]   Checking for promiscuous interfaces             [ None found ]
[11:59:04]
[11:59:04] Info: Test 'packet_cap_apps' disabled at users request.
[11:59:04]
[11:59:04] Checking the local host...
[11:59:04] Info: Starting test name 'local_host'
[11:59:04]
[11:59:04] Performing system boot checks
[11:59:04] Info: Starting test name 'startup_files'
[11:59:04]   Checking for local host name                    [ Found ]
[11:59:04] Info: Starting test name 'startup_malware'
[11:59:04] Info: Found local startup file: /etc/rc.local
[11:59:04]   Checking for local startup files                [ Found ]
[11:59:04]   Checking local startup files for malware        [ None found ]
[11:59:04] Info: Found system startup directory: /etc/init.d
[11:59:05]   Checking system startup files for malware       [ None found ]
[11:59:05]
[11:59:05] Performing group and account checks
[11:59:05] Info: Starting test name 'group_accounts'
[11:59:05]   Checking for passwd file                        [ Found ]
[11:59:05] Info: Found password file: /etc/passwd
[11:59:05]   Checking for root equivalent (UID 0) accounts   [ None found ]
[11:59:05] Info: Found shadow file: /etc/shadow
[11:59:05]   Checking for passwordless accounts              [ None found ]
[11:59:06] Info: Starting test name 'passwd_changes'
[11:59:06]   Checking for passwd file changes                [ None found ]
[11:59:06] Info: Starting test name 'group_changes'
[11:59:06]   Checking for group file changes                 [ None found ]
[11:59:06]   Checking root account shell history files       [ OK ]
[11:59:06]
[11:59:06] Performing system configuration file checks
[11:59:06] Info: Starting test name 'system_configs'
[11:59:06]   Checking for SSH configuration file             [ Not found ]
[11:59:06]   Checking for running syslog daemon              [ Found ]
[11:59:06]   Checking for syslog configuration file          [ Found ]
[11:59:06] Info: Found syslog configuration file: /etc/syslog.conf
[11:59:06]   Checking if syslog remote logging is allowed    [ Not allowed ]
[11:59:06]
[11:59:06] Performing filesystem checks
[11:59:06] Info: Starting test name 'filesystem'
[11:59:06] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:59:18]   Checking /dev for suspicious file types         [ Warning ]
[11:59:18] Warning: Suspicious file types found in /dev:
[11:59:18]          /dev/shm/pulse-shm-550581904: data
[11:59:18]   Checking for hidden files and directories       [ Warning ]
[11:59:18] Warning: Hidden directory found: /etc/.java
[11:59:18] Warning: Hidden directory found: /dev/.static
[11:59:18] Warning: Hidden directory found: /dev/.udev
[11:59:18] Warning: Hidden directory found: /dev/.initramfs
[11:59:18]
[11:59:18] Checking application versions...
[11:59:18] Info: Starting test name 'apps'
[11:59:19]   Checking version of Exim MTA                    [ OK ]
[11:59:19] Info: Application 'exim' version '4.69' found.
[11:59:19]   Checking version of GnuPG                       [ OK ]
[11:59:19] Info: Application 'gpg' version '1.4.6' found.
[11:59:19] Info: Application 'httpd' not found.
[11:59:19] Info: Application 'named' not found.
[11:59:19]   Checking version of OpenSSL                     [ OK ]
[11:59:19] Info: Application 'openssl' version '0.9.8g' found.
[11:59:19] Info: Application 'php' not found.
[11:59:19] Info: Application 'procmail' not found.
[11:59:19] Info: Application 'proftpd' not found.
[11:59:19] Info: Application 'sshd' not found.
[11:59:19] Info: Applications checked: 3 out of 9
[11:59:19]
[11:59:19] System checks summary
[11:59:19] =====================
[11:59:19]
[11:59:19] File properties checks...
[11:59:19] Files checked: 126
[11:59:19] Suspect files: 11
[11:59:19]
[11:59:19] Rootkit checks...
[11:59:19] Rootkits checked : 109
[11:59:19] Possible rootkits: 0
[11:59:19]
[11:59:19] Applications checks...
[11:59:19] Applications checked: 3
[11:59:19] Suspect applications: 0
[11:59:19]
[11:59:19] The system checks took: 1 minute and 3 seconds
[11:59:20]
[11:59:20] Info: End date is Wed Jul 30 11:59:20 EDT 2008

```Ok...   now what?

I have never had a rootkit, and nothing has been acting all that funny. I do have portsentry on... could it be a false positive?

Edit: Alright, here is the tiger log.

```
Security scripts *** 3.2.2, 2007.08.28.00.00 ***
Wed Jul 30 12:10:57 EDT 2008
12:10> Beginning security report for leo-laptop (x86_64 Linux 2.6.24-20-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.
--WARN-- [pass014w] Login (backup) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (bin) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (daemon) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (games) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (gnats) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (irc) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (libuuid) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (list) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (lp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (mail) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (man) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (news) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (nobody) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (proxy) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (root) is disabled, but has a valid shell. 
--WARN-- [pass015w] Login ID sync does not have a valid shell (/bin/sync). 
--WARN-- [pass014w] Login (sys) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (uucp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (www-data) is disabled, but has a valid shell. 
--WARN-- [pass012w] Home directory /nonexistent exists multiple times (2) in 
         /etc/passwd. 
--WARN-- [pass006w] Integrity of password files questionable (/usr/sbin/pwck 
         -r). 

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.
--WARN-- [acc006w] Login ID gdm's home directory (/var/lib/gdm) has group 
         `gdm' write access. 
--WARN-- [acc021w] Login ID libuuid appears to be a dormant account. 
--WARN-- [acc022w] Login ID nobody home directory (/nonexistent) is not 
         accessible. 

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...
--WARN-- [root003w] Root user has message capability turned on. 

# Performing check of PATH components...
--WARN-- [path009w] /etc/profile does not export an initial setting for PATH. 
# Only checking user 'root'

# Performing check of anonymous FTP...

# Performing checks of mail aliases...
# Checking aliases from /etc/aliases.

# Performing check of `cron' entries...
--WARN-- [cron004w] Root crontab does not exist 
--WARN-- [cron005w] Use of cron is not restricted 

# Performing check of 'inetd'...
# Checking inetd entries from /etc/inetd.conf

# Performing check of services with tcp wrappers...
# Analysing inetd entries from /etc/inetd.conf

# Performing check of 'services' ...
# Checking services from /etc/services.
--WARN-- [inet003w] The port for service postgres is also assigned to service 
         postgresql. 
--WARN-- [inet003w] The port for service postgres is also assigned to service 
         postgresql. 
--WARN-- [inet003w] The port for service sane is also assigned to service 
         sane-port. 

# Performing NFS exports check...

# Performing check of system file permissions...

# Checking for known intrusion signs...
# Testing for promiscuous interfaces with /bin/ip
# Testing for backdoors in inetd.conf

# Performing check of files in system mail spool...

# Performing check for rookits...
# Running chkrootkit (/usr/sbin/chkrootkit) to perform further checks...
--ALERT-- [rootkit005a] Chkrootkit has found a file which seems to be infected 
          because of a rootkit 
--ALERT-- [rootkit009a] A rootkit seems to be installed in the system 
INFECTED (PORTS: 1524 6667 31337)

# Performing system specific checks...
# Performing checks for Linux/2...

# Checking boot loader file permissions...
--WARN-- [boot02] The configuration file /boot/grub/menu.lst has group 
         permissions. Should be 0600 
--FAIL-- [boot02] The configuration file /boot/grub/menu.lst has world 
         permissions. Should be 0600 
--WARN-- [boot06] The Grub bootloader does not have a password configured. 

# Checking for vulnerabilities in inittab configuration...

# Checking for correct umask settings for init scripts...
--WARN-- [misc021w] There are no umask entries in /etc/init.d/rcS 

# Checking Logins not used on the system ...

# Checking network configuration
--FAIL-- [lin013f] The system is not protected against Syn flooding attacks 
--WARN-- [lin017w] The system is not configured to log suspicious (martian) 
         packets 

# Verifying system specific password checks...

# Checking OS release...
--WARN-- [osv004w] Unreleased Debian GNU/Linux version `lenny/sid' 

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.pcimap' checksum differs from 
         installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-20-generic/modules.dep' 
         checksum differs from installed package 
         'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.ieee1394map' checksum differs 
         from installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.usbmap' checksum differs from 
         installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.isapnpmap' checksum differs 
         from installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.inputmap' checksum differs 
         from installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.seriomap' checksum differs 
         from installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.alias' checksum differs from 
         installed package 'linux-image-2.6.24-20-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.24-20-generic/modules.symbols' checksum differs 
         from installed package 'linux-image-2.6.24-20-generic'. 

# Checking installed files against packages...
--WARN-- [lin001w] File `/lib/linux-restricted-modules/.nvidia_new_installed' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-17-generic/misc/vboxdrv.ko' does 
         not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-19-generic/misc/vboxdrv.ko' does 
         not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/wl.ko' does 
         not belong to any package. 
--WARN-- [lin001w] File 
         `/lib/modules/2.6.24-20-generic/volatile/nvidia_new.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File 
         `/lib/modules/2.6.24-20-generic/volatile/nvidia_legacy.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/nvidia.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fglrx.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fcpci.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fcdslusb2.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fcdslusb.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File 
         `/lib/modules/2.6.24-20-generic/volatile/fcdslslusb.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fcdslsl.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/fcdsl2.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/ath_hal.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/volatile/.mounted' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.24-20-generic/misc/vboxdrv.ko' does 
         not belong to any package. 

# Performing check of root directory...

# Checking device permissions...
--FAIL-- [dev002f] /dev/log has world permissions 
--FAIL-- [dev002f] /dev/nvidia0 has world permissions 
--FAIL-- [dev002f] /dev/nvidiactl has world permissions 
--WARN-- [dev003w] File /dev/sndstat is a regular file in a device directory. 

# Checking for existence of log files...
--FAIL-- [logf005f] Log file /var/log/btmp permission should be 660 

# Checking for correct umask settings...

# Checking listening processes 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 34124 
         (UDP on every interface) is run by avahi. 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP 
         on every interface) is run by avahi. 
--WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on 
         every interface) is run by dhcp. 
--WARN-- [lin002i] The process `nmbd' is listening on socket 137 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `nmbd' is listening on socket 138 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 1 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 1080 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 11 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 111 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 119 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 12345 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 12346 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 143 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 15 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 1524 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 2000 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 20034 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 27665 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 31337 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32771 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32772 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32773 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32774 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 40421 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 49724 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 540 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 54320 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 5742 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 635 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 6667 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 79 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 1 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 161 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 162 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 31335 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 31337 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32770 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32771 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32772 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32773 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 32774 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 34555 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 37444 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 513 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 54321 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 635 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 640 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 641 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 69 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 7 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 700 (UDP) 
         on every interface. 
--WARN-- [lin002i] The process `portsentry' is listening on socket 9 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `smbd' is listening on socket 139 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `smbd' is listening on socket 445 (TCP) on 
         every interface. 

# Checking sshd_config configuration files...
--FAIL-- [ssh005w] Cannot find a configuration file for SSH. 

# Performing common access checks for root...
--FAIL-- [netw020f] There is no /etc/ftpusers file. 

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...
--ALERT-- [fsys006a] Unexpected device files found: 
lrwxrwxrwx 1 leo leo 9 Jun 13 18:44 /home/leo/.wine/dosdevices/e:: -> /dev/scd0
crw------- 1 root root 5, 1 Apr 22 14:04 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Apr 22 14:04 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Apr 22 14:04 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Apr 22 14:04 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Apr 22 14:04 /lib/udev/devices/null
crw------- 1 root root 108, 0 Apr 22 14:04 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 May 21 04:14 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...
--WARN-- [xxxxx] The following files have undefined groups ownership:
/boot/grub
/boot/grub/default
/boot/grub/device.map
/boot/grub/e2fs_stage1_5
/boot/grub/fat_stage1_5
/boot/grub/installed-version
/boot/grub/jfs_stage1_5
/boot/grub/minix_stage1_5
/boot/grub/reiserfs_stage1_5
/boot/grub/stage1
/boot/grub/stage2
/boot/grub/xfs_stage1_5
/cdrom
/etc/apt/apt.conf.d/00trustcdrom
/etc/apt/sources.list
/etc/default/console-setup
/etc/default/locale
/etc/hosts
/etc/initramfs-tools/conf.d/resume
/etc/papersize
/etc/popularity-contest.conf
/home/leo/.wine/dosdevices/e:
/media/cdrom
/media/cdrom0
/var/cache/debconf/passwords.dat
/var/lib/apt/cdroms.list
/var/lib/locales/supported.d/local
/var/log/installer
/var/log/installer/initial-status.gz
/var/log/installer/partman


# Performing check of embedded pathnames...
12:22> Security report completed for leo-laptop.
```

---

### Post by unoodles on 2008-07-30
Do you have nepenthes installed?
run the command: `netstat -tupl` to see which programs are accessing which ports.

---

### Post by LeoSolaris on 2008-07-30
I don't yet, but I am about to. I'll run it as soon as I get it downloaded.

Thanks

---

### Post by LeoSolaris on 2008-07-30
Alright, I picked up nepenthes and ran the requested command, here's the output:

```

12:44 PM on Wed Jul 30 leo-laptop: ~$ sudo netstat -tupl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:1025                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:imaps                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:tcpmux                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:20034                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:pop3s                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:32771                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:3140                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:32772                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:40421                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:32773                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:32774                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:loc-srv               *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:5000                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:31337                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:nameserver            *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ircd                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:systat                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      7188/smbd       
tcp        0      0 *:3372                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:pop3                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:5742                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:imap2                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:sunrpc                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:finger                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:netstat               *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:www                   *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:webmin                *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:54320                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:sieve                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:6129                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ssmtp                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:27665                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:5554                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:27347                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:17300                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ingreslock            *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:ftp                   *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:3127                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:2103                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:nntp                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 localhost:ipp           *:*                     LISTEN      6810/cupsd      
tcp        0      0 *:socks                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:eklogin               *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:2745                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:12345                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 localhost:smtp          *:*                     LISTEN      7078/exim4      
tcp        0      0 *:12346                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:2107                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:https                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:635                   *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:imap3                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:49724                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:uucp                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      7188/smbd       
tcp        0      0 *:1023                  *:*                     LISTEN      9238/nepenthes  
udp        0      0 *:640                   *:*                                 8193/portsentry 
udp        0      0 *:641                   *:*                                 8193/portsentry 
udp        0      0 *:who                   *:*                                 8193/portsentry 
udp        0      0 *:1                     *:*                                 8193/portsentry 
udp        0      0 *:32770                 *:*                                 8193/portsentry 
udp        0      0 *:32771                 *:*                                 8193/portsentry 
udp        0      0 *:32772                 *:*                                 8193/portsentry 
udp        0      0 *:32773                 *:*                                 8193/portsentry 
udp        0      0 *:32774                 *:*                                 8193/portsentry 
udp        0      0 *:echo                  *:*                                 8193/portsentry 
udp        0      0 leo-laptop.l:netbios-ns *:*                                 7172/nmbd       
udp        0      0 *:discard               *:*                                 8193/portsentry 
udp        0      0 *:netbios-ns            *:*                                 7172/nmbd       
udp        0      0 leo-laptop.:netbios-dgm *:*                                 7172/nmbd       
udp        0      0 *:netbios-dgm           *:*                                 7172/nmbd       
udp        0      0 *:ms-sql-m              *:*                                 9238/nepenthes  
udp        0      0 *:snmp                  *:*                                 8193/portsentry 
udp        0      0 *:snmp-trap             *:*                                 8193/portsentry 
udp        0      0 *:54321                 *:*                                 8193/portsentry 
udp        0      0 *:700                   *:*                                 8193/portsentry 
udp        0      0 *:bootpc                *:*                                 8571/dhclient   
udp        0      0 *:37444                 *:*                                 8193/portsentry 
udp        0      0 *:tftp                  *:*                                 8193/portsentry 
udp        0      0 *:34124                 *:*                                 6769/avahi-daemon: 
udp        0      0 *:31335                 *:*                                 8193/portsentry 
udp        0      0 *:31337                 *:*                                 8193/portsentry 
udp        0      0 *:mdns                  *:*                                 6769/avahi-daemon: 
udp        0      0 *:34555                 *:*                                 8193/portsentry 
udp        0      0 *:635                   *:*                                 8193/portsentry 

```

---

### Post by LeoSolaris on 2008-07-30
After studying the help and manpages for nepenthes, I ran a secondary scan for some more information with the command netstat -vap

Here is the result:
```

12:52 PM on Wed Jul 30 leo-laptop: ~$ sudo netstat -vap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:1025                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:imaps                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:tcpmux                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:20034                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:pop3s                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:32771                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:3140                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:32772                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:40421                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:32773                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:32774                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:loc-srv               *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:5000                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:31337                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:nameserver            *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ircd                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:systat                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      7188/smbd       
tcp        0      0 *:3372                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:pop3                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:5742                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:imap2                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:sunrpc                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:finger                *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:netstat               *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:www                   *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:webmin                *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:54320                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:sieve                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:6129                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ssmtp                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:27665                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:5554                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:27347                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:17300                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:ingreslock            *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:ftp                   *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:3127                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:2103                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:nntp                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 localhost:ipp           *:*                     LISTEN      6810/cupsd      
tcp        0      0 *:socks                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:eklogin               *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:2745                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:12345                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 localhost:smtp          *:*                     LISTEN      7078/exim4      
tcp        0      0 *:12346                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:2107                  *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:https                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:635                   *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:imap3                 *:*                     LISTEN      9238/nepenthes  
tcp        0      0 *:49724                 *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:uucp                  *:*                     LISTEN      8185/portsentry 
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      7188/smbd       
tcp        0      0 *:1023                  *:*                     LISTEN      9238/nepenthes  
udp        0      0 *:640                   *:*                                 8193/portsentry 
udp        0      0 *:641                   *:*                                 8193/portsentry 
udp        0      0 *:who                   *:*                                 8193/portsentry 
udp        0      0 *:1                     *:*                                 8193/portsentry 
udp        0      0 *:32770                 *:*                                 8193/portsentry 
udp        0      0 *:32771                 *:*                                 8193/portsentry 
udp        0      0 *:32772                 *:*                                 8193/portsentry 
udp        0      0 *:32773                 *:*                                 8193/portsentry 
udp        0      0 *:32774                 *:*                                 8193/portsentry 
udp        0      0 *:echo                  *:*                                 8193/portsentry 
udp        0      0 leo-laptop.l:netbios-ns *:*                                 7172/nmbd       
udp        0      0 *:discard               *:*                                 8193/portsentry 
udp        0      0 *:netbios-ns            *:*                                 7172/nmbd       
udp        0      0 leo-laptop.:netbios-dgm *:*                                 7172/nmbd       
udp        0      0 *:netbios-dgm           *:*                                 7172/nmbd       
udp        0      0 *:ms-sql-m              *:*                                 9238/nepenthes  
udp        0      0 *:snmp                  *:*                                 8193/portsentry 
udp        0      0 *:snmp-trap             *:*                                 8193/portsentry 
udp        0      0 *:54321                 *:*                                 8193/portsentry 
udp        0      0 *:700                   *:*                                 8193/portsentry 
udp        0      0 *:bootpc                *:*                                 8571/dhclient   
udp        0      0 *:37444                 *:*                                 8193/portsentry 
udp        0      0 *:tftp                  *:*                                 8193/portsentry 
udp        0      0 *:34124                 *:*                                 6769/avahi-daemon: 
udp        0      0 *:31335                 *:*                                 8193/portsentry 
udp        0      0 *:31337                 *:*                                 8193/portsentry 
udp        0      0 *:mdns                  *:*                                 6769/avahi-daemon: 
udp        0      0 *:34555                 *:*                                 8193/portsentry 
udp        0      0 *:635                   *:*                                 8193/portsentry 
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     16663    6769/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17700    7423/winbindd       /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     17898    7447/xfstt          /tmp/.font-unix/fs7101
unix  2      [ ACC ]     STREAM     LISTENING     17702    7423/winbindd       /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     18921    7794/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     19928    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  2      [ ACC ]     STREAM     LISTENING     19938    8301/gnome-keyring- /tmp/orbit-leo/linc-2066-0-1556d84778eb
unix  2      [ ACC ]     STREAM     LISTENING     20111    8301/gnome-keyring- /tmp/keyring-XRaIfV/socket
unix  2      [ ACC ]     STREAM     LISTENING     20113    8301/gnome-keyring- /tmp/keyring-XRaIfV/ssh
unix  2      [ ACC ]     STREAM     LISTENING     20115    8301/gnome-keyring- /tmp/keyring-XRaIfV/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     20276    8356/seahorse-agent /tmp/orbit-leo/linc-206e-0-2b722f10c6519
unix  2      [ ACC ]     STREAM     LISTENING     20307    8302/gnome-session  /tmp/seahorse-zSHsPz/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     20347    8302/gnome-session  /tmp/orbit-leo/linc-206e-0-5b07c71e4fb6b
unix  2      [ ]         DGRAM                    6985     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     20351    8302/gnome-session  /tmp/.ICE-unix/8302
unix  2      [ ACC ]     STREAM     LISTENING     20408    8361/gnome-settings /tmp/orbit-leo/linc-20a9-0-597d09c6d1cf2
unix  2      [ ACC ]     STREAM     LISTENING     23782    8365/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     23789    8365/pulseaudio     /tmp/pulse-leo/native
unix  2      [ ACC ]     STREAM     LISTENING     23830    8372/gconf-helper   /tmp/orbit-leo/linc-20b4-0-5c52a53720cdf
unix  2      [ ACC ]     STREAM     LISTENING     23951    8393/gnome-screensa /tmp/orbit-leo/linc-20bc-0-106e8f325a1fc
unix  2      [ ACC ]     STREAM     LISTENING     18753    7777/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     24158    8398/gnome-panel    /tmp/orbit-leo/linc-20ce-0-13e218f4c9b02
unix  2      [ ACC ]     STREAM     LISTENING     24164    8395/nautilus       /tmp/orbit-leo/linc-20cb-0-13e218f4ca7db
unix  2      [ ACC ]     STREAM     LISTENING     24363    8413/bonobo-activat /tmp/orbit-leo/linc-20dd-0-103ceb0ee6319
unix  2      [ ACC ]     STREAM     LISTENING     24564    8465/gnome-volume-m /tmp/orbit-leo/linc-210e-0-7084c56060d47
unix  2      [ ACC ]     STREAM     LISTENING     24695    8456/compiz.real    /tmp/orbit-leo/linc-2108-0-205dba599959e
unix  2      [ ACC ]     STREAM     LISTENING     24699    8457/update-notifie /tmp/orbit-leo/linc-2109-0-1e834b49969a
unix  2      [ ACC ]     STREAM     LISTENING     24701    8470/gnome-power-ma /tmp/orbit-leo/linc-210a-0-7084c56099790
unix  2      [ ACC ]     STREAM     LISTENING     24722    8460/avant-window-n /tmp/orbit-leo/linc-210c-0-35aeadc4d7fdd
unix  2      [ ACC ]     STREAM     LISTENING     24747    8464/nm-applet      /tmp/orbit-leo/linc-2110-0-2807e8dc2fe23
unix  2      [ ACC ]     STREAM     LISTENING     16204    6455/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     24948    8480/drivemount_app /tmp/orbit-leo/linc-2120-0-1bc42400e470
unix  2      [ ACC ]     STREAM     LISTENING     16718    6810/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     25085    8503/gnome-vfs-daem /tmp/orbit-leo/linc-2137-0-2a62829e321c7
unix  2      [ ACC ]     STREAM     LISTENING     25366    8495/python         /tmp/orbit-leo/linc-212f-0-1f1c297131c79
unix  2      [ ACC ]     STREAM     LISTENING     25390    8580/gtk-window-dec /tmp/orbit-leo/linc-2184-0-63807166428dc
unix  2      [ ACC ]     STREAM     LISTENING     25404    8491/python         /tmp/orbit-leo/linc-212b-0-67b0eba276040
unix  2      [ ACC ]     STREAM     LISTENING     25609    8493/python         /tmp/orbit-leo/linc-212d-0-e88917a89a50
unix  2      [ ACC ]     STREAM     LISTENING     75214    2710/firefox        /tmp/orbit-leo/linc-a96-0-67453211bf43b
unix  2      [ ACC ]     STREAM     LISTENING     20365    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  2      [ ACC ]     STREAM     LISTENING     76494    2951/gnome-terminal /tmp/orbit-leo/linc-b87-0-7d8f567c7b045
unix  3      [ ]         DGRAM                    25179    8501/wpa_supplicant /var/run/wpa_supplicant0/wlan0
unix  2      [ ]         DGRAM                    25181    6710/NetworkManager /var/run/NetworkManager/wpa_ctrl_6710-2
unix  2      [ ]         DGRAM                    8528     3785/udevd          @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     123177   29446/dbus-daemon   @/tmp/dbus-0gCB9I7gsF
unix  2      [ ]         DGRAM                    17913    7541/hald           @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     17874    7541/hald           @/var/run/hald/dbus-bNTXvFTg9J
unix  2      [ ACC ]     STREAM     LISTENING     17047    7142/powertweakd    /var/run/powertweakd
unix  2      [ ACC ]     STREAM     LISTENING     16537    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     122441   29445/dbus-launch   /tmp/gedit-svn.root.123364257
unix  2      [ ACC ]     STREAM     LISTENING     17829    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  2      [ ]         DGRAM                    25028    8501/wpa_supplicant /var/run/wpa_supplicant-global
unix  8      [ ]         DGRAM                    16368    6579/syslogd        /dev/log
unix  3      [ ]         STREAM     CONNECTED     128796   7423/winbindd       
unix  3      [ ]         STREAM     CONNECTED     128795   30507/winbindd      
unix  3      [ ]         STREAM     CONNECTED     128793   7423/winbindd       
unix  3      [ ]         STREAM     CONNECTED     128792   30506/winbindd      
unix  2      [ ]         STREAM     CONNECTED     128791   30506/winbindd      /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     123183   7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     123182   29445/dbus-launch   
unix  3      [ ]         STREAM     CONNECTED     123179   29446/dbus-daemon   
unix  3      [ ]         STREAM     CONNECTED     123178   29446/dbus-daemon   
unix  3      [ ]         STREAM     CONNECTED     123165   7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     123164   29445/dbus-launch   
unix  3      [ ]         STREAM     CONNECTED     76517    2955/gnome-pty-help 
unix  3      [ ]         STREAM     CONNECTED     76516    2951/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     76501    2951/gnome-terminal /tmp/orbit-leo/linc-b87-0-7d8f567c7b045
unix  3      [ ]         STREAM     CONNECTED     76500    8413/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     76499    8413/bonobo-activat /tmp/orbit-leo/linc-20dd-0-103ceb0ee6319
unix  3      [ ]         STREAM     CONNECTED     76498    2951/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     76497    2951/gnome-terminal /tmp/orbit-leo/linc-b87-0-7d8f567c7b045
unix  3      [ ]         STREAM     CONNECTED     76496    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     76493    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     76492    2951/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     76490    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     76489    2951/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     76485    7794/X              /tmp/.X11-unix/X0
unix  8      [ ]         STREAM     CONNECTED     76484    2951/gnome-terminal 
unix  3      [ ]         STREAM     CONNECTED     75225    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     75224    2710/firefox        
unix  3      [ ]         STREAM     CONNECTED     75217    2710/firefox        /tmp/orbit-leo/linc-a96-0-67453211bf43b
unix  3      [ ]         STREAM     CONNECTED     75216    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     75213    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     75212    2710/firefox        
unix  3      [ ]         STREAM     CONNECTED     75210    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     75209    2710/firefox        
unix  3      [ ]         STREAM     CONNECTED     75203    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     75202    2710/firefox        
unix  3      [ ]         STREAM     CONNECTED     25803    7794/X              /tmp/.X11-unix/X0
unix  4      [ ]         STREAM     CONNECTED     25802    8649/conky          
unix  2      [ ]         STREAM     CONNECTED     25751    8301/gnome-keyring- /tmp/keyring-XRaIfV/socket
unix  3      [ ]         STREAM     CONNECTED     25614    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25613    8493/python         
unix  3      [ ]         STREAM     CONNECTED     25612    8493/python         /tmp/orbit-leo/linc-212d-0-e88917a89a50
unix  3      [ ]         STREAM     CONNECTED     25611    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     25608    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     25607    8493/python         
unix  3      [ ]         STREAM     CONNECTED     25467    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25466    8495/python         
unix  3      [ ]         STREAM     CONNECTED     25431    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25430    8456/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     25410    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25409    8491/python         
unix  3      [ ]         STREAM     CONNECTED     25407    8491/python         /tmp/orbit-leo/linc-212b-0-67b0eba276040
unix  3      [ ]         STREAM     CONNECTED     25406    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     25403    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     25402    8491/python         
unix  3      [ ]         STREAM     CONNECTED     25393    8580/gtk-window-dec /tmp/orbit-leo/linc-2184-0-63807166428dc
unix  3      [ ]         STREAM     CONNECTED     25392    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     25389    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     25388    8580/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     25384    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25383    8580/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     25369    8495/python         /tmp/orbit-leo/linc-212f-0-1f1c297131c79
unix  3      [ ]         STREAM     CONNECTED     25368    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     25365    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     25364    8495/python         
unix  2      [ ]         DGRAM                    25348    8571/dhclient       
unix  3      [ ]         STREAM     CONNECTED     25267    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25266    8493/python         
unix  3      [ ]         STREAM     CONNECTED     25262    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25261    8493/python         
unix  3      [ ]         STREAM     CONNECTED     25258    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25257    8491/python         
unix  3      [ ]         STREAM     CONNECTED     25252    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25251    8495/python         
unix  3      [ ]         STREAM     CONNECTED     25222    8518/gvfsd-trash    @/dbus-vfs-daemon/socket-vfNwdPHJ
unix  3      [ ]         STREAM     CONNECTED     25221    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25223    8518/gvfsd-trash    @/dbus-vfs-daemon/socket-t7pk8U19
unix  3      [ ]         STREAM     CONNECTED     25220    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25147    8518/gvfsd-trash    @/dbus-vfs-daemon/socket-ncWGgje6
unix  3      [ ]         STREAM     CONNECTED     25146    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25148    8518/gvfsd-trash    @/dbus-vfs-daemon/socket-8zEo8DjB
unix  3      [ ]         STREAM     CONNECTED     25145    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25123    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25122    8518/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     25117    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25116    8518/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     25090    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     25089    8503/gnome-vfs-daem 
unix  3      [ ]         STREAM     CONNECTED     25088    8503/gnome-vfs-daem /tmp/orbit-leo/linc-2137-0-2a62829e321c7
unix  3      [ ]         STREAM     CONNECTED     25087    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     25077    8509/gvfsd-burn     @/dbus-vfs-daemon/socket-MUFxWlzM
unix  3      [ ]         STREAM     CONNECTED     25076    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25075    8509/gvfsd-burn     @/dbus-vfs-daemon/socket-reKaKzVg
unix  3      [ ]         STREAM     CONNECTED     25074    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25067    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25066    8509/gvfsd-burn     
unix  3      [ ]         STREAM     CONNECTED     25045    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25044    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     25080    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     25039    8503/gnome-vfs-daem 
unix  3      [ ]         STREAM     CONNECTED     25036    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25035    8503/gnome-vfs-daem 
unix  3      [ ]         STREAM     CONNECTED     25014    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     25013    8480/drivemount_app 
unix  3      [ ]         STREAM     CONNECTED     25015    8398/gnome-panel    /tmp/orbit-leo/linc-20ce-0-13e218f4c9b02
unix  3      [ ]         STREAM     CONNECTED     25012    8480/drivemount_app 
unix  3      [ ]         STREAM     CONNECTED     25011    8480/drivemount_app /tmp/orbit-leo/linc-2120-0-1bc42400e470
unix  3      [ ]         STREAM     CONNECTED     25010    8398/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     24957    8480/drivemount_app /tmp/orbit-leo/linc-2120-0-1bc42400e470
unix  3      [ ]         STREAM     CONNECTED     24956    8413/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     24955    8413/bonobo-activat /tmp/orbit-leo/linc-20dd-0-103ceb0ee6319
unix  3      [ ]         STREAM     CONNECTED     24952    8480/drivemount_app 
unix  3      [ ]         STREAM     CONNECTED     24951    8480/drivemount_app /tmp/orbit-leo/linc-2120-0-1bc42400e470
unix  3      [ ]         STREAM     CONNECTED     24950    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24945    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24944    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24946    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24901    8480/drivemount_app 
unix  3      [ ]         STREAM     CONNECTED     24897    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24896    8480/drivemount_app 
unix  3      [ ]         STREAM     CONNECTED     24840    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24839    8460/avant-window-n 
unix  3      [ ]         STREAM     CONNECTED     24777    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24776    8464/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     24753    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24752    8460/avant-window-n 
unix  3      [ ]         STREAM     CONNECTED     24750    8464/nm-applet      /tmp/orbit-leo/linc-2110-0-2807e8dc2fe23
unix  3      [ ]         STREAM     CONNECTED     24749    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24742    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24741    8365/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     24746    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24740    8464/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     24734    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24733    8457/update-notifie 
unix  3      [ ]         STREAM     CONNECTED     24732    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24731    8470/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     24730    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24729    8470/gnome-power-ma 
unix  2      [ ]         DGRAM                    24725    8470/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     24728    8460/avant-window-n /tmp/orbit-leo/linc-210c-0-35aeadc4d7fdd
unix  3      [ ]         STREAM     CONNECTED     24724    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24721    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24720    8457/update-notifie 
unix  3      [ ]         STREAM     CONNECTED     24718    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24717    8460/avant-window-n 
unix  3      [ ]         STREAM     CONNECTED     24713    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24712    8460/avant-window-n 
unix  3      [ ]         STREAM     CONNECTED     24708    8470/gnome-power-ma /tmp/orbit-leo/linc-210a-0-7084c56099790
unix  3      [ ]         STREAM     CONNECTED     24705    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24707    8457/update-notifie /tmp/orbit-leo/linc-2109-0-1e834b49969a
unix  3      [ ]         STREAM     CONNECTED     24704    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24706    8456/compiz.real    /tmp/orbit-leo/linc-2108-0-205dba599959e
unix  3      [ ]         STREAM     CONNECTED     24703    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24698    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24696    8465/gnome-volume-m 
unix  3      [ ]         STREAM     CONNECTED     24693    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24690    8470/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     24692    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24689    8457/update-notifie 
unix  3      [ ]         STREAM     CONNECTED     24691    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24624    8456/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     24609    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24608    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24607    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24606    8464/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     24569    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     24568    8465/gnome-volume-m 
unix  3      [ ]         STREAM     CONNECTED     24567    8465/gnome-volume-m /tmp/orbit-leo/linc-210e-0-7084c56060d47
unix  3      [ ]         STREAM     CONNECTED     24566    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24563    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24562    8465/gnome-volume-m 
unix  3      [ ]         STREAM     CONNECTED     24525    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24524    8465/gnome-volume-m 
unix  3      [ ]         STREAM     CONNECTED     24457    8395/nautilus       /tmp/orbit-leo/linc-20cb-0-13e218f4ca7db
unix  3      [ ]         STREAM     CONNECTED     24456    8413/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     24455    8398/gnome-panel    /tmp/orbit-leo/linc-20ce-0-13e218f4c9b02
unix  3      [ ]         STREAM     CONNECTED     24454    8413/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     24453    8413/bonobo-activat /tmp/orbit-leo/linc-20dd-0-103ceb0ee6319
unix  3      [ ]         STREAM     CONNECTED     24451    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24452    8413/bonobo-activat /tmp/orbit-leo/linc-20dd-0-103ceb0ee6319
unix  3      [ ]         STREAM     CONNECTED     24450    8398/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     24688    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24449    8470/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     24445    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24444    8470/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     24687    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24373    8457/update-notifie 
unix  3      [ ]         STREAM     CONNECTED     24369    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24368    8457/update-notifie 
unix  3      [ ]         STREAM     CONNECTED     24300    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24299    8456/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     24297    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24296    8456/compiz.real    
unix  3      [ ]         STREAM     CONNECTED     24220    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24219    8421/gvfsd          
unix  3      [ ]         STREAM     CONNECTED     24210    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     24209    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24167    8395/nautilus       /tmp/orbit-leo/linc-20cb-0-13e218f4ca7db
unix  3      [ ]         STREAM     CONNECTED     24166    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24163    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24162    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24161    8398/gnome-panel    /tmp/orbit-leo/linc-20ce-0-13e218f4c9b02
unix  3      [ ]         STREAM     CONNECTED     24160    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     24156    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     24155    8398/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     24157    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24154    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24153    8302/gnome-session  /tmp/.ICE-unix/8302
unix  3      [ ]         STREAM     CONNECTED     24152    8398/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     24145    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24144    8398/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     24141    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24140    8395/nautilus       
unix  3      [ ]         STREAM     CONNECTED     24132    8365/pulseaudio     /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     24131    8302/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     23958    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23957    8393/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     23956    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     23955    8393/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     23954    8393/gnome-screensa /tmp/orbit-leo/linc-20bc-0-106e8f325a1fc
unix  3      [ ]         STREAM     CONNECTED     23953    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     23950    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     23949    8393/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     23945    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23944    8393/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     23835    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23834    8365/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     23833    8372/gconf-helper   /tmp/orbit-leo/linc-20b4-0-5c52a53720cdf
unix  3      [ ]         STREAM     CONNECTED     23832    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     23829    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     23828    8372/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     23839    8365/pulseaudio     /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23787    8361/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     22241    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22240    8365/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     21363    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21362    8356/seahorse-agent 
unix  3      [ ]         STREAM     CONNECTED     20411    8361/gnome-settings /tmp/orbit-leo/linc-20a9-0-597d09c6d1cf2
unix  3      [ ]         STREAM     CONNECTED     20410    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     20407    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     20406    8361/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     20402    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     20401    8361/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     20400    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20399    8361/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     20369    8360/dbus-daemon    @/tmp/dbus-HLGO7BzZAr
unix  3      [ ]         STREAM     CONNECTED     20368    8302/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     20367    8360/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     20366    8360/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     20350    8302/gnome-session  /tmp/orbit-leo/linc-206e-0-5b07c71e4fb6b
unix  3      [ ]         STREAM     CONNECTED     20349    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     20346    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     20345    8302/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     20314    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20313    8302/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     20279    8356/seahorse-agent /tmp/orbit-leo/linc-206e-0-2b722f10c6519
unix  3      [ ]         STREAM     CONNECTED     20278    8296/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     20275    8296/gconfd-2       /tmp/orbit-leo/linc-2068-0-6c4c11c161e29
unix  3      [ ]         STREAM     CONNECTED     20274    8356/seahorse-agent 
unix  3      [ ]         STREAM     CONNECTED     20270    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20269    8356/seahorse-agent 
unix  3      [ ]         STREAM     CONNECTED     20128    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20127    7783/gdm            
unix  3      [ ]         STREAM     CONNECTED     20119    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20118    8301/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     19768    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19767    7794/X              
unix  3      [ ]         STREAM     CONNECTED     19277    6455/acpid          /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     19276    7794/X              
unix  3      [ ]         STREAM     CONNECTED     18965    6455/acpid          /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18964    7794/X              
unix  4      [ ]         STREAM     CONNECTED     19769    7794/X              /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18925    7783/gdm            
unix  3      [ ]         STREAM     CONNECTED     18619    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  3      [ ]         STREAM     CONNECTED     18618    7727/scd0 (every 2  
unix  3      [ ]         STREAM     CONNECTED     18617    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18616    7727/scd0 (every 2  
unix  3      [ ]         STREAM     CONNECTED     18242    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18241    7673/hald-addon-cpu 
unix  3      [ ]         STREAM     CONNECTED     18229    6455/acpid          /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18228    7674/acpid.socket   
unix  3      [ ]         STREAM     CONNECTED     18223    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  3      [ ]         STREAM     CONNECTED     18221    7674/acpid.socket   
unix  3      [ ]         STREAM     CONNECTED     18222    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  3      [ ]         STREAM     CONNECTED     18220    7673/hald-addon-cpu 
unix  3      [ ]         STREAM     CONNECTED     18097    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  3      [ ]         STREAM     CONNECTED     18082    7656/event5         
unix  3      [ ]         STREAM     CONNECTED     18096    7541/hald           @/var/run/hald/dbus-cF2jvw99X9
unix  3      [ ]         STREAM     CONNECTED     18080    7655/hald-addon-del 
unix  3      [ ]         STREAM     CONNECTED     17893    7541/hald           @/var/run/hald/dbus-bNTXvFTg9J
unix  3      [ ]         STREAM     CONNECTED     17892    7557/hald-runner    
unix  3      [ ]         STREAM     CONNECTED     17873    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17872    7556/console-kit-da 
unix  3      [ ]         STREAM     CONNECTED     17831    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17830    7541/hald           
unix  3      [ ]         STREAM     CONNECTED     17777    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17776    7510/dhcdbd         
unix  2      [ ]         DGRAM                    17775    7510/dhcdbd         
unix  3      [ ]         STREAM     CONNECTED     17705    7423/winbindd       
unix  3      [ ]         STREAM     CONNECTED     17704    7437/winbindd       
unix  3      [ ]         STREAM     CONNECTED     16666    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16665    6769/avahi-daemon:  
unix  3      [ ]         STREAM     CONNECTED     16660    6770/avahi-daemon:  
unix  3      [ ]         STREAM     CONNECTED     16659    6769/avahi-daemon:  
unix  2      [ ]         DGRAM                    16657    6769/avahi-daemon:  
unix  3      [ ]         STREAM     CONNECTED     16601    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16600    6737/system-tools-b 
unix  3      [ ]         STREAM     CONNECTED     16592    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16591    6724/NetworkManager 
unix  3      [ ]         STREAM     CONNECTED     16562    6694/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16561    6710/NetworkManager 
unix  2      [ ]         DGRAM                    16557    6710/NetworkManager 
unix  3      [ ]         STREAM     CONNECTED     16540    6694/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     16539    6694/dbus-daemon    
unix  2      [ ]         DGRAM                    16462    6648/klogd          
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.

```

---

### Post by unoodles on 2008-07-30
Actually the reason I asked if you had nepenthes was that it will emulate rootkits and vulnerabilities to pick up malware. I used to think i was infected by bindshell, but it turned out that it was only nepenthes. It could be portsentry.

---

### Post by LeoSolaris on 2008-07-30
ahhh...    I see.

Well then, I'll remove nepenthes...

---

### Post by Sydero on 2008-07-30
You don't have two rootkits, just one.  wlan is normal.  And even then you probably don't have any.

PortSentry is listed is known to give false positives, as listed in the README.

> the sniffer check is just an informational check, it doesn't necessarily
mean that you've been rooted.  there are several legitimate sniffers out
there; however, you may still want to check that the sniffer is the one
that you think it is, etc.

In general, any process starting at around same time as lkm test may
trigger a warning. Just try while true;do chkrootkit lkm;sleep 1;done
during normal system use. See also FAQ 6 on [www.chkrootkit.org](www.chkrootkit.org) -- paolo

chroot environments may cause "suspicious file" false positives.

bindshell listens on a lot of ports.  these ports are also used by other
legitimate programs.  chkrootkit's detection algorithm cannot determine
the difference between a legitimate program and bindshell.

below is a (non-exhaustive) list of packages that are known to cause false
positives.  before filing a bug report, please check this list.

listens on well known ports
  *radius: the Slapper worm listens on 1812
  bitlbee: LDP worms listen on port 6667
  cfs: bindshell listens on port 3049
  erlang-base: bindshell listens on port 4369
  exim-tls: bindshell listens on port 465
  mldonkey-server: bindshell listens on port 4000
  portsentry: listens on several ports that chkrootkit sees as rootkit ports
  postfix-tls: bindshell listens on port 465
  reaim: bindshell listens on port 5190

legitimate sniffers
  dhcpd
  ethereal
  knockd
  p0f
  pppoe
  tcpdump

hidden files [http://www.chkrootkit.org/faq/#8](http://www.chkrootkit.org/faq/#8)
  perl packages sometimes have .packlist files
  blackdown java
  blender
  geomview
  gnustep-make
  kaffe
  obliq
  mindi
  r-cran-hmisc
  realplay
  scilab
  smlnj
  subversion
  tiger
  twiki
  viewglob

contains specific files
  asp: Ramen Worms contain the file /usr/bin/asp
  libgcj-common: the 'OBSD rk v1' contains 
    /usr/lib/security, 
    /usr/lib/security/classpath.security 
    /usr/lib/security/libgcj.security. 
  libproc-dev: t0rn v8 contains a libproc.a
  run: ZK rootkits contain /usr/bin/run
  slice: RH-Sharpe contains /usr/bin/slice


---

### Post by LeoSolaris on 2008-07-30
Thank ya!

The second, other than the bindshell was this one:

Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security

I looked at that, and it did not "seem" to be threatening. At least the comments and the names of the commands. 

I should have known to check the known false positives lists that was likely to be on chkrootkit's homepage.

Leo

---

### Post by pedja_portugalac on 2008-07-31
I also found this:
> eth0: PACKET SNIFFER(/sbin/dhclient3[5648])
Investigating around I found that's DHCP client for linux. What is DHCP? DHCP is the protocol computers use to request and receive a "dynamic" IP address.
As my internet provider use DHCP on cable modem to allocate me one IP address and I have allowed that service on my firewall, I presume that's normal, or maybe not. If you guys know something about it please post it here. 

**DHCP is the protocol computers use to request and receive a "dynamic" IP address.** by Leo Notenboom

What is DHCP?

DHCP stands for "Dynamic Host Configuration Protocol".

So I can hear you thinking, "great ... what's that?"

In a nutshell, it's the request your computer makes and the response it receives that assigns it a "dynamic" IP address.

Let's look at that a little more closely.

•

First, a refresher. Every computer on the internet has an "address". That address is just a number, but it uniquely identifies that computer; no other computer on the internet can have the same address.

There are two types of IP addresses: static and dynamic. Static IP addresses are just that - unchanging. They refer to a particular computer, whether that computer is turned on or not, connected or not. Most typically domain names like "ask-leo.com" map to a single static IP address.

Dynamic IP addresses are assigned to a computer on-the-fly. The most common scenario is dial-up. When you dial-up to your ISP, part of the connection sequence is your computer asking for an IP address, and your ISP assigning it one of the addresses it has available. When you disconnect, that IP address is returned to the list of available addresses and may be reused by another computer when it dials in.

Because most home users tend to turn their computers off, even broadband connections such as DSL and Cable continue to use dynamic addresses. If your computer is off, you don't need an address so someone else might get to use it.

Dynamic addresses are also used by NAT routers. Not necessarily on their internet connection, though it can, but rather on the local area network side. Each computer that you connect to your router will ask for an IP address, and that router will respond with an IP address that's available within your LAN.

The actual DHCP protocol is fairly simple. The computer in need of an IP address broadcasts a request, meaning it sends out a request to anyone who'll listen. That, in essence, says "Hey, anyone? I need an IP address!" By definition on any network (or more correctly, sub-network), there should at most one device who's job it is to answer back "Sure, here ya go, have this one." That's a DHCP server. Along with that answer is additional information as well, such as what machines to ask for domain name (DNS) look-ups and what address to forward all outgoing network traffic, too (the gateway).

In Windows, if your computer doesn't get a response from a DHCP server within a certain amount of time, it will give up or it may fall back to only asking every few minutes. It may "make up" an answer as well. In fact if your IP address begins with "169.", that's probably exactly what's happened; no IP address was assigned, and Windows made one up. And I'll bet your networking and internet don't work.

---

### Post by x3roconf on 2008-08-01
> **unoodles said:**
> Actually the reason I asked if you had nepenthes was that it will emulate rootkits and vulnerabilities to pick up malware. I used to think i was infected by bindshell, but it turned out that it was only nepenthes. It could be portsentry.

Wtf are you talking about? Nepenthes emulates only windows vulnerabilities and it can't emulate any rootkits! :)

---

