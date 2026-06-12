---
title: "RkHunter found 8 suspicious files w/log"
date: 2008-04-15
forum: Security Discussions
---

### Post by Duckyspetrie on 2008-04-15
Not sure what to make of these:
[10:06:06] Running Rootkit Hunter version 1.3.0 on Veritas
[10:06:06]
[10:06:06] Info: Start date is Tue Apr 15 10:06:06 CDT 2008
[10:06:06]
[10:06:06] Checking configuration file and command-line options...
[10:06:06] Info: Detected operating system is 'Linux'
[10:06:06] Info: Found O/S name: Ubuntu hardy (development branch)
[10:06:06] Info: Command line is /usr/bin/rkhunter --checkall
[10:06:06] Info: Environment shell is /bin/bash; rkhunter is using dash
[10:06:06] Info: Using configuration file '/etc/rkhunter.conf'
[10:06:06] Info: Installation directory is '/usr'
[10:06:06] Info: Using language 'en'
[10:06:06] Info: Using '/var/lib/rkhunter/db' as the database directory
[10:06:06] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[10:06:06] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[10:06:06] Info: Using '/' as the root directory
[10:06:06] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[10:06:06] Info: No mail-on-warning address configured
[10:06:06] Info: X will automatically be detected
[10:06:06] Info: Using second color set
[10:06:06] Info: Found the 'diff' command: /usr/bin/diff
[10:06:06] Info: Found the 'file' command: /usr/bin/file
[10:06:06] Info: Found the 'find' command: /usr/bin/find
[10:06:06] Info: Found the 'ifconfig' command: /sbin/ifconfig
[10:06:06] Info: Found the 'ip' command: /sbin/ip
[10:06:06] Info: Found the 'ldd' command: /usr/bin/ldd
[10:06:06] Info: Found the 'lsattr' command: /usr/bin/lsattr
[10:06:06] Info: Found the 'lsmod' command: /sbin/lsmod
[10:06:07] Info: Found the 'lsof' command: /usr/bin/lsof
[10:06:07] Info: Found the 'mktemp' command: /bin/mktemp
[10:06:07] Info: Found the 'netstat' command: /bin/netstat
[10:06:07] Info: Found the 'perl' command: /usr/bin/perl
[10:06:07] Info: Found the 'ps' command: /bin/ps
[10:06:07] Info: Found the 'pwd' command: /bin/pwd
[10:06:07] Info: Found the 'readlink' command: /bin/readlink
[10:06:07] Info: Found the 'sort' command: /usr/bin/sort
[10:06:07] Info: Found the 'stat' command: /usr/bin/stat
[10:06:07] Info: Found the 'strings' command: /usr/bin/strings
[10:06:07] Info: Found the 'uniq' command: /usr/bin/uniq
[10:06:07] Info: System is not using prelinking
[10:06:07] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[10:06:07] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[10:06:07] Info: Stored hash values did not use a package manager
[10:06:07] Info: The hash function field index is set to 1
[10:06:07] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[10:06:07] Info: Previous file attributes were stored
[10:06:07] Info: Enabled tests are: all
[10:06:07] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[10:06:07] Info: Found ksym file '/proc/kallsyms'
[10:06:07]
[10:06:07] Checking if the O/S has changed since last time...
[10:06:07] Warning: The O/S name or version has changed since the last run:
[10:06:07]          Old O/S value: Ubuntu hardy (development branch)    New value: Ubuntu 8.04
[10:06:07]          Because of the change(s) the file properties checks may give some false-positive results.
[10:06:07]          You may need to re-run rkhunter with the '--propupd' option.
[10:06:07]
[10:06:07] Warning: WARNING! It is the users responsibility to ensure that when the '--propupd' option
           is used, all the files on their system are known to be genuine, and installed from a
           reliable source. The rkhunter '--check' option will compare the current file properties
           against previously stored values, and report if any values differ. However, rkhunter
           cannot determine what has caused the change, that is for the user to do.
