---
title: "RKHunter found 5 suspicious files, 4 with changed attributes, + Odd system activity"
date: 2008-07-01
forum: Security
---

### Post by OpenSourceFuture on 2008-07-01
Below are the warnings only

[Make that 5 with changed attributes]

Warning: The file properties have changed:
         File: /bin/bash
         Current hash: 8c74bdbb0d94f4bb162e69a87fd157e5d4c1????
         Stored hash : fc22cc7f937df7042049f30744ae29c13431????
         Current inode: 539688    Stored inode: 540184
         Current size: 702160    Stored size: 701808
         Current file modification time: 1210617204
         Stored file modification time : 1208230594
Warning: The file properties have changed:
         File: /usr/bin/dpkg
         Current hash: 3a524664f9d624cf9d36d58551f91ca12f12????
         Stored hash : fe42506caf6f230122b4607ee3f5006230c9????
         Current inode: 1154301    Stored inode: 1148736
         Current size: 359356    Stored size: 367448
         Current file modification time: 1212166343
         Stored file modification time : 1202867460
Warning: The file properties have changed:
         File: /usr/bin/dpkg-query
         Current hash: e8aa764f57e7f3c693f94fc0329c9ee64e16????
         Stored hash : 57308e30a2c6cc4d4fba0a4059709643e71d????
         Current inode: 1154304    Stored inode: 1148738
         Current file modification time: 1212166343
         Stored file modification time : 1202867460
Warning: The file properties have changed:
         File: /usr/bin/file
         Current hash: 3f1c272113fdffe393a60c212bd6762086e0????
         Stored hash : e65457a0c5662f7d67516734e90d62548d6e????
         Current inode: 1145332    Stored inode: 1145015
         Current file modification time: 1213076369
         Stored file modification time : 1193180590
Warning: The file properties have changed:
         File: /usr/bin/sudo
         Current hash: 0ed9a0d689ad891475eb13d02be7e34b4c10????
         Stored hash : c2e55b1da8a4678df995798fc980f5991fcc????
         Current inode: 539686    Stored inode: 1145825
         Current size: 107872    Stored size: 107840
         Current file modification time: 1210812110
         Stored file modification time : 1209555592
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-2624343252: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

Below is the full log

[02:06:38] Running Rootkit Hunter version 1.3.0 on ubuntu
[02:06:38]
[02:06:38] Info: Start date is Tue Jul  1 02:06:38 CDT 2008
[02:06:38]
[02:06:38] Checking configuration file and command-line options...
[02:06:38] Info: Detected operating system is 'Linux'
[02:06:38] Info: Found O/S name: Ubuntu 8.04
[02:06:38] Info: Command line is /usr/bin/rkhunter -c --rwo
[02:06:38] Info: Environment shell is /bin/bash; rkhunter is using dash
[02:06:38] Info: Using configuration file '/etc/rkhunter.conf'
[02:06:38] Info: Installation directory is '/usr'
[02:06:38] Info: Using language 'en'
[02:06:38] Info: Using '/var/lib/rkhunter/db' as the database directory
[02:06:38] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[02:06:38] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[02:06:38] Info: Using '/' as the root directory
[02:06:38] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[02:06:38] Info: No mail-on-warning address configured
[02:06:38] Info: X will automatically be detected
[02:06:38] Info: Using second color set
[02:06:38] Info: Found the 'diff' command: /usr/bin/diff
[02:06:38] Info: Found the 'file' command: /usr/bin/file
[02:06:38] Info: Found the 'find' command: /usr/bin/find
[02:06:38] Info: Found the 'ifconfig' command: /sbin/ifconfig
[02:06:38] Info: Found the 'ip' command: /sbin/ip
[02:06:38] Info: Found the 'ldd' command: /usr/bin/ldd
[02:06:38] Info: Found the 'lsattr' command: /usr/bin/lsattr
[02:06:38] Info: Found the 'lsmod' command: /sbin/lsmod
[02:06:38] Info: Found the 'lsof' command: /usr/bin/lsof
[02:06:38] Info: Found the 'mktemp' command: /bin/mktemp
[02:06:39] Info: Found the 'netstat' command: /bin/netstat
[02:06:39] Info: Found the 'perl' command: /usr/bin/perl
[02:06:39] Info: Found the 'ps' command: /bin/ps
[02:06:39] Info: Found the 'pwd' command: /bin/pwd
[02:06:39] Info: Found the 'readlink' command: /bin/readlink
[02:06:39] Info: Found the 'sort' command: /usr/bin/sort
[02:06:39] Info: Found the 'stat' command: /usr/bin/stat
[02:06:39] Info: Found the 'strings' command: /usr/bin/strings
[02:06:39] Info: Found the 'uniq' command: /usr/bin/uniq
[02:06:39] Info: System is not using prelinking
[02:06:39] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[02:06:39] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[02:06:39] Info: Stored hash values did not use a package manager
[02:06:39] Info: The hash function field index is set to 1
[02:06:39] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[02:06:39] Info: Previous file attributes were stored
[02:06:39] Info: Enabled tests are: all
[02:06:39] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[02:06:39] Info: Found ksym file '/proc/kallsyms'
[02:06:39]
[02:06:39] Checking if the O/S has changed since last time...
[02:06:39] Warning: The O/S name or version has changed since the last run:
[02:06:39]          Old O/S value: Ubuntu 8.04    New value: Ubuntu 8.04.1
[02:06:39]          Because of the change(s) the file properties checks may give some false-positive results.
[02:06:39]          You may need to re-run rkhunter with the '--propupd' option.
[02:06:39]
[02:06:39] Warning: WARNING! It is the users responsibility to ensure that when the '--propupd' option
           is used, all the files on their system are known to be genuine, and installed from a
           reliable source. The rkhunter '--check' option will compare the current file properties
           against previously stored values, and report if any values differ. However, rkhunter
           cannot determine what has caused the change, that is for the user to do.
