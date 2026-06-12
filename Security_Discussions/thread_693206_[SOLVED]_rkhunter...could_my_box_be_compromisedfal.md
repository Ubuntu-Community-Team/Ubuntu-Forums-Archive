---
title: "[SOLVED] rkhunter...could my box be compromised?false positive?"
date: 2008-02-10
forum: Security Discussions
---

### Post by cgr1fatboyslim on 2008-02-10
Hi all,

just some what worried with rkhunter output.....
....binaries that changed are 

/usr/bin/chattr
/usr/bin/find
/usr/bin/lsattr
/usr/bin/perl

also some hidden directories found....
....any sound advice?

**************************************************************
This is the rkhunter log file output
**************************************************************

```
 [00:33:33] Running Rootkit Hunter version 1.3.0 on xxxxxxxxxxx
[00:33:33]
[00:33:33] Info: Start date is Mon Feb 11 00:33:33 PHT 2008
[00:33:33]
[00:33:33] Checking configuration file and command-line options...
[00:33:33] Info: Detected operating system is 'Linux'
[00:33:33] Info: Found O/S name: Ubuntu 7.10
[00:33:33] Info: Command line is /usr/bin/rkhunter --checkall
[00:33:33] Info: Environment shell is /bin/bash; rkhunter is using dash
[00:33:33] Info: Using configuration file '/etc/rkhunter.conf'
[00:33:33] Info: Installation directory is '/usr'
[00:33:34] Info: Using language 'en'
[00:33:34] Info: Using '/var/lib/rkhunter/db' as the database directory
[00:33:34] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[00:33:34] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[00:33:34] Info: Using '/' as the root directory
[00:33:34] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[00:33:34] Info: No mail-on-warning address configured
[00:33:34] Info: X will automatically be detected
[00:33:34] Info: Found the 'diff' command: /usr/bin/diff
[00:33:34] Info: Found the 'file' command: /usr/bin/file
[00:33:34] Info: Found the 'find' command: /usr/bin/find
[00:33:34] Info: Found the 'ifconfig' command: /sbin/ifconfig
[00:33:34] Info: Found the 'ip' command: /sbin/ip
[00:33:34] Info: Found the 'ldd' command: /usr/bin/ldd
[00:33:34] Info: Found the 'lsattr' command: /usr/bin/lsattr
[00:33:34] Info: Found the 'lsmod' command: /sbin/lsmod
[00:33:34] Info: Found the 'lsof' command: /usr/bin/lsof
[00:33:34] Info: Found the 'mktemp' command: /bin/mktemp
[00:33:34] Info: Found the 'netstat' command: /bin/netstat
[00:33:34] Info: Found the 'perl' command: /usr/bin/perl
[00:33:34] Info: Found the 'ps' command: /bin/ps
[00:33:34] Info: Found the 'pwd' command: /bin/pwd
[00:33:34] Info: Found the 'readlink' command: /bin/readlink
[00:33:34] Info: Found the 'sort' command: /usr/bin/sort
[00:33:34] Info: Found the 'stat' command: /usr/bin/stat
[00:33:34] Info: Found the 'strings' command: /usr/bin/strings
[00:33:34] Info: Found the 'uniq' command: /usr/bin/uniq
[00:33:34] Info: System is not using prelinking
[00:33:34] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[00:33:34] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[00:33:34] Info: Stored hash values did not use a package manager
[00:33:34] Info: The hash function field index is set to 1
[00:33:34] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[00:33:34] Info: Previous file attributes were stored
[00:33:34] Info: Enabled tests are: all
[00:33:34] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[00:33:34] Info: Found ksym file '/proc/kallsyms'
[00:33:34]
[00:33:34] Checking if the O/S has changed since last time...
[00:33:34] Info: Nothing seems to have changed
[00:33:34]
[00:33:34] Starting system checks...
[00:33:34]
[00:33:34] Checking system commands...
[00:33:34] Info: Starting test name 'system_commands'
[00:33:34]
[00:33:34] Performing 'strings' command checks
[00:33:34] Info: Starting test name 'strings'
[00:33:35] Scanning for string /usr/sbin/ntpsx               [ OK ]
[00:33:35] Scanning for string /usr/lib/.../ls               [ OK ]
[00:33:35] Scanning for string /usr/lib/.../netstat          [ OK ]
[00:33:35] Scanning for string /usr/lib/.../lsof             [ OK ]
[00:33:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[00:33:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[00:33:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[00:33:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[00:33:35] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[00:33:35] Scanning for string /usr/lib/.../psr              [ OK ]
[00:33:35] Scanning for string /usr/lib/.../find             [ OK ]
[00:33:35] Scanning for string /usr/lib/.../pstree           [ OK ]
[00:33:35] Scanning for string /usr/lib/.../slocate          [ OK ]
[00:33:35] Scanning for string /usr/lib/.../du               [ OK ]
[00:33:35] Scanning for string /usr/lib/.../top              [ OK ]
[00:33:35] Scanning for string /usr/lib/...                  [ OK ]
[00:33:35] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[00:33:35] Scanning for string /usr/lib/.bkit-               [ OK ]
[00:33:35] Scanning for string /tmp/.bkp                     [ OK ]
[00:33:35] Scanning for string /tmp/.cinik                   [ OK ]
[00:33:35] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[00:33:35] Scanning for string /lib/.sso                     [ OK ]
[00:33:35] Scanning for string /lib/.so                      [ OK ]
[00:33:36] Scanning for string /var/run/...dica/clean        [ OK ]
[00:33:36] Scanning for string /var/run/...dica/xl           [ OK ]
[00:33:36] Scanning for string /var/run/...dica/xdr          [ OK ]
[00:33:36] Scanning for string /var/run/...dica/psg          [ OK ]
[00:33:36] Scanning for string /var/run/...dica/secure       [ OK ]
[00:33:36] Scanning for string /var/run/...dica/rdx          [ OK ]
[00:33:36] Scanning for string /var/run/...dica/va           [ OK ]
[00:33:36] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[00:33:36] Scanning for string /usr/bin/.etc                 [ OK ]
[00:33:36] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[00:33:36] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[00:33:36] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[00:33:36] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[00:33:36] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[00:33:36] Scanning for string /bin/sysback                  [ OK ]
[00:33:36] Scanning for string /usr/local/bin/sysback        [ OK ]
[00:33:36] Scanning for string /usr/lib/.tbd                 [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[00:33:36] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[00:33:37] Scanning for string /usr/info/.torn/sh*           [ OK ]
[00:33:37] Scanning for string /usr/src/.****/.1addr         [ OK ]
[00:33:37] Scanning for string /usr/src/.****/.1file         [ OK ]
[00:33:37] Scanning for string /usr/src/.****/.1proc         [ OK ]
[00:33:37] Scanning for string /usr/src/.****/.1logz         [ OK ]
[00:33:37] Scanning for string /usr/info/.t0rn               [ OK ]
[00:33:37] Scanning for string /dev/.lib                     [ OK ]
[00:33:37] Scanning for string /dev/.lib/lib                 [ OK ]
[00:33:38] Scanning for string /dev/.lib/lib/lib             [ OK ]
[00:33:38] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[00:33:38] Scanning for string /dev/.lib/lib/scan            [ OK ]
[00:33:38] Scanning for string /usr/src/.****                [ OK ]
[00:33:38] Scanning for string /usr/man/man1/man1            [ OK ]
[00:33:38] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[00:33:38] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[00:33:38] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[00:33:38]
[00:33:38] Performing 'shared libraries' checks
[00:33:38] Info: Starting test name 'shared_libs'
[00:33:38] Checking for preloading variables                 [ None found ]
[00:33:38] Checking for preload file                         [ Not found ]
[00:33:38] Info: Starting test name 'shared_libs_path'
[00:33:38] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[00:33:38]
[00:33:38] Performing file properties checks
[00:33:38] Info: Starting test name 'properties'
[00:33:38] Checking for prerequisites                        [ OK ]
[00:33:38] /bin/bash                                         [ OK ]
[00:33:39] /bin/cat                                          [ OK ]
[00:33:39] /bin/chmod                                        [ OK ]
[00:33:39] /bin/chown                                        [ OK ]
[00:33:39] /bin/cp                                           [ OK ]
[00:33:39] /bin/date                                         [ OK ]
[00:33:39] /bin/df                                           [ OK ]
[00:33:39] /bin/dmesg                                        [ OK ]
[00:33:40] /bin/echo                                         [ OK ]
[00:33:40] /bin/ed                                           [ OK ]
[00:33:40] /bin/egrep                                        [ OK ]
[00:33:40] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[00:33:40] /bin/fgrep                                        [ OK ]
[00:33:40] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[00:33:40] /bin/grep                                         [ OK ]
[00:33:40] /bin/ip                                           [ OK ]
[00:33:40] /bin/kill                                         [ OK ]
[00:33:41] /bin/login                                        [ OK ]
[00:33:41] /bin/ls                                           [ OK ]
[00:33:41] /bin/lsmod                                        [ OK ]
[00:33:41] /bin/mktemp                                       [ OK ]
[00:33:41] /bin/more                                         [ OK ]
[00:33:41] /bin/mount                                        [ OK ]
[00:33:41] /bin/mv                                           [ OK ]
[00:33:42] /bin/netstat                                      [ OK ]
[00:33:42] /bin/ps                                           [ OK ]
[00:33:42] /bin/pwd                                          [ OK ]
[00:33:42] /bin/readlink                                     [ OK ]
[00:33:42] /bin/sed                                          [ OK ]
[00:33:42] /bin/sh                                           [ OK ]
[00:33:43] /bin/su                                           [ OK ]
[00:33:43] /bin/touch                                        [ OK ]
[00:33:43] /bin/uname                                        [ OK ]
[00:33:43] /bin/which                                        [ OK ]
[00:33:43] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[00:33:43] /bin/dash                                         [ OK ]
[00:33:43] /usr/bin/awk                                      [ OK ]
[00:33:44] /usr/bin/basename                                 [ OK ]
[00:33:44] /usr/bin/chattr                                   [ Warning ]
[00:33:44] Warning: The file properties have changed:
[00:33:44]          File: /usr/bin/chattr
[00:33:44]          Current hash: 4703e5adba10128a0abbc036cefae73f754db142
[00:33:44]          Stored hash : 2502e2f117415f56cd64568b042a91dd3ef79b80
[00:33:44]          Current inode: 4915581    Stored inode: 4915346
[00:33:44]          Current size: 7228    Stored size: 7296
[00:33:44]          Current file modification time: 1197053992
[00:33:44]          Stored file modification time : 1189103575
[00:33:44] /usr/bin/cut                                      [ OK ]
[00:33:44] /usr/bin/diff                                     [ OK ]
[00:33:44] /usr/bin/dirname                                  [ OK ]
[00:33:44] /usr/bin/dpkg                                     [ OK ]
[00:33:45] /usr/bin/dpkg-query                               [ OK ]
[00:33:45] /usr/bin/du                                       [ OK ]
[00:33:45] /usr/bin/env                                      [ OK ]
[00:33:45] /usr/bin/file                                     [ OK ]
[00:33:45] /usr/bin/find                                     [ Warning ]
[00:33:45] Warning: The file properties have changed:
[00:33:45]          File: /usr/bin/find
[00:33:45]          Current inode: 4915346    Stored inode: 4915502
[00:33:45]          Current file modification time: 1197465595
[00:33:45]          Stored file modification time : 1191436615
[00:33:45] /usr/bin/GET                                      [ OK ]
[00:33:46] /usr/bin/groups                                   [ OK ]
[00:33:46] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[00:33:46] /usr/bin/head                                     [ OK ]
[00:33:46] /usr/bin/id                                       [ OK ]
[00:33:46] /usr/bin/killall                                  [ OK ]
[00:33:46] /usr/bin/last                                     [ OK ]
[00:33:46] /usr/bin/lastlog                                  [ OK ]
[00:33:46] /usr/bin/ldd                                      [ Warning ]
[00:33:46] Warning: The file properties have changed:
[00:33:46]          File: /usr/bin/ldd
[00:33:46]          Current inode: 4921099    Stored inode: 4915831
[00:33:47]          Current file modification time: 1193274171
[00:33:47]          Stored file modification time : 1191200505
[00:33:47] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[00:33:47] /usr/bin/less                                     [ OK ]
[00:33:47] /usr/bin/locate                                   [ OK ]
[00:33:47] /usr/bin/logger                                   [ OK ]
[00:33:47] /usr/bin/lsattr                                   [ Warning ]
[00:33:47] Warning: The file properties have changed:
[00:33:47]          File: /usr/bin/lsattr
[00:33:47]          Current hash: c3eba9c1952ccf894f8f71b999b081fe5ad5f4de
[00:33:47]          Stored hash : 4ba9ee6cb8455509347059f7917ef7ed4bab6891
[00:33:47]          Current inode: 4915583    Stored inode: 4915864
[00:33:47]          Current size: 6000    Stored size: 6068
[00:33:47]          Current file modification time: 1197053992
[00:33:47]          Stored file modification time : 1189103575
[00:33:47] /usr/bin/lsof                                     [ OK ]
[00:33:48] /usr/bin/mail                                     [ OK ]
[00:33:48] /usr/bin/md5sum                                   [ OK ]
[00:33:48] /usr/bin/newgrp                                   [ OK ]
[00:33:48] /usr/bin/passwd                                   [ OK ]
[00:33:48] /usr/bin/perl                                     [ Warning ]
[00:33:48] Warning: The file properties have changed:
[00:33:48]          File: /usr/bin/perl
[00:33:48]          Current hash: 9c4d220d96fbaf9aaedbe4e034a767e8d510d7f6
[00:33:48]          Stored hash : 155faff21807a6ad3687806ba7737223cd56ac68
[00:33:48]          Current inode: 4915374    Stored inode: 4916007
[00:33:48]          Current size: 1078128    Stored size: 1078160
[00:33:48]          Current file modification time: 1196759924
[00:33:48]          Stored file modification time : 1191046830
[00:33:49] /usr/bin/pstree                                   [ OK ]
[00:33:49] /usr/bin/rkhunter                                 [ OK ]
[00:33:49] /usr/bin/runcon                                   [ OK ]
[00:33:49] /usr/bin/sha1sum                                  [ OK ]
[00:33:49] /usr/bin/size                                     [ OK ]
[00:33:49] /usr/bin/slocate                                  [ OK ]
[00:33:49] /usr/bin/sort                                     [ OK ]
[00:33:49] /usr/bin/stat                                     [ OK ]
[00:33:50] /usr/bin/strace                                   [ OK ]
[00:33:50] /usr/bin/strings                                  [ OK ]
[00:33:50] /usr/bin/sudo                                     [ OK ]
[00:33:50] /usr/bin/tail                                     [ OK ]
[00:33:50] /usr/bin/test                                     [ OK ]
[00:33:50] /usr/bin/top                                      [ OK ]
[00:33:50] /usr/bin/touch                                    [ OK ]
[00:33:51] /usr/bin/tr                                       [ OK ]
[00:33:51] /usr/bin/uniq                                     [ OK ]
[00:33:51] /usr/bin/users                                    [ OK ]
[00:33:51] /usr/bin/vmstat                                   [ OK ]
[00:33:51] /usr/bin/w                                        [ OK ]
[00:33:51] /usr/bin/watch                                    [ OK ]
[00:33:51] /usr/bin/wc                                       [ OK ]
[00:33:51] /usr/bin/wget                                     [ OK ]
[00:33:52] /usr/bin/whatis                                   [ OK ]
[00:33:52] /usr/bin/whereis                                  [ OK ]
[00:33:52] /usr/bin/which                                    [ OK ]
[00:33:52] /usr/bin/who                                      [ OK ]
[00:33:52] /usr/bin/whoami                                   [ OK ]
[00:33:52] /usr/bin/mawk                                     [ OK ]
[00:33:52] /usr/bin/lwp-request                              [ OK ]
[00:33:52] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[00:33:53] /usr/bin/w.procps                                 [ OK ]
[00:33:53] /sbin/depmod                                      [ OK ]
[00:33:53] /sbin/ifconfig                                    [ OK ]
[00:33:53] /sbin/ifdown                                      [ OK ]
[00:33:53] /sbin/ifup                                        [ OK ]
[00:33:53] /sbin/init                                        [ OK ]
[00:33:54] /sbin/insmod                                      [ OK ]
[00:33:54] /sbin/ip                                          [ OK ]
[00:33:54] /sbin/lsmod                                       [ OK ]
[00:33:54] /sbin/modinfo                                     [ OK ]
[00:33:54] /sbin/modprobe                                    [ OK ]
[00:33:54] /sbin/rmmod                                       [ OK ]
[00:33:55] /sbin/runlevel                                    [ OK ]
[00:33:55] /sbin/sulogin                                     [ OK ]
[00:33:55] /sbin/sysctl                                      [ OK ]
[00:33:55] /sbin/syslogd                                     [ OK ]
[00:33:55] /usr/sbin/adduser                                 [ OK ]
[00:33:55] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[00:33:56] /usr/sbin/chroot                                  [ OK ]
[00:33:56] /usr/sbin/cron                                    [ OK ]
[00:33:56] /usr/sbin/groupadd                                [ OK ]
[00:33:56] /usr/sbin/groupdel                                [ OK ]
[00:33:56] /usr/sbin/groupmod                                [ OK ]
[00:33:56] /usr/sbin/grpck                                   [ OK ]
[00:33:57] /usr/sbin/nologin                                 [ OK ]
[00:33:57] /usr/sbin/pwck                                    [ OK ]
[00:33:57] /usr/sbin/tcpd                                    [ OK ]
[00:33:57] /usr/sbin/useradd                                 [ OK ]
[00:33:58] /usr/sbin/userdel                                 [ OK ]
[00:33:58] /usr/sbin/usermod                                 [ OK ]
[00:33:58] /usr/sbin/vipw                                    [ OK ]
[00:34:01]
[00:34:01] Checking for rootkits...
[00:34:01] Info: Starting test name 'rootkits'
[00:34:01]
[00:34:01] Performing check of known rootkit files and directories
[00:34:01] Info: Starting test name 'known_rkts'
[00:34:02]
[00:34:02] Checking for 55808 Trojan - Variant A...
[00:34:02]   Checking for file '/tmp/.../r'                  [ Not found ]
[00:34:02]   Checking for file '/tmp/.../a'                  [ Not found ]
[00:34:02] 55808 Trojan - Variant A                          [ Not found ]
[00:34:02]
[00:34:02] Checking for ADM Worm...
[00:34:02]   Checking for string 'w0rm'                      [ Not found ]
[00:34:02] ADM Worm                                          [ Not found ]
[00:34:02]
[00:34:02] Checking for AjaKit Rootkit...
[00:34:02]   Checking for file '/dev/tux/.addr'              [ Not found ]
[00:34:02]   Checking for file '/dev/tux/.proc'              [ Not found ]
[00:34:02]   Checking for file '/dev/tux/.file'              [ Not found ]
[00:34:02]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[00:34:02]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[00:34:02]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[00:34:02]   Checking for directory '/dev/tux'               [ Not found ]
[00:34:02]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[00:34:02] AjaKit Rootkit                                    [ Not found ]
[00:34:02]
[00:34:02] Checking for aPa Kit...
[00:34:02]   Checking for file '/usr/share/.aPa'             [ Not found ]
[00:34:02] aPa Kit                                           [ Not found ]
[00:34:02]
[00:34:02] Checking for Apache Worm...
[00:34:02]   Checking for file '/bin/.log'                   [ Not found ]
[00:34:02] Apache Worm                                       [ Not found ]
[00:34:02]
[00:34:02] Checking for Ambient (ark) Rootkit...
[00:34:02]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[00:34:02]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[00:34:02]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[00:34:03]   Checking for directory '/dev/ptyxx'             [ Not found ]
[00:34:03] Ambient (ark) Rootkit                             [ Not found ]
[00:34:03]
[00:34:03] Checking for Balaur Rootkit...
[00:34:03]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[00:34:03]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[00:34:03]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[00:34:03]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[00:34:03] Balaur Rootkit                                    [ Not found ]
[00:34:03]
[00:34:03] Checking for BeastKit Rootkit...
[00:34:03]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[00:34:03]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[00:34:03]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[00:34:03]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[00:34:03] BeastKit Rootkit                                  [ Not found ]
[00:34:03]
[00:34:03] Checking for beX2 Rootkit...
[00:34:03]   Checking for directory '/usr/include/bex'       [ Not found ]
[00:34:03] beX2 Rootkit                                      [ Not found ]
[00:34:03]
[00:34:03] Checking for BOBKit Rootkit...
[00:34:03]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[00:34:03]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../find'           [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../du'             [ Not found ]
[00:34:04]   Checking for file '/usr/lib/.../top'            [ Not found ]
[00:34:04]   Checking for directory '/usr/lib/...'           [ Not found ]
[00:34:04]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[00:34:04]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[00:34:04]   Checking for directory '/tmp/.bkp'              [ Not found ]
[00:34:04] BOBKit Rootkit                                    [ Not found ]
[00:34:04]
[00:34:04] Checking for CiNIK Worm (Slapper.B variant)...
[00:34:04]   Checking for file '/tmp/.cinik'                 [ Not found ]
[00:34:04]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[00:34:04] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[00:34:04]
[00:34:04] Checking for Danny-Boy's Abuse Kit...
[00:34:04]   Checking for file '/dev/mdev'                   [ Not found ]
[00:34:04]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[00:34:04] Danny-Boy's Abuse Kit                             [ Not found ]
[00:34:05]
[00:34:05] Checking for Devil RootKit...
[00:34:05]   Checking for file '/var/lib/games/.src'         [ Not found ]
[00:34:05]   Checking for file '/dev/dsx'                    [ Not found ]
[00:34:05]   Checking for file '/dev/caca'                   [ Not found ]
[00:34:05] Devil RootKit                                     [ Not found ]
[00:34:05]
[00:34:05] Checking for Dica-Kit Rootkit...
[00:34:05]   Checking for file '/lib/.sso'                   [ Not found ]
[00:34:05]   Checking for file '/lib/.so'                    [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/va'         [ Not found ]
[00:34:05]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[00:34:05]   Checking for file '/usr/bin/.etc'               [ Not found ]
[00:34:05]   Checking for directory '/var/run/...dica'       [ Not found ]
[00:34:05]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[00:34:05]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[00:34:05] Dica-Kit Rootkit                                  [ Not found ]
[00:34:05]
[00:34:05] Checking for Dreams Rootkit...
[00:34:05]   Checking for file '/dev/ttyoa'                  [ Not found ]
[00:34:05]   Checking for file '/dev/ttyof'                  [ Not found ]
[00:34:05]   Checking for file '/dev/ttyop'                  [ Not found ]
[00:34:06]   Checking for file '/usr/bin/sense'              [ Not found ]
[00:34:06]   Checking for file '/usr/bin/sl2'                [ Not found ]
[00:34:06]   Checking for file '/usr/bin/logclear'           [ Not found ]
[00:34:06]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[00:34:06]   Checking for file '/usr/bin/snfs'               [ Not found ]
[00:34:06]   Checking for file '/usr/lib/libsss'             [ Not found ]
[00:34:06]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[00:34:06] Dreams Rootkit                                    [ Not found ]
[00:34:06]
[00:34:06] Checking for Duarawkz Rootkit...
[00:34:06]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[00:34:06]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[00:34:06] Duarawkz Rootkit                                  [ Not found ]
[00:34:06]
[00:34:06] Checking for Enye LKM...
[00:34:06]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[00:34:06] Enye LKM                                          [ Not found ]
[00:34:06]
[00:34:06] Checking for Flea Linux Rootkit...
[00:34:06]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[00:34:06]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[00:34:06]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[00:34:06]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[00:34:06]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[00:34:06]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[00:34:06]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[00:34:06]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[00:34:06]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[00:34:06]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[00:34:07]   Checking for directory '/dev/..0'               [ Not found ]
[00:34:07]   Checking for directory '/dev/..0/backup'        [ Not found ]
[00:34:07] Flea Linux Rootkit                                [ Not found ]
[00:34:07]
[00:34:07] Checking for FreeBSD Rootkit...
[00:34:07]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[00:34:07]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[00:34:07]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[00:34:07]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[00:34:07]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[00:34:07]   Checking for file '/bin/sysback'                [ Not found ]
[00:34:07]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[00:34:07]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[00:34:07]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[00:34:07] FreeBSD Rootkit                                   [ Not found ]
[00:34:07]
[00:34:07] Checking for ****`it Rootkit...
[00:34:07]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[00:34:07]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[00:34:07] ****`it Rootkit                                   [ Not found ]
[00:34:07]
[00:34:07] Checking for GasKit Rootkit...
[00:34:07]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[00:34:08]   Checking for directory '/dev/dev'               [ Not found ]
[00:34:08]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[00:34:08]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[00:34:08] GasKit Rootkit                                    [ Not found ]
[00:34:08]
[00:34:08] Checking for Heroin LKM...
[00:34:08]   Checking for kernel symbol 'heroin'             [ Not found ]
[00:34:08] Heroin LKM                                        [ Not found ]
[00:34:08]
[00:34:08] Checking for HjC Kit...
[00:34:08]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[00:34:08] HjC Kit                                           [ Not found ]
[00:34:08]
[00:34:08] Checking for ignoKit Rootkit...
[00:34:08]   Checking for file '/lib/defs/p'                 [ Not found ]
[00:34:08]   Checking for file '/lib/defs/q'                 [ Not found ]
[00:34:08]   Checking for file '/lib/defs/r'                 [ Not found ]
[00:34:08]   Checking for file '/lib/defs/s'                 [ Not found ]
[00:34:08]   Checking for file '/lib/defs/t'                 [ Not found ]
[00:34:08]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[00:34:08]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[00:34:08]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[00:34:08]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[00:34:08]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[00:34:08]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[00:34:08]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[00:34:08]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[00:34:08]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[00:34:09] ignoKit Rootkit                                   [ Not found ]
[00:34:09]
[00:34:09] Checking for ImperalsS-FBRK Rootkit...
[00:34:09]   Checking for directory '/dev/fd/.88'            [ Not found ]
[00:34:09]   Checking for directory '/dev/fd/.99'            [ Not found ]
[00:34:09] ImperalsS-FBRK Rootkit                            [ Not found ]
[00:34:09]
[00:34:09] Checking for Irix Rootkit...
[00:34:09]   Checking for directory '/dev/pts/01'            [ Not found ]
[00:34:09]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[00:34:09]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[00:34:09]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[00:34:09] Irix Rootkit                                      [ Not found ]
[00:34:09]
[00:34:09] Checking for Kitko Rootkit...
[00:34:09]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[00:34:09] Kitko Rootkit                                     [ Not found ]
[00:34:09]
[00:34:09] Checking for Knark Rootkit...
[00:34:09]   Checking for file '/proc/knark/pids'            [ Not found ]
[00:34:09]   Checking for directory '/proc/knark'            [ Not found ]
[00:34:09] Knark Rootkit                                     [ Not found ]
[00:34:09]
[00:34:09] Checking for Li0n Worm...
[00:34:09]   Checking for file '/bin/in.telnetd'             [ Not found ]
[00:34:09]   Checking for file '/bin/mjy'                    [ Not found ]
[00:34:09]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[00:34:09]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[00:34:09]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[00:34:09]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[00:34:09]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[00:34:09]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[00:34:10]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[00:34:10] Li0n Worm                                         [ Not found ]
[00:34:10]
[00:34:10] Checking for Lockit / LJK2 Rootkit...
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[00:34:10]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[00:34:11]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[00:34:11]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[00:34:11] Lockit / LJK2 Rootkit                             [ Not found ]
[00:34:11]
[00:34:11] Checking for Mood-NT Rootkit...
[00:34:11]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[00:34:12]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[00:34:12]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[00:34:12]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[00:34:12]   Checking for directory '/_cthulhu'              [ Not found ]
[00:34:12] Mood-NT Rootkit                                   [ Not found ]
[00:34:12]
[00:34:12] Checking for MRK Rootkit...
[00:34:12]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[00:34:12]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[00:34:12]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[00:34:12]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[00:34:12]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[00:34:12]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[00:34:12] MRK Rootkit                                       [ Not found ]
[00:34:12]
[00:34:12] Checking for Ni0 Rootkit...
[00:34:12]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[00:34:12]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[00:34:12]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[00:34:12]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[00:34:12]   Checking for directory '/tmp/waza'              [ Not found ]
[00:34:12]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[00:34:12]   Checking for directory '/usr/sbin/es'           [ Not found ]
[00:34:12] Ni0 Rootkit                                       [ Not found ]
[00:34:12]
[00:34:12] Checking for Ohhara Rootkit...
[00:34:12]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[00:34:12]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[00:34:12]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[00:34:13]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[00:34:13]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[00:34:13]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[00:34:13]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[00:34:13] Ohhara Rootkit                                    [ Not found ]
[00:34:13]
[00:34:13] Checking for Optic Kit (Tux) Worm...
[00:34:13]   Checking for directory '/dev/tux'               [ Not found ]
[00:34:13]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[00:34:13]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[00:34:13]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[00:34:13] Optic Kit (Tux) Worm                              [ Not found ]
[00:34:13]
[00:34:13] Checking for Oz Rootkit...
[00:34:13]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[00:34:13]   Checking for directory '/dev/.oz'               [ Not found ]
[00:34:13] Oz Rootkit                                        [ Not found ]
[00:34:13]
[00:34:13] Checking for Phalanx Rootkit...
[00:34:13]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[00:34:13]   Checking for file '/etc/host.ph1'               [ Not found ]
[00:34:13]   Checking for file '/bin/host.ph1'               [ Not found ]
[00:34:13]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[00:34:13]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[00:34:13] Phalanx Rootkit                                   [ Not found ]
[00:34:13]
[00:34:13] Checking for Phalanx Rootkit (strings)...
[00:34:13]   Checking for string 'phalanx'                   [ Not found ]
[00:34:13] Phalanx Rootkit (strings)                         [ Not found ]
[00:34:13]
[00:34:13] Checking for Portacelo Rootkit...
[00:34:14]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../.p'             [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../getty'          [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../show'           [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[00:34:14]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[00:34:14]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[00:34:14] Portacelo Rootkit                                 [ Not found ]
[00:34:14]
[00:34:14] Checking for R3dstorm Toolkit...
[00:34:14]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[00:34:14]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[00:34:14]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[00:34:14]   Checking for file '/bin/.../see_all'            [ Not found ]
[00:34:14]   Checking for directory '/var/log/tk02'          [ Not found ]
[00:34:14]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[00:34:14]   Checking for directory '/bin/...'               [ Not found ]
[00:34:14] R3dstorm Toolkit                                  [ Not found ]
[00:34:14]
[00:34:14] Checking for RH-Sharpe's Rootkit...
[00:34:14]   Checking for file '/bin/lps'                    [ Not found ]
[00:34:14]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[00:34:15]   Checking for file '/usr/bin/ltop'               [ Not found ]
[00:34:15]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[00:34:15]   Checking for file '/usr/bin/ldu'                [ Not found ]
[00:34:15]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[00:34:15]   Checking for file '/usr/bin/wp'                 [ Not found ]
[00:34:15]   Checking for file '/usr/bin/shad'               [ Not found ]
[00:34:15]   Checking for file '/usr/bin/vadim'              [ Not found ]
[00:34:15]   Checking for file '/usr/bin/slice'              [ Not found ]
[00:34:15]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[00:34:15]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[00:34:15] RH-Sharpe's Rootkit                               [ Not found ]
[00:34:15]
[00:34:15] Checking for RSHA's Rootkit...
[00:34:15]   Checking for file '/bin/kr4p'                   [ Not found ]
[00:34:15]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[00:34:15]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[00:34:15]   Checking for file '/usr/bin/slice2'             [ Not found ]
[00:34:15]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[00:34:15]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[00:34:15]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[00:34:15]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[00:34:15] RSHA's Rootkit                                    [ Not found ]
[00:34:15]
[00:34:15] Checking for Scalper Worm...
[00:34:15]   Checking for file '/tmp/.a'                     [ Not found ]
[00:34:15]   Checking for file '/tmp/.uua'                   [ Not found ]
[00:34:15] Scalper Worm                                      [ Not found ]
[00:34:16]
[00:34:16] Checking for Sebek LKM...
[00:34:16]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[00:34:16] Sebek LKM                                         [ Not found ]
[00:34:16]
[00:34:16] Checking for Shutdown Rootkit...
[00:34:16]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[00:34:16]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[00:34:16]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[00:34:16]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[00:34:16]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[00:34:16]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[00:34:16]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[00:34:16]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[00:34:16] Shutdown Rootkit                                  [ Not found ]
[00:34:16]
[00:34:16] Checking for SHV4 Rootkit...
[00:34:16]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[00:34:16]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[00:34:16]   Checking for file '/lib/lidps1.so'              [ Not found ]
[00:34:16]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[00:34:16]   Checking for directory '/lib/security/.config'  [ Not found ]
[00:34:17]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[00:34:17] SHV4 Rootkit                                      [ Not found ]
[00:34:17]
[00:34:17] Checking for SHV5 Rootkit...
[00:34:17]   Checking for file '/etc/sh.conf'                [ Not found ]
[00:34:17]   Checking for file '/dev/srd0'                   [ Not found ]
[00:34:17]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[00:34:17] SHV5 Rootkit                                      [ Not found ]
[00:34:17]
[00:34:17] Checking for Sin Rootkit...
[00:34:17]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[00:34:17]   Checking for file '/dev/ttyoa'                  [ Not found ]
[00:34:17]   Checking for file '/dev/ttyof'                  [ Not found ]
[00:34:17]   Checking for file '/dev/ttyop'                  [ Not found ]
[00:34:17]   Checking for file '/dev/ttyos'                  [ Not found ]
[00:34:17]   Checking for file '/usr/lib/.lib'               [ Not found ]
[00:34:17]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[00:34:17]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[00:34:17]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[00:34:17]   Checking for file '/usr/man/man1/...'           [ Not found ]
[00:34:17]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[00:34:17]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[00:34:17]   Checking for directory '/usr/lib/sn'            [ Not found ]
[00:34:17]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[00:34:17]   Checking for directory '/dev/.haos'             [ Not found ]
[00:34:17] Sin Rootkit                                       [ Not found ]
[00:34:17]
[00:34:17] Checking for Slapper Worm...
[00:34:18]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[00:34:18]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[00:34:18]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[00:34:18]   Checking for file '/tmp/httpd'                  [ Not found ]
[00:34:18]   Checking for file '/tmp/.unlock'                [ Not found ]
[00:34:18]   Checking for file '/tmp/update'                 [ Not found ]
[00:34:18]   Checking for file '/tmp/.cinik'                 [ Not found ]
[00:34:18]   Checking for file '/tmp/.b'                     [ Not found ]
[00:34:18] Slapper Worm                                      [ Not found ]
[00:34:18]
[00:34:18] Checking for Sneakin Rootkit...
[00:34:18]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[00:34:18] Sneakin Rootkit                                   [ Not found ]
[00:34:18]
[00:34:18] Checking for Suckit Rootkit...
[00:34:18]   Checking for file '/sbin/initsk12'              [ Not found ]
[00:34:18]   Checking for file '/sbin/initxrk'               [ Not found ]
[00:34:18]   Checking for file '/usr/bin/null'               [ Not found ]
[00:34:18]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[00:34:18]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[00:34:18]   Checking for directory '/etc/.MG'               [ Not found ]
[00:34:19]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[00:34:19]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[00:34:19] Suckit Rootkit                                    [ Not found ]
[00:34:19]
[00:34:19] Checking for SunOS Rootkit...
[00:34:19]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[00:34:19]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[00:34:19]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[00:34:19]   Checking for file '/bin/xlogin'                 [ Not found ]
[00:34:19]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[00:34:19]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[00:34:19]   Checking for file '/sbin/login'                 [ Not found ]
[00:34:19]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[00:34:19]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[00:34:19]   Checking for file '/dev/kmod'                   [ Not found ]
[00:34:19]   Checking for file '/dev/dos'                    [ Not found ]
[00:34:19] SunOS Rootkit                                     [ Not found ]
[00:34:19]
[00:34:19] Checking for SunOS / NSDAP Rootkit...
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[00:34:19]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[00:34:20]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[00:34:20]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[00:34:20]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[00:34:20]   Checking for file '/usr/lib/lpset'              [ Not found ]
[00:34:20]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[00:34:20] SunOS / NSDAP Rootkit                             [ Not found ]
[00:34:20]
[00:34:20] Checking for Superkit Rootkit...
[00:34:20]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[00:34:20] Superkit Rootkit                                  [ Not found ]
[00:34:20]
[00:34:20] Checking for TBD (Telnet BackDoor)...
[00:34:20]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[00:34:20] TBD (Telnet BackDoor)                             [ Not found ]
[00:34:20]
[00:34:20] Checking for TeLeKiT Rootkit...
[00:34:20]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[00:34:20]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[00:34:20]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[00:34:20]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[00:34:20]   Checking for file '/dev/ptyr'                   [ Not found ]
[00:34:20]   Checking for file '/dev/ptyp'                   [ Not found ]
[00:34:20]   Checking for file '/dev/ptyq'                   [ Not found ]
[00:34:20]   Checking for file '/dev/hda06'                  [ Not found ]
[00:34:20]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[00:34:20]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[00:34:20]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[00:34:20]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[00:34:20] TeLeKiT Rootkit                                   [ Not found ]
[00:34:21]
[00:34:21] Checking for T0rn Rootkit...
[00:34:21]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[00:34:21]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[00:34:21]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[00:34:21]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[00:34:21]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[00:34:22]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[00:34:22]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[00:34:22]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[00:34:22]   Checking for directory '/dev/.lib'              [ Not found ]
[00:34:22]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[00:34:22]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[00:34:22]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[00:34:22]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[00:34:22]   Checking for directory '/usr/src/.****'         [ Not found ]
[00:34:22]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[00:34:22]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[00:34:22]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[00:34:22]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[00:34:22] T0rn Rootkit                                      [ Not found ]
[00:34:22]
[00:34:22] Checking for Trojanit Kit...
[00:34:22]   Checking for file '/bin/.ls'                    [ Not found ]
[00:34:22]   Checking for file '/bin/.ps'                    [ Not found ]
[00:34:22]   Checking for file '/bin/.netstat'               [ Not found ]
[00:34:22]   Checking for file '/usr/bin/.nop'               [ Not found ]
[00:34:22]   Checking for file '/usr/bin/.who'               [ Not found ]
[00:34:22] Trojanit Kit                                      [ Not found ]
[00:34:22]
[00:34:22] Checking for Tuxtendo Rootkit...
[00:34:22]   Checking for file '/dev/tux/.addr'              [ Not found ]
[00:34:22]   Checking for file '/dev/tux/.cron'              [ Not found ]
[00:34:22]   Checking for file '/dev/tux/.file'              [ Not found ]
[00:34:23]   Checking for file '/dev/tux/.log'               [ Not found ]
[00:34:23]   Checking for file '/dev/tux/.proc'              [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[00:34:23]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[00:34:23]   Checking for directory '/dev/tux'               [ Not found ]
[00:34:23]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[00:34:23]   Checking for directory '/dev/tux/backup'        [ Not found ]
[00:34:23] Tuxtendo Rootkit                                  [ Not found ]
[00:34:23]
[00:34:23] Checking for URK Rootkit...
[00:34:23]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[00:34:23]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[00:34:23]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[00:34:23]   Checking for file '/tmp/conf.inf'               [ Not found ]
[00:34:24]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[00:34:24] URK Rootkit                                       [ Not found ]
[00:34:24]
[00:34:24] Checking for VcKit Rootkit...
[00:34:24]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[00:34:24]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[00:34:24] VcKit Rootkit                                     [ Not found ]
[00:34:24]
[00:34:24] Checking for Volc Rootkit...
[00:34:24]   Checking for directory '/var/spool/.recent'     [ Not found ]
[00:34:24]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[00:34:24]   Checking for directory '/usr/lib/volc'          [ Not found ]
[00:34:24]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[00:34:24] Volc Rootkit                                      [ Not found ]
[00:34:24]
[00:34:24] Checking for X-Org SunOS Rootkit...
[00:34:24]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[00:34:24]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[00:34:24]   Checking for file '/usr/bin/srload'             [ Not found ]
[00:34:24]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[00:34:24]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[00:34:24]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[00:34:24]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[00:34:24]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[00:34:24]   Checking for directory '/usr/share/man...'      [ Not found ]
[00:34:24] X-Org SunOS Rootkit                               [ Not found ]
[00:34:24]
[00:34:24] Checking for zaRwT.KiT Rootkit...
[00:34:24]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[00:34:24]   Checking for file '/dev/ttyf'                   [ Not found ]
[00:34:25]   Checking for file '/dev/ttyp'                   [ Not found ]
[00:34:25]   Checking for file '/dev/ttyn'                   [ Not found ]
[00:34:25]   Checking for file '/rk/tulz'                    [ Not found ]
[00:34:25]   Checking for directory '/rk'                    [ Not found ]
[00:34:25]   Checking for directory '/dev/rd/s'              [ Not found ]
[00:34:25] zaRwT.KiT Rootkit                                 [ Not found ]
[00:34:25]
[00:34:25] Performing additional rootkit checks
[00:34:25] Info: Starting test name 'additional_rkts'
[00:34:25]
[00:34:25]   Performing Suckit Rookit additional checks
[00:34:25]     Checking /sbin/init link count                [ OK ]
[00:34:25]     Checking for hidden file extensions           [ None found ]
[00:34:25]     Running skdet command                         [ Skipped ]
[00:34:25] Info: Unable to find the 'skdet' command
[00:34:25]   Suckit Rookit additional checks                 [ OK ]
[00:34:25]
[00:34:25]   Performing check of possible rootkit files and directories
[00:34:25] Info: Starting test name 'possible_rkt_files'
[00:34:25]     Checking for file '/dev/sdr0'                 [ Not found ]
[00:34:25]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[00:34:25]     Checking for file '/tmp/.bash_history'        [ Not found ]
[00:34:25]     Checking for file '/usr/info/.clib'           [ Not found ]
[00:34:25]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[00:34:25]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[00:34:25]     Checking for file '/sbin/create'              [ Not found ]
[00:34:26]     Checking for file '/dev/ttypz'                [ Not found ]
[00:34:26]     Checking for directory '/usr/bin/take'        [ Not found ]
[00:34:26]     Checking for directory '/usr/src/.lib'        [ Not found ]
[00:34:26]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[00:34:26]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[00:34:26]     Checking for directory '/usr/sbin/...'        [ Not found ]
[00:34:26]     Checking for directory '/usr/share/.gun'      [ Not found ]
[00:34:26]   Checking for possible rootkit files and directories [ None found ]
[00:34:26]
[00:34:26]   Performing check for possible rootkit strings
[00:34:26] Info: Starting test name 'possible_rkt_strings'
[00:34:26] Info: Found local startup file: /etc/rc.local
[00:34:26]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[00:34:26]     Checking for string '****'                    [ Not found ]
[00:34:26]     Checking for string 'backdoor'                [ Not found ]
[00:34:26]     Checking for string 'vt200'                   [ Not found ]
[00:34:26]     Checking for string '/usr/bin/xstat'          [ Not found ]
[00:34:26]     Checking for string '/bin/envpc'              [ Not found ]
[00:34:26]     Checking for string 'L4m3r0x'                 [ Not found ]
[00:34:26]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[00:34:27]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[00:34:27]     Checking for string '/dev/sgk'                [ Not found ]
[00:34:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[00:34:27]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[00:34:27]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[00:34:27]     Checking for string '/lib/.sso'               [ Not found ]
[00:34:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[00:34:27]     Checking for string '/dev/caca'               [ Not found ]
[00:34:27]     Checking for string '/dev/ttyoa'              [ Not found ]
[00:34:27]     Checking for string 'syg'                     [ Not found ]
[00:34:27]     Checking for string '/dev/pts/01'             [ Not found ]
[00:34:27]     Checking for string 'tw33dl3'                 [ Not found ]
[00:34:27]     Checking for string 'psniff'                  [ Not found ]
[00:34:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[00:34:27]     Checking for string 'promiscuous'             [ Not found ]
[00:34:28]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[00:34:28]     Checking for string '/dev/xdta'               [ Not found ]
[00:34:28]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[00:34:28]     Checking for string 'in.inetd'                [ Not found ]
[00:34:28]     Checking for string '#<HIDE_.*>'              [ Not found ]
[00:34:28]     Checking for string 'bin/xchk'                [ Not found ]
[00:34:28]     Checking for string 'bin/xsf'                 [ Not found ]
[00:34:28]   Checking for possible rootkit strings           [ None found ]
[00:34:28]
[00:34:28] Performing malware checks
[00:34:28] Info: Starting test name 'malware'
[00:34:28]
[00:34:28] Info: Test 'deleted_files' disabled at users request.
[00:34:28] Info: Starting test name 'running_procs'
[00:34:28]   Checking running processes for suspicious files [ None found ]
[00:34:28]
[00:34:28] Info: Test 'hidden_procs' disabled at users request.
[00:34:28]
[00:34:28] Info: Test 'suspscan' disabled at users request.
[00:34:28]
[00:34:28]   Performing check for login backdoors
[00:34:28] Info: Starting test name 'other_malware'
[00:34:28]     Checking for '/bin/.login'                    [ Not found ]
[00:34:29]     Checking for '/sbin/.login'                   [ Not found ]
[00:34:29]   Checking for login backdoors                    [ None found ]
[00:34:29]
[00:34:29]   Performing check for suspicious directories
[00:34:29]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[00:34:29]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[00:34:29]   Checking for suspicious directories             [ None found ]
[00:34:29]
[00:34:29]   Checking for software intrusions                [ Skipped ]
[00:34:29] Info: Check skipped - tripwire not installed
[00:34:29]
[00:34:29]   Performing check for sniffer log files
[00:34:29]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[00:34:29]   Checking for sniffer log files                  [ None found ]
[00:34:29]
[00:34:29] Performing trojan specific checks
[00:34:29] Info: Starting test name 'trojans'
[00:34:29] Info: Using inetd configuration file '/etc/inetd.conf'
[00:34:29]   Checking for enabled inetd services             [ OK ]
[00:34:29]
[00:34:29]   Performing check for enabled xinetd services
[00:34:29]   Checking for enabled xinetd services            [ Skipped ]
[00:34:29] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[00:34:29] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[00:34:29]
[00:34:29] Performing Linux specific checks
[00:34:29] Info: Starting test name 'os_specific'
[00:34:29]   Checking kernel module commands                 [ OK ]
[00:34:29] Info: Using modules pathname of '/lib/modules/2.6.22-14-generic'
[00:34:29]   Checking kernel module names                    [ OK ]
[00:34:32]
[00:34:32] Checking the network...
[00:34:32] Info: Starting test name 'network'
[00:34:32] Info: Starting test name 'ports'
[00:34:32]
[00:34:32] Performing check for backdoor ports
[00:34:32]   Checking for UDP port 2001                      [ Not found ]
[00:34:32]   Checking for TCP port 2006                      [ Not found ]
[00:34:32]   Checking for TCP port 2128                      [ Not found ]
[00:34:33]   Checking for TCP port 14856                     [ Not found ]
[00:34:33]   Checking for TCP port 47107                     [ Not found ]
[00:34:33]   Checking for TCP port 60922                     [ Not found ]
[00:34:33]
[00:34:33] Performing checks on the network interfaces
[00:34:33] Info: Starting test name 'promisc'
[00:34:33]   Checking for promiscuous interfaces             [ None found ]
[00:34:33]
[00:34:33] Info: Test 'packet_cap_apps' disabled at users request.
[00:34:35]
[00:34:35] Checking the local host...
[00:34:35] Info: Starting test name 'local_host'
[00:34:35]
[00:34:35] Performing system boot checks
[00:34:35] Info: Starting test name 'startup_files'
[00:34:35]   Checking for local host name                    [ Found ]
[00:34:35] Info: Starting test name 'startup_malware'
[00:34:35] Info: Found local startup file: /etc/rc.local
[00:34:35]   Checking for local startup files                [ Found ]
[00:34:35]   Checking local startup files for malware        [ None found ]
[00:34:35] Info: Found system startup directory: /etc/init.d
[00:34:37]   Checking system startup files for malware       [ None found ]
[00:34:37]
[00:34:37] Performing group and account checks
[00:34:37] Info: Starting test name 'group_accounts'
[00:34:37]   Checking for passwd file                        [ Found ]
[00:34:37] Info: Found password file: /etc/passwd
[00:34:37]   Checking for root equivalent (UID 0) accounts   [ None found ]
[00:34:37] Info: Found shadow file: /etc/shadow
[00:34:37]   Checking for passwordless accounts              [ None found ]
[00:34:37] Info: Starting test name 'passwd_changes'
[00:34:37]   Checking for passwd file changes                [ None found ]
[00:34:37] Info: Starting test name 'group_changes'
[00:34:37]   Checking for group file changes                 [ None found ]
[00:34:37]   Checking root account shell history files       [ None found ]
[00:34:37]
[00:34:37] Performing system configuration file checks
[00:34:37] Info: Starting test name 'system_configs'
[00:34:37]   Checking for SSH configuration file             [ Not found ]
[00:34:37]   Checking for running syslog daemon              [ Found ]
[00:34:37]   Checking for syslog configuration file          [ Found ]
[00:34:37] Info: Found syslog configuration file: /etc/syslog.conf
[00:34:37]   Checking if syslog remote logging is allowed    [ Not allowed ]
[00:34:37]
[00:34:37] Performing filesystem checks
[00:34:37] Info: Starting test name 'filesystem'
[00:34:37] Info: SCAN_MODE_DEV set to 'THOROUGH'
[00:34:53]   Checking /dev for suspicious file types         [ None found ]
[00:34:54]   Checking for hidden files and directories       [ Warning ]
[00:34:54] Warning: Hidden directory found: /dev/.static
[00:34:54] Warning: Hidden directory found: /dev/.udev
[00:34:54] Warning: Hidden directory found: /dev/.initramfs
[00:34:54] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)
[00:34:59]
[00:34:59] Checking application versions...
[00:34:59] Info: Starting test name 'apps'
[00:35:00] Info: Application 'exim' not found.
[00:35:00]   Checking version of GnuPG                       [ OK ]
[00:35:00] Info: Application 'gpg' version '1.4.6' found.
[00:35:00] Info: Application 'httpd' not found.
[00:35:00] Info: Application 'named' not found.
[00:35:00]   Checking version of OpenSSL                     [ OK ]
[00:35:00] Info: Application 'openssl' version '0.9.8e' found.
[00:35:00] Info: Application 'php' not found.
[00:35:00] Info: Application 'procmail' not found.
[00:35:00] Info: Application 'proftpd' not found.
[00:35:00] Info: Application 'sshd' not found.
[00:35:00] Info: Applications checked: 2 out of 9
[00:35:00]
[00:35:00] System checks summary
[00:35:00] =====================
[00:35:00]
[00:35:00] File properties checks...
[00:35:00] Files checked: 123
[00:35:00] Suspect files: 5
[00:35:00]
[00:35:00] Rootkit checks...
[00:35:00] Rootkits checked : 109
[00:35:00] Possible rootkits: 0
[00:35:00]
[00:35:00] Applications checks...
[00:35:00] Applications checked: 2
[00:35:00] Suspect applications: 0
[00:35:00]
[00:35:00] The system checks took: 1 minute and 26 seconds
[00:35:00]
[00:35:00] Info: End date is Mon Feb 11 00:35:00 PHT 2008


***************************************************************

***************************************************************
```

---

### Post by euler_fan on 2008-02-11
This comes up pretty frequently, in fact.

As for the scripts that changed, I'd say Google for the Ubuntu versions, open the file, and physically inspect. Simple rule is this: the harder it is for you to read what's in what's on your computer the more you need to post it here for a second opinion. If you see a bunch of garbage, I'd be worried.

As for hidden files . . . I'll have to leave that one to someone else or a forum search. You can also double check with chkrootkit and see what it picks up.

---

### Post by cgr1fatboyslim on 2008-02-11
thanks!

---