[10:06:07]
[10:06:07] Starting system checks...
[10:06:07]
[10:06:07] Checking system commands...
[10:06:07] Info: Starting test name 'system_commands'
[10:06:07]
[10:06:07] Performing 'strings' command checks
[10:06:07] Info: Starting test name 'strings'
[10:06:07] Scanning for string /usr/sbin/ntpsx               [ OK ]
[10:06:07] Scanning for string /usr/lib/.../ls               [ OK ]
[10:06:07] Scanning for string /usr/lib/.../netstat          [ OK ]
[10:06:07] Scanning for string /usr/lib/.../lsof             [ OK ]
[10:06:07] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[10:06:07] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[10:06:07] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[10:06:07] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[10:06:07] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[10:06:07] Scanning for string /usr/lib/.../psr              [ OK ]
[10:06:07] Scanning for string /usr/lib/.../find             [ OK ]
[10:06:07] Scanning for string /usr/lib/.../pstree           [ OK ]
[10:06:07] Scanning for string /usr/lib/.../slocate          [ OK ]
[10:06:07] Scanning for string /usr/lib/.../du               [ OK ]
[10:06:08] Scanning for string /usr/lib/.../top              [ OK ]
[10:06:08] Scanning for string /usr/lib/...                  [ OK ]
[10:06:08] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[10:06:08] Scanning for string /usr/lib/.bkit-               [ OK ]
[10:06:08] Scanning for string /tmp/.bkp                     [ OK ]
[10:06:08] Scanning for string /tmp/.cinik                   [ OK ]
[10:06:08] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[10:06:08] Scanning for string /lib/.sso                     [ OK ]
[10:06:08] Scanning for string /lib/.so                      [ OK ]
[10:06:08] Scanning for string /var/run/...dica/clean        [ OK ]
[10:06:08] Scanning for string /var/run/...dica/xl           [ OK ]
[10:06:08] Scanning for string /var/run/...dica/xdr          [ OK ]
[10:06:08] Scanning for string /var/run/...dica/psg          [ OK ]
[10:06:08] Scanning for string /var/run/...dica/secure       [ OK ]
[10:06:08] Scanning for string /var/run/...dica/rdx          [ OK ]
[10:06:08] Scanning for string /var/run/...dica/va           [ OK ]
[10:06:08] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[10:06:08] Scanning for string /usr/bin/.etc                 [ OK ]
[10:06:08] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[10:06:08] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[10:06:08] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[10:06:08] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[10:06:08] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[10:06:08] Scanning for string /bin/sysback                  [ OK ]
[10:06:08] Scanning for string /usr/local/bin/sysback        [ OK ]
[10:06:08] Scanning for string /usr/lib/.tbd                 [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[10:06:08] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[10:06:09] Scanning for string /usr/info/.torn/sh*           [ OK ]
[10:06:09] Scanning for string /usr/src/.****/.1addr         [ OK ]
[10:06:09] Scanning for string /usr/src/.****/.1file         [ OK ]
[10:06:09] Scanning for string /usr/src/.****/.1proc         [ OK ]
[10:06:09] Scanning for string /usr/src/.****/.1logz         [ OK ]
[10:06:09] Scanning for string /usr/info/.t0rn               [ OK ]
[10:06:09] Scanning for string /dev/.lib                     [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib                 [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib             [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[10:06:09] Scanning for string /dev/.lib/lib/scan            [ OK ]
[10:06:09] Scanning for string /usr/src/.****                [ OK ]
[10:06:09] Scanning for string /usr/man/man1/man1            [ OK ]
[10:06:09] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[10:06:09] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[10:06:09] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[10:06:09]
[10:06:09] Performing 'shared libraries' checks
[10:06:09] Info: Starting test name 'shared_libs'
[10:06:09] Checking for preloading variables                 [ None found ]
[10:06:09] Checking for preload file                         [ Not found ]
[10:06:09] Info: Starting test name 'shared_libs_path'
[10:06:09] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[10:06:09]
[10:06:09] Performing file properties checks
[10:06:09] Info: Starting test name 'properties'
[10:06:10] Warning: Checking for prerequisites               [ Warning ]
[10:06:10]          The local host configuration or operating system has changed.
[10:06:10] /bin/bash                                         [ Warning ]
[10:06:10] Warning: The file properties have changed:
[10:06:10]          File: /bin/bash
[10:06:10]          Current hash: fc22cc7f937df7042049f30744ae29c13431e4f8
[10:06:10]          Stored hash : 7eacee1973e9eb3a87c6345b55606fcd76adf362
[10:06:10]          Current inode: 8519697    Stored inode: 8519685
[10:06:10]          Current size: 701808    Stored size: 701744
[10:06:10]          Current file modification time: 1208230594
[10:06:10]          Stored file modification time : 1204885663
[10:06:10] /bin/cat                                          [ OK ]
[10:06:10] /bin/chmod                                        [ OK ]
[10:06:10] /bin/chown                                        [ OK ]
[10:06:10] /bin/cp                                           [ OK ]
[10:06:10] /bin/date                                         [ OK ]
[10:06:11] /bin/df                                           [ OK ]
[10:06:11] /bin/dmesg                                        [ Warning ]
[10:06:11] Warning: The file properties have changed:
[10:06:11]          File: /bin/dmesg
[10:06:11]          Current inode: 8519700    Stored inode: 8519708
[10:06:11]          Current file modification time: 1208230606
[10:06:11]          Stored file modification time : 1207985053
[10:06:11] /bin/echo                                         [ OK ]
[10:06:11] /bin/ed                                           [ OK ]
[10:06:11] /bin/egrep                                        [ OK ]
[10:06:11] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[10:06:11] /bin/fgrep                                        [ OK ]
[10:06:11] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[10:06:11] /bin/grep                                         [ OK ]
[10:06:11] /bin/ip                                           [ OK ]
[10:06:11] /bin/kill                                         [ OK ]
[10:06:12] /bin/login                                        [ OK ]
[10:06:12] /bin/ls                                           [ OK ]
[10:06:12] /bin/lsmod                                        [ OK ]
[10:06:12] /bin/mktemp                                       [ OK ]
[10:06:12] /bin/more                                         [ Warning ]
[10:06:12] Warning: The file properties have changed:
[10:06:12]          File: /bin/more
[10:06:12]          Current inode: 8519727    Stored inode: 8519709
[10:06:12]          Current file modification time: 1208230606
[10:06:12]          Stored file modification time : 1207985053
[10:06:12] /bin/mount                                        [ Warning ]
[10:06:12] Warning: The file properties have changed:
[10:06:12]          File: /bin/mount
[10:06:12]          Current inode: 8519685    Stored inode: 8519699
[10:06:12]          Current file modification time: 1208230606
[10:06:12]          Stored file modification time : 1207985053
[10:06:12] /bin/mv                                           [ OK ]
[10:06:13] /bin/netstat                                      [ OK ]
[10:06:13] /bin/ps                                           [ OK ]
[10:06:13] /bin/pwd                                          [ OK ]
[10:06:13] /bin/readlink                                     [ OK ]
[10:06:13] /bin/sed                                          [ OK ]
[10:06:13] /bin/sh                                           [ OK ]
[10:06:13] /bin/su                                           [ OK ]
[10:06:13] /bin/touch                                        [ OK ]
[10:06:14] /bin/uname                                        [ OK ]
[10:06:14] /bin/which                                        [ OK ]
[10:06:14] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[10:06:14] /bin/dash                                         [ OK ]
[10:06:14] /usr/bin/awk                                      [ OK ]
[10:06:14] /usr/bin/basename                                 [ OK ]
[10:06:14] /usr/bin/chattr                                   [ OK ]
[10:06:14] /usr/bin/cut                                      [ OK ]
[10:06:14] /usr/bin/diff                                     [ OK ]
[10:06:15] /usr/bin/dirname                                  [ OK ]
[10:06:15] /usr/bin/dpkg                                     [ OK ]
[10:06:15] /usr/bin/dpkg-query                               [ OK ]
[10:06:15] /usr/bin/du                                       [ OK ]
[10:06:15] /usr/bin/env                                      [ OK ]
[10:06:15] /usr/bin/file                                     [ OK ]
[10:06:15] /usr/bin/find                                     [ OK ]
[10:06:15] /usr/bin/GET                                      [ OK ]
[10:06:15] /usr/bin/groups                                   [ OK ]
[10:06:15] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[10:06:16] /usr/bin/head                                     [ OK ]
[10:06:16] /usr/bin/id                                       [ OK ]
[10:06:16] /usr/bin/killall                                  [ OK ]
[10:06:16] /usr/bin/last                                     [ Warning ]
[10:06:16] Warning: The file properties have changed:
[10:06:16]          File: /usr/bin/last
[10:06:16]          Current inode: 13205715    Stored inode: 13205655
[10:06:16]          Current file modification time: 1208179886
[10:06:16]          Stored file modification time : 1207228933
[10:06:16] /usr/bin/lastlog                                  [ OK ]
[10:06:16] /usr/bin/ldd                                      [ OK ]
[10:06:16] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[10:06:16] /usr/bin/less                                     [ OK ]
[10:06:16] /usr/bin/locate                                   [ OK ]
[10:06:16] /usr/bin/logger                                   [ Warning ]
[10:06:16] Warning: The file properties have changed:
[10:06:16]          File: /usr/bin/logger
[10:06:17]          Current inode: 13205722    Stored inode: 13205528
[10:06:17]          Current file modification time: 1208230606
[10:06:17]          Stored file modification time : 1207985053
[10:06:17] /usr/bin/lsattr                                   [ OK ]
[10:06:17] /usr/bin/lsof                                     [ OK ]
[10:06:17] /usr/bin/md5sum                                   [ OK ]
[10:06:17] /usr/bin/mlocate                                  [ OK ]
[10:06:17] /usr/bin/newgrp                                   [ OK ]
[10:06:17] /usr/bin/passwd                                   [ OK ]
[10:06:17] /usr/bin/perl                                     [ OK ]
[10:06:17] /usr/bin/pstree                                   [ OK ]
[10:06:18] /usr/bin/rkhunter                                 [ OK ]
[10:06:18] /usr/bin/runcon                                   [ OK ]
[10:06:18] /usr/bin/sha1sum                                  [ OK ]
[10:06:18] /usr/bin/size                                     [ OK ]
[10:06:18] /usr/bin/sort                                     [ OK ]
[10:06:18] /usr/bin/stat                                     [ OK ]
[10:06:18] /usr/bin/strace                                   [ OK ]
[10:06:18] /usr/bin/strings                                  [ OK ]
[10:06:18] /usr/bin/sudo                                     [ OK ]
[10:06:19] /usr/bin/tail                                     [ OK ]
[10:06:19] /usr/bin/test                                     [ OK ]
[10:06:19] /usr/bin/top                                      [ OK ]
[10:06:19] /usr/bin/touch                                    [ OK ]
[10:06:19] /usr/bin/tr                                       [ OK ]
[10:06:19] /usr/bin/uniq                                     [ OK ]
[10:06:19] /usr/bin/users                                    [ OK ]
[10:06:19] /usr/bin/vmstat                                   [ OK ]
[10:06:19] /usr/bin/w                                        [ OK ]
[10:06:19] /usr/bin/watch                                    [ OK ]
[10:06:20] /usr/bin/wc                                       [ OK ]
[10:06:20] /usr/bin/wget                                     [ OK ]
[10:06:20] /usr/bin/whatis                                   [ OK ]
[10:06:20] /usr/bin/whereis                                  [ Warning ]
[10:06:20] Warning: The file properties have changed:
[10:06:20]          File: /usr/bin/whereis
[10:06:20]          Current inode: 13207467    Stored inode: 13205981
[10:06:20]          Current file modification time: 1208230606
[10:06:20]          Stored file modification time : 1207985053
[10:06:20] /usr/bin/which                                    [ OK ]
[10:06:20] /usr/bin/who                                      [ OK ]
[10:06:20] /usr/bin/whoami                                   [ OK ]
[10:06:20] /usr/bin/gawk                                     [ OK ]
[10:06:20] /usr/bin/lwp-request                              [ OK ]
[10:06:20] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[10:06:21] /usr/bin/w.procps                                 [ OK ]
[10:06:21] /sbin/depmod                                      [ OK ]
[10:06:21] /sbin/ifconfig                                    [ OK ]
[10:06:21] /sbin/ifdown                                      [ OK ]
[10:06:21] /sbin/ifup                                        [ OK ]
[10:06:21] /sbin/init                                        [ OK ]
[10:06:21] /sbin/insmod                                      [ OK ]
[10:06:21] /sbin/ip                                          [ OK ]
[10:06:22] /sbin/lsmod                                       [ OK ]
[10:06:22] /sbin/modinfo                                     [ OK ]
[10:06:22] /sbin/modprobe                                    [ OK ]
[10:06:22] /sbin/rmmod                                       [ OK ]
[10:06:22] /sbin/runlevel                                    [ OK ]
[10:06:22] /sbin/sulogin                                     [ Warning ]
[10:06:22] Warning: The file properties have changed:
[10:06:22]          File: /sbin/sulogin
[10:06:22]          Current inode: 1032204    Stored inode: 1032220
[10:06:22]          Current file modification time: 1208179886
[10:06:22]          Stored file modification time : 1207228933
[10:06:22] /sbin/sysctl                                      [ OK ]
[10:06:23] /sbin/syslogd                                     [ OK ]
[10:06:23] /usr/sbin/adduser                                 [ OK ]
[10:06:23] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[10:06:23] /usr/sbin/chroot                                  [ OK ]
[10:06:23] /usr/sbin/cron                                    [ OK ]
[10:06:23] /usr/sbin/groupadd                                [ OK ]
[10:06:23] /usr/sbin/groupdel                                [ OK ]
[10:06:23] /usr/sbin/groupmod                                [ OK ]
[10:06:24] /usr/sbin/grpck                                   [ OK ]
[10:06:24] /usr/sbin/nologin                                 [ OK ]
[10:06:24] /usr/sbin/pwck                                    [ OK ]
[10:06:24] /usr/sbin/tcpd                                    [ OK ]
[10:06:24] /usr/sbin/useradd                                 [ OK ]
[10:06:24] /usr/sbin/userdel                                 [ OK ]
[10:06:25] /usr/sbin/usermod                                 [ OK ]
[10:06:25] /usr/sbin/vipw                                    [ OK ]
[10:06:41]
[10:06:41] Checking for rootkits...
[10:06:41] Info: Starting test name 'rootkits'
[10:06:41]
[10:06:41] Performing check of known rootkit files and directories
[10:06:41] Info: Starting test name 'known_rkts'
[10:06:41]
[10:06:41] Checking for 55808 Trojan - Variant A...
[10:06:41]   Checking for file '/tmp/.../r'                  [ Not found ]
[10:06:41]   Checking for file '/tmp/.../a'                  [ Not found ]
[10:06:41] 55808 Trojan - Variant A                          [ Not found ]
[10:06:41]
[10:06:41] Checking for ADM Worm...
[10:06:41]   Checking for string 'w0rm'                      [ Not found ]
[10:06:41] ADM Worm                                          [ Not found ]
[10:06:41]
[10:06:41] Checking for AjaKit Rootkit...
[10:06:41]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:06:41]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:06:41]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:06:41]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[10:06:41]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[10:06:41]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[10:06:41]   Checking for directory '/dev/tux'               [ Not found ]
[10:06:41]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[10:06:41] AjaKit Rootkit                                    [ Not found ]
[10:06:41]
[10:06:41] Checking for aPa Kit...
[10:06:41]   Checking for file '/usr/share/.aPa'             [ Not found ]
[10:06:41] aPa Kit                                           [ Not found ]
[10:06:41]
[10:06:41] Checking for Apache Worm...
[10:06:41]   Checking for file '/bin/.log'                   [ Not found ]
[10:06:41] Apache Worm                                       [ Not found ]
[10:06:41]
[10:06:41] Checking for Ambient (ark) Rootkit...
[10:06:41]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[10:06:41]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[10:06:41]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[10:06:41]   Checking for directory '/dev/ptyxx'             [ Not found ]
[10:06:41] Ambient (ark) Rootkit                             [ Not found ]
[10:06:41]
[10:06:41] Checking for Balaur Rootkit...
[10:06:41]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[10:06:41]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[10:06:41]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[10:06:41]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[10:06:42] Balaur Rootkit                                    [ Not found ]
[10:06:42]
[10:06:42] Checking for BeastKit Rootkit...
[10:06:42]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[10:06:42]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[10:06:42]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[10:06:42] BeastKit Rootkit                                  [ Not found ]
[10:06:42]
[10:06:42] Checking for beX2 Rootkit...
[10:06:42]   Checking for directory '/usr/include/bex'       [ Not found ]
[10:06:42] beX2 Rootkit                                      [ Not found ]
[10:06:42]
[10:06:42] Checking for BOBKit Rootkit...
[10:06:42]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../find'           [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../du'             [ Not found ]
[10:06:42]   Checking for file '/usr/lib/.../top'            [ Not found ]
[10:06:42]   Checking for directory '/usr/lib/...'           [ Not found ]
[10:06:42]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[10:06:42]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[10:06:42]   Checking for directory '/tmp/.bkp'              [ Not found ]
[10:06:42] BOBKit Rootkit                                    [ Not found ]
[10:06:42]
[10:06:42] Checking for CiNIK Worm (Slapper.B variant)...
[10:06:42]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:06:43]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[10:06:43] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[10:06:43]
[10:06:43] Checking for Danny-Boy's Abuse Kit...
[10:06:43]   Checking for file '/dev/mdev'                   [ Not found ]
[10:06:43]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[10:06:43] Danny-Boy's Abuse Kit                             [ Not found ]
[10:06:43]
[10:06:43] Checking for Devil RootKit...
[10:06:43]   Checking for file '/var/lib/games/.src'         [ Not found ]
[10:06:43]   Checking for file '/dev/dsx'                    [ Not found ]
[10:06:43]   Checking for file '/dev/caca'                   [ Not found ]
[10:06:43] Devil RootKit                                     [ Not found ]
[10:06:43]
[10:06:43] Checking for Dica-Kit Rootkit...
[10:06:43]   Checking for file '/lib/.sso'                   [ Not found ]
[10:06:43]   Checking for file '/lib/.so'                    [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/va'         [ Not found ]
[10:06:43]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[10:06:43]   Checking for file '/usr/bin/.etc'               [ Not found ]
[10:06:43]   Checking for directory '/var/run/...dica'       [ Not found ]
[10:06:43]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[10:06:43]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[10:06:43] Dica-Kit Rootkit                                  [ Not found ]
[10:06:43]
[10:06:43] Checking for Dreams Rootkit...
[10:06:43]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:06:43]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:06:43]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:06:43]   Checking for file '/usr/bin/sense'              [ Not found ]
[10:06:43]   Checking for file '/usr/bin/sl2'                [ Not found ]
[10:06:43]   Checking for file '/usr/bin/logclear'           [ Not found ]
[10:06:43]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[10:06:43]   Checking for file '/usr/bin/snfs'               [ Not found ]
[10:06:43]   Checking for file '/usr/lib/libsss'             [ Not found ]
[10:06:43]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[10:06:43] Dreams Rootkit                                    [ Not found ]
[10:06:43]
[10:06:43] Checking for Duarawkz Rootkit...
[10:06:44]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[10:06:44]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[10:06:44] Duarawkz Rootkit                                  [ Not found ]
[10:06:44]
[10:06:44] Checking for Enye LKM...
[10:06:44]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[10:06:44] Enye LKM                                          [ Not found ]
[10:06:44]
[10:06:44] Checking for Flea Linux Rootkit...
[10:06:44]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:06:44]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[10:06:44]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[10:06:44]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[10:06:44]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:06:44]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[10:06:44]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[10:06:44]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[10:06:44]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[10:06:44]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:06:44]   Checking for directory '/dev/..0'               [ Not found ]
[10:06:44]   Checking for directory '/dev/..0/backup'        [ Not found ]
[10:06:44] Flea Linux Rootkit                                [ Not found ]
[10:06:44]
[10:06:44] Checking for FreeBSD Rootkit...
[10:06:44]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[10:06:44]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[10:06:44]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[10:06:44]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[10:06:44]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[10:06:44]   Checking for file '/bin/sysback'                [ Not found ]
[10:06:44]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[10:06:44]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[10:06:44]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[10:06:44] FreeBSD Rootkit                                   [ Not found ]
[10:06:44]
[10:06:44] Checking for ****`it Rootkit...
[10:06:44]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[10:06:44]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[10:06:45]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[10:06:45] ****`it Rootkit                                   [ Not found ]
[10:06:45]
[10:06:45] Checking for GasKit Rootkit...
[10:06:45]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[10:06:45]   Checking for directory '/dev/dev'               [ Not found ]
[10:06:45]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[10:06:45]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[10:06:45] GasKit Rootkit                                    [ Not found ]
[10:06:45]
[10:06:45] Checking for Heroin LKM...
[10:06:45]   Checking for kernel symbol 'heroin'             [ Not found ]
[10:06:45] Heroin LKM                                        [ Not found ]
[10:06:45]
[10:06:45] Checking for HjC Kit...
[10:06:45]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[10:06:45] HjC Kit                                           [ Not found ]
[10:06:45]
[10:06:45] Checking for ignoKit Rootkit...
[10:06:45]   Checking for file '/lib/defs/p'                 [ Not found ]
[10:06:45]   Checking for file '/lib/defs/q'                 [ Not found ]
[10:06:45]   Checking for file '/lib/defs/r'                 [ Not found ]
[10:06:45]   Checking for file '/lib/defs/s'                 [ Not found ]
[10:06:45]   Checking for file '/lib/defs/t'                 [ Not found ]
[10:06:45]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[10:06:45]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[10:06:45]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[10:06:45]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[10:06:45]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[10:06:45]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[10:06:45]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[10:06:45]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[10:06:45]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[10:06:45] ignoKit Rootkit                                   [ Not found ]
[10:06:45]
[10:06:45] Checking for ImperalsS-FBRK Rootkit...
[10:06:45]   Checking for directory '/dev/fd/.88'            [ Not found ]
[10:06:45]   Checking for directory '/dev/fd/.99'            [ Not found ]
[10:06:45] ImperalsS-FBRK Rootkit                            [ Not found ]
[10:06:45]
[10:06:45] Checking for Irix Rootkit...
[10:06:45]   Checking for directory '/dev/pts/01'            [ Not found ]
[10:06:45]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[10:06:45]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[10:06:46]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[10:06:46] Irix Rootkit                                      [ Not found ]
[10:06:46]
[10:06:46] Checking for Kitko Rootkit...
[10:06:46]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[10:06:46] Kitko Rootkit                                     [ Not found ]
[10:06:46]
[10:06:46] Checking for Knark Rootkit...
[10:06:46]   Checking for file '/proc/knark/pids'            [ Not found ]
[10:06:46]   Checking for directory '/proc/knark'            [ Not found ]
[10:06:46] Knark Rootkit                                     [ Not found ]
[10:06:46]
[10:06:46] Checking for Li0n Worm...
[10:06:46]   Checking for file '/bin/in.telnetd'             [ Not found ]
[10:06:46]   Checking for file '/bin/mjy'                    [ Not found ]
[10:06:46]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[10:06:46]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[10:06:46]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[10:06:46]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[10:06:46] Li0n Worm                                         [ Not found ]
[10:06:46]
[10:06:46] Checking for Lockit / LJK2 Rootkit...
[10:06:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[10:06:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[10:06:47]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[10:06:47]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[10:06:47] Lockit / LJK2 Rootkit                             [ Not found ]
[10:06:47]
[10:06:47] Checking for Mood-NT Rootkit...
[10:06:47]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[10:06:47]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[10:06:47]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[10:06:47]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[10:06:47]   Checking for directory '/_cthulhu'              [ Not found ]
[10:06:47] Mood-NT Rootkit                                   [ Not found ]
[10:06:48]
[10:06:48] Checking for MRK Rootkit...
[10:06:48]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[10:06:48]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[10:06:48]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[10:06:48]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[10:06:48]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[10:06:48]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[10:06:48] MRK Rootkit                                       [ Not found ]
[10:06:48]
[10:06:48] Checking for Ni0 Rootkit...
[10:06:48]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[10:06:48]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[10:06:48]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[10:06:48]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[10:06:48]   Checking for directory '/tmp/waza'              [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:06:48]   Checking for directory '/usr/sbin/es'           [ Not found ]
[10:06:48] Ni0 Rootkit                                       [ Not found ]
[10:06:48]
[10:06:48] Checking for Ohhara Rootkit...
[10:06:48]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[10:06:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[10:06:48] Ohhara Rootkit                                    [ Not found ]
[10:06:48]
[10:06:48] Checking for Optic Kit (Tux) Worm...
[10:06:48]   Checking for directory '/dev/tux'               [ Not found ]
[10:06:48]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[10:06:48]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[10:06:48]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[10:06:48] Optic Kit (Tux) Worm                              [ Not found ]
[10:06:48]
[10:06:48] Checking for Oz Rootkit...
[10:06:48]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[10:06:48]   Checking for directory '/dev/.oz'               [ Not found ]
[10:06:48] Oz Rootkit                                        [ Not found ]
[10:06:48]
[10:06:48] Checking for Phalanx Rootkit...
[10:06:48]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[10:06:48]   Checking for file '/etc/host.ph1'               [ Not found ]
[10:06:49]   Checking for file '/bin/host.ph1'               [ Not found ]
[10:06:49]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[10:06:49]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[10:06:49] Phalanx Rootkit                                   [ Not found ]
[10:06:49]
[10:06:49] Checking for Phalanx Rootkit (strings)...
[10:06:49]   Checking for string 'phalanx'                   [ Not found ]
[10:06:49] Phalanx Rootkit (strings)                         [ Not found ]
[10:06:49]
[10:06:49] Checking for Portacelo Rootkit...
[10:06:49]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../.p'             [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../getty'          [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../show'           [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[10:06:49]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[10:06:49]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[10:06:49] Portacelo Rootkit                                 [ Not found ]
[10:06:49]
[10:06:49] Checking for R3dstorm Toolkit...
[10:06:49]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[10:06:49]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[10:06:49]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[10:06:49]   Checking for file '/bin/.../see_all'            [ Not found ]
[10:06:49]   Checking for directory '/var/log/tk02'          [ Not found ]
[10:06:49]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[10:06:49]   Checking for directory '/bin/...'               [ Not found ]
[10:06:49] R3dstorm Toolkit                                  [ Not found ]
[10:06:49]
[10:06:49] Checking for RH-Sharpe's Rootkit...
[10:06:49]   Checking for file '/bin/lps'                    [ Not found ]
[10:06:49]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[10:06:49]   Checking for file '/usr/bin/ltop'               [ Not found ]
[10:06:49]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[10:06:49]   Checking for file '/usr/bin/ldu'                [ Not found ]
[10:06:49]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[10:06:49]   Checking for file '/usr/bin/wp'                 [ Not found ]
[10:06:49]   Checking for file '/usr/bin/shad'               [ Not found ]
[10:06:50]   Checking for file '/usr/bin/vadim'              [ Not found ]
[10:06:50]   Checking for file '/usr/bin/slice'              [ Not found ]
[10:06:50]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[10:06:50]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[10:06:50] RH-Sharpe's Rootkit                               [ Not found ]
[10:06:50]
[10:06:50] Checking for RSHA's Rootkit...
[10:06:50]   Checking for file '/bin/kr4p'                   [ Not found ]
[10:06:50]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[10:06:50]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[10:06:50]   Checking for file '/usr/bin/slice2'             [ Not found ]
[10:06:50]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[10:06:50]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[10:06:50]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[10:06:50]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[10:06:50] RSHA's Rootkit                                    [ Not found ]
[10:06:50]
[10:06:50] Checking for Scalper Worm...
[10:06:50]   Checking for file '/tmp/.a'                     [ Not found ]
[10:06:50]   Checking for file '/tmp/.uua'                   [ Not found ]
[10:06:50] Scalper Worm                                      [ Not found ]
[10:06:50]
[10:06:50] Checking for Sebek LKM...
[10:06:50]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[10:06:50] Sebek LKM                                         [ Not found ]
[10:06:50]
[10:06:50] Checking for Shutdown Rootkit...
[10:06:50]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[10:06:50]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[10:06:50]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[10:06:51]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[10:06:51]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[10:06:51]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[10:06:51]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[10:06:51]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[10:06:51] Shutdown Rootkit                                  [ Not found ]
[10:06:51]
[10:06:51] Checking for SHV4 Rootkit...
[10:06:51]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:06:51]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:06:51]   Checking for file '/lib/lidps1.so'              [ Not found ]
[10:06:51]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[10:06:51]   Checking for directory '/lib/security/.config'  [ Not found ]
[10:06:51]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:06:51] SHV4 Rootkit                                      [ Not found ]
[10:06:51]
[10:06:51] Checking for SHV5 Rootkit...
[10:06:51]   Checking for file '/etc/sh.conf'                [ Not found ]
[10:06:51]   Checking for file '/dev/srd0'                   [ Not found ]
[10:06:51]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[10:06:51] SHV5 Rootkit                                      [ Not found ]
[10:06:51]
[10:06:51] Checking for Sin Rootkit...
[10:06:51]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[10:06:51]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:06:51]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:06:51]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:06:51]   Checking for file '/dev/ttyos'                  [ Not found ]
[10:06:51]   Checking for file '/usr/lib/.lib'               [ Not found ]
[10:06:51]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[10:06:51]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[10:06:51]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[10:06:51]   Checking for file '/usr/man/man1/...'           [ Not found ]
[10:06:51]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[10:06:51]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[10:06:51]   Checking for directory '/usr/lib/sn'            [ Not found ]
[10:06:51]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[10:06:51]   Checking for directory '/dev/.haos'             [ Not found ]
[10:06:51] Sin Rootkit                                       [ Not found ]
[10:06:51]
[10:06:51] Checking for Slapper Worm...
[10:06:51]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[10:06:51]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[10:06:52]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[10:06:52]   Checking for file '/tmp/httpd'                  [ Not found ]
[10:06:52]   Checking for file '/tmp/.unlock'                [ Not found ]
[10:06:52]   Checking for file '/tmp/update'                 [ Not found ]
[10:06:52]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:06:52]   Checking for file '/tmp/.b'                     [ Not found ]
[10:06:52] Slapper Worm                                      [ Not found ]
[10:06:52]
[10:06:52] Checking for Sneakin Rootkit...
[10:06:52]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[10:06:52] Sneakin Rootkit                                   [ Not found ]
[10:06:52]
[10:06:52] Checking for Suckit Rootkit...
[10:06:52]   Checking for file '/sbin/initsk12'              [ Not found ]
[10:06:52]   Checking for file '/sbin/initxrk'               [ Not found ]
[10:06:52]   Checking for file '/usr/bin/null'               [ Not found ]
[10:06:52]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[10:06:52]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[10:06:52]   Checking for directory '/etc/.MG'               [ Not found ]
[10:06:52]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[10:06:52]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[10:06:52] Suckit Rootkit                                    [ Not found ]
[10:06:52]
[10:06:52] Checking for SunOS Rootkit...
[10:06:52]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:06:52]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:06:52]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:06:52]   Checking for file '/bin/xlogin'                 [ Not found ]
[10:06:52]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[10:06:52]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[10:06:52]   Checking for file '/sbin/login'                 [ Not found ]
[10:06:52]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[10:06:53]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[10:06:53]   Checking for file '/dev/kmod'                   [ Not found ]
[10:06:53]   Checking for file '/dev/dos'                    [ Not found ]
[10:06:53] SunOS Rootkit                                     [ Not found ]
[10:06:53]
[10:06:53] Checking for SunOS / NSDAP Rootkit...
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[10:06:53]   Checking for file '/usr/lib/lpset'              [ Not found ]
[10:06:53]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[10:06:53] SunOS / NSDAP Rootkit                             [ Not found ]
[10:06:53]
[10:06:53] Checking for Superkit Rootkit...
[10:06:53]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[10:06:53] Superkit Rootkit                                  [ Not found ]
[10:06:53]
[10:06:53] Checking for TBD (Telnet BackDoor)...
[10:06:53]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[10:06:53] TBD (Telnet BackDoor)                             [ Not found ]
[10:06:53]
[10:06:53] Checking for TeLeKiT Rootkit...
[10:06:53]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[10:06:53]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[10:06:53]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[10:06:53]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[10:06:53]   Checking for file '/dev/ptyr'                   [ Not found ]
[10:06:53]   Checking for file '/dev/ptyp'                   [ Not found ]
[10:06:53]   Checking for file '/dev/ptyq'                   [ Not found ]
[10:06:53]   Checking for file '/dev/hda06'                  [ Not found ]
[10:06:53]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[10:06:53]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[10:06:53]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[10:06:53]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[10:06:53] TeLeKiT Rootkit                                   [ Not found ]
[10:06:53]
[10:06:53] Checking for T0rn Rootkit...
[10:06:54]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[10:06:54]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[10:06:54]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[10:06:54]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[10:06:54]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[10:06:54]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[10:06:54]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[10:06:54]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[10:06:54]   Checking for directory '/dev/.lib'              [ Not found ]
[10:06:54]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[10:06:54]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[10:06:54]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[10:06:54]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[10:06:54]   Checking for directory '/usr/src/.****'         [ Not found ]
[10:06:54]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[10:06:54]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[10:06:54]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[10:06:54]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[10:06:54] T0rn Rootkit                                      [ Not found ]
[10:06:55]
[10:06:55] Checking for Trojanit Kit...
[10:06:55]   Checking for file '/bin/.ls'                    [ Not found ]
[10:06:55]   Checking for file '/bin/.ps'                    [ Not found ]
[10:06:55]   Checking for file '/bin/.netstat'               [ Not found ]
[10:06:55]   Checking for file '/usr/bin/.nop'               [ Not found ]
[10:06:55]   Checking for file '/usr/bin/.who'               [ Not found ]
[10:06:55] Trojanit Kit                                      [ Not found ]
[10:06:55]
[10:06:55] Checking for Tuxtendo Rootkit...
[10:06:55]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:06:55]   Checking for file '/dev/tux/.cron'              [ Not found ]
[10:06:55]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:06:55]   Checking for file '/dev/tux/.log'               [ Not found ]
[10:06:55]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[10:06:55]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[10:06:55]   Checking for directory '/dev/tux'               [ Not found ]
[10:06:55]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[10:06:55]   Checking for directory '/dev/tux/backup'        [ Not found ]
[10:06:55] Tuxtendo Rootkit                                  [ Not found ]
[10:06:55]
[10:06:55] Checking for URK Rootkit...
[10:06:55]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[10:06:55]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[10:06:55]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[10:06:55]   Checking for file '/tmp/conf.inf'               [ Not found ]
[10:06:55]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[10:06:55] URK Rootkit                                       [ Not found ]
[10:06:55]
[10:06:55] Checking for VcKit Rootkit...
[10:06:55]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[10:06:56]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[10:06:56] VcKit Rootkit                                     [ Not found ]
[10:06:56]
[10:06:56] Checking for Volc Rootkit...
[10:06:56]   Checking for directory '/var/spool/.recent'     [ Not found ]
[10:06:56]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[10:06:56]   Checking for directory '/usr/lib/volc'          [ Not found ]
[10:06:56]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[10:06:56] Volc Rootkit                                      [ Not found ]
[10:06:56]
[10:06:56] Checking for X-Org SunOS Rootkit...
[10:06:56]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[10:06:56]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[10:06:56]   Checking for file '/usr/bin/srload'             [ Not found ]
[10:06:56]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[10:06:56]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[10:06:56]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[10:06:56]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[10:06:56]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[10:06:56]   Checking for directory '/usr/share/man...'      [ Not found ]
[10:06:56] X-Org SunOS Rootkit                               [ Not found ]
[10:06:56]
[10:06:56] Checking for zaRwT.KiT Rootkit...
[10:06:56]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[10:06:56]   Checking for file '/dev/ttyf'                   [ Not found ]
[10:06:56]   Checking for file '/dev/ttyp'                   [ Not found ]
[10:06:56]   Checking for file '/dev/ttyn'                   [ Not found ]
[10:06:56]   Checking for file '/rk/tulz'                    [ Not found ]
[10:06:56]   Checking for directory '/rk'                    [ Not found ]
[10:06:56]   Checking for directory '/dev/rd/s'              [ Not found ]
[10:06:56] zaRwT.KiT Rootkit                                 [ Not found ]
[10:06:56]
[10:06:56] Performing additional rootkit checks
[10:06:56] Info: Starting test name 'additional_rkts'
[10:06:56]
[10:06:56]   Performing Suckit Rookit additional checks
[10:06:56]     Checking /sbin/init link count                [ OK ]
[10:06:56]     Checking for hidden file extensions           [ None found ]
[10:06:56]     Running skdet command                         [ Skipped ]
[10:06:56] Info: Unable to find the 'skdet' command
[10:06:56]   Suckit Rookit additional checks                 [ OK ]
[10:06:57]
[10:06:57]   Performing check of possible rootkit files and directories
[10:06:57] Info: Starting test name 'possible_rkt_files'
[10:06:57]     Checking for file '/dev/sdr0'                 [ Not found ]
[10:06:57]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[10:06:57]     Checking for file '/tmp/.bash_history'        [ Not found ]
[10:06:57]     Checking for file '/usr/info/.clib'           [ Not found ]
[10:06:57]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[10:06:57]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[10:06:57]     Checking for file '/sbin/create'              [ Not found ]
[10:06:57]     Checking for file '/dev/ttypz'                [ Not found ]
[10:06:57]     Checking for directory '/usr/bin/take'        [ Not found ]
[10:06:57]     Checking for directory '/usr/src/.lib'        [ Not found ]
[10:06:57]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[10:06:57]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[10:06:57]     Checking for directory '/usr/sbin/...'        [ Not found ]
[10:06:57]     Checking for directory '/usr/share/.gun'      [ Not found ]
[10:06:57]   Checking for possible rootkit files and directories [ None found ]
[10:06:57]
[10:06:57]   Performing check for possible rootkit strings
[10:06:57] Info: Starting test name 'possible_rkt_strings'
[10:06:57] Info: Found local startup file: /etc/rc.local
[10:06:57]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:06:57]     Checking for string '****'                    [ Not found ]
[10:06:57]     Checking for string 'backdoor'                [ Not found ]
[10:06:57]     Checking for string 'vt200'                   [ Not found ]
[10:06:57]     Checking for string '/usr/bin/xstat'          [ Not found ]
[10:06:57]     Checking for string '/bin/envpc'              [ Not found ]
[10:06:58]     Checking for string 'L4m3r0x'                 [ Not found ]
[10:06:58]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:06:58]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[10:06:58]     Checking for string '/dev/sgk'                [ Not found ]
[10:06:58]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:06:58]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:06:58]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:06:58]     Checking for string '/lib/.sso'               [ Not found ]
[10:06:58]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:06:58]     Checking for string '/dev/caca'               [ Not found ]
[10:06:58]     Checking for string '/dev/ttyoa'              [ Not found ]
[10:06:58]     Checking for string 'syg'                     [ Not found ]
[10:06:58]     Checking for string '/dev/pts/01'             [ Not found ]
[10:06:58]     Checking for string 'tw33dl3'                 [ Not found ]
[10:06:58]     Checking for string 'psniff'                  [ Not found ]
[10:06:58]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:06:58]     Checking for string 'promiscuous'             [ Not found ]
[10:06:58]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:06:58]     Checking for string '/dev/xdta'               [ Not found ]
[10:06:58]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:06:58]     Checking for string 'in.inetd'                [ Not found ]
[10:06:58]     Checking for string '#<HIDE_.*>'              [ Not found ]
[10:06:58]     Checking for string 'bin/xchk'                [ Not found ]
[10:06:59]     Checking for string 'bin/xsf'                 [ Not found ]
[10:06:59]   Checking for possible rootkit strings           [ None found ]
[10:06:59]
[10:06:59] Performing malware checks
[10:06:59] Info: Starting test name 'malware'
[10:06:59]
[10:06:59] Info: Test 'deleted_files' disabled at users request.
[10:06:59] Info: Starting test name 'running_procs'
[10:06:59]   Checking running processes for suspicious files [ None found ]
[10:06:59]
[10:06:59] Info: Test 'hidden_procs' disabled at users request.
[10:06:59]
[10:06:59] Info: Test 'suspscan' disabled at users request.
[10:06:59]
[10:06:59]   Performing check for login backdoors
[10:06:59] Info: Starting test name 'other_malware'
[10:06:59]     Checking for '/bin/.login'                    [ Not found ]
[10:06:59]     Checking for '/sbin/.login'                   [ Not found ]
[10:06:59]   Checking for login backdoors                    [ None found ]
[10:06:59]
[10:06:59]   Performing check for suspicious directories
[10:06:59]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[10:06:59]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[10:06:59]   Checking for suspicious directories             [ None found ]
[10:06:59]
[10:06:59]   Checking for software intrusions                [ Skipped ]
[10:06:59] Info: Check skipped - tripwire not installed
[10:06:59]
[10:06:59]   Performing check for sniffer log files
[10:06:59]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[10:06:59]   Checking for sniffer log files                  [ None found ]
[10:06:59]
[10:06:59] Performing trojan specific checks
[10:06:59] Info: Starting test name 'trojans'
[10:06:59] Info: Using inetd configuration file '/etc/inetd.conf'
[10:06:59]   Checking for enabled inetd services             [ OK ]
[10:06:59]
[10:06:59]   Performing check for enabled xinetd services
[10:06:59]   Checking for enabled xinetd services            [ Skipped ]
[10:06:59] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[10:06:59] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[10:06:59]
[10:06:59] Performing Linux specific checks
[10:06:59] Info: Starting test name 'os_specific'
[10:06:59]   Checking kernel module commands                 [ OK ]
[10:07:00] Info: Using modules pathname of '/lib/modules/2.6.24-16-generic'
[10:07:02]   Checking kernel module names                    [ OK ]
[10:07:27]
[10:07:27] Checking the network...
[10:07:27] Info: Starting test name 'network'
[10:07:27] Info: Starting test name 'ports'
[10:07:27]
[10:07:27] Performing check for backdoor ports
[10:07:28]   Checking for UDP port 2001                      [ Not found ]
[10:07:28]   Checking for TCP port 2006                      [ Not found ]
[10:07:28]   Checking for TCP port 2128                      [ Not found ]
[10:07:28]   Checking for TCP port 14856                     [ Not found ]
[10:07:28]   Checking for TCP port 47107                     [ Not found ]
[10:07:28]   Checking for TCP port 60922                     [ Not found ]
[10:07:28]
[10:07:28] Performing checks on the network interfaces
[10:07:28] Info: Starting test name 'promisc'
[10:07:28]   Checking for promiscuous interfaces             [ None found ]
[10:07:28]
[10:07:28] Info: Test 'packet_cap_apps' disabled at users request.
[10:07:33]
[10:07:33] Checking the local host...
[10:07:33] Info: Starting test name 'local_host'
[10:07:33]
[10:07:33] Performing system boot checks
[10:07:33] Info: Starting test name 'startup_files'
[10:07:33]   Checking for local host name                    [ Found ]
[10:07:33] Info: Starting test name 'startup_malware'
[10:07:33] Info: Found local startup file: /etc/rc.local
[10:07:33]   Checking for local startup files                [ Found ]
[10:07:33]   Checking local startup files for malware        [ None found ]
[10:07:33] Info: Found system startup directory: /etc/init.d
[10:07:34]   Checking system startup files for malware       [ None found ]
[10:07:34]
[10:07:34] Performing group and account checks
[10:07:34] Info: Starting test name 'group_accounts'
[10:07:34]   Checking for passwd file                        [ Found ]
[10:07:34] Info: Found password file: /etc/passwd
[10:07:34]   Checking for root equivalent (UID 0) accounts   [ None found ]
[10:07:34] Info: Found shadow file: /etc/shadow
[10:07:34]   Checking for passwordless accounts              [ None found ]
[10:07:35] Info: Starting test name 'passwd_changes'
[10:07:35]   Checking for passwd file changes                [ None found ]
[10:07:35] Info: Starting test name 'group_changes'
[10:07:35]   Checking for group file changes                 [ None found ]
[10:07:35]   Checking root account shell history files       [ None found ]
[10:07:35]
[10:07:35] Performing system configuration file checks
[10:07:35] Info: Starting test name 'system_configs'
[10:07:35]   Checking for SSH configuration file             [ Not found ]
[10:07:35]   Checking for running syslog daemon              [ Found ]
[10:07:35]   Checking for syslog configuration file          [ Found ]
[10:07:35] Info: Found syslog configuration file: /etc/syslog.conf
[10:07:35]   Checking if syslog remote logging is allowed    [ Not allowed ]
[10:07:35]
[10:07:35] Performing filesystem checks
[10:07:35] Info: Starting test name 'filesystem'
[10:07:35] Info: SCAN_MODE_DEV set to 'THOROUGH'
[10:07:45]   Checking /dev for suspicious file types         [ Warning ]
[10:07:45] Warning: Suspicious file types found in /dev:
[10:07:45]          /dev/shm/pulse-shm-4147962494: data
[10:07:46]   Checking for hidden files and directories       [ Warning ]
[10:07:46] Warning: Hidden directory found: /dev/.static
[10:07:46] Warning: Hidden directory found: /dev/.udev
[10:07:46] Warning: Hidden directory found: /dev/.initramfs
[10:07:48]
[10:07:48] Checking application versions...
[10:07:48] Info: Starting test name 'apps'
[10:07:48]   Checking version of Exim MTA                    [ OK ]
[10:07:49] Info: Application 'exim' version '4.69' found.
[10:07:49]   Checking version of GnuPG                       [ OK ]
[10:07:49] Info: Application 'gpg' version '1.4.6' found.
[10:07:49] Info: Application 'httpd' not found.
[10:07:49] Info: Application 'named' not found.
[10:07:49]   Checking version of OpenSSL                     [ OK ]
[10:07:49] Info: Application 'openssl' version '0.9.8g' found.
[10:07:49] Info: Application 'php' not found.
[10:07:49] Info: Application 'procmail' not found.
[10:07:49] Info: Application 'proftpd' not found.
[10:07:49] Info: Application 'sshd' not found.
[10:07:49] Info: Applications checked: 3 out of 9
[10:07:49]
[10:07:49] System checks summary
[10:07:49] =====================
[10:07:49]
[10:07:49] File properties checks...
[10:07:49] Required commands check failed
[10:07:49] Files checked: 122
[10:07:49] Suspect files: 8
[10:07:49]
[10:07:49] Rootkit checks...
[10:07:49] Rootkits checked : 109
[10:07:49] Possible rootkits: 0
[10:07:49]
[10:07:49] Applications checks...
[10:07:49] Applications checked: 3
[10:07:49] Suspect applications: 0
[10:07:49]
[10:07:49] The system checks took: 1 minute and 42 seconds
[10:07:49]
[10:07:49] Info: End date is Tue Apr 15 10:07:49 CDT 2008