[02:06:39]
[02:06:39] Starting system checks...
[02:06:39]
[02:06:39] Checking system commands...
[02:06:39] Info: Starting test name 'system_commands'
[02:06:39]
[02:06:39] Performing 'strings' command checks
[02:06:39] Info: Starting test name 'strings'
[02:06:39] Scanning for string /usr/sbin/ntpsx               [ OK ]
[02:06:39] Scanning for string /usr/lib/.../ls               [ OK ]
[02:06:39] Scanning for string /usr/lib/.../netstat          [ OK ]
[02:06:39] Scanning for string /usr/lib/.../lsof             [ OK ]
[02:06:39] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[02:06:39] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[02:06:39] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[02:06:39] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[02:06:40] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[02:06:40] Scanning for string /usr/lib/.../psr              [ OK ]
[02:06:40] Scanning for string /usr/lib/.../find             [ OK ]
[02:06:40] Scanning for string /usr/lib/.../pstree           [ OK ]
[02:06:40] Scanning for string /usr/lib/.../slocate          [ OK ]
[02:06:40] Scanning for string /usr/lib/.../du               [ OK ]
[02:06:40] Scanning for string /usr/lib/.../top              [ OK ]
[02:06:40] Scanning for string /usr/lib/...                  [ OK ]
[02:06:40] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[02:06:40] Scanning for string /usr/lib/.bkit-               [ OK ]
[02:06:40] Scanning for string /tmp/.bkp                     [ OK ]
[02:06:40] Scanning for string /tmp/.cinik                   [ OK ]
[02:06:40] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[02:06:40] Scanning for string /lib/.sso                     [ OK ]
[02:06:40] Scanning for string /lib/.so                      [ OK ]
[02:06:40] Scanning for string /var/run/...dica/clean        [ OK ]
[02:06:40] Scanning for string /var/run/...dica/xl           [ OK ]
[02:06:40] Scanning for string /var/run/...dica/xdr          [ OK ]
[02:06:40] Scanning for string /var/run/...dica/psg          [ OK ]
[02:06:40] Scanning for string /var/run/...dica/secure       [ OK ]
[02:06:40] Scanning for string /var/run/...dica/rdx          [ OK ]
[02:06:40] Scanning for string /var/run/...dica/va           [ OK ]
[02:06:40] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[02:06:40] Scanning for string /usr/bin/.etc                 [ OK ]
[02:06:40] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[02:06:40] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[02:06:40] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[02:06:40] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[02:06:41] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[02:06:41] Scanning for string /bin/sysback                  [ OK ]
[02:06:41] Scanning for string /usr/local/bin/sysback        [ OK ]
[02:06:41] Scanning for string /usr/lib/.tbd                 [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[02:06:41] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[02:06:41] Scanning for string /usr/info/.torn/sh*           [ OK ]
[02:06:41] Scanning for string /usr/src/.****/.1addr         [ OK ]
[02:06:41] Scanning for string /usr/src/.****/.1file         [ OK ]
[02:06:42] Scanning for string /usr/src/.****/.1proc         [ OK ]
[02:06:42] Scanning for string /usr/src/.****/.1logz         [ OK ]
[02:06:42] Scanning for string /usr/info/.t0rn               [ OK ]
[02:06:42] Scanning for string /dev/.lib                     [ OK ]
[02:06:42] Scanning for string /dev/.lib/lib                 [ OK ]
[02:06:42] Scanning for string /dev/.lib/lib/lib             [ OK ]
[02:06:42] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[02:06:42] Scanning for string /dev/.lib/lib/scan            [ OK ]
[02:06:42] Scanning for string /usr/src/.****                [ OK ]
[02:06:42] Scanning for string /usr/man/man1/man1            [ OK ]
[02:06:42] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[02:06:42] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[02:06:42] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[02:06:42]
[02:06:42] Performing 'shared libraries' checks
[02:06:42] Info: Starting test name 'shared_libs'
[02:06:42] Checking for preloading variables                 [ None found ]
[02:06:42] Checking for preload file                         [ Not found ]
[02:06:42] Info: Starting test name 'shared_libs_path'
[02:06:42] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[02:06:42]
[02:06:42] Performing file properties checks
[02:06:42] Info: Starting test name 'properties'
[02:06:42] Checking for prerequisites                        [ OK ]
[02:06:42] /bin/bash                                         [ Warning ]
[02:06:42] Warning: The file properties have changed:
[02:06:43]          File: /bin/bash
[02:06:43]          Current hash: 8c74bdbb0d94f4bb162e69a87fd157e5d4c1????
[02:06:43]          Stored hash : fc22cc7f937df7042049f30744ae29c13431????
[02:06:43]          Current inode: 539688    Stored inode: 540184
[02:06:43]          Current size: 702160    Stored size: 701808
[02:06:43]          Current file modification time: 1210617204
[02:06:43]          Stored file modification time : 1208230594
[02:06:43] /bin/cat                                          [ OK ]
[02:06:43] /bin/chmod                                        [ OK ]
[02:06:43] /bin/chown                                        [ OK ]
[02:06:43] /bin/cp                                           [ OK ]
[02:06:43] /bin/date                                         [ OK ]
[02:06:43] /bin/df                                           [ OK ]
[02:06:43] /bin/dmesg                                        [ OK ]
[02:06:44] /bin/echo                                         [ OK ]
[02:06:44] /bin/ed                                           [ OK ]
[02:06:44] /bin/egrep                                        [ OK ]
[02:06:44] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[02:06:44] /bin/fgrep                                        [ OK ]
[02:06:44] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[02:06:44] /bin/grep                                         [ OK ]
[02:06:44] /bin/ip                                           [ OK ]
[02:06:44] /bin/kill                                         [ OK ]
[02:06:44] /bin/login                                        [ OK ]
[02:06:45] /bin/ls                                           [ OK ]
[02:06:45] /bin/lsmod                                        [ OK ]
[02:06:45] /bin/mktemp                                       [ OK ]
[02:06:45] /bin/more                                         [ OK ]
[02:06:45] /bin/mount                                        [ OK ]
[02:06:45] /bin/mv                                           [ OK ]
[02:06:45] /bin/netstat                                      [ OK ]
[02:06:45] /bin/ps                                           [ OK ]
[02:06:45] /bin/pwd                                          [ OK ]
[02:06:46] /bin/readlink                                     [ OK ]
[02:06:46] /bin/sed                                          [ OK ]
[02:06:46] /bin/sh                                           [ OK ]
[02:06:46] /bin/su                                           [ OK ]
[02:06:46] /bin/touch                                        [ OK ]
[02:06:46] /bin/uname                                        [ OK ]
[02:06:46] /bin/which                                        [ OK ]
[02:06:46] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[02:06:46] /bin/dash                                         [ OK ]
[02:06:47] /usr/bin/awk                                      [ OK ]
[02:06:47] /usr/bin/basename                                 [ OK ]
[02:06:47] /usr/bin/chattr                                   [ OK ]
[02:06:47] /usr/bin/cut                                      [ OK ]
[02:06:47] /usr/bin/diff                                     [ OK ]
[02:06:47] /usr/bin/dirname                                  [ OK ]
[02:06:47] /usr/bin/dpkg                                     [ Warning ]
[02:06:47] Warning: The file properties have changed:
[02:06:47]          File: /usr/bin/dpkg
[02:06:47]          Current hash: 3a524664f9d624cf9d36d58551f91ca12f12????
[02:06:47]          Stored hash : fe42506caf6f230122b4607ee3f5006230c9????
[02:06:47]          Current inode: 1154301    Stored inode: 1148736
[02:06:47]          Current size: 359356    Stored size: 367448
[02:06:47]          Current file modification time: 1212166343
[02:06:48]          Stored file modification time : 1202867460
[02:06:48] /usr/bin/dpkg-query                               [ Warning ]
[02:06:48] Warning: The file properties have changed:
[02:06:48]          File: /usr/bin/dpkg-query
[02:06:48]          Current hash: e8aa764f57e7f3c693f94fc0329c9ee64e16????
[02:06:48]          Stored hash : 57308e30a2c6cc4d4fba0a4059709643e71d????
[02:06:48]          Current inode: 1154304    Stored inode: 1148738
[02:06:48]          Current file modification time: 1212166343
[02:06:48]          Stored file modification time : 1202867460
[02:06:48] /usr/bin/du                                       [ OK ]
[02:06:48] /usr/bin/env                                      [ OK ]
[02:06:48] /usr/bin/file                                     [ Warning ]
[02:06:48] Warning: The file properties have changed:
[02:06:48]          File: /usr/bin/file
[02:06:48]          Current hash: 3f1c272113fdffe393a60c212bd6762086e0????
[02:06:48]          Stored hash : e65457a0c5662f7d67516734e90d62548d6e????
[02:06:48]          Current inode: 1145332    Stored inode: 1145015
[02:06:48]          Current file modification time: 1213076369
[02:06:48]          Stored file modification time : 1193180590
[02:06:49] /usr/bin/find                                     [ OK ]
[02:06:49] /usr/bin/GET                                      [ OK ]
[02:06:49] /usr/bin/groups                                   [ OK ]
[02:06:49] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[02:06:49] /usr/bin/head                                     [ OK ]
[02:06:49] /usr/bin/id                                       [ OK ]
[02:06:49] /usr/bin/killall                                  [ OK ]
[02:06:49] /usr/bin/last                                     [ OK ]
[02:06:49] /usr/bin/lastlog                                  [ OK ]
[02:06:49] /usr/bin/ldd                                      [ OK ]
[02:06:50] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[02:06:50] /usr/bin/less                                     [ OK ]
[02:06:50] /usr/bin/locate                                   [ OK ]
[02:06:50] /usr/bin/logger                                   [ OK ]
[02:06:50] /usr/bin/lsattr                                   [ OK ]
[02:06:50] /usr/bin/lsof                                     [ OK ]
[02:06:50] /usr/bin/md5sum                                   [ OK ]
[02:06:50] /usr/bin/mlocate                                  [ OK ]
[02:06:50] /usr/bin/newgrp                                   [ OK ]
[02:06:51] /usr/bin/passwd                                   [ OK ]
[02:06:51] /usr/bin/perl                                     [ OK ]
[02:06:51] /usr/bin/pstree                                   [ OK ]
[02:06:51] /usr/bin/rkhunter                                 [ OK ]
[02:06:51] /usr/bin/runcon                                   [ OK ]
[02:06:51] /usr/bin/sha1sum                                  [ OK ]
[02:06:51] /usr/bin/size                                     [ OK ]
[02:06:51] /usr/bin/slocate                                  [ OK ]
[02:06:52] /usr/bin/sort                                     [ OK ]
[02:06:52] /usr/bin/stat                                     [ OK ]
[02:06:52] /usr/bin/strace                                   [ OK ]
[02:06:52] /usr/bin/strings                                  [ OK ]
[02:06:52] /usr/bin/sudo                                     [ Warning ]
[02:06:52] Warning: The file properties have changed:
[02:06:52]          File: /usr/bin/sudo
[02:06:52]          Current hash: 0ed9a0d689ad891475eb13d02be7e34b4c10????
[02:06:52]          Stored hash : c2e55b1da8a4678df995798fc980f5991fcc????
[02:06:52]          Current inode: 539686    Stored inode: 1145825
[02:06:52]          Current size: 107872    Stored size: 107840
[02:06:52]          Current file modification time: 1210812110
[02:06:52]          Stored file modification time : 1209555592
[02:06:52] /usr/bin/tail                                     [ OK ]
[02:06:52] /usr/bin/test                                     [ OK ]
[02:06:53] /usr/bin/top                                      [ OK ]
[02:06:53] /usr/bin/touch                                    [ OK ]
[02:06:53] /usr/bin/tr                                       [ OK ]
[02:06:53] /usr/bin/uniq                                     [ OK ]
[02:06:53] /usr/bin/users                                    [ OK ]
[02:06:53] /usr/bin/vmstat                                   [ OK ]
[02:06:53] /usr/bin/w                                        [ OK ]
[02:06:53] /usr/bin/watch                                    [ OK ]
[02:06:53] /usr/bin/wc                                       [ OK ]
[02:06:54] /usr/bin/wget                                     [ OK ]
[02:06:54] /usr/bin/whatis                                   [ OK ]
[02:06:54] /usr/bin/whereis                                  [ OK ]
[02:06:54] /usr/bin/which                                    [ OK ]
[02:06:54] /usr/bin/who                                      [ OK ]
[02:06:54] /usr/bin/whoami                                   [ OK ]
[02:06:54] /usr/bin/mawk                                     [ OK ]
[02:06:54] /usr/bin/lwp-request                              [ OK ]
[02:06:54] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[02:06:54] /usr/bin/w.procps                                 [ OK ]
[02:06:55] /sbin/depmod                                      [ OK ]
[02:06:55] /sbin/ifconfig                                    [ OK ]
[02:06:55] /sbin/ifdown                                      [ OK ]
[02:06:55] /sbin/ifup                                        [ OK ]
[02:06:55] /sbin/init                                        [ OK ]
[02:06:55] /sbin/insmod                                      [ OK ]
[02:06:55] /sbin/ip                                          [ OK ]
[02:06:55] /sbin/lsmod                                       [ OK ]
[02:06:56] /sbin/modinfo                                     [ OK ]
[02:06:56] /sbin/modprobe                                    [ OK ]
[02:06:56] /sbin/rmmod                                       [ OK ]
[02:06:56] /sbin/runlevel                                    [ OK ]
[02:06:56] /sbin/sulogin                                     [ OK ]
[02:06:56] /sbin/sysctl                                      [ OK ]
[02:06:56] /sbin/syslogd                                     [ OK ]
[02:06:57] /usr/sbin/adduser                                 [ OK ]
[02:06:57] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[02:06:57] /usr/sbin/chroot                                  [ OK ]
[02:06:57] /usr/sbin/cron                                    [ OK ]
[02:06:57] /usr/sbin/groupadd                                [ OK ]
[02:06:57] /usr/sbin/groupdel                                [ OK ]
[02:06:57] /usr/sbin/groupmod                                [ OK ]
[02:06:57] /usr/sbin/grpck                                   [ OK ]
[02:06:58] /usr/sbin/nologin                                 [ OK ]
[02:06:58] /usr/sbin/pwck                                    [ OK ]
[02:06:58] /usr/sbin/tcpd                                    [ OK ]
[02:06:58] /usr/sbin/useradd                                 [ OK ]
[02:06:58] /usr/sbin/userdel                                 [ OK ]
[02:06:59] /usr/sbin/usermod                                 [ OK ]
[02:06:59] /usr/sbin/vipw                                    [ OK ]
[02:07:00]
[02:07:00] Checking for rootkits...
[02:07:00] Info: Starting test name 'rootkits'
[02:07:00]
[02:07:00] Performing check of known rootkit files and directories
[02:07:00] Info: Starting test name 'known_rkts'
[02:07:00]
[02:07:00] Checking for 55808 Trojan - Variant A...
[02:07:00]   Checking for file '/tmp/.../r'                  [ Not found ]
[02:07:00]   Checking for file '/tmp/.../a'                  [ Not found ]
[02:07:01] 55808 Trojan - Variant A                          [ Not found ]
[02:07:01]
[02:07:01] Checking for ADM Worm...
[02:07:01]   Checking for string 'w0rm'                      [ Not found ]
[02:07:01] ADM Worm                                          [ Not found ]
[02:07:01]
[02:07:01] Checking for AjaKit Rootkit...
[02:07:01]   Checking for file '/dev/tux/.addr'              [ Not found ]
[02:07:01]   Checking for file '/dev/tux/.proc'              [ Not found ]
[02:07:01]   Checking for file '/dev/tux/.file'              [ Not found ]
[02:07:01]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[02:07:01]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[02:07:01]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[02:07:01]   Checking for directory '/dev/tux'               [ Not found ]
[02:07:01]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[02:07:01] AjaKit Rootkit                                    [ Not found ]
[02:07:01]
[02:07:01] Checking for aPa Kit...
[02:07:01]   Checking for file '/usr/share/.aPa'             [ Not found ]
[02:07:01] aPa Kit                                           [ Not found ]
[02:07:01]
[02:07:01] Checking for Apache Worm...
[02:07:01]   Checking for file '/bin/.log'                   [ Not found ]
[02:07:01] Apache Worm                                       [ Not found ]
[02:07:01]
[02:07:01] Checking for Ambient (ark) Rootkit...
[02:07:01]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[02:07:01]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[02:07:01]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[02:07:01]   Checking for directory '/dev/ptyxx'             [ Not found ]
[02:07:01] Ambient (ark) Rootkit                             [ Not found ]
[02:07:01]
[02:07:01] Checking for Balaur Rootkit...
[02:07:01]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[02:07:01]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[02:07:01]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[02:07:01]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[02:07:01] Balaur Rootkit                                    [ Not found ]
[02:07:01]
[02:07:01] Checking for BeastKit Rootkit...
[02:07:02]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[02:07:02]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[02:07:02]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[02:07:02] BeastKit Rootkit                                  [ Not found ]
[02:07:02]
[02:07:02] Checking for beX2 Rootkit...
[02:07:02]   Checking for directory '/usr/include/bex'       [ Not found ]
[02:07:02] beX2 Rootkit                                      [ Not found ]
[02:07:02]
[02:07:02] Checking for BOBKit Rootkit...
[02:07:02]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[02:07:02]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[02:07:03]   Checking for file '/usr/lib/.../find'           [ Not found ]
[02:07:03]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[02:07:03]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[02:07:03]   Checking for file '/usr/lib/.../du'             [ Not found ]
[02:07:03]   Checking for file '/usr/lib/.../top'            [ Not found ]
[02:07:03]   Checking for directory '/usr/lib/...'           [ Not found ]
[02:07:03]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[02:07:03]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[02:07:03]   Checking for directory '/tmp/.bkp'              [ Not found ]
[02:07:03] BOBKit Rootkit                                    [ Not found ]
[02:07:03]
[02:07:03] Checking for CiNIK Worm (Slapper.B variant)...
[02:07:03]   Checking for file '/tmp/.cinik'                 [ Not found ]
[02:07:03]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[02:07:03] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[02:07:03]
[02:07:03] Checking for Danny-Boy's Abuse Kit...
[02:07:03]   Checking for file '/dev/mdev'                   [ Not found ]
[02:07:03]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[02:07:03] Danny-Boy's Abuse Kit                             [ Not found ]
[02:07:03]
[02:07:03] Checking for Devil RootKit...
[02:07:03]   Checking for file '/var/lib/games/.src'         [ Not found ]
[02:07:03]   Checking for file '/dev/dsx'                    [ Not found ]
[02:07:03]   Checking for file '/dev/caca'                   [ Not found ]
[02:07:03] Devil RootKit                                     [ Not found ]
[02:07:03]
[02:07:03] Checking for Dica-Kit Rootkit...
[02:07:03]   Checking for file '/lib/.sso'                   [ Not found ]
[02:07:03]   Checking for file '/lib/.so'                    [ Not found ]
[02:07:03]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[02:07:03]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[02:07:03]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[02:07:04]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[02:07:04]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[02:07:04]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[02:07:04]   Checking for file '/var/run/...dica/va'         [ Not found ]
[02:07:04]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[02:07:04]   Checking for file '/usr/bin/.etc'               [ Not found ]
[02:07:04]   Checking for directory '/var/run/...dica'       [ Not found ]
[02:07:04]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[02:07:04]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[02:07:04] Dica-Kit Rootkit                                  [ Not found ]
[02:07:04]
[02:07:04] Checking for Dreams Rootkit...
[02:07:04]   Checking for file '/dev/ttyoa'                  [ Not found ]
[02:07:04]   Checking for file '/dev/ttyof'                  [ Not found ]
[02:07:04]   Checking for file '/dev/ttyop'                  [ Not found ]
[02:07:04]   Checking for file '/usr/bin/sense'              [ Not found ]
[02:07:04]   Checking for file '/usr/bin/sl2'                [ Not found ]
[02:07:04]   Checking for file '/usr/bin/logclear'           [ Not found ]
[02:07:04]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[02:07:04]   Checking for file '/usr/bin/snfs'               [ Not found ]
[02:07:04]   Checking for file '/usr/lib/libsss'             [ Not found ]
[02:07:04]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[02:07:04] Dreams Rootkit                                    [ Not found ]
[02:07:04]
[02:07:04] Checking for Duarawkz Rootkit...
[02:07:04]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[02:07:04]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[02:07:04] Duarawkz Rootkit                                  [ Not found ]
[02:07:04]
[02:07:04] Checking for Enye LKM...
[02:07:04]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[02:07:04] Enye LKM                                          [ Not found ]
[02:07:04]
[02:07:04] Checking for Flea Linux Rootkit...
[02:07:04]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[02:07:04]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[02:07:04]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[02:07:05]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[02:07:05]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[02:07:05]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[02:07:05]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[02:07:05]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[02:07:05]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[02:07:05]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[02:07:05]   Checking for directory '/dev/..0'               [ Not found ]
[02:07:05]   Checking for directory '/dev/..0/backup'        [ Not found ]
[02:07:05] Flea Linux Rootkit                                [ Not found ]
[02:07:05]
[02:07:05] Checking for FreeBSD Rootkit...
[02:07:05]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[02:07:05]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[02:07:05]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[02:07:05]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[02:07:05]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[02:07:05]   Checking for file '/bin/sysback'                [ Not found ]
[02:07:05]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[02:07:05]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[02:07:05]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[02:07:05] FreeBSD Rootkit                                   [ Not found ]
[02:07:05]
[02:07:05] Checking for ****`it Rootkit...
[02:07:05]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[02:07:05]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[02:07:05] ****`it Rootkit                                   [ Not found ]
[02:07:05]
[02:07:05] Checking for GasKit Rootkit...
[02:07:05]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[02:07:06]   Checking for directory '/dev/dev'               [ Not found ]
[02:07:06]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[02:07:06]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[02:07:06] GasKit Rootkit                                    [ Not found ]
[02:07:06]
[02:07:06] Checking for Heroin LKM...
[02:07:06]   Checking for kernel symbol 'heroin'             [ Not found ]
[02:07:06] Heroin LKM                                        [ Not found ]
[02:07:06]
[02:07:06] Checking for HjC Kit...
[02:07:06]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[02:07:06] HjC Kit                                           [ Not found ]
[02:07:06]
[02:07:06] Checking for ignoKit Rootkit...
[02:07:06]   Checking for file '/lib/defs/p'                 [ Not found ]
[02:07:06]   Checking for file '/lib/defs/q'                 [ Not found ]
[02:07:06]   Checking for file '/lib/defs/r'                 [ Not found ]
[02:07:06]   Checking for file '/lib/defs/s'                 [ Not found ]
[02:07:06]   Checking for file '/lib/defs/t'                 [ Not found ]
[02:07:06]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[02:07:06]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[02:07:06]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[02:07:06]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[02:07:06]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[02:07:06]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[02:07:06]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[02:07:06]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[02:07:06]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[02:07:06] ignoKit Rootkit                                   [ Not found ]
[02:07:06]
[02:07:06] Checking for ImperalsS-FBRK Rootkit...
[02:07:06]   Checking for directory '/dev/fd/.88'            [ Not found ]
[02:07:06]   Checking for directory '/dev/fd/.99'            [ Not found ]
[02:07:07] ImperalsS-FBRK Rootkit                            [ Not found ]
[02:07:07]
[02:07:07] Checking for Irix Rootkit...
[02:07:07]   Checking for directory '/dev/pts/01'            [ Not found ]
[02:07:07]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[02:07:07]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[02:07:07]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[02:07:07] Irix Rootkit                                      [ Not found ]
[02:07:07]
[02:07:07] Checking for Kitko Rootkit...
[02:07:07]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[02:07:07] Kitko Rootkit                                     [ Not found ]
[02:07:07]
[02:07:07] Checking for Knark Rootkit...
[02:07:07]   Checking for file '/proc/knark/pids'            [ Not found ]
[02:07:07]   Checking for directory '/proc/knark'            [ Not found ]
[02:07:07] Knark Rootkit                                     [ Not found ]
[02:07:07]
[02:07:07] Checking for Li0n Worm...
[02:07:07]   Checking for file '/bin/in.telnetd'             [ Not found ]
[02:07:07]   Checking for file '/bin/mjy'                    [ Not found ]
[02:07:07]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[02:07:07]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[02:07:07]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[02:07:07]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[02:07:08]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[02:07:08] Li0n Worm                                         [ Not found ]
[02:07:08]
[02:07:08] Checking for Lockit / LJK2 Rootkit...
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[02:07:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[02:07:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[02:07:09]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[02:07:09] Lockit / LJK2 Rootkit                             [ Not found ]
[02:07:09]
[02:07:09] Checking for Mood-NT Rootkit...
[02:07:09]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[02:07:09]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[02:07:09]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[02:07:09]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[02:07:09]   Checking for directory '/_cthulhu'              [ Not found ]
[02:07:09] Mood-NT Rootkit                                   [ Not found ]
[02:07:09]
[02:07:09] Checking for MRK Rootkit...
[02:07:09]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[02:07:09]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[02:07:09]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[02:07:09]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[02:07:09]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[02:07:09]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[02:07:09] MRK Rootkit                                       [ Not found ]
[02:07:09]
[02:07:09] Checking for Ni0 Rootkit...
[02:07:09]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[02:07:09]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[02:07:09]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[02:07:09]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[02:07:09]   Checking for directory '/tmp/waza'              [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[02:07:10]   Checking for directory '/usr/sbin/es'           [ Not found ]
[02:07:10] Ni0 Rootkit                                       [ Not found ]
[02:07:10]
[02:07:10] Checking for Ohhara Rootkit...
[02:07:10]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[02:07:10]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[02:07:10] Ohhara Rootkit                                    [ Not found ]
[02:07:10]
[02:07:10] Checking for Optic Kit (Tux) Worm...
[02:07:10]   Checking for directory '/dev/tux'               [ Not found ]
[02:07:10]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[02:07:10]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[02:07:10]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[02:07:10] Optic Kit (Tux) Worm                              [ Not found ]
[02:07:10]
[02:07:10] Checking for Oz Rootkit...
[02:07:10]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[02:07:10]   Checking for directory '/dev/.oz'               [ Not found ]
[02:07:10] Oz Rootkit                                        [ Not found ]
[02:07:10]
[02:07:10] Checking for Phalanx Rootkit...
[02:07:10]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[02:07:10]   Checking for file '/etc/host.ph1'               [ Not found ]
[02:07:10]   Checking for file '/bin/host.ph1'               [ Not found ]
[02:07:10]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[02:07:10]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[02:07:10] Phalanx Rootkit                                   [ Not found ]
[02:07:10]
[02:07:10] Checking for Phalanx Rootkit (strings)...
[02:07:10]   Checking for string 'phalanx'                   [ Not found ]
[02:07:10] Phalanx Rootkit (strings)                         [ Not found ]
[02:07:10]
[02:07:10] Checking for Portacelo Rootkit...
[02:07:10]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[02:07:10]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../.p'             [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../getty'          [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../show'           [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[02:07:11]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[02:07:11]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[02:07:11] Portacelo Rootkit                                 [ Not found ]
[02:07:11]
[02:07:11] Checking for R3dstorm Toolkit...
[02:07:11]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[02:07:11]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[02:07:11]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[02:07:11]   Checking for file '/bin/.../see_all'            [ Not found ]
[02:07:11]   Checking for directory '/var/log/tk02'          [ Not found ]
[02:07:11]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[02:07:11]   Checking for directory '/bin/...'               [ Not found ]
[02:07:11] R3dstorm Toolkit                                  [ Not found ]
[02:07:11]
[02:07:11] Checking for RH-Sharpe's Rootkit...
[02:07:11]   Checking for file '/bin/lps'                    [ Not found ]
[02:07:11]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[02:07:11]   Checking for file '/usr/bin/ltop'               [ Not found ]
[02:07:11]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[02:07:11]   Checking for file '/usr/bin/ldu'                [ Not found ]
[02:07:11]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[02:07:11]   Checking for file '/usr/bin/wp'                 [ Not found ]
[02:07:11]   Checking for file '/usr/bin/shad'               [ Not found ]
[02:07:11]   Checking for file '/usr/bin/vadim'              [ Not found ]
[02:07:11]   Checking for file '/usr/bin/slice'              [ Not found ]
[02:07:12]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[02:07:12]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[02:07:12] RH-Sharpe's Rootkit                               [ Not found ]
[02:07:12]
[02:07:12] Checking for RSHA's Rootkit...
[02:07:12]   Checking for file '/bin/kr4p'                   [ Not found ]
[02:07:12]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[02:07:12]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[02:07:12]   Checking for file '/usr/bin/slice2'             [ Not found ]
[02:07:12]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[02:07:12]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[02:07:12]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[02:07:12]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[02:07:12] RSHA's Rootkit                                    [ Not found ]
[02:07:12]
[02:07:12] Checking for Scalper Worm...
[02:07:12]   Checking for file '/tmp/.a'                     [ Not found ]
[02:07:12]   Checking for file '/tmp/.uua'                   [ Not found ]
[02:07:12] Scalper Worm                                      [ Not found ]
[02:07:12]
[02:07:12] Checking for Sebek LKM...
[02:07:13]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[02:07:13] Sebek LKM                                         [ Not found ]
[02:07:13]
[02:07:13] Checking for Shutdown Rootkit...
[02:07:13]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[02:07:13]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[02:07:13]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[02:07:13]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[02:07:13]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[02:07:13]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[02:07:13]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[02:07:13]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[02:07:13] Shutdown Rootkit                                  [ Not found ]
[02:07:13]
[02:07:13] Checking for SHV4 Rootkit...
[02:07:13]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[02:07:13]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[02:07:13]   Checking for file '/lib/lidps1.so'              [ Not found ]
[02:07:13]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[02:07:13]   Checking for directory '/lib/security/.config'  [ Not found ]
[02:07:13]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[02:07:13] SHV4 Rootkit                                      [ Not found ]
[02:07:13]
[02:07:13] Checking for SHV5 Rootkit...
[02:07:13]   Checking for file '/etc/sh.conf'                [ Not found ]
[02:07:13]   Checking for file '/dev/srd0'                   [ Not found ]
[02:07:13]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[02:07:13] SHV5 Rootkit                                      [ Not found ]
[02:07:13]
[02:07:13] Checking for Sin Rootkit...
[02:07:13]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[02:07:13]   Checking for file '/dev/ttyoa'                  [ Not found ]
[02:07:13]   Checking for file '/dev/ttyof'                  [ Not found ]
[02:07:13]   Checking for file '/dev/ttyop'                  [ Not found ]
[02:07:13]   Checking for file '/dev/ttyos'                  [ Not found ]
[02:07:13]   Checking for file '/usr/lib/.lib'               [ Not found ]
[02:07:13]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[02:07:13]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[02:07:14]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[02:07:14]   Checking for file '/usr/man/man1/...'           [ Not found ]
[02:07:14]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[02:07:14]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[02:07:14]   Checking for directory '/usr/lib/sn'            [ Not found ]
[02:07:14]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[02:07:14]   Checking for directory '/dev/.haos'             [ Not found ]
[02:07:14] Sin Rootkit                                       [ Not found ]
[02:07:14]
[02:07:14] Checking for Slapper Worm...
[02:07:14]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[02:07:14]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[02:07:14]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[02:07:14]   Checking for file '/tmp/httpd'                  [ Not found ]
[02:07:14]   Checking for file '/tmp/.unlock'                [ Not found ]
[02:07:14]   Checking for file '/tmp/update'                 [ Not found ]
[02:07:14]   Checking for file '/tmp/.cinik'                 [ Not found ]
[02:07:14]   Checking for file '/tmp/.b'                     [ Not found ]
[02:07:14] Slapper Worm                                      [ Not found ]
[02:07:14]
[02:07:14] Checking for Sneakin Rootkit...
[02:07:14]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[02:07:14] Sneakin Rootkit                                   [ Not found ]
[02:07:14]
[02:07:14] Checking for Suckit Rootkit...
[02:07:14]   Checking for file '/sbin/initsk12'              [ Not found ]
[02:07:14]   Checking for file '/sbin/initxrk'               [ Not found ]
[02:07:14]   Checking for file '/usr/bin/null'               [ Not found ]
[02:07:14]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[02:07:14]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[02:07:14]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[02:07:14]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[02:07:14]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[02:07:14]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[02:07:15]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[02:07:15]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[02:07:15]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[02:07:15]   Checking for directory '/etc/.MG'               [ Not found ]
[02:07:15]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[02:07:15]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[02:07:15] Suckit Rootkit                                    [ Not found ]
[02:07:15]
[02:07:15] Checking for SunOS Rootkit...
[02:07:15]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[02:07:15]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[02:07:15]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[02:07:15]   Checking for file '/bin/xlogin'                 [ Not found ]
[02:07:15]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[02:07:15]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[02:07:15]   Checking for file '/sbin/login'                 [ Not found ]
[02:07:15]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[02:07:15]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[02:07:15]   Checking for file '/dev/kmod'                   [ Not found ]
[02:07:15]   Checking for file '/dev/dos'                    [ Not found ]
[02:07:15] SunOS Rootkit                                     [ Not found ]
[02:07:15]
[02:07:15] Checking for SunOS / NSDAP Rootkit...
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[02:07:15]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[02:07:16]   Checking for file '/usr/lib/lpset'              [ Not found ]
[02:07:16]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[02:07:16] SunOS / NSDAP Rootkit                             [ Not found ]
[02:07:16]
[02:07:16] Checking for Superkit Rootkit...
[02:07:16]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[02:07:16] Superkit Rootkit                                  [ Not found ]
[02:07:16]
[02:07:16] Checking for TBD (Telnet BackDoor)...
[02:07:16]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[02:07:16] TBD (Telnet BackDoor)                             [ Not found ]
[02:07:16]
[02:07:16] Checking for TeLeKiT Rootkit...
[02:07:16]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[02:07:16]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[02:07:16]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[02:07:16]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[02:07:16]   Checking for file '/dev/ptyr'                   [ Not found ]
[02:07:16]   Checking for file '/dev/ptyp'                   [ Not found ]
[02:07:16]   Checking for file '/dev/ptyq'                   [ Not found ]
[02:07:16]   Checking for file '/dev/hda06'                  [ Not found ]
[02:07:16]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[02:07:16]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[02:07:16]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[02:07:16]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[02:07:16] TeLeKiT Rootkit                                   [ Not found ]
[02:07:16]
[02:07:16] Checking for T0rn Rootkit...
[02:07:16]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[02:07:16]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[02:07:17]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[02:07:17]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[02:07:17]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[02:07:17]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[02:07:17]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[02:07:17]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[02:07:17]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[02:07:17]   Checking for directory '/dev/.lib'              [ Not found ]
[02:07:17]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[02:07:17]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[02:07:17]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[02:07:17]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[02:07:17]   Checking for directory '/usr/src/.****'         [ Not found ]
[02:07:17]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[02:07:17]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[02:07:17]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[02:07:17]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[02:07:17] T0rn Rootkit                                      [ Not found ]
[02:07:17]
[02:07:17] Checking for Trojanit Kit...
[02:07:17]   Checking for file '/bin/.ls'                    [ Not found ]
[02:07:18]   Checking for file '/bin/.ps'                    [ Not found ]
[02:07:18]   Checking for file '/bin/.netstat'               [ Not found ]
[02:07:18]   Checking for file '/usr/bin/.nop'               [ Not found ]
[02:07:18]   Checking for file '/usr/bin/.who'               [ Not found ]
[02:07:18] Trojanit Kit                                      [ Not found ]
[02:07:18]
[02:07:18] Checking for Tuxtendo Rootkit...
[02:07:18]   Checking for file '/dev/tux/.addr'              [ Not found ]
[02:07:18]   Checking for file '/dev/tux/.cron'              [ Not found ]
[02:07:18]   Checking for file '/dev/tux/.file'              [ Not found ]
[02:07:18]   Checking for file '/dev/tux/.log'               [ Not found ]
[02:07:18]   Checking for file '/dev/tux/.proc'              [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[02:07:18]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[02:07:18]   Checking for directory '/dev/tux'               [ Not found ]
[02:07:18]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[02:07:18]   Checking for directory '/dev/tux/backup'        [ Not found ]
[02:07:18] Tuxtendo Rootkit                                  [ Not found ]
[02:07:18]
[02:07:18] Checking for URK Rootkit...
[02:07:18]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[02:07:19]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[02:07:19]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[02:07:19]   Checking for file '/tmp/conf.inf'               [ Not found ]
[02:07:19]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[02:07:19] URK Rootkit                                       [ Not found ]
[02:07:19]
[02:07:19] Checking for VcKit Rootkit...
[02:07:19]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[02:07:19]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[02:07:19] VcKit Rootkit                                     [ Not found ]
[02:07:19]
[02:07:19] Checking for Volc Rootkit...
[02:07:19]   Checking for directory '/var/spool/.recent'     [ Not found ]
[02:07:19]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[02:07:19]   Checking for directory '/usr/lib/volc'          [ Not found ]
[02:07:19]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[02:07:19] Volc Rootkit                                      [ Not found ]
[02:07:19]
[02:07:19] Checking for X-Org SunOS Rootkit...
[02:07:19]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[02:07:19]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[02:07:19]   Checking for file '/usr/bin/srload'             [ Not found ]
[02:07:19]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[02:07:19]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[02:07:19]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[02:07:19]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[02:07:19]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[02:07:19]   Checking for directory '/usr/share/man...'      [ Not found ]
[02:07:19] X-Org SunOS Rootkit                               [ Not found ]
[02:07:19]
[02:07:19] Checking for zaRwT.KiT Rootkit...
[02:07:19]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[02:07:19]   Checking for file '/dev/ttyf'                   [ Not found ]
[02:07:19]   Checking for file '/dev/ttyp'                   [ Not found ]
[02:07:19]   Checking for file '/dev/ttyn'                   [ Not found ]
[02:07:19]   Checking for file '/rk/tulz'                    [ Not found ]
[02:07:20]   Checking for directory '/rk'                    [ Not found ]
[02:07:20]   Checking for directory '/dev/rd/s'              [ Not found ]
[02:07:20] zaRwT.KiT Rootkit                                 [ Not found ]
[02:07:20]
[02:07:20] Performing additional rootkit checks
[02:07:20] Info: Starting test name 'additional_rkts'
[02:07:20]
[02:07:20]   Performing Suckit Rookit additional checks
[02:07:20]     Checking /sbin/init link count                [ OK ]
[02:07:20]     Checking for hidden file extensions           [ None found ]
[02:07:20]     Running skdet command                         [ Skipped ]
[02:07:20] Info: Unable to find the 'skdet' command
[02:07:20]   Suckit Rookit additional checks                 [ OK ]
[02:07:20]
[02:07:20]   Performing check of possible rootkit files and directories
[02:07:20] Info: Starting test name 'possible_rkt_files'
[02:07:20]     Checking for file '/dev/sdr0'                 [ Not found ]
[02:07:20]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[02:07:20]     Checking for file '/tmp/.bash_history'        [ Not found ]
[02:07:20]     Checking for file '/usr/info/.clib'           [ Not found ]
[02:07:20]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[02:07:20]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[02:07:20]     Checking for file '/sbin/create'              [ Not found ]
[02:07:20]     Checking for file '/dev/ttypz'                [ Not found ]
[02:07:20]     Checking for directory '/usr/bin/take'        [ Not found ]
[02:07:20]     Checking for directory '/usr/src/.lib'        [ Not found ]
[02:07:20]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[02:07:20]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[02:07:20]     Checking for directory '/usr/sbin/...'        [ Not found ]
[02:07:21]     Checking for directory '/usr/share/.gun'      [ Not found ]
[02:07:21]   Checking for possible rootkit files and directories [ None found ]
[02:07:21]
[02:07:21]   Performing check for possible rootkit strings
[02:07:21] Info: Starting test name 'possible_rkt_strings'
[02:07:21] Info: Found local startup file: /etc/rc.local
[02:07:21]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[02:07:21]     Checking for string '****'                    [ Not found ]
[02:07:21]     Checking for string 'backdoor'                [ Not found ]
[02:07:21]     Checking for string 'vt200'                   [ Not found ]
[02:07:21]     Checking for string '/usr/bin/xstat'          [ Not found ]
[02:07:21]     Checking for string '/bin/envpc'              [ Not found ]
[02:07:21]     Checking for string 'L4m3r0x'                 [ Not found ]
[02:07:21]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[02:07:21]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[02:07:21]     Checking for string '/dev/sgk'                [ Not found ]
[02:07:21]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[02:07:21]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[02:07:21]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[02:07:21]     Checking for string '/lib/.sso'               [ Not found ]
[02:07:21]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[02:07:21]     Checking for string '/dev/caca'               [ Not found ]
[02:07:22]     Checking for string '/dev/ttyoa'              [ Not found ]
[02:07:22]     Checking for string 'syg'                     [ Not found ]
[02:07:22]     Checking for string '/dev/pts/01'             [ Not found ]
[02:07:22]     Checking for string 'tw33dl3'                 [ Not found ]
[02:07:22]     Checking for string 'psniff'                  [ Not found ]
[02:07:22]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[02:07:22]     Checking for string 'promiscuous'             [ Not found ]
[02:07:22]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[02:07:22]     Checking for string '/dev/xdta'               [ Not found ]
[02:07:22]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[02:07:22]     Checking for string 'in.inetd'                [ Not found ]
[02:07:22]     Checking for string '#<HIDE_.*>'              [ Not found ]
[02:07:22]     Checking for string 'bin/xchk'                [ Not found ]
[02:07:22]     Checking for string 'bin/xsf'                 [ Not found ]
[02:07:22]   Checking for possible rootkit strings           [ None found ]
[02:07:22]
[02:07:22] Performing malware checks
[02:07:22] Info: Starting test name 'malware'
[02:07:22]
[02:07:22] Info: Test 'deleted_files' disabled at users request.
[02:07:22] Info: Starting test name 'running_procs'
[02:07:23]   Checking running processes for suspicious files [ None found ]
[02:07:23]
[02:07:23] Info: Test 'hidden_procs' disabled at users request.
[02:07:23]
[02:07:23] Info: Test 'suspscan' disabled at users request.
[02:07:23]
[02:07:23]   Performing check for login backdoors
[02:07:23] Info: Starting test name 'other_malware'
[02:07:23]     Checking for '/bin/.login'                    [ Not found ]
[02:07:23]     Checking for '/sbin/.login'                   [ Not found ]
[02:07:23]   Checking for login backdoors                    [ None found ]
[02:07:23]
[02:07:23]   Performing check for suspicious directories
[02:07:23]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[02:07:23]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[02:07:23]   Checking for suspicious directories             [ None found ]
[02:07:23]
[02:07:23]   Checking for software intrusions                [ Skipped ]
[02:07:23] Info: Check skipped - tripwire not installed
[02:07:23]
[02:07:23]   Performing check for sniffer log files
[02:07:23]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[02:07:23]   Checking for sniffer log files                  [ None found ]
[02:07:23]
[02:07:23] Performing trojan specific checks
[02:07:23] Info: Starting test name 'trojans'
[02:07:23] Info: Using inetd configuration file '/etc/inetd.conf'
[02:07:23]   Checking for enabled inetd services             [ OK ]
[02:07:23]
[02:07:23]   Performing check for enabled xinetd services
[02:07:23]   Checking for enabled xinetd services            [ Skipped ]
[02:07:23] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[02:07:23] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[02:07:23]
[02:07:23] Performing Linux specific checks
[02:07:23] Info: Starting test name 'os_specific'
[02:07:23]   Checking kernel module commands                 [ OK ]
[02:07:24] Info: Using modules pathname of '/lib/modules/2.6.24-19-generic'
[02:07:25]   Checking kernel module names                    [ OK ]
[02:07:25]
[02:07:25] Checking the network...
[02:07:25] Info: Starting test name 'network'
[02:07:25] Info: Starting test name 'ports'
[02:07:25]
[02:07:25] Performing check for backdoor ports
[02:07:25]   Checking for UDP port 2001                      [ Not found ]
[02:07:25]   Checking for TCP port 2006                      [ Not found ]
[02:07:26]   Checking for TCP port 2128                      [ Not found ]
[02:07:26]   Checking for TCP port 14856                     [ Not found ]
[02:07:26]   Checking for TCP port 47107                     [ Not found ]
[02:07:26]   Checking for TCP port 60922                     [ Not found ]
[02:07:26]
[02:07:26] Performing checks on the network interfaces
[02:07:26] Info: Starting test name 'promisc'
[02:07:26]   Checking for promiscuous interfaces             [ None found ]
[02:07:26]
[02:07:26] Info: Test 'packet_cap_apps' disabled at users request.
[02:07:26]
[02:07:26] Checking the local host...
[02:07:26] Info: Starting test name 'local_host'
[02:07:26]
[02:07:26] Performing system boot checks
[02:07:26] Info: Starting test name 'startup_files'
[02:07:26]   Checking for local host name                    [ Found ]
[02:07:26] Info: Starting test name 'startup_malware'
[02:07:26] Info: Found local startup file: /etc/rc.local
[02:07:26]   Checking for local startup files                [ Found ]
[02:07:26]   Checking local startup files for malware        [ None found ]
[02:07:26] Info: Found system startup directory: /etc/init.d
[02:07:28]   Checking system startup files for malware       [ None found ]
[02:07:28]
[02:07:28] Performing group and account checks
[02:07:28] Info: Starting test name 'group_accounts'
[02:07:28]   Checking for passwd file                        [ Found ]
[02:07:28] Info: Found password file: /etc/passwd
[02:07:28]   Checking for root equivalent (UID 0) accounts   [ None found ]
[02:07:28] Info: Found shadow file: /etc/shadow
[02:07:28]   Checking for passwordless accounts              [ None found ]
[02:07:28] Info: Starting test name 'passwd_changes'
[02:07:28]   Checking for passwd file changes                [ None found ]
[02:07:28] Info: Starting test name 'group_changes'
[02:07:28]   Checking for group file changes                 [ None found ]
[02:07:28]   Checking root account shell history files       [ None found ]
[02:07:28]
[02:07:28] Performing system configuration file checks
[02:07:28] Info: Starting test name 'system_configs'
[02:07:28]   Checking for SSH configuration file             [ Not found ]
[02:07:28]   Checking for running syslog daemon              [ Found ]
[02:07:28]   Checking for syslog configuration file          [ Found ]
[02:07:28] Info: Found syslog configuration file: /etc/syslog.conf
[02:07:28]   Checking if syslog remote logging is allowed    [ Not allowed ]
[02:07:28]
[02:07:28] Performing filesystem checks
[02:07:28] Info: Starting test name 'filesystem'
[02:07:28] Info: SCAN_MODE_DEV set to 'THOROUGH'
[02:08:08]   Checking /dev for suspicious file types         [ Warning ]
[02:08:08] Warning: Suspicious file types found in /dev:
[02:08:08]          /dev/shm/pulse-shm-2624343252: data
[02:08:10]   Checking for hidden files and directories       [ Warning ]
[02:08:10] Warning: Hidden directory found: /etc/.java
[02:08:10] Warning: Hidden directory found: /dev/.static
[02:08:10] Warning: Hidden directory found: /dev/.udev
[02:08:10] Warning: Hidden directory found: /dev/.initramfs
[02:08:10]
[02:08:10] Checking application versions...
[02:08:10] Info: Starting test name 'apps'
[02:08:10]   Checking version of Exim MTA                    [ OK ]
[02:08:10] Info: Application 'exim' version '4.69' found.
[02:08:10]   Checking version of GnuPG                       [ OK ]
[02:08:10] Info: Application 'gpg' version '1.4.6' found.
[02:08:11] Info: Application 'httpd' not found.
[02:08:11] Info: Application 'named' not found.
[02:08:11]   Checking version of OpenSSL                     [ OK ]
[02:08:11] Info: Application 'openssl' version '0.9.8g' found.
[02:08:11] Info: Application 'php' not found.
[02:08:11] Info: Application 'procmail' not found.
[02:08:11] Info: Application 'proftpd' not found.
[02:08:11] Info: Application 'sshd' not found.
[02:08:11] Info: Applications checked: 3 out of 9
[02:08:11]
[02:08:11] System checks summary
[02:08:11] =====================
[02:08:11]
[02:08:11] File properties checks...
[02:08:11] Files checked: 123
[02:08:11] Suspect files: 5
[02:08:11]
[02:08:11] Rootkit checks...
[02:08:11] Rootkits checked : 109
[02:08:11] Possible rootkits: 0
[02:08:11]
[02:08:11] Applications checks...
[02:08:11] Applications checked: 3
[02:08:11] Suspect applications: 0
[02:08:11]
[02:08:11] The system checks took: 1 minute and 32 seconds
[02:08:11]
[02:08:11] Info: End date is Tue Jul  1 02:08:11 CDT 2008

I had some odd system behavior that involved firefox being unable to access the internet, I couldn't start certain applications. My internet keeps going dropping out, which may be another odd unrelated occurrence. I'm not sure if this is the result of random errors and false positives, or something more serious. Any help is appreciated.

---

### Post by OpenSourceFuture on 2008-07-01
bump :popcorn:

---

### Post by imjscn on 2008-07-03
what's the proper commond line to run rkhunter and get a report, please?

---

