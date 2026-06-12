---
title: "Hey guys have Ibeen hacked into?"
date: 2011-04-24
forum: Security
---

### Post by macminiuser on 2011-04-24
Have I been hacked into?
I ran rkhunter today and it showed some files changed here is the log
```

[17:20:01] Running Rootkit Hunter version 1.3.6 on jim-laptop
[17:20:01]
[17:20:01] Info: Start date is Sun Apr 24 17:20:01 CDT 2011
[17:20:02]
[17:20:02] Checking configuration file and command-line options...
[17:20:02] Info: Detected operating system is 'Linux'
[17:20:02] Info: Found O/S name: Ubuntu 10.04.2 LTS
[17:20:02] Info: Command line is /usr/bin/rkhunter --check
[17:20:02] Info: Environment shell is /bin/bash; rkhunter is using dash
[17:20:02] Info: Using configuration file '/etc/rkhunter.conf'
[17:20:02] Info: Installation directory is '/usr'
[17:20:02] Info: Using language 'en'
[17:20:02] Info: Using '/var/lib/rkhunter/db' as the database directory
[17:20:02] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[17:20:02] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[17:20:02] Info: Using '/' as the root directory by default
[17:20:02] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[17:20:02] Info: No mail-on-warning address configured
[17:20:02] Info: X will be automatically detected
[17:20:02] Info: Using second color set
[17:20:02] Info: Found the 'basename' command: /usr/bin/basename
[17:20:02] Info: Found the 'diff' command: /usr/bin/diff
[17:20:02] Info: Found the 'dirname' command: /usr/bin/dirname
[17:20:02] Info: Found the 'file' command: /usr/bin/file
[17:20:02] Info: Found the 'find' command: /usr/bin/find
[17:20:02] Info: Found the 'ifconfig' command: /sbin/ifconfig
[17:20:02] Info: Found the 'ip' command: /sbin/ip
[17:20:02] Info: Found the 'ldd' command: /usr/bin/ldd
[17:20:02] Info: Found the 'lsattr' command: /usr/bin/lsattr
[17:20:02] Info: Found the 'lsmod' command: /sbin/lsmod
[17:20:02] Info: Found the 'lsof' command: /usr/bin/lsof
[17:20:02] Info: Found the 'mktemp' command: /bin/mktemp
[17:20:02] Info: Found the 'netstat' command: /bin/netstat
[17:20:02] Info: Found the 'perl' command: /usr/bin/perl
[17:20:02] Info: Found the 'pgrep' command: /usr/bin/pgrep
[17:20:02] Info: Found the 'ps' command: /bin/ps
[17:20:02] Info: Found the 'pwd' command: /bin/pwd
[17:20:02] Info: Found the 'readlink' command: /bin/readlink
[17:20:02] Info: Found the 'sort' command: /usr/bin/sort
[17:20:02] Info: Found the 'stat' command: /usr/bin/stat
[17:20:02] Info: Found the 'strings' command: /usr/bin/strings
[17:20:02] Info: Found the 'uniq' command: /usr/bin/uniq
[17:20:02] Info: System is not using prelinking
[17:20:02] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[17:20:02] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[17:20:02] Info: Stored hash values did not use a package manager
[17:20:02] Info: The hash function field index is set to 1
[17:20:02] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[17:20:02] Info: Previous file attributes were stored
[17:20:02] Info: Enabled tests are: all
[17:20:02] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[17:20:02] Info: Found ksym file '/proc/kallsyms'
[17:20:02] Info: Using 'date' to process epoch second times.
[17:20:02]
[17:20:02] Checking if the O/S has changed since last time...
[17:20:02] Info: Nothing seems to have changed
[17:20:02] Info: Locking is not being used
[17:20:02]
[17:20:02] Starting system checks...
[17:20:02]
[17:20:02] Checking system commands...
[17:20:02] Info: Starting test name 'system_commands'
[17:20:02]
[17:20:02] Performing 'strings' command checks
[17:20:02] Info: Starting test name 'strings'
[17:20:03] Scanning for string /usr/sbin/ntpsx               [ OK ]
[17:20:03] Scanning for string /usr/sbin/.../bkit-ava        [ OK ]
[17:20:03] Scanning for string /usr/sbin/.../bkit-d          [ OK ]
[17:20:03] Scanning for string /usr/sbin/.../bkit-shd        [ OK ]
[17:20:03] Scanning for string /usr/sbin/.../bkit-f          [ OK ]
[17:20:03] Scanning for string /usr/include/.../proc.h       [ OK ]
[17:20:03] Scanning for string /usr/include/.../.bash_history [ OK ]
[17:20:03] Scanning for string /usr/include/.../bkit-get     [ OK ]
[17:20:03] Scanning for string /usr/include/.../bkit-dl      [ OK ]
[17:20:03] Scanning for string /usr/include/.../bkit-screen  [ OK ]
[17:20:03] Scanning for string /usr/include/.../bkit-sleep   [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-adore.o     [ OK ]
[17:20:03] Scanning for string /usr/lib/.../ls               [ OK ]
[17:20:03] Scanning for string /usr/lib/.../netstat          [ OK ]
[17:20:03] Scanning for string /usr/lib/.../lsof             [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[17:20:03] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[17:20:03] Scanning for string /usr/lib/.../psr              [ OK ]
[17:20:03] Scanning for string /usr/lib/.../find             [ OK ]
[17:20:03] Scanning for string /usr/lib/.../pstree           [ OK ]
[17:20:03] Scanning for string /usr/lib/.../slocate          [ OK ]
[17:20:03] Scanning for string /usr/lib/.../du               [ OK ]
[17:20:03] Scanning for string /usr/lib/.../top              [ OK ]
[17:20:03] Scanning for string /usr/sbin/...                 [ OK ]
[17:20:03] Scanning for string /usr/include/...              [ OK ]
[17:20:03] Scanning for string /usr/include/.../.tmp         [ OK ]
[17:20:03] Scanning for string /usr/lib/...                  [ OK ]
[17:20:03] Scanning for string /usr/lib/.../.ssh             [ OK ]
[17:20:03] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[17:20:04] Scanning for string /usr/lib/.bkit-               [ OK ]
[17:20:04] Scanning for string /tmp/.bkp                     [ OK ]
[17:20:04] Scanning for string /tmp/.cinik                   [ OK ]
[17:20:04] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[17:20:04] Scanning for string /lib/.sso                     [ OK ]
[17:20:04] Scanning for string /lib/.so                      [ OK ]
[17:20:04] Scanning for string /var/run/...dica/clean        [ OK ]
[17:20:04] Scanning for string /var/run/...dica/dxr          [ OK ]
[17:20:04] Scanning for string /var/run/...dica/read         [ OK ]
[17:20:04] Scanning for string /var/run/...dica/write        [ OK ]
[17:20:04] Scanning for string /var/run/...dica/lf           [ OK ]
[17:20:04] Scanning for string /var/run/...dica/xl           [ OK ]
[17:20:04] Scanning for string /var/run/...dica/xdr          [ OK ]
[17:20:04] Scanning for string /var/run/...dica/psg          [ OK ]
[17:20:04] Scanning for string /var/run/...dica/secure       [ OK ]
[17:20:04] Scanning for string /var/run/...dica/rdx          [ OK ]
[17:20:04] Scanning for string /var/run/...dica/va           [ OK ]
[17:20:04] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[17:20:04] Scanning for string /var/run/...dica/last.log     [ OK ]
[17:20:04] Scanning for string /usr/bin/.etc                 [ OK ]
[17:20:04] Scanning for string /etc/sshd_config              [ OK ]
[17:20:04] Scanning for string /etc/ssh_host_key             [ OK ]
[17:20:04] Scanning for string /etc/ssh_random_seed          [ OK ]
[17:20:04] Scanning for string /dev/ptyp                     [ OK ]
[17:20:04] Scanning for string /dev/ptyq                     [ OK ]
[17:20:04] Scanning for string /dev/ptyr                     [ OK ]
[17:20:04] Scanning for string /dev/ptys                     [ OK ]
[17:20:04] Scanning for string /dev/ptyt                     [ OK ]
[17:20:04] Scanning for string /dev/fd/.88/freshb-bsd        [ OK ]
[17:20:04] Scanning for string /dev/fd/.88/fresht            [ OK ]
[17:20:04] Scanning for string /dev/fd/.88/zxsniff           [ OK ]
[17:20:04] Scanning for string /dev/fd/.88/zxsniff.log       [ OK ]
[17:20:05] Scanning for string /dev/fd/.99/.ttyf00           [ OK ]
[17:20:05] Scanning for string /dev/fd/.99/.ttyp00           [ OK ]
[17:20:05] Scanning for string /dev/fd/.99/.ttyq00           [ OK ]
[17:20:05] Scanning for string /dev/fd/.99/.ttys00           [ OK ]
[17:20:05] Scanning for string /dev/fd/.99/.pwsx00           [ OK ]
[17:20:05] Scanning for string /etc/.acid                    [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/setrgrp.2        [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/TOHIDE           [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/adore/ava/ava    [ OK ]
[17:20:05] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[17:20:05] Scanning for string /bin/sysback                  [ OK ]
[17:20:05] Scanning for string /usr/local/bin/sysback        [ OK ]
[17:20:05] Scanning for string /usr/lib/.tbd                 [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[17:20:05] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[17:20:06] Scanning for string /usr/info/.torn/sh*           [ OK ]
[17:20:06] Scanning for string /usr/src/.puta/.1addr         [ OK ]
[17:20:06] Scanning for string /usr/src/.puta/.1file         [ OK ]
[17:20:06] Scanning for string /usr/src/.puta/.1proc         [ OK ]
[17:20:06] Scanning for string /usr/src/.puta/.1logz         [ OK ]
[17:20:06] Scanning for string /usr/info/.t0rn               [ OK ]
[17:20:06] Scanning for string /dev/.lib                     [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib                 [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib             [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[17:20:06] Scanning for string /dev/.lib/lib/scan            [ OK ]
[17:20:06] Scanning for string /usr/src/.puta                [ OK ]
[17:20:06] Scanning for string /usr/man/man1/man1            [ OK ]
[17:20:06] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[17:20:06] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[17:20:06] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[17:20:06]
[17:20:06] Performing 'shared libraries' checks
[17:20:06] Info: Starting test name 'shared_libs'
[17:20:06] Checking for preloading variables                 [ None found ]
[17:20:06] Checking for preloaded libraries                  [ None found ]
[17:20:06] Info: Starting test name 'shared_libs_path'
[17:20:06] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[17:20:06]
[17:20:06] Performing file properties checks
[17:20:06] Info: Starting test name 'properties'
[17:20:06] Checking for prerequisites                        [ OK ]
[17:20:07] /bin/bash                                         [ OK ]
[17:20:07] /bin/cat                                          [ OK ]
[17:20:07] /bin/chmod                                        [ OK ]
[17:20:07] /bin/chown                                        [ OK ]
[17:20:07] /bin/cp                                           [ OK ]
[17:20:07] /bin/date                                         [ OK ]
[17:20:07] /bin/df                                           [ OK ]
[17:20:07] /bin/dmesg                                        [ OK ]
[17:20:08] /bin/echo                                         [ OK ]
[17:20:08] /bin/ed                                           [ OK ]
[17:20:08] /bin/egrep                                        [ OK ]
[17:20:08] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[17:20:08] /bin/fgrep                                        [ OK ]
[17:20:08] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[17:20:08] /bin/fuser                                        [ OK ]
[17:20:08] /bin/grep                                         [ OK ]
[17:20:08] /bin/ip                                           [ OK ]
[17:20:08] /bin/kill                                         [ OK ]
[17:20:09] /bin/less                                         [ OK ]
[17:20:09] /bin/login                                        [ Warning ]
[17:20:09] Warning: The file properties have changed:
[17:20:09]          File: /bin/login
[17:20:09]          Current hash: 0c8941d3d50b8d50ec36468e04f80132cf0bcae6
[17:20:09]          Stored hash : d2b0a66038c61a400786ec385142350b147d8782
[17:20:09]          Current inode: 2621492    Stored inode: 2621511
[17:20:09]          Current file modification time: 1297721482 (14-Feb-2011 16:11:22)
[17:20:09]          Stored file modification time : 1264525785 (26-Jan-2010 11:09:45)
[17:20:09] /bin/ls                                           [ OK ]
[17:20:09] /bin/lsmod                                        [ OK ]
[17:20:09] /bin/mktemp                                       [ OK ]
[17:20:09] /bin/more                                         [ OK ]
[17:20:09] /bin/mount                                        [ OK ]
[17:20:09] /bin/mv                                           [ OK ]
[17:20:10] /bin/netstat                                      [ OK ]
[17:20:10] /bin/ps                                           [ OK ]
[17:20:10] /bin/pwd                                          [ OK ]
[17:20:10] /bin/readlink                                     [ OK ]
[17:20:10] /bin/sed                                          [ OK ]
[17:20:10] /bin/sh                                           [ OK ]
[17:20:10] /bin/su                                           [ Warning ]
[17:20:10] Warning: The file properties have changed:
[17:20:10]          File: /bin/su
[17:20:10]          Current hash: 19775a548eeba7a279808ef6e62120916f1499f0
[17:20:11]          Stored hash : 1ac8d28e4a0620af622dc40dafa066aaa7995b6c
[17:20:11]          Current inode: 2621493    Stored inode: 2621566
[17:20:11]          Current file modification time: 1297721482 (14-Feb-2011 16:11:22)
[17:20:11]          Stored file modification time : 1264525785 (26-Jan-2010 11:09:45)
[17:20:11] /bin/touch                                        [ OK ]
[17:20:11] /bin/uname                                        [ OK ]
[17:20:11] /bin/which                                        [ OK ]
[17:20:11] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[17:20:11] /bin/dash                                         [ OK ]
[17:20:11] /usr/bin/awk                                      [ OK ]
[17:20:11] /usr/bin/basename                                 [ OK ]
[17:20:12] /usr/bin/chattr                                   [ OK ]
[17:20:12] /usr/bin/curl                                     [ OK ]
[17:20:12] /usr/bin/cut                                      [ OK ]
[17:20:12] /usr/bin/diff                                     [ OK ]
[17:20:12] /usr/bin/dirname                                  [ OK ]
[17:20:12] /usr/bin/dpkg                                     [ OK ]
[17:20:12] /usr/bin/dpkg-query                               [ OK ]
[17:20:12] /usr/bin/du                                       [ OK ]
[17:20:13] /usr/bin/env                                      [ OK ]
[17:20:13] /usr/bin/file                                     [ OK ]
[17:20:13] /usr/bin/find                                     [ OK ]
[17:20:13] /usr/bin/GET                                      [ OK ]
[17:20:13] /usr/bin/groups                                   [ OK ]
[17:20:13] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[17:20:13] /usr/bin/head                                     [ OK ]
[17:20:13] /usr/bin/id                                       [ OK ]
[17:20:13] /usr/bin/killall                                  [ OK ]
[17:20:13] /usr/bin/last                                     [ OK ]
[17:20:14] /usr/bin/lastlog                                  [ Warning ]
[17:20:14] Warning: The file properties have changed:
[17:20:14]          File: /usr/bin/lastlog
[17:20:14]          Current hash: 78dffd6222db22e8d2cf25b5e44613331e1b5cb5
[17:20:14]          Stored hash : 147605d3b996369d1f476a2c6ad1fbbfa70d3688
[17:20:14]          Current inode: 8389792    Stored inode: 8389250
[17:20:14]          Current file modification time: 1297721482 (14-Feb-2011 16:11:22)
[17:20:14]          Stored file modification time : 1264525785 (26-Jan-2010 11:09:45)
[17:20:14] /usr/bin/ldd                                      [ OK ]
[17:20:14] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[17:20:14] /usr/bin/less                                     [ OK ]
[17:20:14] /usr/bin/locate                                   [ OK ]
[17:20:14] /usr/bin/logger                                   [ OK ]
[17:20:14] /usr/bin/lsattr                                   [ OK ]
[17:20:14] /usr/bin/lsof                                     [ OK ]
[17:20:14] /usr/bin/mail                                     [ OK ]
[17:20:15] /usr/bin/md5sum                                   [ OK ]
[17:20:15] /usr/bin/mlocate                                  [ OK ]
[17:20:15] /usr/bin/newgrp                                   [ Warning ]
[17:20:15] Warning: The file properties have changed:
[17:20:15]          File: /usr/bin/newgrp
[17:20:15]          Current hash: 7e3f1455bbda39079993b9317cc1941290e3866e
[17:20:15]          Stored hash : 574d9337020705c662e426f2e74cc22ba08bf4f9
[17:20:15]          Current inode: 8389803    Stored inode: 8389401
[17:20:15]          Current file modification time: 1297721482 (14-Feb-2011 16:11:22)
[17:20:15]          Stored file modification time : 1264525785 (26-Jan-2010 11:09:45)
[17:20:15] /usr/bin/passwd                                   [ Warning ]
[17:20:15] Warning: The file properties have changed:
[17:20:15]          File: /usr/bin/passwd
[17:20:15]          Current hash: c682f5c72dcd78a8bd4d3070efc0b33a185c0c58
[17:20:15]          Stored hash : c441bae1b4075a38f1834a03c973127850c09967
[17:20:15]          Current inode: 8390071    Stored inode: 8389465
[17:20:15]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:15]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:15] /usr/bin/perl                                     [ OK ]
[17:20:15] /usr/bin/pgrep                                    [ OK ]
[17:20:16] /usr/bin/pstree                                   [ OK ]
[17:20:16] /usr/bin/rkhunter                                 [ OK ]
[17:20:16] /usr/bin/rpm                                      [ Warning ]
[17:20:16] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
[17:20:16] /usr/bin/runcon                                   [ OK ]
[17:20:16] /usr/bin/sha1sum                                  [ OK ]
[17:20:16] /usr/bin/sha224sum                                [ OK ]
[17:20:16] /usr/bin/sha256sum                                [ OK ]
[17:20:16] /usr/bin/sha384sum                                [ OK ]
[17:20:16] /usr/bin/sha512sum                                [ OK ]
[17:20:16] /usr/bin/size                                     [ Warning ]
[17:20:17] Warning: The file properties have changed:
[17:20:17]          File: /usr/bin/size
[17:20:17]          Current inode: 8397691    Stored inode: 8390471
[17:20:17]          Current file modification time: 1299208925 (03-Mar-2011 21:22:05)
[17:20:17]          Stored file modification time : 1282315301 (20-Aug-2010 09:41:41)
[17:20:17] /usr/bin/sort                                     [ OK ]
[17:20:17] /usr/bin/stat                                     [ OK ]
[17:20:17] /usr/bin/strace                                   [ OK ]
[17:20:17] /usr/bin/strings                                  [ Warning ]
[17:20:17] Warning: The file properties have changed:
[17:20:17]          File: /usr/bin/strings
[17:20:17]          Current inode: 8398016    Stored inode: 8390474
[17:20:17]          Current file modification time: 1299208925 (03-Mar-2011 21:22:05)
[17:20:17]          Stored file modification time : 1282315301 (20-Aug-2010 09:41:41)
[17:20:17] /usr/bin/sudo                                     [ OK ]
[17:20:17] /usr/bin/tail                                     [ OK ]
[17:20:17] /usr/bin/test                                     [ OK ]
[17:20:18] /usr/bin/top                                      [ OK ]
[17:20:18] /usr/bin/touch                                    [ OK ]
[17:20:18] /usr/bin/tr                                       [ OK ]
[17:20:18] /usr/bin/uniq                                     [ OK ]
[17:20:18] /usr/bin/users                                    [ OK ]
[17:20:18] /usr/bin/vmstat                                   [ OK ]
[17:20:18] /usr/bin/w                                        [ OK ]
[17:20:18] /usr/bin/watch                                    [ OK ]
[17:20:18] /usr/bin/wc                                       [ OK ]
[17:20:18] /usr/bin/wget                                     [ OK ]
[17:20:19] /usr/bin/whatis                                   [ OK ]
[17:20:19] /usr/bin/whereis                                  [ OK ]
[17:20:19] /usr/bin/which                                    [ OK ]
[17:20:19] /usr/bin/who                                      [ OK ]
[17:20:19] /usr/bin/whoami                                   [ OK ]
[17:20:19] /usr/bin/gawk                                     [ OK ]
[17:20:19] /usr/bin/lwp-request                              [ OK ]
[17:20:19] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[17:20:19] /usr/bin/bsd-mailx                                [ OK ]
[17:20:19] /usr/bin/w.procps                                 [ OK ]
[17:20:20] /sbin/depmod                                      [ OK ]
[17:20:20] /sbin/ifconfig                                    [ OK ]
[17:20:20] /sbin/ifdown                                      [ OK ]
[17:20:20] /sbin/ifup                                        [ OK ]
[17:20:20] /sbin/init                                        [ OK ]
[17:20:20] /sbin/insmod                                      [ OK ]
[17:20:20] /sbin/ip                                          [ OK ]
[17:20:21] /sbin/lsmod                                       [ OK ]
[17:20:21] /sbin/modinfo                                     [ OK ]
[17:20:21] /sbin/modprobe                                    [ OK ]
[17:20:21] /sbin/rmmod                                       [ OK ]
[17:20:21] /sbin/runlevel                                    [ OK ]
[17:20:22] /sbin/sulogin                                     [ OK ]
[17:20:22] /sbin/sysctl                                      [ OK ]
[17:20:22] /usr/sbin/adduser                                 [ OK ]
[17:20:22] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[17:20:22] /usr/sbin/chroot                                  [ OK ]
[17:20:22] /usr/sbin/cron                                    [ OK ]
[17:20:23] /usr/sbin/groupadd                                [ Warning ]
[17:20:23] Warning: The file properties have changed:
[17:20:23]          File: /usr/sbin/groupadd
[17:20:23]          Current hash: f0b6f921d7a9f8e766ff6c7d631465941128aab2
[17:20:23]          Stored hash : b6bb3cca5d0c399b26e3688246401e5f1dc34347
[17:20:23]          Current inode: 8390092    Stored inode: 8398743
[17:20:23]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:23]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:23] /usr/sbin/groupdel                                [ Warning ]
[17:20:23] Warning: The file properties have changed:
[17:20:23]          File: /usr/sbin/groupdel
[17:20:23]          Current hash: 56aacc3944251bb90f62a8b07bfb26d3ec461290
[17:20:23]          Stored hash : b82e70b0fa073a246acd9a38d2dc390ec5d1da70
[17:20:23]          Current inode: 8390787    Stored inode: 8398744
[17:20:23]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:23]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:23] /usr/sbin/groupmod                                [ Warning ]
[17:20:23] Warning: The file properties have changed:
[17:20:23]          File: /usr/sbin/groupmod
[17:20:23]          Current hash: 14986f28df8a51f7d1bedf58436ed964c892dc03
[17:20:23]          Stored hash : c926dd68bb84106b842c016a5cecc261e216362e
[17:20:23]          Current inode: 8394631    Stored inode: 8398745
[17:20:23]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:23]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:23] /usr/sbin/grpck                                   [ Warning ]
[17:20:23] Warning: The file properties have changed:
[17:20:23]          File: /usr/sbin/grpck
[17:20:23]          Current hash: 859940113007639652052fdd907cedd40ab232ea
[17:20:23]          Stored hash : 5534b46a3b439ebccf26e617f57944ea4c1a3d40
[17:20:23]          Current inode: 8394632    Stored inode: 8398746
[17:20:23]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:24]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:24] /usr/sbin/nologin                                 [ Warning ]
[17:20:24] Warning: The file properties have changed:
[17:20:24]          File: /usr/sbin/nologin
[17:20:24]          Current hash: 9a95253cdcf4139962c9d948af35d13e928f6bd7
[17:20:24]          Stored hash : cc8decc7c1c6fdfd7dbd7d3f14f6ea546f9b4edb
[17:20:24]          Current inode: 8389789    Stored inode: 8398802
[17:20:24]          Current file modification time: 1297721482 (14-Feb-2011 16:11:22)
[17:20:24]          Stored file modification time : 1264525785 (26-Jan-2010 11:09:45)
[17:20:24] /usr/sbin/pwck                                    [ Warning ]
[17:20:24] Warning: The file properties have changed:
[17:20:24]          File: /usr/sbin/pwck
[17:20:24]          Current hash: 03529084f7eb3ee517c779b69b67b46d464164a3
[17:20:24]          Stored hash : a984bcd9f369a768cf9b6aa51e273d2299865646
[17:20:24]          Current inode: 8394636    Stored inode: 8398829
[17:20:24]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:24]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:25] /usr/sbin/rsyslogd                                [ OK ]
[17:20:25] /usr/sbin/tcpd                                    [ OK ]
[17:20:25] /usr/sbin/useradd                                 [ Warning ]
[17:20:25] Warning: The file properties have changed:
[17:20:25]          File: /usr/sbin/useradd
[17:20:25]          Current hash: f7c92b5ff4eb606f2b38c2b1d97cf5da7fb2b722
[17:20:25]          Stored hash : c1de7c5992a668a02f307f8444a85a4e6f98a004
[17:20:25]          Current inode: 8394639    Stored inode: 8398902
[17:20:25]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:25]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:25] /usr/sbin/userdel                                 [ Warning ]
[17:20:25] Warning: The file properties have changed:
[17:20:25]          File: /usr/sbin/userdel
[17:20:25]          Current hash: e55fbf6c2ebd789ec0d27e5311d37a119d662283
[17:20:25]          Stored hash : 8655e4d47b79b5358a39aaaa9d419f71e0bf3d5d
[17:20:25]          Current inode: 8394640    Stored inode: 8398903
[17:20:25]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:25]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:26] /usr/sbin/usermod                                 [ Warning ]
[17:20:26] Warning: The file properties have changed:
[17:20:26]          File: /usr/sbin/usermod
[17:20:26]          Current hash: d7b450301ea8991cc196af8bd9422766188410e5
[17:20:26]          Stored hash : 9fcfe3e8b08576e4cc97a9aa03b4df1944c0a023
[17:20:26]          Current inode: 8394641    Stored inode: 8398904
[17:20:26]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:26]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:26] /usr/sbin/vipw                                    [ Warning ]
[17:20:26] Warning: The file properties have changed:
[17:20:26]          File: /usr/sbin/vipw
[17:20:26]          Current hash: fbc5ca38d299484ed3e0ee09c6e92497a71ae58b
[17:20:26]          Stored hash : d8486ae5f7a92ef181d7378b9e5ea2c82e1caf89
[17:20:26]          Current inode: 8394642    Stored inode: 8398911
[17:20:26]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:26]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
[17:20:26] /usr/sbin/unhide-linux26                          [ OK ]
[17:20:51]
[17:20:51] Checking for rootkits...
[17:20:51] Info: Starting test name 'rootkits'
[17:20:51]
[17:20:51] Performing check of known rootkit files and directories
[17:20:51] Info: Starting test name 'known_rkts'
[17:20:51]
[17:20:51] Checking for 55808 Trojan - Variant A...
[17:20:51]   Checking for file '/tmp/.../r'                  [ Not found ]
[17:20:51]   Checking for file '/tmp/.../a'                  [ Not found ]
[17:20:51] 55808 Trojan - Variant A                          [ Not found ]
[17:20:51]
[17:20:51] Checking for ADM Worm...
[17:20:51]   Checking for string 'w0rm'                      [ Not found ]
[17:20:51] ADM Worm                                          [ Not found ]
[17:20:51]
[17:20:51] Checking for AjaKit Rootkit...
[17:20:51]   Checking for file '/dev/tux/.addr'              [ Not found ]
[17:20:51]   Checking for file '/dev/tux/.proc'              [ Not found ]
[17:20:51]   Checking for file '/dev/tux/.file'              [ Not found ]
[17:20:51]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[17:20:51]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[17:20:51]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[17:20:51]   Checking for directory '/dev/tux'               [ Not found ]
[17:20:52]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[17:20:52] AjaKit Rootkit                                    [ Not found ]
[17:20:52]
[17:20:52] Checking for Adore Rootkit...
[17:20:52]   Checking for file '/usr/secure'                 [ Not found ]
[17:20:52]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[17:20:52]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[17:20:52]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[17:20:52]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[17:20:52]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[17:20:52]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[17:20:52]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[17:20:52]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[17:20:52]   Checking for file '/var/log/ssh/old'            [ Not found ]
[17:20:52]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/kern'          [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/backup'        [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[17:20:52]   Checking for directory '/lib/backup'            [ Not found ]
[17:20:52]   Checking for directory '/lib/backup/txt'        [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/work'          [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/sys'           [ Not found ]
[17:20:52]   Checking for directory '/var/log/ssh'           [ Not found ]
[17:20:52]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[17:20:52]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[17:20:52] Adore Rootkit                                     [ Not found ]
[17:20:52]
[17:20:52] Checking for aPa Kit...
[17:20:52]   Checking for file '/usr/share/.aPa'             [ Not found ]
[17:20:52] aPa Kit                                           [ Not found ]
[17:20:52]
[17:20:52] Checking for Apache Worm...
[17:20:52]   Checking for file '/bin/.log'                   [ Not found ]
[17:20:52] Apache Worm                                       [ Not found ]
[17:20:52]
[17:20:52] Checking for Ambient (ark) Rootkit...
[17:20:52]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[17:20:52]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[17:20:52]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[17:20:53]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[17:20:53]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[17:20:53]   Checking for directory '/dev/ptyxx'             [ Not found ]
[17:20:53] Ambient (ark) Rootkit                             [ Not found ]
[17:20:53]
[17:20:53] Checking for Balaur Rootkit...
[17:20:53]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[17:20:53]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[17:20:53]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[17:20:53]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[17:20:53] Balaur Rootkit                                    [ Not found ]
[17:20:53]
[17:20:53] Checking for BeastKit Rootkit...
[17:20:53]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[17:20:53]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[17:20:53]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[17:20:53]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[17:20:53] BeastKit Rootkit                                  [ Not found ]
[17:20:53]
[17:20:53] Checking for beX2 Rootkit...
[17:20:53]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[17:20:53]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[17:20:53]   Checking for directory '/usr/include/bex'       [ Not found ]
[17:20:53] beX2 Rootkit                                      [ Not found ]
[17:20:53]
[17:20:53] Checking for BOBKit Rootkit...
[17:20:53]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[17:20:53]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[17:20:53]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[17:20:53]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[17:20:53]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[17:20:53]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[17:20:53]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[17:20:54]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[17:20:54]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[17:20:54]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[17:20:54]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../find'           [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../du'             [ Not found ]
[17:20:54]   Checking for file '/usr/lib/.../top'            [ Not found ]
[17:20:54]   Checking for directory '/usr/sbin/...'          [ Not found ]
[17:20:54]   Checking for directory '/usr/include/...'       [ Not found ]
[17:20:54]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[17:20:54]   Checking for directory '/usr/lib/...'           [ Not found ]
[17:20:54]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[17:20:54]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[17:20:54]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[17:20:54]   Checking for directory '/tmp/.bkp'              [ Not found ]
[17:20:54] BOBKit Rootkit                                    [ Not found ]
[17:20:54]
[17:20:54] Checking for cb Rootkit...
[17:20:54]   Checking for file '/dev/srd0'                   [ Not found ]
[17:20:54]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[17:20:55]   Checking for file '/dev/mounnt'                 [ Not found ]
[17:20:55]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /cl'       [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /.x.tgz'   [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /statdx'   [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /wted'     [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /write'    [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /scan'     [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /sc'       [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /sl2'      [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /wroot'    [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /wscan'    [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /wu'       [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /v'        [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /read'     [ Not found ]
[17:20:55]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[17:20:55]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[17:20:55]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[17:20:55]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[17:20:55]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[17:20:55]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[17:20:55]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[17:20:55]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.system/.. /tcp.log' [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /curatare/attrib' [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /curatare/chattr' [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /curatare/ps' [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.zeen/.. /curatare/pstree' [ Not found ]
[17:20:55]   Checking for file '/usr/bin/.system/.. /.x/xC.o' [ Not found ]
[17:20:55]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[17:20:55]   Checking for directory '/usr/bin/.zeen/.. /curatare' [ Not found ]
[17:20:55]   Checking for directory '/usr/bin/.zeen/.. /scan' [ Not found ]
[17:20:55]   Checking for directory '/usr/bin/.system/.. '   [ Not found ]
[17:20:55] cb Rootkit                                        [ Not found ]
[17:20:56]
[17:20:56] Checking for CiNIK Worm (Slapper.B variant)...
[17:20:56]   Checking for file '/tmp/.cinik'                 [ Not found ]
[17:20:56]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[17:20:56] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[17:20:56]
[17:20:56] Checking for Danny-Boy's Abuse Kit...
[17:20:56]   Checking for file '/dev/mdev'                   [ Not found ]
[17:20:56]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[17:20:56] Danny-Boy's Abuse Kit                             [ Not found ]
[17:20:56]
[17:20:56] Checking for Devil RootKit...
[17:20:56]   Checking for file '/var/lib/games/.src'         [ Not found ]
[17:20:56]   Checking for file '/dev/dsx'                    [ Not found ]
[17:20:56]   Checking for file '/dev/caca'                   [ Not found ]
[17:20:56]   Checking for file '/dev/pro'                    [ Not found ]
[17:20:56]   Checking for file '/bin/bye'                    [ Not found ]
[17:20:56]   Checking for file '/bin/homedir'                [ Not found ]
[17:20:56]   Checking for file '/usr/bin/xfss'               [ Not found ]
[17:20:56]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[17:20:56]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[17:20:57]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[17:20:57]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[17:20:57] Devil RootKit                                     [ Not found ]
[17:20:57]
[17:20:57] Checking for Dica-Kit Rootkit...
[17:20:57]   Checking for file '/lib/.sso'                   [ Not found ]
[17:20:57]   Checking for file '/lib/.so'                    [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/read'       [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/write'      [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/va'         [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[17:20:57]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[17:20:57]   Checking for file '/usr/bin/.etc'               [ Not found ]
[17:20:57]   Checking for file '/etc/sshd_config'            [ Not found ]
[17:20:57]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[17:20:57]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[17:20:57]   Checking for directory '/var/run/...dica'       [ Not found ]
[17:20:57]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[17:20:57]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[17:20:57] Dica-Kit Rootkit                                  [ Not found ]
[17:20:57]
[17:20:57] Checking for Dreams Rootkit...
[17:20:57]   Checking for file '/dev/ttyoa'                  [ Not found ]
[17:20:57]   Checking for file '/dev/ttyof'                  [ Not found ]
[17:20:57]   Checking for file '/dev/ttyop'                  [ Not found ]
[17:20:57]   Checking for file '/usr/bin/sense'              [ Not found ]
[17:20:57]   Checking for file '/usr/bin/sl2'                [ Not found ]
[17:20:58]   Checking for file '/usr/bin/logclear'           [ Not found ]
[17:20:58]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[17:20:58]   Checking for file '/usr/bin/initrd'             [ Not found ]
[17:20:58]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[17:20:58]   Checking for file '/usr/bin/snfs'               [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libsss'             [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[17:20:58]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[17:20:58]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[17:20:58]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[17:20:58]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[17:20:58]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[17:20:58]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[17:20:58]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[17:20:58]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[17:20:58]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[17:20:58]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[17:20:58]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[17:20:58] Dreams Rootkit                                    [ Not found ]
[17:20:58]
[17:20:58] Checking for Duarawkz Rootkit...
[17:20:58]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[17:20:58]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[17:20:58] Duarawkz Rootkit                                  [ Not found ]
[17:20:58]
[17:20:58] Checking for Enye LKM...
[17:20:58]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[17:20:58]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[17:20:58] Enye LKM                                          [ Not found ]
[17:20:58]
[17:20:58] Checking for Flea Linux Rootkit...
[17:20:59]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[17:20:59]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[17:20:59]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[17:20:59]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[17:20:59]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[17:20:59]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[17:20:59]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[17:20:59]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[17:20:59]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[17:20:59]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[17:20:59]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[17:20:59]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[17:20:59]   Checking for directory '/dev/..0'               [ Not found ]
[17:20:59]   Checking for directory '/dev/..0/backup'        [ Not found ]
[17:20:59] Flea Linux Rootkit                                [ Not found ]
[17:20:59]
[17:20:59] Checking for FreeBSD Rootkit...
[17:20:59]   Checking for file '/dev/ptyp'                   [ Not found ]
[17:20:59]   Checking for file '/dev/ptyq'                   [ Not found ]
[17:20:59]   Checking for file '/dev/ptyr'                   [ Not found ]
[17:20:59]   Checking for file '/dev/ptys'                   [ Not found ]
[17:20:59]   Checking for file '/dev/ptyt'                   [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.88/freshb-bsd'      [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.88/fresht'          [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.88/zxsniff'         [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.88/zxsniff.log'     [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.99/.ttyf00'         [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.99/.ttyp00'         [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.99/.ttyq00'         [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.99/.ttys00'         [ Not found ]
[17:20:59]   Checking for file '/dev/fd/.99/.pwsx00'         [ Not found ]
[17:20:59]   Checking for file '/etc/.acid'                  [ Not found ]
[17:20:59]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[17:20:59]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/setrgrp.2'      [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/TOHIDE'         [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/adore/ava/ava'  [ Not found ]
[17:21:00]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[17:21:00]   Checking for file '/bin/sysback'                [ Not found ]
[17:21:00]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[17:21:00]   Checking for directory '/dev/fd/.88'            [ Not found ]
[17:21:00]   Checking for directory '/dev/fd/.99'            [ Not found ]
[17:21:00]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[17:21:00]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[17:21:00] FreeBSD Rootkit                                   [ Not found ]
[17:21:00]
[17:21:00] Checking for Fu Rootkit...
[17:21:00]   Checking for file '/sbin/xc'                    [ Not found ]
[17:21:00]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[17:21:00]   Checking for file '/bin/.lib'                   [ Not found ]
[17:21:00] Fu Rootkit                                        [ Not found ]
[17:21:00]
[17:21:00] Checking for ****`it Rootkit...
[17:21:00]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[17:21:00]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[17:21:00]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[17:21:00]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[17:21:00]   Checking for file '/dev/proc/fuckit/system-bins/init' [ Not found ]
[17:21:00]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[17:21:00]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[17:21:01]   Checking for directory '/dev/proc'              [ Not found ]
[17:21:01]   Checking for directory '/dev/proc/fuckit'       [ Not found ]
[17:21:01]   Checking for directory '/dev/proc/fuckit/system-bins' [ Not found ]
[17:21:01]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[17:21:01] ****`it Rootkit                                   [ Not found ]
[17:21:01]
[17:21:01] Checking for GasKit Rootkit...
[17:21:01]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[17:21:01]   Checking for directory '/dev/dev'               [ Not found ]
[17:21:01]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[17:21:01]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[17:21:01] GasKit Rootkit                                    [ Not found ]
[17:21:01]
[17:21:01] Checking for Heroin LKM...
[17:21:01]   Checking for kernel symbol 'heroin'             [ Not found ]
[17:21:01] Heroin LKM                                        [ Not found ]
[17:21:01]
[17:21:01] Checking for HjC Kit...
[17:21:01]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[17:21:01] HjC Kit                                           [ Not found ]
[17:21:01]
[17:21:01] Checking for ignoKit Rootkit...
[17:21:01]   Checking for file '/lib/defs/p'                 [ Not found ]
[17:21:01]   Checking for file '/lib/defs/q'                 [ Not found ]
[17:21:01]   Checking for file '/lib/defs/r'                 [ Not found ]
[17:21:01]   Checking for file '/lib/defs/s'                 [ Not found ]
[17:21:01]   Checking for file '/lib/defs/t'                 [ Not found ]
[17:21:01]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[17:21:01]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[17:21:01]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[17:21:01]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[17:21:01]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[17:21:01]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[17:21:01]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[17:21:01]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[17:21:01]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[17:21:01] ignoKit Rootkit                                   [ Not found ]
[17:21:02]
[17:21:02] Checking for iLLogiC Rootkit...
[17:21:02]   Checking for file '/dev/kmod'                   [ Not found ]
[17:21:02]   Checking for file '/dev/dos'                    [ Not found ]
[17:21:02]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[17:21:02]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[17:21:02]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[17:21:02]   Checking for file '/usr/bin/sia'                [ Not found ]
[17:21:02]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/iver'  [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/uconf.inv' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/ssh/sshport' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/ava'   [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/cleaner' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/sz'    [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/rcp'   [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/patcher' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/pg'    [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/crypt' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/utime' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/wget'  [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/instmod' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/find' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/du' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/ls' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/psr' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/netstat' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/su' [ Not found ]
[17:21:02]   Checking for file '/lib/security/.config/bin/ping' [ Not found ]
[17:21:03]   Checking for file '/lib/security/.config/bin/passwd' [ Not found ]
[17:21:03]   Checking for directory '/lib/security/.config'  [ Not found ]
[17:21:03]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[17:21:03]   Checking for directory '/lib/security/.config/bin' [ Not found ]
[17:21:03]   Checking for directory '/lib/security/.config/backup' [ Not found ]
[17:21:03]   Checking for directory '/root/   /.dir'         [ Not found ]
[17:21:03]   Checking for directory '/root/   /.dir/mass-scan' [ Not found ]
[17:21:03]   Checking for directory '/root/   /.dir/flood'   [ Not found ]
[17:21:03] iLLogiC Rootkit                                   [ Not found ]
[17:21:03]
[17:21:03] Checking for IntoXonia-NG Rootkit...
[17:21:03]   Checking for kernel symbol 'funces'             [ Not found ]
[17:21:03]   Checking for kernel symbol 'ixinit'             [ Not found ]
[17:21:03]   Checking for kernel symbol 'tricks'             [ Not found ]
[17:21:03]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[17:21:03]   Checking for kernel symbol 'rootme'             [ Not found ]
[17:21:03]   Checking for kernel symbol 'hide_module'        [ Not found ]
[17:21:03]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[17:21:03] IntoXonia-NG Rootkit                              [ Not found ]
[17:21:03]
[17:21:03] Checking for Irix Rootkit...
[17:21:03]   Checking for directory '/dev/pts/01'            [ Not found ]
[17:21:03]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[17:21:03]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[17:21:04]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[17:21:04] Irix Rootkit                                      [ Not found ]
[17:21:04]
[17:21:04] Checking for Kitko Rootkit...
[17:21:04]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[17:21:04] Kitko Rootkit                                     [ Not found ]
[17:21:04]
[17:21:04] Checking for Knark Rootkit...
[17:21:04]   Checking for file '/proc/knark/pids'            [ Not found ]
[17:21:04]   Checking for directory '/proc/knark'            [ Not found ]
[17:21:04] Knark Rootkit                                     [ Not found ]
[17:21:04]
[17:21:04] Checking for ld-linuxv.so Rootkit...
[17:21:04]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[17:21:04]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[17:21:04]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[17:21:04]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[17:21:04] ld-linuxv.so Rootkit                              [ Not found ]
[17:21:04]
[17:21:04] Checking for Li0n Worm...
[17:21:04]   Checking for file '/bin/in.telnetd'             [ Not found ]
[17:21:04]   Checking for file '/bin/mjy'                    [ Not found ]
[17:21:04]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[17:21:04]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[17:21:04]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[17:21:04]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[17:21:05]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[17:21:05]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[17:21:05] Li0n Worm                                         [ Not found ]
[17:21:05]
[17:21:05] Checking for Lockit / LJK2 Rootkit...
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[17:21:05]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[17:21:06]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[17:21:06]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[17:21:06]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[17:21:06]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[17:21:06]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[17:21:06] Lockit / LJK2 Rootkit                             [ Not found ]
[17:21:06]
[17:21:06] Checking for Mood-NT Rootkit...
[17:21:06]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[17:21:06]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[17:21:06]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[17:21:06]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[17:21:06]   Checking for directory '/_cthulhu'              [ Not found ]
[17:21:06] Mood-NT Rootkit                                   [ Not found ]
[17:21:06]
[17:21:06] Checking for MRK Rootkit...
[17:21:06]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[17:21:06]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[17:21:06]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[17:21:06]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[17:21:06]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[17:21:06]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[17:21:06] MRK Rootkit                                       [ Not found ]
[17:21:06]
[17:21:06] Checking for Ni0 Rootkit...
[17:21:06]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[17:21:06]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[17:21:06]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[17:21:06]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[17:21:06]   Checking for directory '/tmp/waza'              [ Not found ]
[17:21:06]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:06]   Checking for directory '/usr/sbin/es'           [ Not found ]
[17:21:06] Ni0 Rootkit                                       [ Not found ]
[17:21:06]
[17:21:06] Checking for Ohhara Rootkit...
[17:21:06]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[17:21:06]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:06]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[17:21:06]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[17:21:06]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[17:21:07]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[17:21:07]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[17:21:07] Ohhara Rootkit                                    [ Not found ]
[17:21:07]
[17:21:07] Checking for Optic Kit (Tux) Worm...
[17:21:07]   Checking for directory '/dev/tux'               [ Not found ]
[17:21:07]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[17:21:07]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[17:21:07]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[17:21:07] Optic Kit (Tux) Worm                              [ Not found ]
[17:21:07]
[17:21:07] Checking for Oz Rootkit...
[17:21:07]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[17:21:07]   Checking for directory '/dev/.oz'               [ Not found ]
[17:21:07] Oz Rootkit                                        [ Not found ]
[17:21:07]
[17:21:07] Checking for Phalanx Rootkit...
[17:21:07]   Checking for file '/uNFuNF'                     [ Not found ]
[17:21:07]   Checking for file '/etc/host.ph1'               [ Not found ]
[17:21:07]   Checking for file '/bin/host.ph1'               [ Not found ]
[17:21:07]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[17:21:07]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[17:21:07]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[17:21:07]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[17:21:07]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[17:21:07] Phalanx Rootkit                                   [ Not found ]
[17:21:07]
[17:21:07] Checking for Phalanx2 Rootkit...
[17:21:07]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[17:21:07]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[17:21:07]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[17:21:07]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[17:21:07]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[17:21:07]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[17:21:07]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[17:21:07]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[17:21:07]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[17:21:07]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[17:21:08]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[17:21:08]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[17:21:08]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[17:21:08]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[17:21:08] Phalanx2 Rootkit                                  [ Not found ]
[17:21:08]
[17:21:08] Checking for Phalanx2 Rootkit (extended tests)...
[17:21:08]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[17:21:08]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[17:21:08]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[17:21:08]   Checking process list for process 'ata/0'       [ OK ]
[17:21:08] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[17:21:08]
[17:21:08] Checking for Portacelo Rootkit...
[17:21:08]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../.p'             [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../getty'          [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../show'           [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[17:21:08]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[17:21:08]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[17:21:08] Portacelo Rootkit                                 [ Not found ]
[17:21:08]
[17:21:08] Checking for R3dstorm Toolkit...
[17:21:08]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[17:21:08]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[17:21:08]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[17:21:08]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[17:21:08]   Checking for file '/bin/.../see_all'            [ Not found ]
[17:21:08]   Checking for directory '/var/log/tk02'          [ Not found ]
[17:21:09]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[17:21:09]   Checking for directory '/bin/...'               [ Not found ]
[17:21:09] R3dstorm Toolkit                                  [ Not found ]
[17:21:09]
[17:21:09] Checking for RH-Sharpe's Rootkit...
[17:21:09]   Checking for file '/bin/lps'                    [ Not found ]
[17:21:09]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[17:21:09]   Checking for file '/usr/bin/ltop'               [ Not found ]
[17:21:09]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[17:21:09]   Checking for file '/usr/bin/ldu'                [ Not found ]
[17:21:09]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[17:21:09]   Checking for file '/usr/bin/wp'                 [ Not found ]
[17:21:09]   Checking for file '/usr/bin/shad'               [ Not found ]
[17:21:09]   Checking for file '/usr/bin/vadim'              [ Not found ]
[17:21:09]   Checking for file '/usr/bin/slice'              [ Not found ]
[17:21:09]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[17:21:09]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[17:21:09] RH-Sharpe's Rootkit                               [ Not found ]
[17:21:09]
[17:21:09] Checking for RSHA's Rootkit...
[17:21:09]   Checking for file '/bin/kr4p'                   [ Not found ]
[17:21:09]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[17:21:09]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[17:21:09]   Checking for file '/usr/bin/slice2'             [ Not found ]
[17:21:09]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[17:21:09]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[17:21:09]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[17:21:09]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[17:21:09] RSHA's Rootkit                                    [ Not found ]
[17:21:09]
[17:21:09] Checking for Scalper Worm...
[17:21:09]   Checking for file '/tmp/.a'                     [ Not found ]
[17:21:09]   Checking for file '/tmp/.uua'                   [ Not found ]
[17:21:09] Scalper Worm                                      [ Not found ]
[17:21:09]
[17:21:09] Checking for Sebek LKM...
[17:21:10]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[17:21:10] Sebek LKM                                         [ Not found ]
[17:21:10]
[17:21:10] Checking for Shutdown Rootkit...
[17:21:10]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[17:21:10]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[17:21:10]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[17:21:10]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[17:21:10]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[17:21:10]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[17:21:10]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[17:21:10]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[17:21:10] Shutdown Rootkit                                  [ Not found ]
[17:21:10]
[17:21:10] Checking for SHV4 Rootkit...
[17:21:10]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[17:21:10]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[17:21:10]   Checking for file '/lib/lidps1.so'              [ Not found ]
[17:21:10]   Checking for file '/lib/libproc.a'              [ Not found ]
[17:21:10]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[17:21:10]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[17:21:10]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[17:21:10]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[17:21:10]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[17:21:10]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[17:21:10]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[17:21:10]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[17:21:11]   Checking for file '/usr/include/file.h'         [ Not found ]
[17:21:11]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[17:21:11]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[17:21:11]   Checking for file '/usr/include/log.h'          [ Not found ]
[17:21:11]   Checking for file '/usr/include/proc.h'         [ Not found ]
[17:21:11]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[17:21:11]   Checking for file '/dev/srd0'                   [ Not found ]
[17:21:11]   Checking for directory '/lib/ldd.so'            [ Not found ]
[17:21:11]   Checking for directory '/lib/security/.config'  [ Not found ]
[17:21:11]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[17:21:11] SHV4 Rootkit                                      [ Not found ]
[17:21:11]
[17:21:11] Checking for SHV5 Rootkit...
[17:21:11]   Checking for file '/etc/sh.conf'                [ Not found ]
[17:21:11]   Checking for file '/lib/libproc.a'              [ Not found ]
[17:21:11]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[17:21:11]   Checking for file '/lib/lidps1.so'              [ Not found ]
[17:21:11]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[17:21:11]   Checking for file '/usr/include/file.h'         [ Not found ]
[17:21:11]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[17:21:11]   Checking for file '/usr/include/log.h'          [ Not found ]
[17:21:11]   Checking for file '/usr/include/proc.h'         [ Not found ]
[17:21:11]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[17:21:11]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[17:21:11]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[17:21:11]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[17:21:11]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[17:21:11]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[17:21:11]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[17:21:11]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[17:21:11]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[17:21:11]   Checking for file '/dev/srd0'                   [ Not found ]
[17:21:11]   Checking for directory '/lib/libsh.so'          [ Not found ]
[17:21:11]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[17:21:12]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[17:21:12]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[17:21:12] SHV5 Rootkit                                      [ Not found ]
[17:21:12]
[17:21:12] Checking for Sin Rootkit...
[17:21:12]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[17:21:12]   Checking for file '/dev/ttyoa'                  [ Not found ]
[17:21:12]   Checking for file '/dev/ttyof'                  [ Not found ]
[17:21:12]   Checking for file '/dev/ttyop'                  [ Not found ]
[17:21:12]   Checking for file '/dev/ttyos'                  [ Not found ]
[17:21:12]   Checking for file '/usr/lib/.lib'               [ Not found ]
[17:21:12]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[17:21:12]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[17:21:12]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[17:21:12]   Checking for file '/usr/man/man1/...'           [ Not found ]
[17:21:12]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[17:21:12]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[17:21:12]   Checking for directory '/usr/lib/sn'            [ Not found ]
[17:21:12]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[17:21:12]   Checking for directory '/dev/.haos'             [ Not found ]
[17:21:12] Sin Rootkit                                       [ Not found ]
[17:21:12]
[17:21:12] Checking for Slapper Worm...
[17:21:12]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[17:21:12]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[17:21:12]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[17:21:12]   Checking for file '/tmp/httpd'                  [ Not found ]
[17:21:12]   Checking for file '/tmp/.unlock'                [ Not found ]
[17:21:12]   Checking for file '/tmp/update'                 [ Not found ]
[17:21:12]   Checking for file '/tmp/.cinik'                 [ Not found ]
[17:21:12]   Checking for file '/tmp/.b'                     [ Not found ]
[17:21:12] Slapper Worm                                      [ Not found ]
[17:21:12]
[17:21:12] Checking for Sneakin Rootkit...
[17:21:12]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[17:21:12] Sneakin Rootkit                                   [ Not found ]
[17:21:13]
[17:21:13] Checking for 'Spanish' Rootkit...
[17:21:13]   Checking for file '/dev/ptyq'                   [ Not found ]
[17:21:13]   Checking for file '/bin/ad'                     [ Not found ]
[17:21:13]   Checking for file '/bin/ava'                    [ Not found ]
[17:21:13]   Checking for file '/bin/server'                 [ Not found ]
[17:21:13]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[17:21:13]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[17:21:13]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[17:21:13]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[17:21:13]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[17:21:13]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[17:21:13]   Checking for directory '/usr/share/...'         [ Not found ]
[17:21:13] 'Spanish' Rootkit                                 [ Not found ]
[17:21:13]
[17:21:13] Checking for Suckit Rootkit...
[17:21:13]   Checking for file '/sbin/initsk12'              [ Not found ]
[17:21:13]   Checking for file '/sbin/initxrk'               [ Not found ]
[17:21:13]   Checking for file '/usr/bin/null'               [ Not found ]
[17:21:13]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[17:21:13]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[17:21:14]   Checking for directory '/etc/.MG'               [ Not found ]
[17:21:14]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[17:21:14]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[17:21:14] Suckit Rootkit                                    [ Not found ]
[17:21:14]
[17:21:14] Checking for SunOS Rootkit...
[17:21:14]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[17:21:14]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[17:21:14]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[17:21:14]   Checking for file '/bin/xlogin'                 [ Not found ]
[17:21:14]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[17:21:14]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[17:21:14]   Checking for file '/sbin/login'                 [ Not found ]
[17:21:14]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[17:21:14]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[17:21:14]   Checking for file '/dev/kmod'                   [ Not found ]
[17:21:14]   Checking for file '/dev/dos'                    [ Not found ]
[17:21:14] SunOS Rootkit                                     [ Not found ]
[17:21:14]
[17:21:14] Checking for SunOS / NSDAP Rootkit...
[17:21:14]   Checking for file '/dev/pts/01/55su'            [ Not found ]
[17:21:14]   Checking for file '/dev/pts/01/55ps'            [ Not found ]
[17:21:14]   Checking for file '/dev/pts/01/55ping'          [ Not found ]
[17:21:14]   Checking for file '/dev/pts/01/55login'         [ Not found ]
[17:21:14]   Checking for file '/dev/pts/01/PATCHER_COMPLETED' [ Not found ]
[17:21:14]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[17:21:14]   Checking for file '/dev/prom/dos'               [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[17:21:14]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[17:21:15]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[17:21:15]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[17:21:15]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[17:21:15]   Checking for file '/usr/lib/lpset'              [ Not found ]
[17:21:15]   Checking for file '/usr/lib/lpstart'            [ Not found ]
[17:21:15]   Checking for file '/usr/bin/mc68000'            [ Not found ]
[17:21:15]   Checking for file '/usr/bin/mc68010'            [ Not found ]
[17:21:15]   Checking for file '/usr/bin/mc68020'            [ Not found ]
[17:21:15]   Checking for file '/usr/ucb/bin/ps'             [ Not found ]
[17:21:15]   Checking for file '/usr/bin/m68k'               [ Not found ]
[17:21:15]   Checking for file '/usr/bin/sun2'               [ Not found ]
[17:21:15]   Checking for file '/usr/bin/mc68030'            [ Not found ]
[17:21:15]   Checking for file '/usr/bin/mc68040'            [ Not found ]
[17:21:15]   Checking for file '/usr/bin/sun3'               [ Not found ]
[17:21:15]   Checking for file '/usr/bin/sun3x'              [ Not found ]
[17:21:15]   Checking for file '/usr/bin/lso'                [ Not found ]
[17:21:15]   Checking for file '/usr/bin/u370'               [ Not found ]
[17:21:15]   Checking for directory '/dev/pts/01'            [ Not found ]
[17:21:15]   Checking for directory '/dev/prom'              [ Not found ]
[17:21:15]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[17:21:15]   Checking for directory '/.pat'                  [ Not found ]
[17:21:15] SunOS / NSDAP Rootkit                             [ Not found ]
[17:21:15]
[17:21:15] Checking for Superkit Rootkit...
[17:21:15]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[17:21:15]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[17:21:15]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[17:21:15]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[17:21:15]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[17:21:15] Superkit Rootkit                                  [ Not found ]
[17:21:15]
[17:21:15] Checking for TBD (Telnet BackDoor)...
[17:21:15]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[17:21:15] TBD (Telnet BackDoor)                             [ Not found ]
[17:21:15]
[17:21:15] Checking for TeLeKiT Rootkit...
[17:21:15]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[17:21:16]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[17:21:16]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[17:21:16]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[17:21:16]   Checking for file '/dev/ptyr'                   [ Not found ]
[17:21:16]   Checking for file '/dev/ptyp'                   [ Not found ]
[17:21:16]   Checking for file '/dev/ptyq'                   [ Not found ]
[17:21:16]   Checking for file '/dev/hda06'                  [ Not found ]
[17:21:16]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[17:21:16]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[17:21:16]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[17:21:16]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[17:21:16] TeLeKiT Rootkit                                   [ Not found ]
[17:21:16]
[17:21:16] Checking for T0rn Rootkit...
[17:21:16]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[17:21:16]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[17:21:17]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[17:21:17]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[17:21:17]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[17:21:17]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[17:21:17]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[17:21:17]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[17:21:17]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[17:21:17]   Checking for directory '/dev/.lib'              [ Not found ]
[17:21:17]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[17:21:17]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[17:21:17]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[17:21:17]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[17:21:17]   Checking for directory '/usr/src/.puta'         [ Not found ]
[17:21:17]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[17:21:17]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[17:21:17]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[17:21:17]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[17:21:17] T0rn Rootkit                                      [ Not found ]
[17:21:17]
[17:21:17] Checking for trNkit Rootkit...
[17:21:17]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[17:21:17]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[17:21:17]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[17:21:18]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[17:21:18]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[17:21:18]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[17:21:18] trNkit Rootkit                                    [ Not found ]
[17:21:18]
[17:21:18] Checking for Trojanit Kit...
[17:21:18]   Checking for file '/bin/.ls'                    [ Not found ]
[17:21:18]   Checking for file '/bin/.ps'                    [ Not found ]
[17:21:18]   Checking for file '/bin/.netstat'               [ Not found ]
[17:21:18]   Checking for file '/usr/bin/.nop'               [ Not found ]
[17:21:18]   Checking for file '/usr/bin/.who'               [ Not found ]
[17:21:18] Trojanit Kit                                      [ Not found ]
[17:21:18]
[17:21:18] Checking for Tuxtendo Rootkit...
[17:21:18]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[17:21:18]   Checking for file '/usr/bin/xchk'               [ Not found ]
[17:21:18]   Checking for file '/usr/bin/xsf'                [ Not found ]
[17:21:18]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.addr'              [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.cron'              [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.file'              [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.log'               [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.proc'              [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.iface'             [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.pw'                [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.df'                [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[17:21:18]   Checking for file '/dev/tux/.tux'               [ Not found ]
[17:21:18]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[17:21:18]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[17:21:18]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[17:21:18]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[17:21:18]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[17:21:18]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[17:21:18]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[17:21:19]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[17:21:19]   Checking for directory '/dev/tux'               [ Not found ]
[17:21:19]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[17:21:19]   Checking for directory '/dev/tux/backup'        [ Not found ]
[17:21:19] Tuxtendo Rootkit                                  [ Not found ]
[17:21:19]
[17:21:19] Checking for URK Rootkit...
[17:21:19]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[17:21:19]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[17:21:19]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[17:21:19]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[17:21:20]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[17:21:20]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[17:21:20]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[17:21:20]   Checking for file '/tmp/conf.inv'               [ Not found ]
[17:21:20]   Checking for directory '/dev/prom'              [ Not found ]
[17:21:20]   Checking for directory '/dev/pts/01'            [ Not found ]
[17:21:20]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[17:21:20]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[17:21:20] URK Rootkit                                       [ Not found ]
[17:21:20]
[17:21:20] Checking for Vampire Rootkit...
[17:21:20]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[17:21:20]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[17:21:20]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[17:21:20]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[17:21:20] Vampire Rootkit                                   [ Not found ]
[17:21:20]
[17:21:20] Checking for VcKit Rootkit...
[17:21:21]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[17:21:21]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[17:21:21] VcKit Rootkit                                     [ Not found ]
[17:21:21]
[17:21:21] Checking for Volc Rootkit...
[17:21:21]   Checking for file '/usr/bin/volc'               [ Not found ]
[17:21:21]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[17:21:21]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[17:21:21]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[17:21:21]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[17:21:21]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[17:21:21]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[17:21:21]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[17:21:21]   Checking for directory '/var/spool/.recent'     [ Not found ]
[17:21:21]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[17:21:21]   Checking for directory '/usr/lib/volc'          [ Not found ]
[17:21:21]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[17:21:21] Volc Rootkit                                      [ Not found ]
[17:21:21]
[17:21:21] Checking for Xzibit Rootkit...
[17:21:21]   Checking for file '/dev/dsx'                    [ Not found ]
[17:21:21]   Checking for file '/dev/caca'                   [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[17:21:21]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[17:21:21]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[17:21:21]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[17:21:21]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[17:21:21]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[17:21:22]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[17:21:22]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[17:21:22] Xzibit Rootkit                                    [ Not found ]
[17:21:22]
[17:21:22] Checking for X-Org SunOS Rootkit...
[17:21:22]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[17:21:22]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[17:21:22]   Checking for file '/usr/bin/srload'             [ Not found ]
[17:21:22]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[17:21:22]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[17:21:22]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[17:21:22]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[17:21:22]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[17:21:22]   Checking for directory '/usr/share/man...'      [ Not found ]
[17:21:22] X-Org SunOS Rootkit                               [ Not found ]
[17:21:22]
[17:21:22] Checking for zaRwT.KiT Rootkit...
[17:21:22]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[17:21:22]   Checking for file '/dev/ttyf'                   [ Not found ]
[17:21:22]   Checking for file '/dev/ttyp'                   [ Not found ]
[17:21:22]   Checking for file '/dev/ttyn'                   [ Not found ]
[17:21:22]   Checking for file '/rk/tulz'                    [ Not found ]
[17:21:22]   Checking for directory '/rk'                    [ Not found ]
[17:21:22]   Checking for directory '/dev/rd/s'              [ Not found ]
[17:21:22] zaRwT.KiT Rootkit                                 [ Not found ]
[17:21:22]
[17:21:22] Checking for ZK Rootkit...
[17:21:22]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[17:21:22]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[17:21:22]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[17:21:22]   Checking for file '/etc/1ssue.net'              [ Not found ]
[17:21:22]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[17:21:22]   Checking for directory '/usr/share/.zk'         [ Not found ]
[17:21:22]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[17:21:22] ZK Rootkit                                        [ Not found ]
[17:21:22]
[17:21:22] Performing additional rootkit checks
[17:21:23] Info: Starting test name 'additional_rkts'
[17:21:23]
[17:21:23]   Performing Suckit Rookit additional checks
[17:21:23]     Checking hard link count on '/sbin/init'      [ OK ]
[17:21:23]     Checking for hidden file extensions           [ None found ]
[17:21:23]     Running skdet command                         [ Skipped ]
[17:21:23] Info: Unable to find the 'skdet' command
[17:21:23]   Suckit Rookit additional checks                 [ OK ]
[17:21:23]
[17:21:23]   Performing check of possible rootkit files and directories
[17:21:23] Info: Starting test name 'possible_rkt_files'
[17:21:23]     Checking for file '/dev/sdr0'                 [ Not found ]
[17:21:23]     Checking for file '/dev/pisu'                 [ Not found ]
[17:21:23]     Checking for file '/dev/xdta'                 [ Not found ]
[17:21:23]     Checking for file '/dev/saux'                 [ Not found ]
[17:21:23]     Checking for file '/dev/hdx'                  [ Not found ]
[17:21:23]     Checking for file '/dev/hdx1'                 [ Not found ]
[17:21:23]     Checking for file '/dev/hdx2'                 [ Not found ]
[17:21:23]     Checking for file '/dev/ptyy'                 [ Not found ]
[17:21:23]     Checking for file '/dev/ptyu'                 [ Not found ]
[17:21:23]     Checking for file '/dev/ptyv'                 [ Not found ]
[17:21:23]     Checking for file '/dev/hdbb'                 [ Not found ]
[17:21:23]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[17:21:23]     Checking for file '/tmp/.bash_history'        [ Not found ]
[17:21:23]     Checking for file '/usr/info/.clib'           [ Not found ]
[17:21:23]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[17:21:23]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[17:21:23]     Checking for file '/sbin/create'              [ Not found ]
[17:21:23]     Checking for file '/dev/ttypz'                [ Not found ]
[17:21:23]     Checking for file '/var/log/tcp.log'          [ Not found ]
[17:21:24]     Checking for file '/usr/include/audit.h'      [ Not found ]
[17:21:24]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[17:21:24]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[17:21:24]     Checking for file '/dev/xmx'                  [ Not found ]
[17:21:24]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[17:21:24]     Checking for file '/bin/vobiscum'             [ Not found ]
[17:21:24]     Checking for file '/bin/psr'                  [ Not found ]
[17:21:24]     Checking for file '/dev/kdx'                  [ Not found ]
[17:21:24]     Checking for file '/dev/dkx'                  [ Not found ]
[17:21:24]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[17:21:24]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[17:21:24]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[17:21:24]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[17:21:24]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[17:21:24]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[17:21:24]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[17:21:24]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[17:21:24]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[17:21:24]     Checking for file '/tmp/.ush'                 [ Not found ]
[17:21:24]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[17:21:24]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[17:21:24]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[17:21:24]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[17:21:24]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[17:21:24]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[17:21:25]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[17:21:25]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[17:21:25]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[17:21:25]     Checking for directory '/dev/ptyas'           [ Not found ]
[17:21:25]     Checking for directory '/usr/bin/take'        [ Not found ]
[17:21:25]     Checking for directory '/usr/src/.lib'        [ Not found ]
[17:21:25]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[17:21:25]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[17:21:25]     Checking for directory '/usr/sbin/...'        [ Not found ]
[17:21:25]     Checking for directory '/usr/share/.gun'      [ Not found ]
[17:21:25]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[17:21:25]     Checking for directory '/usr/man/man1/..  /.dir' [ Not found ]
[17:21:25]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[17:21:25]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[17:21:25]     Checking for directory '/tmp/.sys'            [ Not found ]
[17:21:25]     Checking for directory '/tmp/''               [ Not found ]
[17:21:25]     Checking for directory '/tmp/.,'              [ Not found ]
[17:21:25]     Checking for directory '/tmp/,.,'             [ Not found ]
[17:21:25]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[17:21:25]     Checking for directory '/var/tmp/.log'        [ Not found ]
[17:21:25]     Checking for directory '/tmp/zmeu/... '       [ Not found ]
[17:21:25]     Checking for directory '/var/log/ssh'         [ Not found ]
[17:21:25]     Checking for directory '/dev/ida'             [ Not found ]
[17:21:25]     Checking for directory '/lib/java'            [ Not found ]
[17:21:25]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[17:21:25]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[17:21:26]     Checking for directory '/usr/src/.poop'       [ Not found ]
[17:21:26]     Checking for directory '/dev/wd4'             [ Not found ]
[17:21:26]     Checking for directory '/var/run/.tmp'        [ Not found ]
[17:21:26]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[17:21:26]     Checking for directory '/dev/portd'           [ Not found ]
[17:21:26]     Checking for directory '/dev/...'             [ Not found ]
[17:21:26]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[17:21:26]     Checking for directory '/lib/.so'             [ Not found ]
[17:21:26]     Checking for directory '/lib/.sso'            [ Not found ]
[17:21:26]   Checking for possible rootkit files and directories [ None found ]
[17:21:26]
[17:21:26]   Performing check for possible rootkit strings
[17:21:26] Info: Starting test name 'possible_rkt_strings'
[17:21:26] Info: Using system startup paths: /etc/rc.local /etc/init.d
[17:21:26]     Checking for string 'phalanx'                 [ Not found ]
[17:21:26]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[17:21:26]     Checking for string '****'                    [ Not found ]
[17:21:26]     Checking for string 'backdoor'                [ Not found ]
[17:21:26]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[17:21:26]     Checking for string '/usr/sbin/login'         [ Not found ]
[17:21:26]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[17:21:26]     Checking for string 'vt200'                   [ Not found ]
[17:21:26]     Checking for string '/usr/bin/xstat'          [ Not found ]
[17:21:26]     Checking for string '/bin/envpc'              [ Not found ]
[17:21:26]     Checking for string 'L4m3r0x'                 [ Not found ]
[17:21:27]     Checking for string '/lib/libext'             [ Not found ]
[17:21:27]     Checking for string '/usr/sbin/login'         [ Not found ]
[17:21:27]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[17:21:27]     Checking for string 'sendmail'                [ Not found ]
[17:21:27]     Checking for string 'cocacola'                [ Not found ]
[17:21:27]     Checking for string 'joao'                    [ Not found ]
[17:21:27]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[17:21:27]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[17:21:27]     Checking for string '/dev/sgk'                [ Not found ]
[17:21:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:27]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[17:21:27]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[17:21:27]     Checking for string '/lib/.sso'               [ Not found ]
[17:21:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:27]     Checking for string '/dev/caca'               [ Not found ]
[17:21:27]     Checking for string '/dev/ttyoa'              [ Not found ]
[17:21:27]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[17:21:27]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[17:21:27]     Checking for string 'syg'                     [ Not found ]
[17:21:27]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:28]     Checking for string '/dev/pts/01'             [ Not found ]
[17:21:28]     Checking for string 'tw33dl3'                 [ Not found ]
[17:21:28]     Checking for string 'psniff'                  [ Not found ]
[17:21:28]     Checking for string 'uconf.inv'               [ Not found ]
[17:21:28]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[17:21:28]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[17:21:28]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[17:21:28]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:28]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[17:21:28]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[17:21:28]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:28]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:28]     Checking for string '/bin/bash'               [ Not found ]
[17:21:28]     Checking for string '/dev/xdta'               [ Not found ]
[17:21:28]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[17:21:28]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[17:21:29]     Checking for string 'in.inetd'                [ Not found ]
[17:21:29]     Checking for string '#<HIDE_.*>'              [ Not found ]
[17:21:29]     Checking for string 'bin/xchk'                [ Not found ]
[17:21:29]     Checking for string 'bin/xsf'                 [ Not found ]
[17:21:30]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[17:21:30]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[17:21:30]     Checking for string 'ttyload'                 [ Not found ]
[17:21:30]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[17:21:30]     Checking for string 'usr/bin/xfss'            [ Not found ]
[17:21:31]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[17:21:31]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[17:21:31]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[17:21:31]     Checking for string '/ssh2d'                  [ Not found ]
[17:21:32]     Checking for string '/dev/kmod'               [ Not found ]
[17:21:32]     Checking for string '/crth.o'                 [ Not found ]
[17:21:32]     Checking for string '/crtz.o'                 [ Not found ]
[17:21:32]     Checking for string '/dev/dos'                [ Not found ]
[17:21:32]     Checking for string '/lpq'                    [ Not found ]
[17:21:33]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[17:21:33]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[17:21:33]     Checking for string '/volc'                   [ Not found ]
[17:21:33]     Checking for string 'sourcemask'              [ Not found ]
[17:21:33]     Checking for string '/bin/vobiscum'           [ Not found ]
[17:21:34]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[17:21:34]     Checking for string 'hdparm'                  [ Not found ]
[17:21:34]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[17:21:34]     Checking for string 't0rnkit'                 [ Not found ]
[17:21:34]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[17:21:34]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:34]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:34]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:34]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[17:21:34]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[17:21:34]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[17:21:34]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[17:21:34]     Checking for string '/dev/ida/.inet'          [ Not found ]
[17:21:34]   Checking for possible rootkit strings           [ None found ]
[17:21:35]
[17:21:35] Performing malware checks
[17:21:35] Info: Starting test name 'malware'
[17:21:35]
[17:21:35] Info: Test 'deleted_files' disabled at users request.
[17:21:35] Info: Starting test name 'running_procs'
[17:21:35]   Checking running processes for suspicious files [ None found ]
[17:21:36]
[17:21:36] Info: Test 'hidden_procs' disabled at users request.
[17:21:36]
[17:21:36] Info: Test 'suspscan' disabled at users request.
[17:21:36]
[17:21:36]   Performing check for login backdoors
[17:21:36] Info: Starting test name 'other_malware'
[17:21:36]     Checking for '/bin/.login'                    [ Not found ]
[17:21:36]     Checking for '/sbin/.login'                   [ Not found ]
[17:21:36]   Checking for login backdoors                    [ None found ]
[17:21:36]
[17:21:36]   Performing check for suspicious directories
[17:21:36]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[17:21:36]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[17:21:36]   Checking for suspicious directories             [ None found ]
[17:21:36]
[17:21:36]   Checking for software intrusions                [ Skipped ]
[17:21:36] Info: Check skipped - tripwire not installed
[17:21:36]
[17:21:36]   Performing check for sniffer log files
[17:21:36]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[17:21:36]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[17:21:36]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[17:21:36]   Checking for sniffer log files                  [ None found ]
[17:21:36]
[17:21:36] Performing trojan specific checks
[17:21:36] Info: Starting test name 'trojans'
[17:21:36]   Checking for enabled inetd services             [ Skipped ]
[17:21:36] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[17:21:36]
[17:21:36]   Performing check for enabled xinetd services
[17:21:36]   Checking for enabled xinetd services            [ Skipped ]
[17:21:36] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[17:21:36] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[17:21:36]
[17:21:36] Performing Linux specific checks
[17:21:36] Info: Starting test name 'os_specific'
[17:21:36]   Checking loaded kernel modules                  [ OK ]
[17:21:36] Info: Using modules pathname of '/lib/modules/2.6.32-30-generic'
[17:21:37]   Checking kernel module names                    [ OK ]
[17:21:42]
[17:21:42] Checking the network...
[17:21:42] Info: Starting test name 'network'
[17:21:42] Info: Starting test name 'ports'
[17:21:42]
[17:21:42] Performing check for backdoor ports
[17:21:42]   Checking for TCP port 1524                      [ Not found ]
[17:21:42]   Checking for TCP port 1984                      [ Not found ]
[17:21:42]   Checking for UDP port 2001                      [ Not found ]
[17:21:42]   Checking for TCP port 2006                      [ Not found ]
[17:21:43]   Checking for TCP port 2128                      [ Not found ]
[17:21:43]   Checking for TCP port 6666                      [ Not found ]
[17:21:43]   Checking for TCP port 6667                      [ Not found ]
[17:21:43]   Checking for TCP port 6668                      [ Not found ]
[17:21:43]   Checking for TCP port 6669                      [ Not found ]
[17:21:43]   Checking for TCP port 7000                      [ Not found ]
[17:21:43]   Checking for TCP port 13000                     [ Not found ]
[17:21:43]   Checking for TCP port 14856                     [ Not found ]
[17:21:44]   Checking for TCP port 25000                     [ Not found ]
[17:21:44]   Checking for TCP port 29812                     [ Not found ]
[17:21:44]   Checking for TCP port 31337                     [ Not found ]
[17:21:44]   Checking for TCP port 32982                     [ Not found ]
[17:21:44]   Checking for TCP port 33369                     [ Not found ]
[17:21:44]   Checking for TCP port 47107                     [ Not found ]
[17:21:44]   Checking for TCP port 47018                     [ Not found ]
[17:21:44]   Checking for TCP port 60922                     [ Not found ]
[17:21:45]   Checking for TCP port 62883                     [ Not found ]
[17:21:45]   Checking for TCP port 65535                     [ Not found ]
[17:21:45]
[17:21:45] Performing checks on the network interfaces
[17:21:45] Info: Starting test name 'promisc'
[17:21:45]   Checking for promiscuous interfaces             [ None found ]
[17:21:45]
[17:21:45] Info: Test 'packet_cap_apps' disabled at users request.
[17:21:47]
[17:21:47] Checking the local host...
[17:21:47] Info: Starting test name 'local_host'
[17:21:47]
[17:21:47] Performing system boot checks
[17:21:48] Info: Starting test name 'startup_files'
[17:21:48]   Checking for local host name                    [ Found ]
[17:21:48] Info: Starting test name 'startup_malware'
[17:21:48]   Checking for system startup files               [ Found ]
[17:21:48]   Checking system startup files for malware       [ None found ]
[17:21:48]
[17:21:48] Performing group and account checks
[17:21:48] Info: Starting test name 'group_accounts'
[17:21:48]   Checking for passwd file                        [ Found ]
[17:21:48] Info: Found password file: /etc/passwd
[17:21:48]   Checking for root equivalent (UID 0) accounts   [ None found ]
[17:21:48] Info: Found shadow file: /etc/shadow
[17:21:48]   Checking for passwordless accounts              [ None found ]
[17:21:48] Info: Starting test name 'passwd_changes'
[17:21:48]   Checking for passwd file changes                [ None found ]
[17:21:48] Info: Starting test name 'group_changes'
[17:21:48]   Checking for group file changes                 [ None found ]
[17:21:49]   Checking root account shell history files       [ None found ]
[17:21:49]
[17:21:49] Performing system configuration file checks
[17:21:49] Info: Starting test name 'system_configs'
[17:21:49]   Checking for SSH configuration file             [ Not found ]
[17:21:49]   Checking for running syslog daemon              [ Found ]
[17:21:49]   Checking for syslog configuration file          [ Found ]
[17:21:49] Info: Found syslog configuration file: /etc/rsyslog.conf
[17:21:49]   Checking if syslog remote logging is allowed    [ Not allowed ]
[17:21:49]
[17:21:49] Performing filesystem checks
[17:21:49] Info: Starting test name 'filesystem'
[17:21:49] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:21:49]   Checking /dev for suspicious file types         [ Warning ]
[17:21:49] Warning: Suspicious file types found in /dev:
[17:21:49]          /dev/shm/pulse-shm-3141997040: data
[17:21:49]          /dev/shm/pulse-shm-2998124072: data
[17:21:49]          /dev/shm/pulse-shm-865720883: data
[17:21:49]          /dev/shm/pulse-shm-1380443056: data
[17:21:49]          /dev/shm/pulse-shm-2426268243: data
[17:21:49]          /dev/shm/pulse-shm-4089632560: data
[17:21:49]          /dev/shm/pulse-shm-1090320326: data
[17:21:49]          /dev/shm/pulse-shm-3380647762: data
[17:21:50]          /dev/shm/mono-shared-1000-shared_fileshare-jim-laptop-Linux-i686-36-12-0: data
[17:21:50]          /dev/shm/mono-shared-1000-shared_data-jim-laptop-Linux-i686-312-12-0: data
[17:21:50]          /dev/shm/mono.20431: data
[17:21:50]          /dev/shm/pulse-shm-739584310: data
[17:21:50]          /dev/shm/pulse-shm-494360063: data
[17:21:50]          /dev/shm/pulse-shm-1265473844: data
[17:21:50]   Checking for hidden files and directories       [ Warning ]
[17:21:50] Warning: Hidden directory found: /dev/.udev
[17:21:50] Warning: Hidden directory found: /dev/.initramfs
[17:21:57]
[17:21:57] Info: Test 'apps' disabled at users request.
[17:21:57]
[17:21:57] System checks summary
[17:21:57] =====================
[17:21:57]
[17:21:57] File properties checks...
[17:21:57] Files checked: 134
[17:21:57] Suspect files: 18
[17:21:57]
[17:21:57] Rootkit checks...
[17:21:57] Rootkits checked : 242
[17:21:57] Possible rootkits: 0
[17:21:57]
[17:21:57] Applications checks...
[17:21:57] All checks skipped
[17:21:57]
[17:21:57] The system checks took: 1 minute and 55 seconds
[17:21:57]
[17:21:57] Info: End date is Sun Apr 24 17:21:57 CDT 2011
```