---

### Post by The Tronyx on 2008-04-16
My first concern is that rkhunter is not terribly authoritative.

Secondly, to make it easier for reading, in the future please use code tags or pastebin when you have a massive amount of data to give us.

Sometimes distros upgrade frequently used binaries like `ls` and `ps`. When you run rkhunter, it might not be aware of these newly changed and updated files and as a result may return some false positives or warnings.

---

### Post by moonpup on 2008-04-16
Here's a tip when using rkhunter... use the pkgmgr flag. This will use the distribution's package manager for verification.

ubuntu example:

sudo rkhunter --check --pkgmgr dpkg

redhat example:

rkhunter --check --pkgmgr rpm

just run rkhunter with no flags to see all the options available.

---

### Post by pedja_portugalac on 2008-04-29
> **moonpup said:**
> Here's a tip when using rkhunter... use the pkgmgr flag. This will use the distribution's package manager for verification.

ubuntu example:

sudo rkhunter --check --pkgmgr dpkg

Still have this warning **/dev/shm/pulse-shm-3801237314** :sad:

---

### Post by say2sky on 2008-06-02
> **2point0 said:**
> My first concern is that rkhunter is not terribly authoritative.

Secondly, to make it easier for reading, in the future please use code tags or pastebin when you have a massive amount of data to give us.

Sometimes distros upgrade frequently used binaries like `ls` and `ps`. When you run rkhunter, it might not be aware of these newly changed and updated files and as a result may return some false positives or warnings.

Is there some way which can be used to confirm these warning is harmless.
In my hardy system all 126 files checked is showed with warning. :confused:

> 
[11:00:00] System checks summary
[11:00:00] =====================
[11:00:00]
[11:00:00] File properties checks...
[11:00:00] Files checked: 126
[11:00:00] Suspect files: 126
[11:00:00]
[11:00:00] Rootkit checks...
[11:00:00] Rootkits checked : 109
[11:00:00] Possible rootkits: 0
[11:00:00]
[11:00:00] Applications checks...
[11:00:00] Applications checked: 3
[11:00:00] Suspect applications: 0



---

