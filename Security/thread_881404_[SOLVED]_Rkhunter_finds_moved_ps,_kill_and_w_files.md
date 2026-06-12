---
title: "[SOLVED] Rkhunter finds moved ps, kill and w files, and hidden files in /java, /initr"
date: 2008-08-06
forum: Security
---

### Post by Thorzilla on 2008-08-06
Here is the logfile for rkhunter. Is there a chance my computer is compromised?

Note: I did change my login password recently, would that explain the change in the hash keys?

I've also noticed that after the change in my password, the password that protects the keys to the various wireless networks I connect to is still protected by the old password.

Also, is exim4 a normal process (checkgmail dependency?)? I didn't explicitly install exim, so I'm not sure.

I'm dual booting Ubuntu 8.04 (Primary) and Vista, on an AMD 64 X2, 1.8 GHz, 1 GB Ram, 200GB HDD. Toshiba A200-5. I've got Privoxy, Polipo and Tor. 

> [23:49:20] Running Rootkit Hunter version 1.3.0 on Aar
[23:49:20]
[23:49:20] Info: Start date is Tue Aug  5 23:49:20 EDT 2008
[23:49:20]
[23:49:20] Checking configuration file and command-line options...
[23:49:20] Info: Detected operating system is 'Linux'
[23:49:20] Info: Found O/S name: Ubuntu 8.04.1
[23:49:20] Info: Command line is /usr/bin/rkhunter --check
[23:49:20] Info: Environment shell is /bin/bash; rkhunter is using dash
[23:49:20] Info: Using configuration file '/etc/rkhunter.conf'
[23:49:21] Info: Installation directory is '/usr'
[23:49:21] Info: Using language 'en'
[23:49:21] Info: Using '/var/lib/rkhunter/db' as the database directory
[23:49:21] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[23:49:21] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[23:49:21] Info: Using '/' as the root directory
[23:49:21] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[23:49:21] Info: No mail-on-warning address configured
[23:49:21] Info: X will automatically be detected
[23:49:21] Info: Using second color set
[23:49:21] Info: Found the 'diff' command: /usr/bin/diff
[23:49:21] Info: Found the 'file' command: /usr/bin/file
[23:49:21] Info: Found the 'find' command: /usr/bin/find
[23:49:21] Info: Found the 'ifconfig' command: /sbin/ifconfig
[23:49:21] Info: Found the 'ip' command: /sbin/ip
[23:49:21] Info: Found the 'ldd' command: /usr/bin/ldd
[23:49:21] Info: Found the 'lsattr' command: /usr/bin/lsattr
[23:49:21] Info: Found the 'lsmod' command: /sbin/lsmod
[23:49:21] Info: Found the 'lsof' command: /usr/bin/lsof
[23:49:21] Info: Found the 'mktemp' command: /bin/mktemp
[23:49:21] Info: Found the 'netstat' command: /bin/netstat
[23:49:21] Info: Found the 'perl' command: /usr/bin/perl
[23:49:21] Info: Found the 'ps' command: /bin/ps
[23:49:21] Info: Found the 'pwd' command: /bin/pwd
[23:49:21] Info: Found the 'readlink' command: /bin/readlink
[23:49:21] Info: Found the 'sort' command: /usr/bin/sort
[23:49:21] Info: Found the 'stat' command: /usr/bin/stat
[23:49:21] Info: Found the 'strings' command: /usr/bin/strings
[23:49:21] Info: Found the 'uniq' command: /usr/bin/uniq
[23:49:21] Info: System is not using prelinking
[23:49:21] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[23:49:21] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[23:49:21] Info: Stored hash values did not use a package manager
[23:49:21] Info: The hash function field index is set to 1
[23:49:21] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[23:49:21] Info: Previous file attributes were stored
[23:49:21] Info: Enabled tests are: all
[23:49:21] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[23:49:21] Info: Found ksym file '/proc/kallsyms'
[23:49:21]
[23:49:21] Checking if the O/S has changed since last time...
[23:49:21] Info: Nothing seems to have changed
[23:49:21]
[23:49:21] Starting system checks...
[23:49:21]
[23:49:21] Checking system commands...
[23:49:21] Info: Starting test name 'system_commands'
[23:49:21]
[23:49:21] Performing 'strings' command checks
[23:49:21] Info: Starting test name 'strings'
[23:49:21] Scanning for string /usr/sbin/ntpsx               [ OK ]
[23:49:21] Scanning for string /usr/lib/.../ls               [ OK ]
[23:49:22] Scanning for string /usr/lib/.../netstat          [ OK ]
[23:49:22] Scanning for string /usr/lib/.../lsof             [ OK ]
[23:49:22] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[23:49:22] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[23:49:22] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[23:49:22] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[23:49:22] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[23:49:22] Scanning for string /usr/lib/.../psr              [ OK ]
[23:49:22] Scanning for string /usr/lib/.../find             [ OK ]
[23:49:22] Scanning for string /usr/lib/.../pstree           [ OK ]
[23:49:22] Scanning for string /usr/lib/.../slocate          [ OK ]
[23:49:22] Scanning for string /usr/lib/.../du               [ OK ]
[23:49:22] Scanning for string /usr/lib/.../top              [ OK ]
[23:49:22] Scanning for string /usr/lib/...                  [ OK ]
[23:49:22] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[23:49:22] Scanning for string /usr/lib/.bkit-               [ OK ]
[23:49:22] Scanning for string /tmp/.bkp                     [ OK ]
[23:49:22] Scanning for string /tmp/.cinik                   [ OK ]
[23:49:22] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[23:49:22] Scanning for string /lib/.sso                     [ OK ]
[23:49:22] Scanning for string /lib/.so                      [ OK ]
[23:49:22] Scanning for string /var/run/...dica/clean        [ OK ]
[23:49:22] Scanning for string /var/run/...dica/xl           [ OK ]
[23:49:22] Scanning for string /var/run/...dica/xdr          [ OK ]
[23:49:22] Scanning for string /var/run/...dica/psg          [ OK ]
[23:49:22] Scanning for string /var/run/...dica/secure       [ OK ]
[23:49:22] Scanning for string /var/run/...dica/rdx          [ OK ]
[23:49:22] Scanning for string /var/run/...dica/va           [ OK ]
[23:49:23] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[23:49:23] Scanning for string /usr/bin/.etc                 [ OK ]
[23:49:23] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[23:49:23] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[23:49:23] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[23:49:23] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[23:49:23] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[23:49:23] Scanning for string /bin/sysback                  [ OK ]
[23:49:23] Scanning for string /usr/local/bin/sysback        [ OK ]
[23:49:23] Scanning for string /usr/lib/.tbd                 [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[23:49:23] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[23:49:24] Scanning for string /usr/info/.torn/sh*           [ OK ]
[23:49:24] Scanning for string /usr/src/.****/.1addr         [ OK ]
[23:49:24] Scanning for string /usr/src/.****/.1file         [ OK ]
[23:49:24] Scanning for string /usr/src/.****/.1proc         [ OK ]
[23:49:24] Scanning for string /usr/src/.****/.1logz         [ OK ]
[23:49:24] Scanning for string /usr/info/.t0rn               [ OK ]
[23:49:24] Scanning for string /dev/.lib                     [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib                 [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib             [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[23:49:24] Scanning for string /dev/.lib/lib/scan            [ OK ]
[23:49:24] Scanning for string /usr/src/.****                [ OK ]
[23:49:24] Scanning for string /usr/man/man1/man1            [ OK ]
[23:49:24] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[23:49:24] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[23:49:24] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[23:49:24]
[23:49:24] Performing 'shared libraries' checks
[23:49:24] Info: Starting test name 'shared_libs'
[23:49:25] Checking for preloading variables                 [ None found ]
[23:49:25] Checking for preload file                         [ Not found ]
[23:49:25] Info: Starting test name 'shared_libs_path'
[23:49:25] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[23:49:25]
[23:49:25] Performing file properties checks
[23:49:25] Info: Starting test name 'properties'
[23:49:25] Checking for prerequisites                        [ OK ]
[23:49:25] /bin/bash                                         [ OK ]
[23:49:25] /bin/cat                                          [ OK ]
[23:49:25] /bin/chmod                                        [ OK ]
[23:49:26] /bin/chown                                        [ OK ]
[23:49:26] /bin/cp                                           [ OK ]
[23:49:26] /bin/date                                         [ OK ]
[23:49:26] /bin/df                                           [ OK ]
[23:49:26] /bin/dmesg                                        [ OK ]
[23:49:26] /bin/echo                                         [ OK ]
[23:49:26] /bin/ed                                           [ OK ]
[23:49:26] /bin/egrep                                        [ OK ]
[23:49:26] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[23:49:27] /bin/fgrep                                        [ OK ]
[23:49:27] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[23:49:27] /bin/grep                                         [ OK ]
[23:49:27] /bin/ip                                           [ Warning ]
[23:49:27] Warning: The file properties have changed:
[23:49:27]          File: /bin/ip
[23:49:27]          Current inode: 9756721    Stored inode: 9756719
[23:49:27]          Current file modification time: 1215618519
[23:49:27]          Stored file modification time : 1207985171
[23:49:27] /bin/kill                                         [ Warning ]
[23:49:27] Warning: The file properties have changed:
[23:49:27]          File: /bin/kill
[23:49:27]          Current hash: 5f85ce91eafbd85f79441f71ecad0f0db722c1bf
[23:49:27]          Stored hash : 18e7cde8dfbeac32608ae47f857d2b168cfc72cb
[23:49:27]          Current inode: 9756770    Stored inode: 9756721
[23:49:27]          Current file modification time: 1215682114
[23:49:27]          Stored file modification time : 1205447087
[23:49:27] /bin/login                                        [ OK ]
[23:49:28] /bin/ls                                           [ OK ]
[23:49:28] /bin/lsmod                                        [ OK ]
[23:49:28] /bin/mktemp                                       [ OK ]
[23:49:28] /bin/more                                         [ OK ]
[23:49:28] /bin/mount                                        [ OK ]
[23:49:28] /bin/mv                                           [ OK ]
[23:49:28] /bin/netstat                                      [ OK ]
[23:49:29] /bin/ps                                           [ Warning ]
[23:49:29] Warning: The file properties have changed:
[23:49:29]          File: /bin/ps
[23:49:29]          Current hash: 62c7d1839f644c5dfb6179015e7e3017ac6a6afa
[23:49:29]          Stored hash : 7cbcd8aa6df2ffbfbe783ae7fe7d1ea5a790ed81
[23:49:29]          Current inode: 9756773    Stored inode: 9756757
[23:49:29]          Current file modification time: 1215682114
[23:49:29]          Stored file modification time : 1205447087
[23:49:29] /bin/pwd                                          [ OK ]
[23:49:29] /bin/readlink                                     [ OK ]
[23:49:29] /bin/sed                                          [ OK ]
[23:49:29] /bin/sh                                           [ OK ]
[23:49:30] /bin/su                                           [ OK ]
[23:49:30] /bin/touch                                        [ OK ]
[23:49:30] /bin/uname                                        [ OK ]
[23:49:30] /bin/which                                        [ OK ]
[23:49:30] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[23:49:30] /bin/dash                                         [ OK ]
[23:49:30] /usr/bin/awk                                      [ OK ]
[23:49:31] /usr/bin/basename                                 [ OK ]
[23:49:31] /usr/bin/chattr                                   [ OK ]
[23:49:31] /usr/bin/cut                                      [ OK ]
[23:49:31] /usr/bin/diff                                     [ OK ]
[23:49:31] /usr/bin/dirname                                  [ OK ]
[23:49:31] /usr/bin/dpkg                                     [ OK ]
[23:49:31] /usr/bin/dpkg-query                               [ OK ]
[23:49:31] /usr/bin/du                                       [ OK ]
[23:49:32] /usr/bin/env                                      [ OK ]
[23:49:32] /usr/bin/file                                     [ OK ]
[23:49:32] /usr/bin/find                                     [ OK ]
[23:49:32] /usr/bin/GET                                      [ OK ]
[23:49:32] /usr/bin/groups                                   [ OK ]
[23:49:32] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[23:49:32] /usr/bin/head                                     [ OK ]
[23:49:32] /usr/bin/id                                       [ OK ]
[23:49:33] /usr/bin/killall                                  [ OK ]
[23:49:33] /usr/bin/last                                     [ OK ]
[23:49:33] /usr/bin/lastlog                                  [ OK ]
[23:49:33] /usr/bin/ldd                                      [ OK ]
[23:49:33] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[23:49:33] /usr/bin/less                                     [ OK ]
[23:49:33] /usr/bin/locate                                   [ OK ]
[23:49:33] /usr/bin/logger                                   [ OK ]
[23:49:33] /usr/bin/lsattr                                   [ OK ]
[23:49:34] /usr/bin/lsof                                     [ OK ]
[23:49:34] /usr/bin/md5sum                                   [ OK ]
[23:49:34] /usr/bin/mlocate                                  [ OK ]
[23:49:34] /usr/bin/newgrp                                   [ OK ]
[23:49:34] /usr/bin/passwd                                   [ OK ]
[23:49:35] /usr/bin/perl                                     [ OK ]
[23:49:35] /usr/bin/pstree                                   [ OK ]
[23:49:35] /usr/bin/rkhunter                                 [ OK ]
[23:49:35] /usr/bin/rpm                                      [ OK ]
[23:49:35] /usr/bin/runcon                                   [ OK ]
[23:49:35] /usr/bin/sha1sum                                  [ OK ]
[23:49:35] /usr/bin/size                                     [ OK ]
[23:49:36] /usr/bin/sort                                     [ OK ]
[23:49:36] /usr/bin/stat                                     [ OK ]
[23:49:36] /usr/bin/strace                                   [ OK ]
[23:49:36] /usr/bin/strings                                  [ OK ]
[23:49:36] /usr/bin/sudo                                     [ OK ]
[23:49:36] /usr/bin/tail                                     [ OK ]
[23:49:36] /usr/bin/test                                     [ OK ]
[23:49:36] /usr/bin/top                                      [ Warning ]
[23:49:36] Warning: The file properties have changed:
[23:49:36]          File: /usr/bin/top
[23:49:36]          Current hash: 44a0ffadc915dbfee905ddf267eec4d4a00ddc0a
[23:49:36]          Stored hash : 2bdb1ac9ff1361716edf86da5946e7bd3facd39e
[23:49:36]          Current inode: 5361190    Stored inode: 5358607
[23:49:37]          Current file modification time: 1215682114
[23:49:37]          Stored file modification time : 1205447087
[23:49:37] /usr/bin/touch                                    [ OK ]
[23:49:37] /usr/bin/tr                                       [ OK ]
[23:49:37] /usr/bin/uniq                                     [ OK ]
[23:49:37] /usr/bin/users                                    [ OK ]
[23:49:37] /usr/bin/vmstat                                   [ Warning ]
[23:49:37] Warning: The file properties have changed:
[23:49:37]          File: /usr/bin/vmstat
[23:49:37]          Current hash: d1cd4f460631b3da1d1591d21cce213fff21bfcf
[23:49:37]          Stored hash : 202013298ba7b465c485db690c81b51a094b2484
[23:49:37]          Current inode: 5361191    Stored inode: 5358683
[23:49:37]          Current file modification time: 1215682114
[23:49:37]          Stored file modification time : 1205447087
[23:49:37] /usr/bin/w                                        [ Warning ]
[23:49:37] Warning: The file properties have changed:
[23:49:37]          File: /usr/bin/w
[23:49:38]          Current hash: fb2819df7d1c7a261311a105100fcae1333b71e7
[23:49:38]          Stored hash : 1afb9e68b386be6926900bf05585f9d8fff4ecf2
[23:49:38] /usr/bin/watch                                    [ Warning ]
[23:49:38] Warning: The file properties have changed:
[23:49:38]          File: /usr/bin/watch
[23:49:38]          Current hash: 11794147771ea0c82010a929013d620ab555f067
[23:49:38]          Stored hash : 4c674887699b7866e1325b190bcf40183e439b5d
[23:49:38]          Current inode: 5361192    Stored inode: 5358692
[23:49:38]          Current file modification time: 1215682114
[23:49:38]          Stored file modification time : 1205447087
[23:49:38] /usr/bin/wc                                       [ OK ]
[23:49:38] /usr/bin/wget                                     [ OK ]
[23:49:38] /usr/bin/whatis                                   [ OK ]
[23:49:38] /usr/bin/whereis                                  [ OK ]
[23:49:38] /usr/bin/which                                    [ OK ]
[23:49:38] /usr/bin/who                                      [ OK ]
[23:49:39] /usr/bin/whoami                                   [ OK ]
[23:49:39] /usr/bin/gawk                                     [ OK ]
[23:49:39] /usr/bin/lwp-request                              [ OK ]
[23:49:39] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[23:49:39] /usr/bin/w.procps                                 [ Warning ]
[23:49:39] Warning: The file properties have changed:
[23:49:39]          File: /usr/bin/w.procps
[23:49:39]          Current hash: fb2819df7d1c7a261311a105100fcae1333b71e7
[23:49:39]          Stored hash : 1afb9e68b386be6926900bf05585f9d8fff4ecf2
[23:49:39]          Current inode: 5361198    Stored inode: 5358688
[23:49:39]          Current file modification time: 1215682114
[23:49:39]          Stored file modification time : 1205447087
[23:49:39] /sbin/depmod                                      [ OK ]
[23:49:40] /sbin/ifconfig                                    [ OK ]
[23:49:40] /sbin/ifdown                                      [ OK ]
[23:49:40] /sbin/ifup                                        [ OK ]
[23:49:40] /sbin/init                                        [ OK ]
[23:49:40] /sbin/insmod                                      [ OK ]
[23:49:40] /sbin/ip                                          [ Warning ]
[23:49:40] Warning: The file properties have changed:
[23:49:40]          File: /sbin/ip
[23:49:40]          Current inode: 688229    Stored inode: 688185
[23:49:40]          Current file modification time: 1217639772
[23:49:40]          Stored file modification time : 1211419777
[23:49:41] /sbin/lsmod                                       [ OK ]
[23:49:41] /sbin/modinfo                                     [ OK ]
[23:49:41] /sbin/modprobe                                    [ OK ]
[23:49:41] /sbin/rmmod                                       [ OK ]
[23:49:41] /sbin/runlevel                                    [ OK ]
[23:49:41] /sbin/sulogin                                     [ OK ]
[23:49:41] /sbin/sysctl                                      [ Warning ]
[23:49:42] Warning: The file properties have changed:
[23:49:42]          File: /sbin/sysctl
[23:49:42]          Current hash: 766ec5bbeaff6678203d5e78b2b173a5026c8870
[23:49:42]          Stored hash : d212033ab99f586e64725af5770d0eaeed172ffe
[23:49:42]          Current inode: 688147    Stored inode: 688278
[23:49:42]          Current file modification time: 1215682114
[23:49:42]          Stored file modification time : 1205447087
[23:49:42] /sbin/syslogd                                     [ OK ]
[23:49:42] /usr/sbin/adduser                                 [ OK ]
[23:49:42] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[23:49:42] /usr/sbin/chroot                                  [ OK ]
[23:49:42] /usr/sbin/cron                                    [ OK ]
[23:49:43] /usr/sbin/groupadd                                [ OK ]
[23:49:43] /usr/sbin/groupdel                                [ OK ]
[23:49:43] /usr/sbin/groupmod                                [ OK ]
[23:49:43] /usr/sbin/grpck                                   [ OK ]
[23:49:43] /usr/sbin/nologin                                 [ OK ]
[23:49:44] /usr/sbin/pwck                                    [ OK ]
[23:49:44] /usr/sbin/tcpd                                    [ OK ]
[23:49:44] /usr/sbin/unhide                                  [ Warning ]
[23:49:44] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[23:49:44] /usr/sbin/useradd                                 [ OK ]
[23:49:44] /usr/sbin/userdel                                 [ OK ]
[23:49:44] /usr/sbin/usermod                                 [ OK ]
[23:49:45] /usr/sbin/vipw                                    [ OK ]
[23:49:45] /usr/sbin/unhide-linux26                          [ Warning ]
[23:49:45] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[23:49:49]
[23:49:49] Checking for rootkits...
[23:49:49] Info: Starting test name 'rootkits'
[23:49:49]
[23:49:49] Performing check of known rootkit files and directories
[23:49:49] Info: Starting test name 'known_rkts'
[23:49:49]
[23:49:49] Checking for 55808 Trojan - Variant A...
[23:49:49]   Checking for file '/tmp/.../r'                  [ Not found ]
[23:49:49]   Checking for file '/tmp/.../a'                  [ Not found ]
[23:49:49] 55808 Trojan - Variant A                          [ Not found ]
[23:49:49]
[23:49:49] Checking for ADM Worm...
[23:49:49]   Checking for string 'w0rm'                      [ Not found ]
[23:49:49] ADM Worm                                          [ Not found ]
[23:49:49]
[23:49:49] Checking for AjaKit Rootkit...
[23:49:49]   Checking for file '/dev/tux/.addr'              [ Not found ]
[23:49:49]   Checking for file '/dev/tux/.proc'              [ Not found ]
[23:49:49]   Checking for file '/dev/tux/.file'              [ Not found ]
[23:49:49]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[23:49:49]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[23:49:49]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[23:49:49]   Checking for directory '/dev/tux'               [ Not found ]
[23:49:49]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[23:49:49] AjaKit Rootkit                                    [ Not found ]
[23:49:49]
[23:49:49] Checking for aPa Kit...
[23:49:50]   Checking for file '/usr/share/.aPa'             [ Not found ]
[23:49:50] aPa Kit                                           [ Not found ]
[23:49:50]
[23:49:50] Checking for Apache Worm...
[23:49:50]   Checking for file '/bin/.log'                   [ Not found ]
[23:49:50] Apache Worm                                       [ Not found ]
[23:49:50]
[23:49:50] Checking for Ambient (ark) Rootkit...
[23:49:50]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[23:49:50]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[23:49:50]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[23:49:50]   Checking for directory '/dev/ptyxx'             [ Not found ]
[23:49:50] Ambient (ark) Rootkit                             [ Not found ]
[23:49:50]
[23:49:50] Checking for Balaur Rootkit...
[23:49:50]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[23:49:50]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[23:49:50]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[23:49:50]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[23:49:50] Balaur Rootkit                                    [ Not found ]
[23:49:50]
[23:49:50] Checking for BeastKit Rootkit...
[23:49:50]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[23:49:50]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[23:49:50]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[23:49:50]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[23:49:51] BeastKit Rootkit                                  [ Not found ]
[23:49:51]
[23:49:51] Checking for beX2 Rootkit...
[23:49:51]   Checking for directory '/usr/include/bex'       [ Not found ]
[23:49:51] beX2 Rootkit                                      [ Not found ]
[23:49:51]
[23:49:51] Checking for BOBKit Rootkit...
[23:49:51]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../find'           [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../du'             [ Not found ]
[23:49:51]   Checking for file '/usr/lib/.../top'            [ Not found ]
[23:49:51]   Checking for directory '/usr/lib/...'           [ Not found ]
[23:49:51]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[23:49:51]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[23:49:51]   Checking for directory '/tmp/.bkp'              [ Not found ]
[23:49:51] BOBKit Rootkit                                    [ Not found ]
[23:49:51]
[23:49:51] Checking for CiNIK Worm (Slapper.B variant)...
[23:49:51]   Checking for file '/tmp/.cinik'                 [ Not found ]
[23:49:52]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[23:49:52] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[23:49:52]
[23:49:52] Checking for Danny-Boy's Abuse Kit...
[23:49:52]   Checking for file '/dev/mdev'                   [ Not found ]
[23:49:52]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[23:49:52] Danny-Boy's Abuse Kit                             [ Not found ]
[23:49:52]
[23:49:52] Checking for Devil RootKit...
[23:49:52]   Checking for file '/var/lib/games/.src'         [ Not found ]
[23:49:52]   Checking for file '/dev/dsx'                    [ Not found ]
[23:49:52]   Checking for file '/dev/caca'                   [ Not found ]
[23:49:52] Devil RootKit                                     [ Not found ]
[23:49:52]
[23:49:52] Checking for Dica-Kit Rootkit...
[23:49:52]   Checking for file '/lib/.sso'                   [ Not found ]
[23:49:52]   Checking for file '/lib/.so'                    [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/va'         [ Not found ]
[23:49:52]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[23:49:52]   Checking for file '/usr/bin/.etc'               [ Not found ]
[23:49:52]   Checking for directory '/var/run/...dica'       [ Not found ]
[23:49:52]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[23:49:53]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[23:49:53] Dica-Kit Rootkit                                  [ Not found ]
[23:49:53]
[23:49:53] Checking for Dreams Rootkit...
[23:49:53]   Checking for file '/dev/ttyoa'                  [ Not found ]
[23:49:53]   Checking for file '/dev/ttyof'                  [ Not found ]
[23:49:53]   Checking for file '/dev/ttyop'                  [ Not found ]
[23:49:53]   Checking for file '/usr/bin/sense'              [ Not found ]
[23:49:53]   Checking for file '/usr/bin/sl2'                [ Not found ]
[23:49:53]   Checking for file '/usr/bin/logclear'           [ Not found ]
[23:49:53]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[23:49:53]   Checking for file '/usr/bin/snfs'               [ Not found ]
[23:49:53]   Checking for file '/usr/lib/libsss'             [ Not found ]
[23:49:53]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[23:49:53] Dreams Rootkit                                    [ Not found ]
[23:49:53]
[23:49:53] Checking for Duarawkz Rootkit...
[23:49:53]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[23:49:53]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[23:49:53] Duarawkz Rootkit                                  [ Not found ]
[23:49:53]
[23:49:53] Checking for Enye LKM...
[23:49:53]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[23:49:53] Enye LKM                                          [ Not found ]
[23:49:53]
[23:49:53] Checking for Flea Linux Rootkit...
[23:49:53]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[23:49:53]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[23:49:53]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[23:49:53]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[23:49:53]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[23:49:53]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[23:49:53]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[23:49:53]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[23:49:53]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[23:49:54]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[23:49:54]   Checking for directory '/dev/..0'               [ Not found ]
[23:49:54]   Checking for directory '/dev/..0/backup'        [ Not found ]
[23:49:54] Flea Linux Rootkit                                [ Not found ]
[23:49:54]
[23:49:54] Checking for FreeBSD Rootkit...
[23:49:54]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[23:49:54]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[23:49:54]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[23:49:54]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[23:49:54]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[23:49:54]   Checking for file '/bin/sysback'                [ Not found ]
[23:49:54]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[23:49:54]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[23:49:54]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[23:49:54] FreeBSD Rootkit                                   [ Not found ]
[23:49:54]
[23:49:54] Checking for ****`it Rootkit...
[23:49:54]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[23:49:54]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[23:49:54] ****`it Rootkit                                   [ Not found ]
[23:49:54]
[23:49:54] Checking for GasKit Rootkit...
[23:49:54]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[23:49:54]   Checking for directory '/dev/dev'               [ Not found ]
[23:49:55]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[23:49:55]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[23:49:55] GasKit Rootkit                                    [ Not found ]
[23:49:55]
[23:49:55] Checking for Heroin LKM...
[23:49:55]   Checking for kernel symbol 'heroin'             [ Not found ]
[23:49:55] Heroin LKM                                        [ Not found ]
[23:49:55]
[23:49:55] Checking for HjC Kit...
[23:49:55]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[23:49:55] HjC Kit                                           [ Not found ]
[23:49:55]
[23:49:55] Checking for ignoKit Rootkit...
[23:49:55]   Checking for file '/lib/defs/p'                 [ Not found ]
[23:49:55]   Checking for file '/lib/defs/q'                 [ Not found ]
[23:49:55]   Checking for file '/lib/defs/r'                 [ Not found ]
[23:49:55]   Checking for file '/lib/defs/s'                 [ Not found ]
[23:49:55]   Checking for file '/lib/defs/t'                 [ Not found ]
[23:49:55]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[23:49:55]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[23:49:55]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[23:49:55]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[23:49:55]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[23:49:55]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[23:49:55]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[23:49:55]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[23:49:55]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[23:49:55] ignoKit Rootkit                                   [ Not found ]
[23:49:55]
[23:49:55] Checking for ImperalsS-FBRK Rootkit...
[23:49:55]   Checking for directory '/dev/fd/.88'            [ Not found ]
[23:49:56]   Checking for directory '/dev/fd/.99'            [ Not found ]
[23:49:56] ImperalsS-FBRK Rootkit                            [ Not found ]
[23:49:56]
[23:49:56] Checking for Irix Rootkit...
[23:49:56]   Checking for directory '/dev/pts/01'            [ Not found ]
[23:49:56]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[23:49:56]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[23:49:56]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[23:49:56] Irix Rootkit                                      [ Not found ]
[23:49:56]
[23:49:56] Checking for Kitko Rootkit...
[23:49:56]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[23:49:56] Kitko Rootkit                                     [ Not found ]
[23:49:56]
[23:49:56] Checking for Knark Rootkit...
[23:49:56]   Checking for file '/proc/knark/pids'            [ Not found ]
[23:49:56]   Checking for directory '/proc/knark'            [ Not found ]
[23:49:56] Knark Rootkit                                     [ Not found ]
[23:49:56]
[23:49:56] Checking for Li0n Worm...
[23:49:56]   Checking for file '/bin/in.telnetd'             [ Not found ]
[23:49:56]   Checking for file '/bin/mjy'                    [ Not found ]
[23:49:56]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[23:49:56]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[23:49:56]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[23:49:56]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[23:49:57]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[23:49:57] Li0n Worm                                         [ Not found ]
[23:49:57]
[23:49:57] Checking for Lockit / LJK2 Rootkit...
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[23:49:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[23:49:58]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[23:49:58]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[23:49:58] Lockit / LJK2 Rootkit                             [ Not found ]
[23:49:58]
[23:49:58] Checking for Mood-NT Rootkit...
[23:49:58]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[23:49:58]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[23:49:58]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[23:49:58]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[23:49:58]   Checking for directory '/_cthulhu'              [ Not found ]
[23:49:58] Mood-NT Rootkit                                   [ Not found ]
[23:49:58]
[23:49:58] Checking for MRK Rootkit...
[23:49:58]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[23:49:58]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[23:49:58]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[23:49:58]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[23:49:58]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[23:49:59]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[23:49:59] MRK Rootkit                                       [ Not found ]
[23:49:59]
[23:49:59] Checking for Ni0 Rootkit...
[23:49:59]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[23:49:59]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[23:49:59]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[23:49:59]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[23:49:59]   Checking for directory '/tmp/waza'              [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[23:49:59]   Checking for directory '/usr/sbin/es'           [ Not found ]
[23:49:59] Ni0 Rootkit                                       [ Not found ]
[23:49:59]
[23:49:59] Checking for Ohhara Rootkit...
[23:49:59]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[23:49:59]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[23:49:59] Ohhara Rootkit                                    [ Not found ]
[23:49:59]
[23:49:59] Checking for Optic Kit (Tux) Worm...
[23:49:59]   Checking for directory '/dev/tux'               [ Not found ]
[23:49:59]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[23:49:59]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[23:49:59]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[23:49:59] Optic Kit (Tux) Worm                              [ Not found ]
[23:49:59]
[23:49:59] Checking for Oz Rootkit...
[23:49:59]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[23:49:59]   Checking for directory '/dev/.oz'               [ Not found ]
[23:50:00] Oz Rootkit                                        [ Not found ]
[23:50:00]
[23:50:00] Checking for Phalanx Rootkit...
[23:50:00]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[23:50:00]   Checking for file '/etc/host.ph1'               [ Not found ]
[23:50:00]   Checking for file '/bin/host.ph1'               [ Not found ]
[23:50:00]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[23:50:00]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[23:50:00] Phalanx Rootkit                                   [ Not found ]
[23:50:00]
[23:50:00] Checking for Phalanx Rootkit (strings)...
[23:50:00]   Checking for string 'phalanx'                   [ Not found ]
[23:50:00] Phalanx Rootkit (strings)                         [ Not found ]
[23:50:00]
[23:50:00] Checking for Portacelo Rootkit...
[23:50:00]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../.p'             [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../getty'          [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../show'           [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[23:50:00]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[23:50:00]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[23:50:00] Portacelo Rootkit                                 [ Not found ]
[23:50:00]
[23:50:00] Checking for R3dstorm Toolkit...
[23:50:00]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[23:50:00]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[23:50:01]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[23:50:01]   Checking for file '/bin/.../see_all'            [ Not found ]
[23:50:01]   Checking for directory '/var/log/tk02'          [ Not found ]
[23:50:01]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[23:50:01]   Checking for directory '/bin/...'               [ Not found ]
[23:50:01] R3dstorm Toolkit                                  [ Not found ]
[23:50:01]
[23:50:01] Checking for RH-Sharpe's Rootkit...
[23:50:01]   Checking for file '/bin/lps'                    [ Not found ]
[23:50:01]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[23:50:01]   Checking for file '/usr/bin/ltop'               [ Not found ]
[23:50:01]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[23:50:01]   Checking for file '/usr/bin/ldu'                [ Not found ]
[23:50:01]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[23:50:01]   Checking for file '/usr/bin/wp'                 [ Not found ]
[23:50:01]   Checking for file '/usr/bin/shad'               [ Not found ]
[23:50:01]   Checking for file '/usr/bin/vadim'              [ Not found ]
[23:50:01]   Checking for file '/usr/bin/slice'              [ Not found ]
[23:50:01]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[23:50:01]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[23:50:01] RH-Sharpe's Rootkit                               [ Not found ]
[23:50:01]
[23:50:01] Checking for RSHA's Rootkit...
[23:50:01]   Checking for file '/bin/kr4p'                   [ Not found ]
[23:50:01]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[23:50:01]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[23:50:01]   Checking for file '/usr/bin/slice2'             [ Not found ]
[23:50:01]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[23:50:01]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[23:50:01]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[23:50:01]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[23:50:01] RSHA's Rootkit                                    [ Not found ]
[23:50:01]
[23:50:01] Checking for Scalper Worm...
[23:50:02]   Checking for file '/tmp/.a'                     [ Not found ]
[23:50:02]   Checking for file '/tmp/.uua'                   [ Not found ]
[23:50:02] Scalper Worm                                      [ Not found ]
[23:50:02]
[23:50:02] Checking for Sebek LKM...
[23:50:02]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[23:50:02] Sebek LKM                                         [ Not found ]
[23:50:02]
[23:50:02] Checking for Shutdown Rootkit...
[23:50:02]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[23:50:02]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[23:50:02]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[23:50:02]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[23:50:02]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[23:50:02]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[23:50:02]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[23:50:02]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[23:50:02] Shutdown Rootkit                                  [ Not found ]
[23:50:02]
[23:50:02] Checking for SHV4 Rootkit...
[23:50:02]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[23:50:03]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[23:50:03]   Checking for file '/lib/lidps1.so'              [ Not found ]
[23:50:03]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[23:50:03]   Checking for directory '/lib/security/.config'  [ Not found ]
[23:50:03]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[23:50:03] SHV4 Rootkit                                      [ Not found ]
[23:50:03]
[23:50:03] Checking for SHV5 Rootkit...
[23:50:03]   Checking for file '/etc/sh.conf'                [ Not found ]
[23:50:03]   Checking for file '/dev/srd0'                   [ Not found ]
[23:50:03]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[23:50:03] SHV5 Rootkit                                      [ Not found ]
[23:50:03]
[23:50:03] Checking for Sin Rootkit...
[23:50:03]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[23:50:03]   Checking for file '/dev/ttyoa'                  [ Not found ]
[23:50:03]   Checking for file '/dev/ttyof'                  [ Not found ]
[23:50:03]   Checking for file '/dev/ttyop'                  [ Not found ]
[23:50:03]   Checking for file '/dev/ttyos'                  [ Not found ]
[23:50:03]   Checking for file '/usr/lib/.lib'               [ Not found ]
[23:50:03]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[23:50:03]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[23:50:03]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[23:50:03]   Checking for file '/usr/man/man1/...'           [ Not found ]
[23:50:03]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[23:50:03]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[23:50:03]   Checking for directory '/usr/lib/sn'            [ Not found ]
[23:50:03]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[23:50:03]   Checking for directory '/dev/.haos'             [ Not found ]
[23:50:03] Sin Rootkit                                       [ Not found ]
[23:50:03]
[23:50:03] Checking for Slapper Worm...
[23:50:03]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[23:50:04]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[23:50:04]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[23:50:04]   Checking for file '/tmp/httpd'                  [ Not found ]
[23:50:04]   Checking for file '/tmp/.unlock'                [ Not found ]
[23:50:04]   Checking for file '/tmp/update'                 [ Not found ]
[23:50:04]   Checking for file '/tmp/.cinik'                 [ Not found ]
[23:50:04]   Checking for file '/tmp/.b'                     [ Not found ]
[23:50:04] Slapper Worm                                      [ Not found ]
[23:50:04]
[23:50:04] Checking for Sneakin Rootkit...
[23:50:04]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[23:50:04] Sneakin Rootkit                                   [ Not found ]
[23:50:04]
[23:50:04] Checking for Suckit Rootkit...
[23:50:04]   Checking for file '/sbin/initsk12'              [ Not found ]
[23:50:04]   Checking for file '/sbin/initxrk'               [ Not found ]
[23:50:04]   Checking for file '/usr/bin/null'               [ Not found ]
[23:50:04]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[23:50:04]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[23:50:04]   Checking for directory '/etc/.MG'               [ Not found ]
[23:50:04]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[23:50:04]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[23:50:04] Suckit Rootkit                                    [ Not found ]
[23:50:04]
[23:50:04] Checking for SunOS Rootkit...
[23:50:05]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[23:50:05]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[23:50:05]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[23:50:05]   Checking for file '/bin/xlogin'                 [ Not found ]
[23:50:05]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[23:50:05]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[23:50:05]   Checking for file '/sbin/login'                 [ Not found ]
[23:50:05]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[23:50:05]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[23:50:05]   Checking for file '/dev/kmod'                   [ Not found ]
[23:50:05]   Checking for file '/dev/dos'                    [ Not found ]
[23:50:05] SunOS Rootkit                                     [ Not found ]
[23:50:05]
[23:50:05] Checking for SunOS / NSDAP Rootkit...
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[23:50:05]   Checking for file '/usr/lib/lpset'              [ Not found ]
[23:50:05]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[23:50:05] SunOS / NSDAP Rootkit                             [ Not found ]
[23:50:05]
[23:50:05] Checking for Superkit Rootkit...
[23:50:05]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[23:50:05] Superkit Rootkit                                  [ Not found ]
[23:50:06]
[23:50:06] Checking for TBD (Telnet BackDoor)...
[23:50:06]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[23:50:06] TBD (Telnet BackDoor)                             [ Not found ]
[23:50:06]
[23:50:06] Checking for TeLeKiT Rootkit...
[23:50:06]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[23:50:06]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[23:50:06]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[23:50:06]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[23:50:06]   Checking for file '/dev/ptyr'                   [ Not found ]
[23:50:06]   Checking for file '/dev/ptyp'                   [ Not found ]
[23:50:06]   Checking for file '/dev/ptyq'                   [ Not found ]
[23:50:06]   Checking for file '/dev/hda06'                  [ Not found ]
[23:50:06]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[23:50:06]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[23:50:06]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[23:50:06]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[23:50:06] TeLeKiT Rootkit                                   [ Not found ]
[23:50:06]
[23:50:06] Checking for T0rn Rootkit...
[23:50:06]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[23:50:06]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[23:50:07]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[23:50:07]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[23:50:07]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[23:50:07]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[23:50:07]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[23:50:07]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[23:50:07]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[23:50:07]   Checking for directory '/dev/.lib'              [ Not found ]
[23:50:07]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[23:50:07]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[23:50:07]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[23:50:07]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[23:50:07]   Checking for directory '/usr/src/.****'         [ Not found ]
[23:50:07]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[23:50:07]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[23:50:07]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[23:50:07]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[23:50:07] T0rn Rootkit                                      [ Not found ]
[23:50:07]
[23:50:07] Checking for Trojanit Kit...
[23:50:07]   Checking for file '/bin/.ls'                    [ Not found ]
[23:50:07]   Checking for file '/bin/.ps'                    [ Not found ]
[23:50:07]   Checking for file '/bin/.netstat'               [ Not found ]
[23:50:08]   Checking for file '/usr/bin/.nop'               [ Not found ]
[23:50:08]   Checking for file '/usr/bin/.who'               [ Not found ]
[23:50:08] Trojanit Kit                                      [ Not found ]
[23:50:08]
[23:50:08] Checking for Tuxtendo Rootkit...
[23:50:08]   Checking for file '/dev/tux/.addr'              [ Not found ]
[23:50:08]   Checking for file '/dev/tux/.cron'              [ Not found ]
[23:50:08]   Checking for file '/dev/tux/.file'              [ Not found ]
[23:50:08]   Checking for file '/dev/tux/.log'               [ Not found ]
[23:50:08]   Checking for file '/dev/tux/.proc'              [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[23:50:08]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[23:50:08]   Checking for directory '/dev/tux'               [ Not found ]
[23:50:08]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[23:50:08]   Checking for directory '/dev/tux/backup'        [ Not found ]
[23:50:08] Tuxtendo Rootkit                                  [ Not found ]
[23:50:08]
[23:50:08] Checking for URK Rootkit...
[23:50:08]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[23:50:08]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[23:50:09]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[23:50:09]   Checking for file '/tmp/conf.inf'               [ Not found ]
[23:50:09]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[23:50:09] URK Rootkit                                       [ Not found ]
[23:50:09]
[23:50:09] Checking for VcKit Rootkit...
[23:50:09]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[23:50:09]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[23:50:09] VcKit Rootkit                                     [ Not found ]
[23:50:09]
[23:50:09] Checking for Volc Rootkit...
[23:50:09]   Checking for directory '/var/spool/.recent'     [ Not found ]
[23:50:09]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[23:50:09]   Checking for directory '/usr/lib/volc'          [ Not found ]
[23:50:09]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[23:50:09] Volc Rootkit                                      [ Not found ]
[23:50:09]
[23:50:09] Checking for X-Org SunOS Rootkit...
[23:50:09]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[23:50:09]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[23:50:09]   Checking for file '/usr/bin/srload'             [ Not found ]
[23:50:09]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[23:50:09]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[23:50:09]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[23:50:09]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[23:50:09]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[23:50:09]   Checking for directory '/usr/share/man...'      [ Not found ]
[23:50:09] X-Org SunOS Rootkit                               [ Not found ]
[23:50:09]
[23:50:09] Checking for zaRwT.KiT Rootkit...
[23:50:09]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[23:50:09]   Checking for file '/dev/ttyf'                   [ Not found ]
[23:50:09]   Checking for file '/dev/ttyp'                   [ Not found ]
[23:50:09]   Checking for file '/dev/ttyn'                   [ Not found ]
[23:50:09]   Checking for file '/rk/tulz'                    [ Not found ]
[23:50:10]   Checking for directory '/rk'                    [ Not found ]
[23:50:10]   Checking for directory '/dev/rd/s'              [ Not found ]
[23:50:10] zaRwT.KiT Rootkit                                 [ Not found ]
[23:50:10]
[23:50:10] Performing additional rootkit checks
[23:50:10] Info: Starting test name 'additional_rkts'
[23:50:10]
[23:50:10]   Performing Suckit Rookit additional checks
[23:50:10]     Checking /sbin/init link count                [ OK ]
[23:50:10]     Checking for hidden file extensions           [ None found ]
[23:50:10]     Running skdet command                         [ Skipped ]
[23:50:10] Info: Unable to find the 'skdet' command
[23:50:10]   Suckit Rookit additional checks                 [ OK ]
[23:50:10]
[23:50:10]   Performing check of possible rootkit files and directories
[23:50:10] Info: Starting test name 'possible_rkt_files'
[23:50:10]     Checking for file '/dev/sdr0'                 [ Not found ]
[23:50:10]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[23:50:10]     Checking for file '/tmp/.bash_history'        [ Not found ]
[23:50:10]     Checking for file '/usr/info/.clib'           [ Not found ]
[23:50:10]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[23:50:10]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[23:50:10]     Checking for file '/sbin/create'              [ Not found ]
[23:50:10]     Checking for file '/dev/ttypz'                [ Not found ]
[23:50:10]     Checking for directory '/usr/bin/take'        [ Not found ]
[23:50:10]     Checking for directory '/usr/src/.lib'        [ Not found ]
[23:50:10]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[23:50:10]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[23:50:10]     Checking for directory '/usr/sbin/...'        [ Not found ]
[23:50:11]     Checking for directory '/usr/share/.gun'      [ Not found ]
[23:50:11]   Checking for possible rootkit files and directories [ None found ]
[23:50:11]
[23:50:11]   Performing check for possible rootkit strings
[23:50:11] Info: Starting test name 'possible_rkt_strings'
[23:50:11] Info: Found local startup file: /etc/rc.local
[23:50:11]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[23:50:11]     Checking for string '****'                    [ Not found ]
[23:50:11]     Checking for string 'backdoor'                [ Not found ]
[23:50:11]     Checking for string 'vt200'                   [ Not found ]
[23:50:11]     Checking for string '/usr/bin/xstat'          [ Not found ]
[23:50:11]     Checking for string '/bin/envpc'              [ Not found ]
[23:50:11]     Checking for string 'L4m3r0x'                 [ Not found ]
[23:50:11]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:50:11]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[23:50:11]     Checking for string '/dev/sgk'                [ Not found ]
[23:50:11]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:50:11]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:50:11]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[23:50:11]     Checking for string '/lib/.sso'               [ Not found ]
[23:50:12]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:50:12]     Checking for string '/dev/caca'               [ Not found ]
[23:50:12]     Checking for string '/dev/ttyoa'              [ Not found ]
[23:50:12]     Checking for string 'syg'                     [ Not found ]
[23:50:12]     Checking for string '/dev/pts/01'             [ Not found ]
[23:50:12]     Checking for string 'tw33dl3'                 [ Not found ]
[23:50:12]     Checking for string 'psniff'                  [ Not found ]
[23:50:12]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[23:50:12]     Checking for string 'promiscuous'             [ Not found ]
[23:50:12]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:50:12]     Checking for string '/dev/xdta'               [ Not found ]
[23:50:12]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[23:50:12]     Checking for string 'in.inetd'                [ Not found ]
[23:50:12]     Checking for string '#<HIDE_.*>'              [ Not found ]
[23:50:13]     Checking for string 'bin/xchk'                [ Not found ]
[23:50:13]     Checking for string 'bin/xsf'                 [ Not found ]
[23:50:13]   Checking for possible rootkit strings           [ None found ]
[23:50:13]
[23:50:13] Performing malware checks
[23:50:13] Info: Starting test name 'malware'
[23:50:13]
[23:50:13] Info: Test 'deleted_files' disabled at users request.
[23:50:13] Info: Starting test name 'running_procs'
[23:50:13]   Checking running processes for suspicious files [ None found ]
[23:50:13]
[23:50:13] Info: Test 'hidden_procs' disabled at users request.
[23:50:13]
[23:50:13] Info: Test 'suspscan' disabled at users request.
[23:50:13]
[23:50:13]   Performing check for login backdoors
[23:50:13] Info: Starting test name 'other_malware'
[23:50:13]     Checking for '/bin/.login'                    [ Not found ]
[23:50:13]     Checking for '/sbin/.login'                   [ Not found ]
[23:50:13]   Checking for login backdoors                    [ None found ]
[23:50:13]
[23:50:13]   Performing check for suspicious directories
[23:50:13]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[23:50:13]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[23:50:13]   Checking for suspicious directories             [ None found ]
[23:50:13]
[23:50:13]   Checking for software intrusions                [ Skipped ]
[23:50:13] Info: Check skipped - tripwire not installed
[23:50:13]
[23:50:13]   Performing check for sniffer log files
[23:50:13]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[23:50:14]   Checking for sniffer log files                  [ None found ]
[23:50:14]
[23:50:14] Performing trojan specific checks
[23:50:14] Info: Starting test name 'trojans'
[23:50:14]   Checking for enabled inetd services             [ Skipped ]
[23:50:14] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[23:50:14]
[23:50:14]   Performing check for enabled xinetd services
[23:50:14]   Checking for enabled xinetd services            [ Skipped ]
[23:50:14] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[23:50:14] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[23:50:14]
[23:50:14] Performing Linux specific checks
[23:50:14] Info: Starting test name 'os_specific'
[23:50:14]   Checking kernel module commands                 [ OK ]
[23:50:14] Info: Using modules pathname of '/lib/modules/2.6.24-19-generic'
[23:50:17]   Checking kernel module names                    [ OK ]
[23:50:19]
[23:50:19] Checking the network...
[23:50:19] Info: Starting test name 'network'
[23:50:19] Info: Starting test name 'ports'
[23:50:19]
[23:50:19] Performing check for backdoor ports
[23:50:19]   Checking for UDP port 2001                      [ Not found ]
[23:50:19]   Checking for TCP port 2006                      [ Not found ]
[23:50:19]   Checking for TCP port 2128                      [ Not found ]
[23:50:19]   Checking for TCP port 14856                     [ Not found ]
[23:50:20]   Checking for TCP port 47107                     [ Not found ]
[23:50:20]   Checking for TCP port 60922                     [ Not found ]
[23:50:20]
[23:50:20] Performing checks on the network interfaces
[23:50:20] Info: Starting test name 'promisc'
[23:50:20]   Checking for promiscuous interfaces             [ None found ]
[23:50:20]
[23:50:20] Info: Test 'packet_cap_apps' disabled at users request.
[23:50:22]
[23:50:22] Checking the local host...
[23:50:22] Info: Starting test name 'local_host'
[23:50:22]
[23:50:22] Performing system boot checks
[23:50:22] Info: Starting test name 'startup_files'
[23:50:22]   Checking for local host name                    [ Found ]
[23:50:22] Info: Starting test name 'startup_malware'
[23:50:22] Info: Found local startup file: /etc/rc.local
[23:50:22]   Checking for local startup files                [ Found ]
[23:50:22]   Checking local startup files for malware        [ None found ]
[23:50:22] Info: Found system startup directory: /etc/rc.d
[23:50:23]   Checking system startup files for malware       [ None found ]
[23:50:23]
[23:50:23] Performing group and account checks
[23:50:23] Info: Starting test name 'group_accounts'
[23:50:23]   Checking for passwd file                        [ Found ]
[23:50:23] Info: Found password file: /etc/passwd
[23:50:23]   Checking for root equivalent (UID 0) accounts   [ None found ]
[23:50:23] Info: Found shadow file: /etc/shadow
[23:50:23]   Checking for passwordless accounts              [ None found ]
[23:50:23] Info: Starting test name 'passwd_changes'
[23:50:23]   Checking for passwd file changes                [ None found ]
[23:50:23] Info: Starting test name 'group_changes'
[23:50:23]   Checking for group file changes                 [ None found ]
[23:50:23]   Checking root account shell history files       [ None found ]
[23:50:23]
[23:50:23] Performing system configuration file checks
[23:50:23] Info: Starting test name 'system_configs'
[23:50:23]   Checking for SSH configuration file             [ Not found ]
[23:50:23]   Checking for running syslog daemon              [ Found ]
[23:50:23]   Checking for syslog configuration file          [ Found ]
[23:50:23] Info: Found syslog configuration file: /etc/syslog.conf
[23:50:23]   Checking if syslog remote logging is allowed    [ Not allowed ]
[23:50:23]
[23:50:23] Performing filesystem checks
[23:50:23] Info: Starting test name 'filesystem'
[23:50:23] Info: SCAN_MODE_DEV set to 'THOROUGH'
[23:50:36]   Checking /dev for suspicious file types         [ Warning ]
[23:50:36] Warning: Suspicious file types found in /dev:
[23:50:36]          /dev/shm/pulse-shm-852574596: data
[23:50:37]   Checking for hidden files and directories       [ Warning ]
[23:50:37] Warning: Hidden directory found: /etc/.java
[23:50:37] Warning: Hidden directory found: /dev/.static
[23:50:37] Warning: Hidden directory found: /dev/.udev
[23:50:37] Warning: Hidden directory found: /dev/.initramfs
[23:50:37]
[23:50:37] Checking application versions...
[23:50:37] Info: Starting test name 'apps'
[23:50:38]   Checking version of Exim MTA                    [ OK ]
[23:50:38] Info: Application 'exim' version '4.69' found.
[23:50:38]   Checking version of GnuPG                       [ OK ]
[23:50:38] Info: Application 'gpg' version '1.4.6' found.
[23:50:38] Info: Application 'httpd' not found.
[23:50:38] Info: Application 'named' not found.
[23:50:38]   Checking version of OpenSSL                     [ OK ]
[23:50:38] Info: Application 'openssl' version '0.9.8g' found.
[23:50:38] Info: Application 'php' not found.
[23:50:38] Info: Application 'procmail' not found.
[23:50:38] Info: Application 'proftpd' not found.
[23:50:38] Info: Application 'sshd' not found.
[23:50:38] Info: Applications checked: 3 out of 9
[23:50:38]
[23:50:38] System checks summary
[23:50:38] =====================
[23:50:38]
[23:50:38] File properties checks...
[23:50:38] Files checked: 125
[23:50:38] Suspect files: 12
[23:50:38]
[23:50:38] Rootkit checks...
[23:50:38] Rootkits checked : 109
[23:50:38] Possible rootkits: 0
[23:50:38]
[23:50:38] Applications checks...
[23:50:38] Applications checked: 3
[23:50:38] Suspect applications: 0
[23:50:38]
[23:50:38] The system checks took: 1 minute and 17 seconds
[23:50:38]
[23:50:38] Info: End date is Tue Aug  5 23:50:38 EDT 2008


Please clear my doubts. Thanks!

---

### Post by pedja_portugalac on 2008-08-06
There's topic about rkhunter and chkrootkit (few topics). You can find there all you need just check before you post new thread if there is one someone else already have posted.

[http://ubuntuforums.org/showthread.php?t=774783](http://ubuntuforums.org/showthread.php?t=774783)

---

### Post by pedja_portugalac on 2008-08-06
I can see you have installed ubuntu-restricted package so you can watch movies, listening mp3's and so on. If you want rkhunter not to warn you again about that open terminal and type:

```
sudo gedit /etc/rkhunter.conf
```

Erase "#" in the beginning of lines in question: 

# Allow the specified hidden directories.
# One directory per line (use multiple ALLOWHIDDENDIR lines).
#
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
#ALLOWHIDDENDIR=/dev/.udevdb
#ALLOWHIDDENDIR=/dev/.udev.tdb
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs
#ALLOWHIDDENDIR=/dev/.SRC-unix

Like I have done. Then scroll down and add the following line (ALLOWDEVFILE=/dev/shm/pulse-shm-*) to:

# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-*

Save and close gedit (text editor).
Run in terminal:
```
sudo rkhunter --propupdate
```

And that's it. Now

sudo rkhunter --update
sudo rkhunter -c -sk 

to check again.

---

### Post by Thorzilla on 2008-08-06
I should've checked the threads more thoroughly, thanks!

---