---

### Post by Ryan Dwyer on 2011-04-24
> **macminiuser said:**
> [17:21:57] Possible rootkits: 0

No. It's fine.

---

### Post by cipherboy_loc on 2011-04-24
1) Wrap in code tags. Soo much easier to read. 
2) Could you post ONLY the lines that you think pertain (and a couple surrounding)?
3) rkhunter gives a lot of false positives. 

Cipherboy

---

### Post by brian_p on 2011-04-24
> **macminiuser said:**
> Have I been hacked into?

No

> I ran rkhunter today and it showed some files changed here is the log

It often does that. Ignore it. You can remove the irritation it causes by removing the program from your system. It will be no great loss.

---

### Post by macminiuser on 2011-04-24
> **cipherboy_loc said:**
> 1) Wrap in code tags. Soo much easier to read. 
2) Could you post ONLY the lines that you think pertain (and a couple surrounding)?
3) rkhunter gives a lot of false positives. 

Cipherboy

Yes sir I will do that next time Thanks
Jim

---

### Post by macminiuser on 2011-04-24
> **brian_p said:**
> No



It often does that. Ignore it. You can remove the irritation it causes by removing the program from your system. It will be no great loss.

Thanks Brian!
Jim

---

### Post by macminiuser on 2011-04-24
> **Ryan Dwyer said:**
> No. It's fine.

Thanks Ryan!
Jim

---

### Post by doas777 on 2011-04-24
is it the stanzas like this that have you worried?
```
[17:20:23]          File: /usr/sbin/groupadd
[17:20:23]          Current hash: f0b6f921d7a9f8e766ff6c7d631465941128aab2
[17:20:23]          Stored hash : b6bb3cca5d0c399b26e3688246401e5f1dc34347
[17:20:23]          Current inode: 8390092    Stored inode: 8398743
[17:20:23]          Current file modification time: 1297721480 (14-Feb-2011 16:11:20)
[17:20:23]          Stored file modification time : 1264525783 (26-Jan-2010 11:09:43)
```?

earlier this year, all the componenets related to GDM, Passwd, and Sudo have been upgraded. notice the data of the stored modification is in early 2010. it indicates that the file has changed since the last time you ran rkhunter, but nothing else. that might be a sign your system has been tampered with, but more likely it's the updater. you can check with synaptic I think to determine when those components were last updated.

---

