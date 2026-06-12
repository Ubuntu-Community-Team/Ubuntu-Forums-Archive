---
title: "Rkhunter &amp; correct hashes"
date: 2012-09-01
forum: Security
---

### Post by FreedomOverdose on 2012-09-01
Hey everyone, 

So i was doing a scan with rkhunter and it gave me **a lot** of warnings regarding hash mismatches from the previous versions. Now, I have updated my system twice and I haven't --propupd rkhunter, so they're all probably false positives. 

However, my question is, is there any way I can find the correct md5 hashes of the scripts in /bin, /sbin, etc? So that I know that what I currently have is just an updated version of the old scripts.

Here is my log just for reference:

```
[13:25:47] Running Rootkit Hunter version 1.4.0 on wwnndo
[13:25:47]
[13:25:47] Info: Start date is Sat Sep  1 13:25:47 CEST 2012
[13:25:47]
[13:25:47] Checking configuration file and command-line options...
[13:25:47] Info: Detected operating system is 'Linux'
[13:25:47] Info: Found O/S name: Ubuntu 11.10
[13:25:47] Info: Command line is /usr/local/bin/rkhunter -c
[13:25:47] Info: Environment shell is /bin/bash; rkhunter is using dash
[13:25:47] Info: Using configuration file '/etc/rkhunter.conf'
[13:25:47] Info: Installation directory is '/usr'
[13:25:47] Info: Using language 'en'
[13:25:47] Info: Using '/var/lib/rkhunter/db' as the database directory
[13:25:47] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[13:25:47] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin' as the command directories
[13:25:47] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[13:25:47] Info: No mail-on-warning address configured
[13:25:47] Info: X will be automatically detected
[13:25:47] Info: Using second color set
[13:25:47] Info: Found the 'basename' command: /usr/bin/basename
[13:25:47] Info: Found the 'diff' command: /usr/bin/diff
[13:25:47] Info: Found the 'dirname' command: /usr/bin/dirname
[13:25:47] Info: Found the 'file' command: /usr/bin/file
[13:25:47] Info: Found the 'find' command: /usr/bin/find
[13:25:47] Info: Found the 'ifconfig' command: /sbin/ifconfig
[13:25:47] Info: Found the 'ip' command: /sbin/ip
[13:25:47] Info: Found the 'ldd' command: /usr/bin/ldd
[13:25:47] Info: Found the 'lsattr' command: /usr/bin/lsattr
[13:25:47] Info: Found the 'lsmod' command: /sbin/lsmod
[13:25:47] Info: Found the 'lsof' command: /usr/bin/lsof
[13:25:47] Info: Found the 'mktemp' command: /bin/mktemp
[13:25:47] Info: Found the 'netstat' command: /bin/netstat
[13:25:47] Info: Found the 'perl' command: /usr/bin/perl
[13:25:47] Info: Found the 'pgrep' command: /usr/bin/pgrep
[13:25:47] Info: Found the 'ps' command: /bin/ps
[13:25:47] Info: Found the 'pwd' command: /bin/pwd
[13:25:47] Info: Found the 'readlink' command: /bin/readlink
[13:25:47] Info: Found the 'stat' command: /usr/bin/stat
[13:25:47] Info: Found the 'strings' command: /usr/bin/strings
[13:25:47] Info: System is not using prelinking
[13:25:47] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[13:25:47] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[13:25:47] Info: Stored hash values did not use a package manager
[13:25:48] Info: The hash function field index is set to 1
[13:25:48] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[13:25:48] Info: Previous file attributes were stored
[13:25:48] Info: Enabled tests are: all
[13:25:48] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[13:25:48] Info: Found ksym file '/proc/kallsyms'
[13:25:48] Info: Using 'date' to process epoch second times.
[13:25:48]
[13:25:48] Checking if the O/S has changed since last time...
[13:25:48] Warning: The O/S name or version has changed since the last run:
[13:25:48]          Old O/S value: Ubuntu 11.10    New value: Ubuntu 12.04.1 LTS
[13:25:48]          Because of the change(s) the file properties checks may give some false-positive results.
[13:25:48]          You may need to re-run rkhunter with the '--propupd' option.
[13:25:48]
[13:25:48] Warning: WARNING! It is the users responsibility to ensure that when the '--propupd' option
           is used, all the files on their system are known to be genuine, and installed from a
           reliable source. The rkhunter '--check' option will compare the current file properties
           against previously stored values, and report if any values differ. However, rkhunter
           cannot determine what has caused the change, that is for the user to do.
[13:25:48] Info: Locking is not being used
[13:25:48]
[13:25:48] Starting system checks...
[13:25:48]
[13:25:48] Info: Starting test name 'system_commands'
[13:25:48] Checking system commands...
[13:25:48]
[13:25:48] Info: Starting test name 'strings'
[13:25:48] Performing 'strings' command checks
[13:25:48]   Scanning for string /usr/sbin/ntpsx             [ OK ]
[13:25:48]   Scanning for string /usr/sbin/.../bkit-ava      [ OK ]
[13:25:48]   Scanning for string /usr/sbin/.../bkit-d        [ OK ]
[13:25:48]   Scanning for string /usr/sbin/.../bkit-shd      [ OK ]
[13:25:48]   Scanning for string /usr/sbin/.../bkit-f        [ OK ]
[13:25:48]   Scanning for string /usr/include/.../proc.h     [ OK ]
[13:25:48]   Scanning for string /usr/include/.../.bash_history [ OK ]
[13:25:48]   Scanning for string /usr/include/.../bkit-get   [ OK ]
[13:25:48]   Scanning for string /usr/include/.../bkit-dl    [ OK ]
[13:25:48]   Scanning for string /usr/include/.../bkit-screen [ OK ]
[13:25:48]   Scanning for string /usr/include/.../bkit-sleep [ OK ]
[13:25:48]   Scanning for string /usr/lib/.../bkit-adore.o   [ OK ]
[13:25:48]   Scanning for string /usr/lib/.../ls             [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../netstat        [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../lsof           [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../uconf.inv      [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../psr            [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../find           [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../pstree         [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../slocate        [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../du             [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../top            [ OK ]
[13:25:49]   Scanning for string /usr/sbin/...               [ OK ]
[13:25:49]   Scanning for string /usr/include/...            [ OK ]
[13:25:49]   Scanning for string /usr/include/.../.tmp       [ OK ]
[13:25:49]   Scanning for string /usr/lib/...                [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../.ssh           [ OK ]
[13:25:49]   Scanning for string /usr/lib/.../bkit-ssh       [ OK ]
[13:25:49]   Scanning for string /usr/lib/.bkit-             [ OK ]
[13:25:49]   Scanning for string /tmp/.bkp                   [ OK ]
[13:25:49]   Scanning for string /tmp/.cinik                 [ OK ]
[13:25:49]   Scanning for string /tmp/.font-unix/.cinik      [ OK ]
[13:25:49]   Scanning for string /lib/.sso                   [ OK ]
[13:25:49]   Scanning for string /lib/.so                    [ OK ]
[13:25:49]   Scanning for string /var/run/...dica/clean      [ OK ]
[13:25:49]   Scanning for string /var/run/...dica/dxr        [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/read       [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/write      [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/lf         [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/xl         [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/xdr        [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/psg        [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/secure     [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/rdx        [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/va         [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/cl.sh      [ OK ]
[13:25:50]   Scanning for string /var/run/...dica/last.log   [ OK ]
[13:25:50]   Scanning for string /usr/bin/.etc               [ OK ]
[13:25:50]   Scanning for string /etc/sshd_config            [ OK ]
[13:25:50]   Scanning for string /etc/ssh_host_key           [ OK ]
[13:25:50]   Scanning for string /etc/ssh_random_seed        [ OK ]
[13:25:50]   Scanning for string /dev/ptyp                   [ OK ]
[13:25:50]   Scanning for string /dev/ptyq                   [ OK ]
[13:25:50]   Scanning for string /dev/ptyr                   [ OK ]
[13:25:50]   Scanning for string /dev/ptys                   [ OK ]
[13:25:50]   Scanning for string /dev/ptyt                   [ OK ]
[13:25:50]   Scanning for string /dev/fd/.88/freshb-bsd      [ OK ]
[13:25:50]   Scanning for string /dev/fd/.88/fresht          [ OK ]
[13:25:50]   Scanning for string /dev/fd/.88/zxsniff         [ OK ]
[13:25:50]   Scanning for string /dev/fd/.88/zxsniff.log     [ OK ]
[13:25:50]   Scanning for string /dev/fd/.99/.ttyf00         [ OK ]
[13:25:51]   Scanning for string /dev/fd/.99/.ttyp00         [ OK ]
[13:25:51]   Scanning for string /dev/fd/.99/.ttyq00         [ OK ]
[13:25:51]   Scanning for string /dev/fd/.99/.ttys00         [ OK ]
[13:25:51]   Scanning for string /dev/fd/.99/.pwsx00         [ OK ]
[13:25:51]   Scanning for string /etc/.acid                  [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/sched_host.2   [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/random_d.2     [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/set_pid.2      [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/setrgrp.2      [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/TOHIDE         [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/cons.saver     [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/adore/ava/ava  [ OK ]
[13:25:51]   Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[13:25:51]   Scanning for string /bin/sysback                [ OK ]
[13:25:51]   Scanning for string /usr/local/bin/sysback      [ OK ]
[13:25:51]   Scanning for string /usr/lib/.tbd               [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/t0rns     [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/du        [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/ls        [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/t0rnsb    [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/ps        [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/t0rnp     [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/find      [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/ifconfig  [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/pg        [ OK ]
[13:25:51]   Scanning for string /dev/.lib/lib/lib/ssh.tgz   [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/top       [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/sz        [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/login     [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/in.fingerd [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/1i0n.sh   [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/pstree    [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/in.telnetd [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/mjy       [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/sush      [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/tfn       [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/name      [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/getip.sh  [ OK ]
[13:25:52]   Scanning for string /usr/info/.torn/sh*         [ OK ]
[13:25:52]   Scanning for string /usr/src/.puta/.1addr       [ OK ]
[13:25:52]   Scanning for string /usr/src/.puta/.1file       [ OK ]
[13:25:52]   Scanning for string /usr/src/.puta/.1proc       [ OK ]
[13:25:52]   Scanning for string /usr/src/.puta/.1logz       [ OK ]
[13:25:52]   Scanning for string /usr/info/.t0rn             [ OK ]
[13:25:52]   Scanning for string /dev/.lib                   [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib               [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib           [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/lib/dev       [ OK ]
[13:25:52]   Scanning for string /dev/.lib/lib/scan          [ OK ]
[13:25:52]   Scanning for string /usr/src/.puta              [ OK ]
[13:25:53]   Scanning for string /usr/man/man1/man1          [ OK ]
[13:25:53]   Scanning for string /usr/man/man1/man1/lib      [ OK ]
[13:25:53]   Scanning for string /usr/man/man1/man1/lib/.lib [ OK ]
[13:25:53]   Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[13:25:53]
[13:25:53] Info: Starting test name 'shared_libs'
[13:25:53] Performing 'shared libraries' checks
[13:25:53]   Checking for preloading variables               [ None found ]
[13:25:53]   Checking for preloaded libraries                [ None found ]
[13:25:53]
[13:25:53] Info: Starting test name 'shared_libs_path'
[13:25:53]   Checking LD_LIBRARY_PATH variable               [ Not found ]
[13:25:53]
[13:25:53] Info: Starting test name 'properties'
[13:25:53] Performing file properties checks
[13:25:53] Warning: Checking for prerequisites               [ Warning ]
[13:25:53]          The local host configuration or operating system has changed.
[13:25:56]   /usr/local/bin/rkhunter                         [ Warning ]
[13:25:56] Warning: The file '/usr/local/bin/rkhunter' exists on the system, but it is not present in the rkhunter.dat file.
[13:25:56]   /usr/sbin/adduser                               [ Warning ]
[13:25:56] Warning: The file properties have changed:
[13:25:56]          File: /usr/sbin/adduser
[13:25:56]          Current hash: 7a6b1d06ca7bbfd9997b784bb109bb464cea6d7c
[13:25:56]          Stored hash : ddf00d43d5d2e4a6b49f02df13ee2e87f9e78e76
[13:25:57]          Current inode: 11145593    Stored inode: 11149791
[13:25:57]          Current size: 35120    Stored size: 35111
[13:25:57]          Current file modification time: 1319061692 (20-Oct-2011 00:01:32)
[13:25:57]          Stored file modification time : 1299669745 (09-Mar-2011 12:22:25)
[13:25:57] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[13:25:57]   /usr/sbin/chroot                                [ Warning ]
[13:25:57] Warning: The file properties have changed:
[13:25:57]          File: /usr/sbin/chroot
[13:25:57]          Current hash: fa822ab0833ff8e39c8932601f93f706953f66da
[13:25:57]          Stored hash : dafd89e63840e836adf5b353ca5ebfb51d890b54
[13:25:57]          Current inode: 11163331    Stored inode: 11149808
[13:25:57]          Current size: 30304    Stored size: 26180
[13:25:57]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:25:57]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:25:57]   /usr/sbin/cron                                  [ Warning ]
[13:25:57] Warning: The file properties have changed:
[13:25:57]          File: /usr/sbin/cron
[13:25:57]          Current hash: 5fe5400f31f5e87555c116d9e28a63a36b035299
[13:25:57]          Stored hash : a1728713ff4849729d7f1a36787c79e47220ada0
[13:25:57]          Current inode: 11144967    Stored inode: 11141169
[13:25:57]          Current file modification time: 1340137572 (19-Jun-2012 22:26:12)
[13:25:57]          Stored file modification time : 1316477279 (20-Sep-2011 02:07:59)
[13:25:58]   /usr/sbin/groupadd                              [ Warning ]
[13:25:58] Warning: The file properties have changed:
[13:25:58]          File: /usr/sbin/groupadd
[13:25:58]          Current hash: 98a09c8b926a8106f710586f5764ca7455001db1
[13:25:58]          Stored hash : af878a380c525ad0c257f29d0718e3feca317894
[13:25:58]          Current inode: 11142419    Stored inode: 11144380
[13:25:58]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:25:58]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:25:58]   /usr/sbin/groupdel                              [ Warning ]
[13:25:58] Warning: The file properties have changed:
[13:25:58]          File: /usr/sbin/groupdel
[13:25:58]          Current hash: 2ba0c7ea0a35874596b907572f945618d24186f3
[13:25:58]          Stored hash : f2e0085f5b8a431f7e1880d9d403672e8c3021fd
[13:25:58]          Current inode: 11143502    Stored inode: 11144381
[13:25:58]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:25:58]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:25:58]   /usr/sbin/groupmod                              [ Warning ]
[13:25:58] Warning: The file properties have changed:
[13:25:58]          File: /usr/sbin/groupmod
[13:25:58]          Current hash: 222b4da88cccbcfc9b76c0bf6278eaced717ad88
[13:25:58]          Stored hash : 1024a3832d098d70b5af3d35fd4813d00ad9de34
[13:25:58]          Current inode: 11143503    Stored inode: 11144382
[13:25:58]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:25:58]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:25:59]   /usr/sbin/grpck                                 [ Warning ]
[13:25:59] Warning: The file properties have changed:
[13:25:59]          File: /usr/sbin/grpck
[13:25:59]          Current hash: 08d7ff945baef43986bb2468a9da5a92d97a0399
[13:25:59]          Stored hash : 99f8b1ca22352d6cea119b76ede39b9e8b6fad3e
[13:25:59]          Current inode: 11143504    Stored inode: 11144383
[13:25:59]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:25:59]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:25:59]   /usr/sbin/nologin                               [ Warning ]
[13:25:59] Warning: The file properties have changed:
[13:25:59]          File: /usr/sbin/nologin
[13:25:59]          Current hash: 2a7c80844a5d256bea7abef28148191b6764d77b
[13:25:59]          Stored hash : 72f194cca8626a6ad42f87f03154bde556b20c52
[13:25:59]          Current inode: 11141208    Stored inode: 11141291
[13:25:59]          Current file modification time: 1333939214 (09-Apr-2012 04:40:14)
[13:25:59]          Stored file modification time : 1308908220 (24-Jun-2011 11:37:00)
[13:26:00]   /usr/sbin/pwck                                  [ Warning ]
[13:26:00] Warning: The file properties have changed:
[13:26:00]          File: /usr/sbin/pwck
[13:26:00]          Current hash: ed6c93844c07e2bfc2c9cd8f174e3d98e1aa641e
[13:26:00]          Stored hash : 4cd67de2375719636f3a62aee25a65ccd1dc0f9b
[13:26:00]          Current inode: 11143508    Stored inode: 11144387
[13:26:00]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:00]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:00]   /usr/sbin/rsyslogd                              [ Warning ]
[13:26:00] Warning: The file properties have changed:
[13:26:00]          File: /usr/sbin/rsyslogd
[13:26:00]          Current hash: 1b7f6f505dbe88d338d8eca3dd6488b1a15b4b24
[13:26:00]          Stored hash : 6bef647c815f0109462aa95c8df2d15fb297d0e5
[13:26:00]          Current inode: 11141781    Stored inode: 11148896
[13:26:00]          Current size: 388540    Stored size: 384444
[13:26:00]          Current file modification time: 1333128169 (30-Mar-2012 19:22:49)
[13:26:00]          Stored file modification time : 1317676900 (03-Oct-2011 23:21:40)
[13:26:01]   /usr/sbin/tcpd                                  [ OK ]
[13:26:01]   /usr/sbin/useradd                               [ Warning ]
[13:26:01] Warning: The file properties have changed:
[13:26:01]          File: /usr/sbin/useradd
[13:26:01]          Current hash: 6d76d57a52f5087060cd51fc2b78b5cff4d39106
[13:26:01]          Stored hash : 5facd128d951c72e7b8e29542a8931984f75ab09
[13:26:01]          Current inode: 11144348    Stored inode: 11144390
[13:26:01]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:01]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:01]   /usr/sbin/userdel                               [ Warning ]
[13:26:01] Warning: The file properties have changed:
[13:26:01]          File: /usr/sbin/userdel
[13:26:01]          Current hash: a012b4c69ddfc8a27b4516966e0a2976b50c1526
[13:26:01]          Stored hash : 506ba2f5d5da0d0e422a9e62332115f5b34114b4
[13:26:01]          Current inode: 11144350    Stored inode: 11144391
[13:26:01]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:01]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:02]   /usr/sbin/usermod                               [ Warning ]
[13:26:02] Warning: The file properties have changed:
[13:26:02]          File: /usr/sbin/usermod
[13:26:02]          Current hash: d9c5a30d31ee8803027022da1c7471f0df4fe8bd
[13:26:02]          Stored hash : 340f486a016fd517a7533832fbf976b572f25ad5
[13:26:02]          Current inode: 11144351    Stored inode: 11144392
[13:26:02]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:02]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:02]   /usr/sbin/vipw                                  [ Warning ]
[13:26:02] Warning: The file properties have changed:
[13:26:02]          File: /usr/sbin/vipw
[13:26:02]          Current hash: 521d9c8e4e52a82778e0d7668d9ca2ac20907229
[13:26:02]          Stored hash : d9e1658db3cb530bc1a46bade6e55b0c4b7a4fbe
[13:26:02]          Current inode: 11144352    Stored inode: 11144393
[13:26:02]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:02]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:02]   /usr/sbin/unhide                                [ Warning ]
[13:26:02] Warning: The file properties have changed:
[13:26:02]          File: /usr/sbin/unhide
[13:26:02]          Current hash: daa3e041fa727d8aad405ba384d610a84bd18758
[13:26:03]          Stored hash : d28942ac743b0f7fa9922c1950c83f42fcabfe7f
[13:26:03]          Current permissions: 0755    Stored permissions: 0777
[13:26:03]          Current inode: 11152911    Stored inode: 11162068
[13:26:03]          Current size: 750344    Stored size: 24
[13:26:03]          Current file modification time: 1332421278 (22-Mar-2012 14:01:18)
[13:26:03]          Stored file modification time : 1327105455 (21-Jan-2012 01:24:15)
[13:26:03]   /usr/sbin/unhide-tcp                            [ Warning ]
[13:26:03] Warning: The file properties have changed:
[13:26:03]          File: /usr/sbin/unhide-tcp
[13:26:03]          Current hash: 6c3d96274c6a5757bd3c7d8f519ca38bf5624694
[13:26:03]          Stored hash : 2ac700ced1b8104528f898eeb1f686f7429461fe
[13:26:03]          Current inode: 11152913    Stored inode: 11162059
[13:26:03]          Current size: 680788    Stored size: 556464
[13:26:03]          Current file modification time: 1332421278 (22-Mar-2012 14:01:18)
[13:26:03]          Stored file modification time : 1307104360 (03-Jun-2011 14:32:40)
[13:26:03]   /usr/bin/awk                                    [ Warning ]
[13:26:03] Warning: The file properties have changed:
[13:26:03]          File: /usr/bin/awk
[13:26:03]          Current hash: 251768e354db35bd5109ebfdc947cc6bf79b7df5
[13:26:03]          Stored hash : 758bca135d99a296e2f86f72c314deb498654a2e
[13:26:03]   /usr/bin/basename                               [ Warning ]
[13:26:03] Warning: The file properties have changed:
[13:26:03]          File: /usr/bin/basename
[13:26:03]          Current hash: 1ea19adcd3fdba67dee764c5031d7459924a21db
[13:26:03]          Stored hash : 6e14db246a76151bf55c05c1c28e39c2d1a990f1
[13:26:03]          Current inode: 11147179    Stored inode: 11141207
[13:26:04]          Current size: 22060    Stored size: 17880
[13:26:04]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:04]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:04]   /usr/bin/chattr                                 [ Warning ]
[13:26:04] Warning: The file properties have changed:
[13:26:04]          File: /usr/bin/chattr
[13:26:04]          Current hash: bbc424235299048bd50258ac92d424b22024ec46
[13:26:04]          Stored hash : a04230cae7cf8b66d51f054f16c9a54e7af0a9f6
[13:26:04]          Current inode: 11141294    Stored inode: 11141276
[13:26:04]          Current size: 9692    Stored size: 9628
[13:26:04]          Current file modification time: 1333139128 (30-Mar-2012 22:25:28)
[13:26:04]          Stored file modification time : 1300385203 (17-Mar-2011 19:06:43)
[13:26:04]   /usr/bin/curl                                   [ Warning ]
[13:26:04] Warning: The file properties have changed:
[13:26:04]          File: /usr/bin/curl
[13:26:04]          Current hash: 20a0913ec8f438c5d2415b6ac8225b16a6ccba68
[13:26:04]          Stored hash : 65e0a1b68dd9ff062f225125ddad57ca953d3b87
[13:26:04]          Current inode: 11141345    Stored inode: 11141823
[13:26:04]          Current size: 124576    Stored size: 124580
[13:26:04]          Current file modification time: 1332459396 (23-Mar-2012 00:36:36)
[13:26:04]          Stored file modification time : 1316119657 (15-Sep-2011 22:47:37)
[13:26:04]   /usr/bin/cut                                    [ Warning ]
[13:26:05] Warning: The file properties have changed:
[13:26:05]          File: /usr/bin/cut
[13:26:05]          Current hash: e79a07bfa063a8cb20c49aa0aff3dafa77927014
[13:26:05]          Stored hash : debea843673de2ff8fe18fe582aa8bfd31423a8f
[13:26:05]          Current inode: 11147191    Stored inode: 11141322
[13:26:05]          Current size: 38488    Stored size: 30220
[13:26:05]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:05]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:05]   /usr/bin/diff                                   [ Warning ]
[13:26:05] Warning: The file properties have changed:
[13:26:05]          File: /usr/bin/diff
[13:26:05]          Current hash: 5c16136472e0dfd47893a835f7d44e7b4c021429
[13:26:05]          Stored hash : 5854ed6332d77278690a7af6296e91075b2e9344
[13:26:05]          Current inode: 11142378    Stored inode: 11141355
[13:26:05]          Current size: 112324    Stored size: 104168
[13:26:05]          Current file modification time: 1332139001 (19-Mar-2012 07:36:41)
[13:26:05]          Stored file modification time : 1273413047 (09-May-2010 15:50:47)
[13:26:05]   /usr/bin/dirname                                [ Warning ]
[13:26:05] Warning: The file properties have changed:
[13:26:05]          File: /usr/bin/dirname
[13:26:05]          Current hash: 007eb03d338575ca17e6a48d63bad92d06327d7b
[13:26:05]          Stored hash : 74215ad760eaadb71229a2fcae64d68dea0143f0
[13:26:05]          Current inode: 11147199    Stored inode: 11141361
[13:26:05]          Current size: 22056    Stored size: 17876
[13:26:05]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:05]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:06]   /usr/bin/dpkg                                   [ Warning ]
[13:26:06] Warning: The file properties have changed:
[13:26:06]          File: /usr/bin/dpkg
[13:26:06]          Current hash: 48b702977fe8a82c129cf7eb1e8ff4a43632f119
[13:26:06]          Stored hash : 6725b32896b78ffbe789ccbb98ec216575a350ca
[13:26:06]          Current inode: 11141166    Stored inode: 11141625
[13:26:06]          Current size: 252032    Stored size: 247936
[13:26:06]          Current file modification time: 1334274491 (13-Apr-2012 01:48:11)
[13:26:06]          Stored file modification time : 1317888300 (06-Oct-2011 10:05:00)
[13:26:06]   /usr/bin/dpkg-query                             [ Warning ]
[13:26:06] Warning: The file properties have changed:
[13:26:06]          File: /usr/bin/dpkg-query
[13:26:06]          Current hash: 2cb2bace64518d1c3b1104ea6f543cba1bbd11c1
[13:26:06]          Stored hash : 542d4d3e046a0d36d54c03def617525087864ee4
[13:26:06]          Current inode: 11147053    Stored inode: 11141628
[13:26:06]          Current size: 120684    Stored size: 116584
[13:26:06]          Current file modification time: 1334274491 (13-Apr-2012 01:48:11)
[13:26:06]          Stored file modification time : 1317888300 (06-Oct-2011 10:05:00)
[13:26:06]   /usr/bin/du                                     [ Warning ]
[13:26:06] Warning: The file properties have changed:
[13:26:06]          File: /usr/bin/du
[13:26:06]          Current hash: a84da9d013af90d8290bc8d149ddf9a22566d0b7
[13:26:06]          Stored hash : 828dda2106985b67d36e9419297be2df1e967a65
[13:26:06]          Current inode: 11147201    Stored inode: 11141391
[13:26:06]          Current size: 100096    Stored size: 87792
[13:26:06]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:07]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:07]   /usr/bin/env                                    [ Warning ]
[13:26:07] Warning: The file properties have changed:
[13:26:07]          File: /usr/bin/env
[13:26:07]          Current hash: 652f033c4ba2afd812d105c229ff689b218fe9d2
[13:26:07]          Stored hash : 3e2597f87a66006bb936fff313ac5a6e11dd9ea1
[13:26:07]          Current inode: 11147386    Stored inode: 11141426
[13:26:07]          Current size: 22060    Stored size: 17880
[13:26:07]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:07]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:07]   /usr/bin/file                                   [ Warning ]
[13:26:07] Warning: The file properties have changed:
[13:26:07]          File: /usr/bin/file
[13:26:07]          Current hash: 79d2094a20c84ada117c7120e15a572b4b070709
[13:26:07]          Stored hash : 3f43f47880d0a08abe6b8f5e096f9e805d0288cf
[13:26:07]          Current inode: 11141758    Stored inode: 11141418
[13:26:07]          Current size: 13812    Stored size: 13804
[13:26:07]          Current file modification time: 1320144047 (01-Nov-2011 11:40:47)
[13:26:07]          Stored file modification time : 1312836918 (08-Aug-2011 22:55:18)
[13:26:07]   /usr/bin/find                                   [ Warning ]
[13:26:07] Warning: The file properties have changed:
[13:26:07]          File: /usr/bin/find
[13:26:07]          Current hash: c5af2f17201487e1931d227971bcd1795cc93209
[13:26:07]          Stored hash : 8f67695299bb31713444e82bd616ecf51be187b2
[13:26:07]          Current inode: 11147492    Stored inode: 11141462
[13:26:07]          Current size: 162452    Stored size: 141972
[13:26:07]          Current file modification time: 1327358920 (23-Jan-2012 23:48:40)
[13:26:07]          Stored file modification time : 1297297406 (10-Feb-2011 01:23:26)
[13:26:08]   /usr/bin/GET                                    [ Warning ]
[13:26:08] Warning: The file properties have changed:
[13:26:08]          File: /usr/bin/GET
[13:26:08]          Current hash: 2ecd423401689d1b74365364f3e849c0473f3915
[13:26:08]          Stored hash : ad3706af1726f6253ed11705f4a54ce91f0b80fe
[13:26:08]          Current inode: 11147482    Stored inode: 11144676
[13:26:08]          Current file modification time: 1322068266 (23-Nov-2011 18:11:06)
[13:26:08]          Stored file modification time : 1318554665 (14-Oct-2011 03:11:05)
[13:26:08]   /usr/bin/groups                                 [ Warning ]
[13:26:08] Warning: The file properties have changed:
[13:26:08]          File: /usr/bin/groups
[13:26:08]          Current hash: 4698e0310b6b80c2418737a3e2fb397d49c05f35
[13:26:08]          Stored hash : e45bb6e1fd9e2bb5e8ed6d03766e11bb3ef8ab79
[13:26:08]          Current inode: 11149510    Stored inode: 11141623
[13:26:08]          Current size: 26180    Stored size: 22000
[13:26:08]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:08]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:08] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[13:26:08]   /usr/bin/head                                   [ Warning ]
[13:26:08] Warning: The file properties have changed:
[13:26:08]          File: /usr/bin/head
[13:26:08]          Current hash: 84e6127f1298081afaf155f422676a207aebf889
[13:26:08]          Stored hash : c28e82a2cec407e60eb9effc58497443ee8c7019
[13:26:08]          Current inode: 11149512    Stored inode: 11141676
[13:26:08]          Current size: 34380    Stored size: 34356
[13:26:08]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:08]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:09]   /usr/bin/id                                     [ Warning ]
[13:26:09] Warning: The file properties have changed:
[13:26:09]          File: /usr/bin/id
[13:26:09]          Current hash: 361c65c43c05c62d0d24a53232769fc6c94604ec
[13:26:09]          Stored hash : a6072a5b4b3ee566857b4ce3caedb0306eaa44d0
[13:26:09]          Current inode: 11149514    Stored inode: 11141716
[13:26:09]          Current size: 30296    Stored size: 22020
[13:26:09]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:09]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:09]   /usr/bin/killall                                [ Warning ]
[13:26:09] Warning: The file properties have changed:
[13:26:09]          File: /usr/bin/killall
[13:26:09]          Current hash: f1ca3ee43d914964d22b7e3b0dff404fa55c2c61
[13:26:09]          Stored hash : 6a11f1742083e8f51adf17316644cf40fd245fb2
[13:26:09]          Current inode: 11146362    Stored inode: 11144992
[13:26:09]          Current file modification time: 1342483144 (17-Jul-2012 01:59:04)
[13:26:09]          Stored file modification time : 1308736462 (22-Jun-2011 11:54:22)
[13:26:09]   /usr/bin/last                                   [ Warning ]
[13:26:09] Warning: The file properties have changed:
[13:26:09]          File: /usr/bin/last
[13:26:09]          Current hash: 2625728968b194b87e9f77a58d990c9294b4017d
[13:26:09]          Stored hash : b278e69e86979d2293bbdb7049fa4b4fdc7c6c17
[13:26:09]          Current inode: 11141991    Stored inode: 11145526
[13:26:10]          Current file modification time: 1343327018 (26-Jul-2012 20:23:38)
[13:26:10]          Stored file modification time : 1323931247 (15-Dec-2011 07:40:47)
[13:26:10]   /usr/bin/lastlog                                [ Warning ]
[13:26:10] Warning: The file properties have changed:
[13:26:10]          File: /usr/bin/lastlog
[13:26:10]          Current hash: 54c11b7404bb7ed4279e50d4a8a93ab3c6578923
[13:26:10]          Stored hash : fbf0dd41fbec3bfd28de80951d8ca59fe73a71ff
[13:26:10]          Current inode: 11144733    Stored inode: 11141976
[13:26:10]          Current file modification time: 1333939214 (09-Apr-2012 04:40:14)
[13:26:10]          Stored file modification time : 1308908220 (24-Jun-2011 11:37:00)
[13:26:10]   /usr/bin/ldd                                    [ Warning ]
[13:26:10] Warning: The file properties have changed:
[13:26:10]          File: /usr/bin/ldd
[13:26:10]          Current hash: ba7c47b3f3d0c162f617a3d9aed90e4d6e64bfc9
[13:26:10]          Stored hash : d61d46508e2138f4cc8e1713a0fbad2bdfdec315
[13:26:10]          Current inode: 11151906    Stored inode: 11142607
[13:26:10]          Current size: 5267    Stored size: 5279
[13:26:10]          Current file modification time: 1334883658 (20-Apr-2012 03:00:58)
[13:26:10]          Stored file modification time : 1317766006 (05-Oct-2011 00:06:46)
[13:26:10] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[13:26:10]   /usr/bin/less                                   [ OK ]
[13:26:10]   /usr/bin/locate                                 [ OK ]
[13:26:10]   /usr/bin/logger                                 [ Warning ]
[13:26:11] Warning: The file properties have changed:
[13:26:11]          File: /usr/bin/logger
[13:26:11]          Current hash: 836f2026923964ac7c03ec86eaaeb64b51709d7a
[13:26:11]          Stored hash : 04a2a801ae8a17b7be26c30ec041a2dda5aac764
[13:26:11]          Current inode: 11141979    Stored inode: 11141250
[13:26:11]          Current size: 18284    Stored size: 10056
[13:26:11]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:11]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:11]   /usr/bin/lsattr                                 [ Warning ]
[13:26:11] Warning: The file properties have changed:
[13:26:11]          File: /usr/bin/lsattr
[13:26:11]          Current hash: 93cb203c6946ddc4702adaa5be62cd5457cc3464
[13:26:11]          Stored hash : 0a157f7b5b88666934dd02e9440b198aeaab197c
[13:26:11]          Current inode: 11141355    Stored inode: 11141828
[13:26:11]          Current size: 9684    Stored size: 9620
[13:26:11]          Current file modification time: 1333139128 (30-Mar-2012 22:25:28)
[13:26:11]          Stored file modification time : 1300385203 (17-Mar-2011 19:06:43)
[13:26:11]   /usr/bin/lsof                                   [ OK ]
[13:26:11]   /usr/bin/md5sum                                 [ Warning ]
[13:26:11] Warning: The file properties have changed:
[13:26:11]          File: /usr/bin/md5sum
[13:26:11]          Current hash: 2bbf9c7348e71f08e4049b1180d734dd7423323e
[13:26:11]          Stored hash : 571b0b0f74eb66d97988ed57418e57fd7906fff9
[13:26:11]          Current inode: 11149518    Stored inode: 11141876
[13:26:11]          Current size: 34388    Stored size: 30264
[13:26:12]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:12]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:12]   /usr/bin/mlocate                                [ OK ]
[13:26:12]   /usr/bin/newgrp                                 [ Warning ]
[13:26:12] Warning: The file properties have changed:
[13:26:12]          File: /usr/bin/newgrp
[13:26:12]          Current hash: 14d17d5cd146d36d2491784be316527aa54d5e73
[13:26:12]          Stored hash : 7673489f5a2ea8f54ac5f2389d115870667cba57
[13:26:12]          Current inode: 11148472    Stored inode: 11141977
[13:26:12]          Current file modification time: 1333939214 (09-Apr-2012 04:40:14)
[13:26:12]          Stored file modification time : 1308908220 (24-Jun-2011 11:37:00)
[13:26:12]   /usr/bin/passwd                                 [ Warning ]
[13:26:12] Warning: The file properties have changed:
[13:26:12]          File: /usr/bin/passwd
[13:26:12]          Current hash: 880227a648e432a36a6d80d5ca7b72125694b330
[13:26:12]          Stored hash : 7cf3965cc16baead73918d7b47c2ed4a9179cb6e
[13:26:12]          Current inode: 11142102    Stored inode: 11144376
[13:26:12]          Current file modification time: 1333939212 (09-Apr-2012 04:40:12)
[13:26:12]          Stored file modification time : 1308908218 (24-Jun-2011 11:36:58)
[13:26:12]   /usr/bin/perl                                   [ Warning ]
[13:26:12] Warning: The file properties have changed:
[13:26:12]          File: /usr/bin/perl
[13:26:13]          Current hash: 88f66ee08d5007685c53f35cea870a6b6f55a2e6
[13:26:13]          Stored hash : 5a5edc8b6bf955a67f6aa4d339525611e07b23c2
[13:26:13]          Current inode: 11142480    Stored inode: 11145081
[13:26:13]          Current size: 1462760    Stored size: 1417064
[13:26:13]          Current file modification time: 1344636070 (11-Aug-2012 00:01:10)
[13:26:13]          Stored file modification time : 1315297373 (06-Sep-2011 10:22:53)
[13:26:13]   /usr/bin/pgrep                                  [ Warning ]
[13:26:13] Warning: The file properties have changed:
[13:26:13]          File: /usr/bin/pgrep
[13:26:13]          Current hash: f25a0d59ea8d1934d328e1d83bb8b5d499408b28
[13:26:13]          Stored hash : 25146fac7de4008d171a38779eeb4f189d67b167
[13:26:13]          Current inode: 11142026    Stored inode: 11143987
[13:26:13]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:13]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:13]   /usr/bin/pkill                                  [ Warning ]
[13:26:13] Warning: The file '/usr/bin/pkill' exists on the system, but it is not present in the rkhunter.dat file.
[13:26:13]   /usr/bin/pstree                                 [ Warning ]
[13:26:13] Warning: The file properties have changed:
[13:26:13]          File: /usr/bin/pstree
[13:26:13]          Current hash: 513387a0aa8864bf0e7a45691966f2ae38ac0adf
[13:26:13]          Stored hash : 0c6b3db667b2ab6f0b7a9dce8cf7c4a3e2265d45
[13:26:13]          Current inode: 11146364    Stored inode: 11144993
[13:26:13]          Current file modification time: 1342483144 (17-Jul-2012 01:59:04)
[13:26:13]          Stored file modification time : 1308736462 (22-Jun-2011 11:54:22)
[13:26:13]   /usr/bin/rkhunter                               [ Warning ]
[13:26:14] Warning: The file properties have changed:
[13:26:14]          File: /usr/bin/rkhunter
[13:26:14]          Current hash: 2ac9e2d1a42624475180907bc8e0cbcea3d9c49a
[13:26:14]          Stored hash : d26a91ad9933c889a07a220a884d1fb65934eb18
[13:26:14]          Current inode: 11141685    Stored inode: 11162012
[13:26:14]          Current size: 496633    Stored size: 496629
[13:26:14]          Current file modification time: 1321268691 (14-Nov-2011 12:04:51)
[13:26:14]          Stored file modification time : 1311778994 (27-Jul-2011 17:03:14)
[13:26:14]   /usr/bin/runcon                                 [ Warning ]
[13:26:14] Warning: The file properties have changed:
[13:26:14]          File: /usr/bin/runcon
[13:26:14]          Current hash: d3fcfcfac41d4870ea451a225915d0898589da20
[13:26:14]          Stored hash : fc4ff549823365527862865e60fdf7e48015fd4c
[13:26:14]          Current inode: 11149530    Stored inode: 11142184
[13:26:14]          Current size: 26212    Stored size: 22032
[13:26:14]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:14]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:14]   /usr/bin/sha1sum                                [ Warning ]
[13:26:14] Warning: The file properties have changed:
[13:26:14]          File: /usr/bin/sha1sum
[13:26:14]          Current hash: 007e69fff5ad5f84e96df341734d7f6f82738a77
[13:26:14]          Stored hash : da3445d0b1b7a2d407822f2ca51fce0643e6d532
[13:26:14]          Current inode: 11149532    Stored inode: 11142235
[13:26:14]          Current size: 34388    Stored size: 30264
[13:26:14]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:14]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:15]   /usr/bin/sha224sum                              [ Warning ]
[13:26:15] Warning: The file properties have changed:
[13:26:15]          File: /usr/bin/sha224sum
[13:26:15]          Current hash: d919ed3e203ae82b573dc9e48a97441cdd58a4ef
[13:26:15]          Stored hash : ff83d33bcc92b46a322863aa4d9fc47c100af9f7
[13:26:15]          Current inode: 11149534    Stored inode: 11142236
[13:26:15]          Current size: 42584    Stored size: 38460
[13:26:15]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:15]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:15]   /usr/bin/sha256sum                              [ Warning ]
[13:26:15] Warning: The file properties have changed:
[13:26:15]          File: /usr/bin/sha256sum
[13:26:15]          Current hash: a977f16eac1454ec1c6ca87c75ed59b94a01df72
[13:26:15]          Stored hash : c2fe8d76c0f373ef80ff8930abdfb65fde9b344b
[13:26:15]          Current inode: 11149536    Stored inode: 11142237
[13:26:15]          Current size: 42584    Stored size: 38460
[13:26:15]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:15]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:15]   /usr/bin/sha384sum                              [ Warning ]
[13:26:15] Warning: The file properties have changed:
[13:26:15]          File: /usr/bin/sha384sum
[13:26:15]          Current hash: 25e822f1c91c45a147ebaf09ce70d01abc74ffe4
[13:26:15]          Stored hash : f768178f3380f40bfd336c002eba4daf141239df
[13:26:15]          Current inode: 11149538    Stored inode: 11142238
[13:26:15]          Current size: 95832    Stored size: 91708
[13:26:15]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:15]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:16]   /usr/bin/sha512sum                              [ Warning ]
[13:26:16] Warning: The file properties have changed:
[13:26:16]          File: /usr/bin/sha512sum
[13:26:16]          Current hash: 134021ebda1e5ffdc984c42e9bad5166a75f3088
[13:26:16]          Stored hash : 902459a8365f9cd4aafd862f4c465142eba631c1
[13:26:16]          Current inode: 11150982    Stored inode: 11142239
[13:26:16]          Current size: 95832    Stored size: 91708
[13:26:16]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:16]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:16]   /usr/bin/size                                   [ Warning ]
[13:26:16] Warning: The file properties have changed:
[13:26:16]          File: /usr/bin/size
[13:26:16]          Current hash: 9fb32ddfdc4279d1435bd4442ec574c4e31a9308
[13:26:16]          Stored hash : c508de720203345854f39e236a63e67215b0c07c
[13:26:16]          Current inode: 11163307    Stored inode: 11149516
[13:26:16]          Current file modification time: 1331236413 (08-Mar-2012 20:53:33)
[13:26:16]          Stored file modification time : 1324662102 (23-Dec-2011 18:41:42)
[13:26:16]   /usr/bin/sort                                   [ Warning ]
[13:26:16] Warning: The file properties have changed:
[13:26:16]          File: /usr/bin/sort
[13:26:16]          Current hash: cb8649c4bda2dfe5eab7dbf71026711bf3a4ff1c
[13:26:16]          Stored hash : f7ea23aeead9c627fc5f3b8605f9c55cc90f4760
[13:26:16]          Current inode: 11151000    Stored inode: 11142269
[13:26:16]          Current size: 92164    Stored size: 75684
[13:26:16]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:16]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:17]   /usr/bin/stat                                   [ Warning ]
[13:26:17] Warning: The file properties have changed:
[13:26:17]          File: /usr/bin/stat
[13:26:17]          Current hash: 75e5943b347761b08f98e5ff7d08c02de586d251
[13:26:17]          Stored hash : 9d1b7052efb3c8f439721d61aa31430c83059bce
[13:26:17]          Current inode: 11151829    Stored inode: 11142290
[13:26:17]          Current size: 67308    Stored size: 42588
[13:26:17]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:17]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:17]   /usr/bin/strace                                 [ OK ]
[13:26:17]   /usr/bin/strings                                [ Warning ]
[13:26:17] Warning: The file properties have changed:
[13:26:17]          File: /usr/bin/strings
[13:26:17]          Current hash: 7e565bf4c888e33ac9b4a73b6bd239230b2d20b1
[13:26:17]          Stored hash : 2ee02e69ac92238c73cb60ca97aaf24a6ba772d9
[13:26:17]          Current inode: 11163310    Stored inode: 11149519
[13:26:17]          Current file modification time: 1331236413 (08-Mar-2012 20:53:33)
[13:26:17]          Stored file modification time : 1324662102 (23-Dec-2011 18:41:42)
[13:26:17]   /usr/bin/sudo                                   [ Warning ]
[13:26:17] Warning: The file properties have changed:
[13:26:17]          File: /usr/bin/sudo
[13:26:17]          Current hash: 43ef98e74deefeb340e84e1bcd101c5b4a3fb342
[13:26:17]          Stored hash : 19061a1c19fada523c2f0e6d8b53bd09f2a6e6b1
[13:26:17]          Current inode: 11144770    Stored inode: 11148897
[13:26:17]          Current size: 69708    Stored size: 156824
[13:26:18]          Current file modification time: 1338522834 (01-Jun-2012 05:53:54)
[13:26:18]          Stored file modification time : 1315767984 (11-Sep-2011 21:06:24)
[13:26:18]   /usr/bin/tail                                   [ Warning ]
[13:26:18] Warning: The file properties have changed:
[13:26:18]          File: /usr/bin/tail
[13:26:18]          Current hash: eff0056c1c86c0f3489db32f456be1a89cf5a663
[13:26:18]          Stored hash : 653af3936ae34d083054f64fbcd153970e84b4ee
[13:26:18]          Current inode: 11151835    Stored inode: 11142307
[13:26:18]          Current size: 59048    Stored size: 50832
[13:26:18]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:18]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:18]   /usr/bin/test                                   [ Warning ]
[13:26:18] Warning: The file properties have changed:
[13:26:18]          File: /usr/bin/test
[13:26:18]          Current hash: 1d77deb0b53abf2ee1bdae3dbeb939ad22f0127b
[13:26:18]          Stored hash : 506cd25a2325d038828bc14bf037151c5460ca0b
[13:26:18]          Current inode: 11151839    Stored inode: 11142319
[13:26:18]          Current size: 30272    Stored size: 26148
[13:26:18]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:18]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:18]   /usr/bin/top                                    [ Warning ]
[13:26:18] Warning: The file properties have changed:
[13:26:18]          File: /usr/bin/top
[13:26:18]          Current hash: b59b251dd4b2957f7fec94c37a652b2f43c3142f
[13:26:18]          Stored hash : 7a4abe4a19ee7b739165f7b6cf1872a82eb23175
[13:26:19]          Current inode: 11151015    Stored inode: 11143986
[13:26:19]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:19]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:19]   /usr/bin/touch                                  [ Warning ]
[13:26:19] Warning: The file properties have changed:
[13:26:19]          File: /usr/bin/touch
[13:26:19]          Current hash: 4a7f12900210158668b7873afc687ce1111a2b54
[13:26:19]          Stored hash : 2d45e9d268e8f32ef6a066ef033052d0f77668bc
[13:26:19]          Current inode: 11163333    Stored inode: 11142335
[13:26:19]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:19]          Stored file modification time : 1315346661 (07-Sep-2011 00:04:21)
[13:26:19]   /usr/bin/tr                                     [ Warning ]
[13:26:19] Warning: The file properties have changed:
[13:26:19]          File: /usr/bin/tr
[13:26:19]          Current hash: 949a559c06385c34a9013455f6d9603d2e3a1edd
[13:26:19]          Stored hash : 65680947a0bf8d829ee7c856c329ab5497c755e5
[13:26:19]          Current inode: 11151843    Stored inode: 11142337
[13:26:19]          Current size: 38472    Stored size: 34348
[13:26:19]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:19]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:19]   /usr/bin/uniq                                   [ Warning ]
[13:26:19] Warning: The file properties have changed:
[13:26:19]          File: /usr/bin/uniq
[13:26:19]          Current hash: f48f413acf102b68a09b4545c69a1f85ddd19a6e
[13:26:19]          Stored hash : 5324a020ee77bcb4867fab638d78fee78ca62dcc
[13:26:19]          Current inode: 11151853    Stored inode: 11142373
[13:26:19]          Current size: 34400    Stored size: 30224
[13:26:19]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:19]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:20]   /usr/bin/users                                  [ Warning ]
[13:26:20] Warning: The file properties have changed:
[13:26:20]          File: /usr/bin/users
[13:26:20]          Current hash: 483a64614c7ab6efc0f4b04c404cc87cb4e7dd94
[13:26:20]          Stored hash : 817c164e42afdd4bb3bb99a8355efde885e46f83
[13:26:20]          Current inode: 11147157    Stored inode: 11142399
[13:26:20]          Current size: 26180    Stored size: 22000
[13:26:20]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:20]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:20]   /usr/bin/vmstat                                 [ Warning ]
[13:26:20] Warning: The file properties have changed:
[13:26:20]          File: /usr/bin/vmstat
[13:26:20]          Current hash: 2a2a5ba8481de245b9de6455a92db86fb3bcef52
[13:26:20]          Stored hash : 29e23048e4e413e71d8856ac65c7541a51b2f34d
[13:26:20]          Current inode: 11151121    Stored inode: 11143990
[13:26:20]          Current size: 22036    Stored size: 22032
[13:26:20]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:20]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:20]   /usr/bin/w                                      [ Warning ]
[13:26:20] Warning: The file properties have changed:
[13:26:20]          File: /usr/bin/w
[13:26:20]          Current hash: 6fb11f07d65e29075c177adade3ab864112eb579
[13:26:20]          Stored hash : ef1c6178cd02d9240a1903796f59371283dc4ab0
[13:26:21]   /usr/bin/watch                                  [ Warning ]
[13:26:21] Warning: The file properties have changed:
[13:26:21]          File: /usr/bin/watch
[13:26:21]          Current hash: b8656131e78aef667c0e96c0e3381554ff05f3a7
[13:26:21]          Stored hash : bdfbf0cfa4914cb5554e8836fdd6f335f443e541
[13:26:21]          Current inode: 11151153    Stored inode: 11143994
[13:26:21]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:21]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:21]   /usr/bin/wc                                     [ Warning ]
[13:26:21] Warning: The file properties have changed:
[13:26:21]          File: /usr/bin/wc
[13:26:21]          Current hash: 215b2024f3333740a2cabcf114746801e7b33fb3
[13:26:21]          Stored hash : 3a85fc0a4367447a375e2b86d102dc141188e718
[13:26:21]          Current inode: 11153230    Stored inode: 11142418
[13:26:21]          Current size: 34420    Stored size: 30300
[13:26:21]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:21]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:21]   /usr/bin/wget                                   [ Warning ]
[13:26:21] Warning: The file properties have changed:
[13:26:21]          File: /usr/bin/wget
[13:26:21]          Current hash: f1fc9a232bf3f4d54b6d1847a81639a9c691ac9e
[13:26:21]          Stored hash : 7b23f912a04ea2ebff57a789724f813b43066a48
[13:26:21]          Current inode: 11142278    Stored inode: 11141161
[13:26:21]          Current size: 370348    Stored size: 357932
[13:26:21]          Current file modification time: 1328923535 (11-Feb-2012 02:25:35)
[13:26:21]          Stored file modification time : 1305663448 (17-May-2011 22:17:28)
[13:26:22]   /usr/bin/whatis                                 [ Warning ]
[13:26:22] Warning: The file properties have changed:
[13:26:22]          File: /usr/bin/whatis
[13:26:22]          Current hash: 83d5f4539f4234a073d1e6ab2e6f21f13200bd05
[13:26:22]          Stored hash : 3f8ab2fbae30baa1f8a1e7a436b74230b4bbeeeb
[13:26:22]          Current inode: 11146619    Stored inode: 11141621
[13:26:22]          Current file modification time: 1333217319 (31-Mar-2012 20:08:39)
[13:26:22]          Stored file modification time : 1311765479 (27-Jul-2011 13:17:59)
[13:26:22]   /usr/bin/whereis                                [ Warning ]
[13:26:22] Warning: The file properties have changed:
[13:26:22]          File: /usr/bin/whereis
[13:26:22]          Current hash: 2eb87d3189a4ae0c11dd98e66beb6082a16ca2e5
[13:26:22]          Stored hash : 55754930706f3d51c27542bfcc527802b9ac8038
[13:26:22]          Current inode: 11144913    Stored inode: 11147478
[13:26:22]          Current size: 9936    Stored size: 9928
[13:26:22]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:22]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:22]   /usr/bin/which                                  [ Warning ]
[13:26:22] Warning: The file properties have changed:
[13:26:22]          File: /usr/bin/which
[13:26:22]          Current inode: 11142096    Stored inode: 11150895
[13:26:22]          Current file modification time: 1333044192 (29-Mar-2012 20:03:12)
[13:26:22]          Stored file modification time : 1318553963 (14-Oct-2011 02:59:23)
[13:26:22]   /usr/bin/who                                    [ Warning ]
[13:26:22] Warning: The file properties have changed:
[13:26:22]          File: /usr/bin/who
[13:26:23]          Current hash: 9e655d3edd1ec02f1dbbb73020894cfb136e004e
[13:26:23]          Stored hash : b7d4268a56b7c93df7994da12f2c6718a3d91eba
[13:26:23]          Current inode: 11147154    Stored inode: 11142425
[13:26:23]          Current size: 46720    Stored size: 42600
[13:26:23]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:23]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:23]   /usr/bin/whoami                                 [ Warning ]
[13:26:23] Warning: The file properties have changed:
[13:26:23]          File: /usr/bin/whoami
[13:26:23]          Current hash: 8825d9f1cb5bfd03e4aecf1f6e807d35bcafbaaa
[13:26:23]          Stored hash : 13f238ebdcab7b7672569482f1c0dd9cb00626c8
[13:26:23]          Current inode: 11153231    Stored inode: 11142426
[13:26:23]          Current size: 22060    Stored size: 17880
[13:26:23]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:23]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:23]   /usr/bin/unhide.rb                              [ Warning ]
[13:26:23] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[13:26:23]   /usr/bin/gawk                                   [ Warning ]
[13:26:23] Warning: The file properties have changed:
[13:26:23]          File: /usr/bin/gawk
[13:26:23]          Current hash: 251768e354db35bd5109ebfdc947cc6bf79b7df5
[13:26:23]          Stored hash : 758bca135d99a296e2f86f72c314deb498654a2e
[13:26:23]          Current inode: 11152603    Stored inode: 11146637
[13:26:23]          Current file modification time: 1333095714 (30-Mar-2012 10:21:54)
[13:26:23]          Stored file modification time : 1312920401 (09-Aug-2011 22:06:41)
[13:26:24]   /usr/bin/lwp-request                            [ Warning ]
[13:26:24] Warning: The file properties have changed:
[13:26:24]          File: /usr/bin/lwp-request
[13:26:24]          Current hash: 2ecd423401689d1b74365364f3e849c0473f3915
[13:26:24]          Stored hash : ad3706af1726f6253ed11705f4a54ce91f0b80fe
[13:26:24]          Current inode: 11147477    Stored inode: 11142120
[13:26:24]          Current size: 15059    Stored size: 14857
[13:26:24]          Current file modification time: 1322068248 (23-Nov-2011 18:10:48)
[13:26:24]          Stored file modification time : 1306474013 (27-May-2011 07:26:53)
[13:26:24] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[13:26:24]   /usr/bin/w.procps                               [ Warning ]
[13:26:24] Warning: The file properties have changed:
[13:26:24]          File: /usr/bin/w.procps
[13:26:24]          Current hash: 6fb11f07d65e29075c177adade3ab864112eb579
[13:26:24]          Stored hash : ef1c6178cd02d9240a1903796f59371283dc4ab0
[13:26:24]          Current inode: 11151133    Stored inode: 11143992
[13:26:24]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:24]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:25]   /sbin/depmod                                    [ Warning ]
[13:26:25] Warning: The file properties have changed:
[13:26:25]          File: /sbin/depmod
[13:26:25]          Current hash: e2e37f2566d94afa3890fdbf71faa34290409a25
[13:26:25]          Stored hash : 5e2f82e720331b528a3bce9a7d57c8308fcf8a04
[13:26:25]          Current inode: 12206    Stored inode: 3127
[13:26:25]          Current size: 67180    Stored size: 67176
[13:26:25]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:25]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:25]   /sbin/fsck                                      [ Warning ]
[13:26:25] Warning: The file properties have changed:
[13:26:25]          File: /sbin/fsck
[13:26:25]          Current hash: bfda05384a7cc0ea06c6a86e12ee8b6303a12fa6
[13:26:25]          Stored hash : b14bfe6fedaa0cb829dac9908b74d84314c688ec
[13:26:25]          Current inode: 17218    Stored inode: 27656
[13:26:25]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:25]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:26]   /sbin/ifconfig                                  [ Warning ]
[13:26:26] Warning: The file properties have changed:
[13:26:26]          File: /sbin/ifconfig
[13:26:26]          Current hash: f219e396b8d74562f3cbc93e593821dd3f00fa84
[13:26:26]          Stored hash : 079675775324db11974ab97956e2314658a87fe5
[13:26:26]          Current inode: 683    Stored inode: 72485
[13:26:26]          Current size: 69572    Stored size: 65708
[13:26:26]          Current file modification time: 1333158485 (31-Mar-2012 03:48:05)
[13:26:26]          Stored file modification time : 1278055671 (02-Jul-2010 09:27:51)
[13:26:26]   /sbin/ifdown                                    [ Warning ]
[13:26:26] Warning: The file properties have changed:
[13:26:26]          File: /sbin/ifdown
[13:26:26]          Current hash: 45d33275bee6dbc868870e269e2a89354629fdc0
[13:26:26]          Stored hash : 508dda71864d53e6526d91ca632966e2e7921d99
[13:26:26]          Current inode: 39105    Stored inode: 21265
[13:26:26]          Current size: 51544    Stored size: 47288
[13:26:26]          Current file modification time: 1333588938 (05-Apr-2012 03:22:18)
[13:26:26]          Stored file modification time : 1316028100 (14-Sep-2011 21:21:40)
[13:26:26]   /sbin/ifup                                      [ Warning ]
[13:26:26] Warning: The file properties have changed:
[13:26:26]          File: /sbin/ifup
[13:26:26]          Current hash: 45d33275bee6dbc868870e269e2a89354629fdc0
[13:26:26]          Stored hash : 508dda71864d53e6526d91ca632966e2e7921d99
[13:26:27]          Current inode: 39105    Stored inode: 21265
[13:26:27]          Current size: 51544    Stored size: 47288
[13:26:27]          Current file modification time: 1333588938 (05-Apr-2012 03:22:18)
[13:26:27]          Stored file modification time : 1316028100 (14-Sep-2011 21:21:40)
[13:26:27]   /sbin/init                                      [ Warning ]
[13:26:27] Warning: The file properties have changed:
[13:26:27]          File: /sbin/init
[13:26:27]          Current hash: 4e71902177fe4284ddf6dadb40c94a642213543c
[13:26:27]          Stored hash : fa94218cf2bc25fe4f55ae1c5abd1b1f38b42abe
[13:26:27]          Current inode: 3912    Stored inode: 2546
[13:26:27]          Current size: 190432    Stored size: 173936
[13:26:27]          Current file modification time: 1335454034 (26-Apr-2012 17:27:14)
[13:26:27]          Stored file modification time : 1319692444 (27-Oct-2011 07:14:04)
[13:26:27]   /sbin/insmod                                    [ Warning ]
[13:26:27] Warning: The file properties have changed:
[13:26:27]          File: /sbin/insmod
[13:26:27]          Current hash: 2d419b2997fe479395bc0bee3d237bc2a40fc757
[13:26:27]          Stored hash : fb8431d1800e112af0553d9e51ff12ef3e52a375
[13:26:27]          Current inode: 433    Stored inode: 184
[13:26:27]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:27]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:27]   /sbin/ip                                        [ Warning ]
[13:26:27] Warning: The file properties have changed:
[13:26:28]          File: /sbin/ip
[13:26:28]          Current hash: 9d944d26bf9d6e132672b1942ebca68f9e3a7c15
[13:26:28]          Stored hash : c4e61d1ee61ab3ae016e7ad2ffe2ea70158f97dd
[13:26:28]          Current inode: 39102    Stored inode: 40338
[13:26:28]          Current file modification time: 1334013614 (10-Apr-2012 01:20:14)
[13:26:28]          Stored file modification time : 1307379189 (06-Jun-2011 18:53:09)
[13:26:28]   /sbin/lsmod                                     [ Warning ]
[13:26:28] Warning: The file properties have changed:
[13:26:28]          File: /sbin/lsmod
[13:26:28]          Current hash: 0c6f96d430594fafc7b124f6c5591c3c5922e6cd
[13:26:28]          Stored hash : d96eabd2342056bec9518a173c9fc737f7a20d20
[13:26:28]          Current inode: 13757    Stored inode: 7160
[13:26:28]          Current file modification time: 1321828013 (20-Nov-2011 23:26:53)
[13:26:28]          Stored file modification time : 1318554254 (14-Oct-2011 03:04:14)
[13:26:28]   /sbin/modinfo                                   [ Warning ]
[13:26:28] Warning: The file properties have changed:
[13:26:28]          File: /sbin/modinfo
[13:26:28]          Current hash: b5285611f00caea2e700013dfc87a475c7062b04
[13:26:28]          Stored hash : 6d09fa650f27ae6b27c78f59f67bfec4f7bacfec
[13:26:28]          Current inode: 12208    Stored inode: 3129
[13:26:29]          Current size: 30220    Stored size: 26120
[13:26:29]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:29]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:29]   /sbin/modprobe                                  [ Warning ]
[13:26:29] Warning: The file properties have changed:
[13:26:29]          File: /sbin/modprobe
[13:26:29]          Current hash: b91a72e0e7945d86f445359985fadedf9d79cac3
[13:26:29]          Stored hash : 7baee7a39d59d150ea91f46fa48c791b4e63c568
[13:26:29]          Current inode: 3121    Stored inode: 3123
[13:26:29]          Current size: 54924    Stored size: 54920
[13:26:29]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:29]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:29]   /sbin/rmmod                                     [ Warning ]
[13:26:29] Warning: The file properties have changed:
[13:26:29]          File: /sbin/rmmod
[13:26:29]          Current hash: fae314cf0f77cecfe40ee2bb2172da9feb9be37a
[13:26:29]          Stored hash : dea9f43d4cfd537d53a8905e4bea4c75957350c3
[13:26:29]          Current inode: 12204    Stored inode: 3125
[13:26:30]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:30]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:30]   /sbin/route                                     [ Warning ]
[13:26:30] Warning: The file properties have changed:
[13:26:30]          File: /sbin/route
[13:26:30]          Current hash: 85e834f1220a69fb82cdac58d7ebe794be5c81ea
[13:26:30]          Stored hash : ef83ed98ee1c8efa47d7dd520245f1e7f0f7869b
[13:26:30]          Current inode: 11624    Stored inode: 72573
[13:26:30]          Current size: 56168    Stored size: 52268
[13:26:30]          Current file modification time: 1333158485 (31-Mar-2012 03:48:05)
[13:26:30]          Stored file modification time : 1278055671 (02-Jul-2010 09:27:51)
[13:26:30]   /sbin/runlevel                                  [ Warning ]
[13:26:30] Warning: The file properties have changed:
[13:26:30]          File: /sbin/runlevel
[13:26:30]          Current hash: b6031c64c325e7156591b981d93c61c05874282f
[13:26:30]          Stored hash : f8c30314f67f12effa73bb48294f239c182f0283
[13:26:30]          Current inode: 3916    Stored inode: 14356
[13:26:30]          Current file modification time: 1335454034 (26-Apr-2012 17:27:14)
[13:26:30]          Stored file modification time : 1319692444 (27-Oct-2011 07:14:04)
[13:26:31]   /sbin/sulogin                                   [ Warning ]
[13:26:31] Warning: The file properties have changed:
[13:26:31]          File: /sbin/sulogin
[13:26:31]          Current hash: d6b62b44207847e92418b10dd88ebe23fb597bd7
[13:26:31]          Stored hash : a341f5865137d2204a05e8e9391432f6d0e5e079
[13:26:31]          Current inode: 1245    Stored inode: 35287
[13:26:31]          Current file modification time: 1343327018 (26-Jul-2012 20:23:38)
[13:26:31]          Stored file modification time : 1323931247 (15-Dec-2011 07:40:47)
[13:26:31]   /sbin/sysctl                                    [ Warning ]
[13:26:31] Warning: The file properties have changed:
[13:26:31]          File: /sbin/sysctl
[13:26:31]          Current hash: 2d0e981e0ecf6b30be0d8a026e60869fb21d1169
[13:26:31]          Stored hash : 5bf6cd6c1e6674d2726b3dd00918d9cc49f6e9fe
[13:26:31]          Current inode: 7642    Stored inode: 39479
[13:26:31]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:31]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:32]   /bin/bash                                       [ Warning ]
[13:26:32] Warning: The file properties have changed:
[13:26:32]          File: /bin/bash
[13:26:32]          Current hash: 57ec2cd52e6e3f3e363073d88ff578d21ddff9d5
[13:26:32]          Stored hash : a464e2fd70e1cba8de9903beaa226ae1361c3ba5
[13:26:32]          Current inode: 3932253    Stored inode: 3932204
[13:26:32]          Current size: 920788    Stored size: 916692
[13:26:32]          Current file modification time: 1333468704 (03-Apr-2012 17:58:24)
[13:26:32]          Stored file modification time : 1305712465 (18-May-2011 11:54:25)
[13:26:32]   /bin/cat                                        [ Warning ]
[13:26:32] Warning: The file properties have changed:
[13:26:32]          File: /bin/cat
[13:26:32]          Current hash: d84f13c0d6fcbbb8e1ada71b38c46cb0f396be44
[13:26:32]          Stored hash : e0c6757116004f4d40684ce488b0d3ab204d680d
[13:26:32]          Current inode: 3932230    Stored inode: 3932179
[13:26:32]          Current size: 46764    Stored size: 38484
[13:26:32]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:33]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:22)
[13:26:33]   /bin/chmod                                      [ Warning ]
[13:26:33] Warning: The file properties have changed:
[13:26:33]          File: /bin/chmod
[13:26:33]          Current hash: 87e5600f729f373db293ee8dc3ae9607527def18
[13:26:33]          Stored hash : 48e93f869afd01baf939fb4006b0ac2f333f8280
[13:26:33]          Current inode: 3932916    Stored inode: 3932182
[13:26:33]          Current size: 50804    Stored size: 42588
[13:26:33]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:33]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:33]   /bin/chown                                      [ Warning ]
[13:26:33] Warning: The file properties have changed:
[13:26:33]          File: /bin/chown
[13:26:33]          Current hash: 85b05f1d49c2c7d5671ffa36f07921f5bd0a14f0
[13:26:33]          Stored hash : 9a862d670680b810ae93f380fd16ca720d7f8903
[13:26:33]          Current inode: 3932917    Stored inode: 3932183
[13:26:33]          Current size: 54936    Stored size: 46720
[13:26:33]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:33]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:33]   /bin/cp                                         [ Warning ]
[13:26:34] Warning: The file properties have changed:
[13:26:34]          File: /bin/cp
[13:26:34]          Current hash: 0c6de5919ea02d8c895ebb9daf408e1a7e9e90bc
[13:26:34]          Stored hash : 52d9102c847fe63421f8cae720eeb98b1e25ba4d
[13:26:34]          Current inode: 3932918    Stored inode: 3932185
[13:26:34]          Current size: 120708    Stored size: 100220
[13:26:34]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:34]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:34]   /bin/date                                       [ Warning ]
[13:26:34] Warning: The file properties have changed:
[13:26:34]          File: /bin/date
[13:26:34]          Current hash: e1d7915039e67113220b05458896c64cffd21c27
[13:26:34]          Stored hash : 07e17f213f973386f4ae7f7b801e8516169bc948
[13:26:34]          Current inode: 3932919    Stored inode: 3932188
[13:26:34]          Current size: 54916    Stored size: 50796
[13:26:34]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:34]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:34]   /bin/df                                         [ Warning ]
[13:26:34] Warning: The file properties have changed:
[13:26:34]          File: /bin/df
[13:26:34]          Current hash: 9d001f9c6525c4b7459e4bbd75648e33b67936b7
[13:26:34]          Stored hash : bd81ddced589bc7068a6f09c9fbad08f00c51e1f
[13:26:34]          Current inode: 3932922    Stored inode: 3932194
[13:26:34]          Current size: 79632    Stored size: 59076
[13:26:34]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:35]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:35]   /bin/dmesg                                      [ Warning ]
[13:26:35] Warning: The file properties have changed:
[13:26:35]          File: /bin/dmesg
[13:26:35]          Current hash: 035d216daf684f88ab46a354781093f5cdaf4717
[13:26:35]          Stored hash : 0f70af3e70ca3e5ade1a5b147685c2296764b7b3
[13:26:35]          Current inode: 3932259    Stored inode: 3932241
[13:26:35]          Current size: 22020    Stored size: 9672
[13:26:35]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:35]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:35]   /bin/echo                                       [ Warning ]
[13:26:35] Warning: The file properties have changed:
[13:26:35]          File: /bin/echo
[13:26:35]          Current hash: d0635facb9e3cbcbcea5f5ec78fb05b05df8578c
[13:26:35]          Stored hash : 1eb88507f8f48cb5de440bda758fc82568ea0ab9
[13:26:35]          Current inode: 3932926    Stored inode: 3932200
[13:26:35]          Current size: 26152    Stored size: 21968
[13:26:35]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:35]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:36]   /bin/ed                                         [ Warning ]
[13:26:36] Warning: The file properties have changed:
[13:26:36]          File: /bin/ed
[13:26:36]          Current hash: 17d26bd8b279b537461c55707becf42d0c65943b
[13:26:36]          Stored hash : 40ec4270e606e6865ba56c0b006c3e48311f12d9
[13:26:36]          Current inode: 3932223    Stored inode: 3932201
[13:26:36]          Current size: 42612    Stored size: 38464
[13:26:36]          Current file modification time: 1318845377 (17-Oct-2011 11:56:17)
[13:26:36]          Stored file modification time : 1288370707 (29-Oct-2010 18:45:07)
[13:26:36]   /bin/egrep                                      [ Warning ]
[13:26:36] Warning: The file properties have changed:
[13:26:36]          File: /bin/egrep
[13:26:36]          Current hash: 0bb41555d1a764bf972c9ec5b9f62ef1bba42308
[13:26:36]          Stored hash : 90a31e21215b0876c3facfc235fe3fc8405dc757
[13:26:36]          Current inode: 3932260    Stored inode: 3932256
[13:26:36]          Current size: 149596    Stored size: 141360
[13:26:36]          Current file modification time: 1324053903 (16-Dec-2011 17:45:03)
[13:26:36]          Stored file modification time : 1311764934 (27-Jul-2011 13:08:54)
[13:26:36] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[13:26:36]   /bin/fgrep                                      [ Warning ]
[13:26:36] Warning: The file properties have changed:
[13:26:36]          File: /bin/fgrep
[13:26:36]          Current hash: bc664a2891acebfc93cfb3b600d90f95e1318df4
[13:26:36]          Stored hash : ef335bc55bb2277a0c5af1ac5dfd4a5fcdcc4626
[13:26:37]          Current inode: 3932261    Stored inode: 3932264
[13:26:37]          Current size: 108500    Stored size: 100264
[13:26:37]          Current file modification time: 1324053903 (16-Dec-2011 17:45:03)
[13:26:37]          Stored file modification time : 1311764934 (27-Jul-2011 13:08:54)
[13:26:37] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[13:26:37]   /bin/fuser                                      [ Warning ]
[13:26:37] Warning: The file properties have changed:
[13:26:37]          File: /bin/fuser
[13:26:37]          Current hash: 6d321869dd7e5cfaf3867339708ae00599d2e911
[13:26:37]          Stored hash : 9e23b3ccddc715680a70ae752ff643202f185383
[13:26:37]          Current inode: 3932184    Stored inode: 3932196
[13:26:37]          Current size: 30832    Stored size: 30864
[13:26:37]          Current file modification time: 1342483144 (17-Jul-2012 01:59:04)
[13:26:37]          Stored file modification time : 1308736462 (22-Jun-2011 11:54:22)
[13:26:37]   /bin/grep                                       [ Warning ]
[13:26:37] Warning: The file properties have changed:
[13:26:37]          File: /bin/grep
[13:26:37]          Current hash: f306e5882a19081b99e84ec2c70917e54a2a0df6
[13:26:37]          Stored hash : ce536291f46f7197746a7457f310ee40ff7a0d17
[13:26:37]          Current inode: 3932219    Stored inode: 3932255
[13:26:37]          Current size: 153692    Stored size: 145488
[13:26:37]          Current file modification time: 1324053903 (16-Dec-2011 17:45:03)
[13:26:37]          Stored file modification time : 1311764934 (27-Jul-2011 13:08:54)
[13:26:38]   /bin/ip                                         [ Warning ]
[13:26:38] Warning: The file properties have changed:
[13:26:38]          File: /bin/ip
[13:26:38]          Current hash: 9d944d26bf9d6e132672b1942ebca68f9e3a7c15
[13:26:38]          Stored hash : c4e61d1ee61ab3ae016e7ad2ffe2ea70158f97dd
[13:26:38]          Current inode: 3932252    Stored inode: 3932199
[13:26:38]          Current size: 253984    Stored size: 244724
[13:26:38]          Current file modification time: 1334013616 (10-Apr-2012 01:20:16)
[13:26:38]          Stored file modification time : 1307379191 (06-Jun-2011 18:53:11)
[13:26:38]   /bin/kill                                       [ Warning ]
[13:26:38] Warning: The file properties have changed:
[13:26:38]          File: /bin/kill
[13:26:38]          Current hash: 02f685fe247a4d36e15028d0f2fdf60368bf6e2d
[13:26:38]          Stored hash : 380d6079e64cf184eda2f6d1d9496add9d060eef
[13:26:38]          Current inode: 3932195    Stored inode: 3932206
[13:26:38]          Current size: 17968    Stored size: 13872
[13:26:38]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:38]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:39]   /bin/less                                       [ OK ]
[13:26:39]   /bin/login                                      [ Warning ]
[13:26:39] Warning: The file properties have changed:
[13:26:39]          File: /bin/login
[13:26:39]          Current hash: 487f3019575eba58d874e9b2140fa4fcef0f955e
[13:26:39]          Stored hash : b3bf5d1034655b627e4c83e4d60ce2135627d0ed
[13:26:39]          Current inode: 3932176    Stored inode: 3932197
[13:26:39]          Current file modification time: 1333939214 (09-Apr-2012 04:40:14)
[13:26:39]          Stored file modification time : 1308908220 (24-Jun-2011 11:37:00)
[13:26:39]   /bin/ls                                         [ Warning ]
[13:26:39] Warning: The file properties have changed:
[13:26:39]          File: /bin/ls
[13:26:39]          Current hash: 9669825f7d0e35391437a61aca3b8d57f64e27eb
[13:26:39]          Stored hash : 093e96092af7fee745341af3a8ef6647b1802cd1
[13:26:39]          Current inode: 3933685    Stored inode: 3932233
[13:26:39]          Current size: 104508    Stored size: 96284
[13:26:39]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:39]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:39]   /bin/lsmod                                      [ Warning ]
[13:26:39] Warning: The file properties have changed:
[13:26:39]          File: /bin/lsmod
[13:26:39]          Current hash: 0c6f96d430594fafc7b124f6c5591c3c5922e6cd
[13:26:40]          Stored hash : d96eabd2342056bec9518a173c9fc737f7a20d20
[13:26:40]          Current inode: 3932208    Stored inode: 3932180
[13:26:40]          Current file modification time: 1321828016 (20-Nov-2011 23:26:56)
[13:26:40]          Stored file modification time : 1308230223 (16-Jun-2011 15:17:03)
[13:26:40]   /bin/mktemp                                     [ Warning ]
[13:26:40] Warning: The file properties have changed:
[13:26:40]          File: /bin/mktemp
[13:26:40]          Current hash: 1a6f1014ca86ed91619a653f02fee914b2ef4f95
[13:26:40]          Stored hash : 93dc7b74e8d02636eb04ba127ef50013c7bf35e9
[13:26:40]          Current inode: 3935635    Stored inode: 3932238
[13:26:40]          Current size: 34436    Stored size: 30316
[13:26:40]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:40]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:40]   /bin/more                                       [ Warning ]
[13:26:40] Warning: The file properties have changed:
[13:26:40]          File: /bin/more
[13:26:40]          Current hash: 67357fddbb41ef05364c71f864b9a1dc220841c9
[13:26:40]          Stored hash : 00985e2b761148b8042982c9d5e791c3a7c1df96
[13:26:40]          Current inode: 3932165    Stored inode: 3932257
[13:26:40]          Current size: 34492    Stored size: 34488
[13:26:40]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:40]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:40]   /bin/mount                                      [ Warning ]
[13:26:40] Warning: The file properties have changed:
[13:26:41]          File: /bin/mount
[13:26:41]          Current hash: 94e2ba76b7cb616c78173c765f333c9c9eef7407
[13:26:41]          Stored hash : 073ee6be8e977ce9ee02f9e59124af2e5ca1251e
[13:26:41]          Current inode: 3932234    Stored inode: 3932217
[13:26:41]          Current size: 88760    Stored size: 88716
[13:26:41]          Current file modification time: 1333082974 (30-Mar-2012 06:49:34)
[13:26:41]          Stored file modification time : 1312906529 (09-Aug-2011 18:15:29)
[13:26:41]   /bin/mv                                         [ Warning ]
[13:26:41] Warning: The file properties have changed:
[13:26:41]          File: /bin/mv
[13:26:41]          Current hash: 3b693826ffc2940b2a9b2a3dda30f415484d35ae
[13:26:41]          Stored hash : 14f253b7fd403bd5a93850263a1c4e31c0bd36ca
[13:26:41]          Current inode: 3933726    Stored inode: 3932244
[13:26:41]          Current size: 112488    Stored size: 92000
[13:26:41]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:41]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:41]   /bin/netstat                                    [ Warning ]
[13:26:41] Warning: The file properties have changed:
[13:26:41]          File: /bin/netstat
[13:26:41]          Current hash: 587159003076c21ba6f215b14b45da9769790e86
[13:26:41]          Stored hash : 77fb05b6622cdc4e087a6a5b26b45223c4d950a1
[13:26:41]          Current inode: 3932199    Stored inode: 3932249
[13:26:41]          Current size: 113920    Stored size: 110088
[13:26:41]          Current file modification time: 1333158485 (31-Mar-2012 03:48:05)
[13:26:41]          Stored file modification time : 1278055671 (02-Jul-2010 09:27:51)
[13:26:42]   /bin/ping                                       [ Warning ]
[13:26:42] Warning: The file '/bin/ping' exists on the system, but it is not present in the rkhunter.dat file.
[13:26:42]   /bin/ps                                         [ Warning ]
[13:26:42] Warning: The file properties have changed:
[13:26:42]          File: /bin/ps
[13:26:42]          Current hash: 19eb1124dba4499f28a669d20723b78fa3a39791
[13:26:42]          Stored hash : faceae36495a5eea3d7748cf3419f63137bd027e
[13:26:42]          Current inode: 3932196    Stored inode: 3932239
[13:26:42]          Current file modification time: 1323711659 (12-Dec-2011 18:40:59)
[13:26:42]          Stored file modification time : 1308866480 (24-Jun-2011 00:01:20)
[13:26:42]   /bin/pwd                                        [ Warning ]
[13:26:42] Warning: The file properties have changed:
[13:26:42]          File: /bin/pwd
[13:26:42]          Current hash: 00296d7d786382e68ca132914aab69c9ccff34b8
[13:26:42]          Stored hash : 6b7a38f3c10bd5146574b01fdb5233e36c3d149a
[13:26:42]          Current inode: 3934471    Stored inode: 3932271
[13:26:42]          Current size: 26220    Stored size: 22036
[13:26:42]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:42]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:42]   /bin/readlink                                   [ Warning ]
[13:26:42] Warning: The file properties have changed:
[13:26:42]          File: /bin/readlink
[13:26:42]          Current hash: d44dcd0e36d3c92e645451e5cdacd3f822f428ec
[13:26:42]          Stored hash : 58aa82f9d08b0577de22e40e6097bfe99a6fb082
[13:26:42]          Current inode: 3934472    Stored inode: 3932273
[13:26:42]          Current size: 34404    Stored size: 30280
[13:26:42]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:42]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:43]   /bin/sed                                        [ OK ]
[13:26:43]   /bin/sh                                         [ Warning ]
[13:26:43] Warning: The file properties have changed:
[13:26:43]          File: /bin/sh
[13:26:43]          Current hash: 09d42c4d133125ca1a45be411eaa8681138d534f
[13:26:43]          Stored hash : 1849a7433201689c678b8b1af604e18569e67132
[13:26:43]          Current inode: 3932229    Stored inode: 3932219
[13:26:43]          Current file modification time: 1333042817 (29-Mar-2012 19:40:17)
[13:26:43]          Stored file modification time : 1304434915 (03-May-2011 17:01:55)
[13:26:43]   /bin/su                                         [ Warning ]
[13:26:43] Warning: The file properties have changed:
[13:26:43]          File: /bin/su
[13:26:43]          Current hash: fff229fe2aa1543902c66255992ae949977bfab3
[13:26:43]          Stored hash : 922107e5884d91c607cd55ace7dfa7dbedf9b6c1
[13:26:43]          Current inode: 3932276    Stored inode: 3932198
[13:26:43]          Current file modification time: 1333939214 (09-Apr-2012 04:40:14)
[13:26:43]          Stored file modification time : 1308908220 (24-Jun-2011 11:37:00)
[13:26:43]   /bin/touch                                      [ Warning ]
[13:26:43] Warning: The file properties have changed:
[13:26:43]          File: /bin/touch
[13:26:43]          Current hash: 4a7f12900210158668b7873afc687ce1111a2b54
[13:26:43]          Stored hash : 2d45e9d268e8f32ef6a066ef033052d0f77668bc
[13:26:43]          Current inode: 3935430    Stored inode: 3932296
[13:26:43]          Current size: 54980    Stored size: 42552
[13:26:43]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:43]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:43]   /bin/uname                                      [ Warning ]
[13:26:43] Warning: The file properties have changed:
[13:26:43]          File: /bin/uname
[13:26:43]          Current hash: 4d2dbe169d5df5aa6680e5839b9477a2f56fc66b
[13:26:43]          Stored hash : b74bb9ee5999aec68a87511137b9cebebada3133
[13:26:43]          Current inode: 3935634    Stored inode: 3932300
[13:26:43]          Current size: 26180    Stored size: 21996
[13:26:44]          Current file modification time: 1333249930 (01-Apr-2012 05:12:10)
[13:26:44]          Stored file modification time : 1298467341 (23-Feb-2011 14:22:21)
[13:26:44]   /bin/which                                      [ Warning ]
[13:26:44] Warning: The file properties have changed:
[13:26:44]          File: /bin/which
[13:26:44]          Current inode: 3933268    Stored inode: 3932193
[13:26:44]          Current file modification time: 1333044192 (29-Mar-2012 20:03:12)
[13:26:44]          Stored file modification time : 1310571280 (13-Jul-2011 17:34:40)
[13:26:44] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[13:26:44]   /bin/dash                                       [ Warning ]
[13:26:44] Warning: The file properties have changed:
[13:26:44]          File: /bin/dash
[13:26:44]          Current hash: 09d42c4d133125ca1a45be411eaa8681138d534f
[13:26:44]          Stored hash : 1849a7433201689c678b8b1af604e18569e67132
[13:26:44]          Current inode: 3932218    Stored inode: 3932164
[13:26:44]          Current size: 100284    Stored size: 96188
[13:26:44]          Current file modification time: 1333042817 (29-Mar-2012 19:40:17)
[13:26:44]          Stored file modification time : 1304434915 (03-May-2011 17:01:55)
[13:26:44]   /usr/sbin/unhide-linux26                        [ Warning ]
[13:26:44] Warning: The file '/usr/sbin/unhide-linux26' does not exist on the system, but it is present in the rkhunter.dat file.
[13:30:40]
[13:30:40] Info: Starting test name 'rootkits'
[13:30:40] Checking for rootkits...
[13:30:40]
[13:30:40] Info: Starting test name 'known_rkts'
[13:30:40] Performing check of known rootkit files and directories
[13:30:40]
[13:30:40] Checking for 55808 Trojan - Variant A...
[13:30:40]   Checking for file '/tmp/.../r'                  [ Not found ]
[13:30:40]   Checking for file '/tmp/.../a'                  [ Not found ]
[13:30:40] 55808 Trojan - Variant A                          [ Not found ]
[13:30:40]
[13:30:40] Checking for ADM Worm...
[13:30:40]   Checking for string 'w0rm'                      [ Not found ]
[13:30:40] ADM Worm                                          [ Not found ]
[13:30:40]
[13:30:40] Checking for AjaKit Rootkit...
[13:30:40]   Checking for file '/dev/tux/.addr'              [ Not found ]
[13:30:40]   Checking for file '/dev/tux/.proc'              [ Not found ]
[13:30:40]   Checking for file '/dev/tux/.file'              [ Not found ]
[13:30:40]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[13:30:40]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[13:30:40]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[13:30:40]   Checking for directory '/dev/tux'               [ Not found ]
[13:30:40]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[13:30:40] AjaKit Rootkit                                    [ Not found ]
[13:30:40]
[13:30:40] Checking for Adore Rootkit...
[13:30:40]   Checking for file '/usr/secure'                 [ Not found ]
[13:30:40]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[13:30:40]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[13:30:41]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[13:30:41]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[13:30:41]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[13:30:41]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[13:30:41]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[13:30:41]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[13:30:41]   Checking for file '/var/log/ssh/old'            [ Not found ]
[13:30:41]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/kern'          [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/backup'        [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[13:30:41]   Checking for directory '/lib/backup'            [ Not found ]
[13:30:41]   Checking for directory '/lib/backup/txt'        [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/work'          [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/sys'           [ Not found ]
[13:30:41]   Checking for directory '/var/log/ssh'           [ Not found ]
[13:30:41]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[13:30:41]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[13:30:41] Adore Rootkit                                     [ Not found ]
[13:30:41]
[13:30:41] Checking for aPa Kit...
[13:30:41]   Checking for file '/usr/share/.aPa'             [ Not found ]
[13:30:41] aPa Kit                                           [ Not found ]
[13:30:41]
[13:30:41] Checking for Apache Worm...
[13:30:41]   Checking for file '/bin/.log'                   [ Not found ]
[13:30:41] Apache Worm                                       [ Not found ]
[13:30:41]
[13:30:41] Checking for Ambient (ark) Rootkit...
[13:30:41]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[13:30:41]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[13:30:41]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[13:30:41]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[13:30:41]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[13:30:41]   Checking for directory '/dev/ptyxx'             [ Not found ]
[13:30:41] Ambient (ark) Rootkit                             [ Not found ]
[13:30:41]
[13:30:41] Checking for Balaur Rootkit...
[13:30:41]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[13:30:41]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[13:30:41]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[13:30:41]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[13:30:41] Balaur Rootkit                                    [ Not found ]
[13:30:41]
[13:30:41] Checking for BeastKit Rootkit...
[13:30:41]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[13:30:41]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[13:30:41]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[13:30:41]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[13:30:41]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[13:30:41]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[13:30:42]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[13:30:42]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[13:30:42] BeastKit Rootkit                                  [ Not found ]
[13:30:42]
[13:30:42] Checking for beX2 Rootkit...
[13:30:42]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[13:30:42]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[13:30:42]   Checking for directory '/usr/include/bex'       [ Not found ]
[13:30:42] beX2 Rootkit                                      [ Not found ]
[13:30:42]
[13:30:42] Checking for BOBKit Rootkit...
[13:30:42]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[13:30:42]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[13:30:42]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[13:30:42]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[13:30:42]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[13:30:42]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../find'           [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../du'             [ Not found ]
[13:30:42]   Checking for file '/usr/lib/.../top'            [ Not found ]
[13:30:42]   Checking for directory '/usr/sbin/...'          [ Not found ]
[13:30:42]   Checking for directory '/usr/include/...'       [ Not found ]
[13:30:42]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[13:30:42]   Checking for directory '/usr/lib/...'           [ Not found ]
[13:30:42]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[13:30:43]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[13:30:43]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[13:30:43]   Checking for directory '/tmp/.bkp'              [ Not found ]
[13:30:43] BOBKit Rootkit                                    [ Not found ]
[13:30:43]
[13:30:43] Checking for cb Rootkit...
[13:30:43]   Checking for file '/dev/srd0'                   [ Not found ]
[13:30:43]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[13:30:43]   Checking for file '/dev/mounnt'                 [ Not found ]
[13:30:43]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /cl'       [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /.x.tgz'   [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /statdx'   [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /wted'     [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /write'    [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /scan'     [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /sc'       [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /sl2'      [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /wroot'    [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /wscan'    [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /wu'       [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /v'        [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /read'     [ Not found ]
[13:30:43]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[13:30:43]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[13:30:43]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[13:30:43]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[13:30:43]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[13:30:43]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[13:30:43]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[13:30:43]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.system/.. /tcp.log' [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /curatare/attrib' [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /curatare/chattr' [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /curatare/ps' [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.zeen/.. /curatare/pstree' [ Not found ]
[13:30:43]   Checking for file '/usr/bin/.system/.. /.x/xC.o' [ Not found ]
[13:30:43]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[13:30:43]   Checking for directory '/usr/bin/.zeen/.. /curatare' [ Not found ]
[13:30:43]   Checking for directory '/usr/bin/.zeen/.. /scan' [ Not found ]
[13:30:43]   Checking for directory '/usr/bin/.system/.. '   [ Not found ]
[13:30:43] cb Rootkit                                        [ Not found ]
[13:30:43]
[13:30:43] Checking for CiNIK Worm (Slapper.B variant)...
[13:30:43]   Checking for file '/tmp/.cinik'                 [ Not found ]
[13:30:43]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[13:30:43] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[13:30:43]
[13:30:43] Checking for Danny-Boy's Abuse Kit...
[13:30:44]   Checking for file '/dev/mdev'                   [ Not found ]
[13:30:44]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[13:30:44] Danny-Boy's Abuse Kit                             [ Not found ]
[13:30:44]
[13:30:44] Checking for Devil RootKit...
[13:30:44]   Checking for file '/var/lib/games/.src'         [ Not found ]
[13:30:44]   Checking for file '/dev/dsx'                    [ Not found ]
[13:30:44]   Checking for file '/dev/caca'                   [ Not found ]
[13:30:44]   Checking for file '/dev/pro'                    [ Not found ]
[13:30:44]   Checking for file '/bin/bye'                    [ Not found ]
[13:30:44]   Checking for file '/bin/homedir'                [ Not found ]
[13:30:44]   Checking for file '/usr/bin/xfss'               [ Not found ]
[13:30:44]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[13:30:44]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[13:30:44]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[13:30:44] Devil RootKit                                     [ Not found ]
[13:30:44]
[13:30:44] Checking for Dica-Kit Rootkit...
[13:30:44]   Checking for file '/lib/.sso'                   [ Not found ]
[13:30:44]   Checking for file '/lib/.so'                    [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/read'       [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/write'      [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/va'         [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[13:30:44]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[13:30:44]   Checking for file '/usr/bin/.etc'               [ Not found ]
[13:30:44]   Checking for file '/etc/sshd_config'            [ Not found ]
[13:30:45]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[13:30:45]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[13:30:45]   Checking for directory '/var/run/...dica'       [ Not found ]
[13:30:45]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[13:30:45]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[13:30:45] Dica-Kit Rootkit                                  [ Not found ]
[13:30:45]
[13:30:45] Checking for Dreams Rootkit...
[13:30:45]   Checking for file '/dev/ttyoa'                  [ Not found ]
[13:30:45]   Checking for file '/dev/ttyof'                  [ Not found ]
[13:30:45]   Checking for file '/dev/ttyop'                  [ Not found ]
[13:30:45]   Checking for file '/usr/bin/sense'              [ Not found ]
[13:30:45]   Checking for file '/usr/bin/sl2'                [ Not found ]
[13:30:45]   Checking for file '/usr/bin/logclear'           [ Not found ]
[13:30:45]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[13:30:45]   Checking for file '/usr/bin/initrd'             [ Not found ]
[13:30:45]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[13:30:45]   Checking for file '/usr/bin/snfs'               [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libsss'             [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[13:30:45]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[13:30:45]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[13:30:45]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[13:30:45]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[13:30:45]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[13:30:45]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[13:30:45]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[13:30:45]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[13:30:45]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[13:30:45]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[13:30:45]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[13:30:45] Dreams Rootkit                                    [ Not found ]
[13:30:45]
[13:30:45] Checking for Duarawkz Rootkit...
[13:30:45]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[13:30:45]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[13:30:45] Duarawkz Rootkit                                  [ Not found ]
[13:30:45]
[13:30:45] Checking for Enye LKM...
[13:30:45]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[13:30:45]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[13:30:45] Enye LKM                                          [ Not found ]
[13:30:45]
[13:30:45] Checking for Flea Linux Rootkit...
[13:30:45]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[13:30:45]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[13:30:45]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[13:30:45]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[13:30:45]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[13:30:46]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[13:30:46]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[13:30:46]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[13:30:46]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[13:30:46]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[13:30:46]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[13:30:46]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[13:30:46]   Checking for directory '/dev/..0'               [ Not found ]
[13:30:46]   Checking for directory '/dev/..0/backup'        [ Not found ]
[13:30:46] Flea Linux Rootkit                                [ Not found ]
[13:30:46]
[13:30:46] Checking for Fu Rootkit...
[13:30:46]   Checking for file '/sbin/xc'                    [ Not found ]
[13:30:46]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[13:30:46]   Checking for file '/bin/.lib'                   [ Not found ]
[13:30:46] Fu Rootkit                                        [ Not found ]
[13:30:46]
[13:30:46] Checking for ****`it Rootkit...
[13:30:46]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[13:30:46]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[13:30:46]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[13:30:46]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[13:30:46]   Checking for file '/dev/proc/fuckit/system-bins/init' [ Not found ]
[13:30:46]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[13:30:46]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[13:30:46]   Checking for directory '/dev/proc'              [ Not found ]
[13:30:46]   Checking for directory '/dev/proc/fuckit'       [ Not found ]
[13:30:46]   Checking for directory '/dev/proc/fuckit/system-bins' [ Not found ]
[13:30:46]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[13:30:46] ****`it Rootkit                                   [ Not found ]
[13:30:46]
[13:30:46] Checking for GasKit Rootkit...
[13:30:46]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[13:30:46]   Checking for directory '/dev/dev'               [ Not found ]
[13:30:46]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[13:30:46]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[13:30:46] GasKit Rootkit                                    [ Not found ]
[13:30:46]
[13:30:46] Checking for Heroin LKM...
[13:30:46]   Checking for kernel symbol 'heroin'             [ Not found ]
[13:30:46] Heroin LKM                                        [ Not found ]
[13:30:46]
[13:30:46] Checking for HjC Kit...
[13:30:46]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[13:30:46] HjC Kit                                           [ Not found ]
[13:30:46]
[13:30:46] Checking for ignoKit Rootkit...
[13:30:47]   Checking for file '/lib/defs/p'                 [ Not found ]
[13:30:47]   Checking for file '/lib/defs/q'                 [ Not found ]
[13:30:47]   Checking for file '/lib/defs/r'                 [ Not found ]
[13:30:47]   Checking for file '/lib/defs/s'                 [ Not found ]
[13:30:47]   Checking for file '/lib/defs/t'                 [ Not found ]
[13:30:47]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[13:30:47]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[13:30:47]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[13:30:47]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[13:30:47]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[13:30:47]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[13:30:47]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[13:30:47]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[13:30:47]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[13:30:47] ignoKit Rootkit                                   [ Not found ]
[13:30:47]
[13:30:47] Checking for IntoXonia-NG Rootkit...
[13:30:47]   Checking for kernel symbol 'funces'             [ Not found ]
[13:30:47]   Checking for kernel symbol 'ixinit'             [ Not found ]
[13:30:47]   Checking for kernel symbol 'tricks'             [ Not found ]
[13:30:47]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[13:30:47]   Checking for kernel symbol 'rootme'             [ Not found ]
[13:30:47]   Checking for kernel symbol 'hide_module'        [ Not found ]
[13:30:47]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[13:30:48] IntoXonia-NG Rootkit                              [ Not found ]
[13:30:48]
[13:30:48] Checking for Irix Rootkit...
[13:30:48]   Checking for directory '/dev/pts/01'            [ Not found ]
[13:30:48]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[13:30:48]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[13:30:48]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[13:30:48] Irix Rootkit                                      [ Not found ]
[13:30:48]
[13:30:48] Checking for Jynx Rootkit...
[13:30:48]   Checking for file '/xochikit/bc'                [ Not found ]
[13:30:48]   Checking for file '/xochikit/ld_poison.so'      [ Not found ]
[13:30:48]   Checking for file '/omgxochi/bc'                [ Not found ]
[13:30:48]   Checking for file '/omgxochi/ld_poison.so'      [ Not found ]
[13:30:48]   Checking for directory '/xochikit'              [ Not found ]
[13:30:48]   Checking for directory '/omgxochi'              [ Not found ]
[13:30:48] Jynx Rootkit                                      [ Not found ]
[13:30:48]
[13:30:48] Checking for KBeast Rootkit...
[13:30:48]   Checking for file '/usr/_h4x_/ipsecs-kbeast-v1.ko' [ Not found ]
[13:30:48]   Checking for file '/usr/_h4x_/_h4x_bd'          [ Not found ]
[13:30:48]   Checking for file '/usr/_h4x_/acctlog'          [ Not found ]
[13:30:48]   Checking for directory '/usr/_h4x_'             [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_delete_module'  [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_getdents64'     [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_kill'           [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_open'           [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_read'           [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_rename'         [ Not found ]
[13:30:48]   Checking for kernel symbol 'h4x_rmdir'          [ Not found ]
[13:30:49]   Checking for kernel symbol 'h4x_tcp4_seq_show'  [ Not found ]
[13:30:49]   Checking for kernel symbol 'h4x_write'          [ Not found ]
[13:30:49] KBeast Rootkit                                    [ Not found ]
[13:30:49]
[13:30:49] Checking for Kitko Rootkit...
[13:30:49]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[13:30:49] Kitko Rootkit                                     [ Not found ]
[13:30:49]
[13:30:49] Checking for Knark Rootkit...
[13:30:49]   Checking for file '/proc/knark/pids'            [ Not found ]
[13:30:49]   Checking for directory '/proc/knark'            [ Not found ]
[13:30:49] Knark Rootkit                                     [ Not found ]
[13:30:49]
[13:30:49] Checking for ld-linuxv.so Rootkit...
[13:30:49]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[13:30:49]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[13:30:49]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[13:30:49]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[13:30:49] ld-linuxv.so Rootkit                              [ Not found ]
[13:30:49]
[13:30:49] Checking for Li0n Worm...
[13:30:49]   Checking for file '/bin/in.telnetd'             [ Not found ]
[13:30:49]   Checking for file '/bin/mjy'                    [ Not found ]
[13:30:49]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[13:30:49]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[13:30:49]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[13:30:49]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[13:30:49] Li0n Worm                                         [ Not found ]
[13:30:49]
[13:30:49] Checking for Lockit / LJK2 Rootkit...
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[13:30:49]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[13:30:50]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[13:30:50]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[13:30:50] Lockit / LJK2 Rootkit                             [ Not found ]
[13:30:50]
[13:30:50] Checking for Mood-NT Rootkit...
[13:30:50]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[13:30:50]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[13:30:50]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[13:30:50]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[13:30:50]   Checking for directory '/_cthulhu'              [ Not found ]
[13:30:50] Mood-NT Rootkit                                   [ Not found ]
[13:30:50]
[13:30:50] Checking for MRK Rootkit...
[13:30:50]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[13:30:50]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[13:30:50]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[13:30:50]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[13:30:50]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[13:30:50]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[13:30:50] MRK Rootkit                                       [ Not found ]
[13:30:50]
[13:30:50] Checking for Ni0 Rootkit...
[13:30:50]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[13:30:51]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[13:30:51]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[13:30:51]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[13:30:51]   Checking for directory '/tmp/waza'              [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[13:30:51]   Checking for directory '/usr/sbin/es'           [ Not found ]
[13:30:51] Ni0 Rootkit                                       [ Not found ]
[13:30:51]
[13:30:51] Checking for Ohhara Rootkit...
[13:30:51]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[13:30:51]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[13:30:51] Ohhara Rootkit                                    [ Not found ]
[13:30:51]
[13:30:51] Checking for Optic Kit (Tux) Worm...
[13:30:51]   Checking for directory '/dev/tux'               [ Not found ]
[13:30:51]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[13:30:51]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[13:30:51]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[13:30:51] Optic Kit (Tux) Worm                              [ Not found ]
[13:30:51]
[13:30:51] Checking for Oz Rootkit...
[13:30:51]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[13:30:51]   Checking for directory '/dev/.oz'               [ Not found ]
[13:30:51] Oz Rootkit                                        [ Not found ]
[13:30:51]
[13:30:51] Checking for Phalanx Rootkit...
[13:30:51]   Checking for file '/uNFuNF'                     [ Not found ]
[13:30:51]   Checking for file '/etc/host.ph1'               [ Not found ]
[13:30:51]   Checking for file '/bin/host.ph1'               [ Not found ]
[13:30:51]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[13:30:51]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[13:30:51]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[13:30:51]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[13:30:51]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[13:30:51] Phalanx Rootkit                                   [ Not found ]
[13:30:51]
[13:30:51] Checking for Phalanx2 Rootkit...
[13:30:51]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[13:30:51]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[13:30:51]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[13:30:51]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[13:30:51]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[13:30:51]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[13:30:51]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[13:30:51]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[13:30:51]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[13:30:51]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[13:30:51]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[13:30:51]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[13:30:51]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[13:30:51]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[13:30:51] Phalanx2 Rootkit                                  [ Not found ]
[13:30:52]
[13:30:52] Checking for Phalanx2 Rootkit (extended tests)...
[13:30:52]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[13:30:52]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[13:30:52]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[13:30:52] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[13:30:52]
[13:30:52] Checking for Portacelo Rootkit...
[13:30:52]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../.p'             [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../getty'          [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../show'           [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[13:30:52]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[13:30:52]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[13:30:52] Portacelo Rootkit                                 [ Not found ]
[13:30:52]
[13:30:52] Checking for R3dstorm Toolkit...
[13:30:52]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[13:30:52]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[13:30:52]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[13:30:52]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[13:30:52]   Checking for file '/bin/.../see_all'            [ Not found ]
[13:30:52]   Checking for directory '/var/log/tk02'          [ Not found ]
[13:30:52]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[13:30:52]   Checking for directory '/bin/...'               [ Not found ]
[13:30:52] R3dstorm Toolkit                                  [ Not found ]
[13:30:52]
[13:30:52] Checking for RH-Sharpe's Rootkit...
[13:30:52]   Checking for file '/bin/lps'                    [ Not found ]
[13:30:52]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[13:30:52]   Checking for file '/usr/bin/ltop'               [ Not found ]
[13:30:52]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[13:30:52]   Checking for file '/usr/bin/ldu'                [ Not found ]
[13:30:52]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[13:30:52]   Checking for file '/usr/bin/wp'                 [ Not found ]
[13:30:52]   Checking for file '/usr/bin/shad'               [ Not found ]
[13:30:52]   Checking for file '/usr/bin/vadim'              [ Not found ]
[13:30:52]   Checking for file '/usr/bin/slice'              [ Not found ]
[13:30:52]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[13:30:52]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[13:30:52] RH-Sharpe's Rootkit                               [ Not found ]
[13:30:52]
[13:30:52] Checking for RSHA's Rootkit...
[13:30:52]   Checking for file '/bin/kr4p'                   [ Not found ]
[13:30:53]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[13:30:53]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[13:30:53]   Checking for file '/usr/bin/slice2'             [ Not found ]
[13:30:53]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[13:30:53]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[13:30:53]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[13:30:53]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[13:30:53] RSHA's Rootkit                                    [ Not found ]
[13:30:53]
[13:30:53] Checking for Scalper Worm...
[13:30:53]   Checking for file '/tmp/.a'                     [ Not found ]
[13:30:53]   Checking for file '/tmp/.uua'                   [ Not found ]
[13:30:53] Scalper Worm                                      [ Not found ]
[13:30:53]
[13:30:53] Checking for Sebek LKM...
[13:30:53]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[13:30:53] Sebek LKM                                         [ Not found ]
[13:30:53]
[13:30:53] Checking for Shutdown Rootkit...
[13:30:53]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[13:30:53]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[13:30:53]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[13:30:53]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[13:30:53]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[13:30:53]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[13:30:53]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[13:30:53]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[13:30:53] Shutdown Rootkit                                  [ Not found ]
[13:30:53]
[13:30:53] Checking for SHV4 Rootkit...
[13:30:54]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[13:30:54]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[13:30:54]   Checking for file '/lib/lidps1.so'              [ Not found ]
[13:30:54]   Checking for file '/lib/libproc.a'              [ Not found ]
[13:30:54]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[13:30:54]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[13:30:54]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[13:30:54]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[13:30:54]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[13:30:54]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[13:30:54]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[13:30:54]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[13:30:54]   Checking for file '/usr/include/file.h'         [ Not found ]
[13:30:54]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[13:30:54]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[13:30:54]   Checking for file '/usr/include/log.h'          [ Not found ]
[13:30:54]   Checking for file '/usr/include/proc.h'         [ Not found ]
[13:30:54]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[13:30:54]   Checking for file '/dev/srd0'                   [ Not found ]
[13:30:54]   Checking for directory '/lib/ldd.so'            [ Not found ]
[13:30:54]   Checking for directory '/lib/security/.config'  [ Not found ]
[13:30:54]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[13:30:54] SHV4 Rootkit                                      [ Not found ]
[13:30:54]
[13:30:54] Checking for SHV5 Rootkit...
[13:30:54]   Checking for file '/etc/sh.conf'                [ Not found ]
[13:30:54]   Checking for file '/lib/libproc.a'              [ Not found ]
[13:30:54]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[13:30:54]   Checking for file '/lib/lidps1.so'              [ Not found ]
[13:30:54]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[13:30:54]   Checking for file '/usr/include/file.h'         [ Not found ]
[13:30:54]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[13:30:54]   Checking for file '/usr/include/log.h'          [ Not found ]
[13:30:54]   Checking for file '/usr/include/proc.h'         [ Not found ]
[13:30:54]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[13:30:54]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[13:30:54]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[13:30:54]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[13:30:54]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[13:30:54]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[13:30:54]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[13:30:54]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[13:30:54]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[13:30:54]   Checking for file '/dev/srd0'                   [ Not found ]
[13:30:54]   Checking for directory '/lib/libsh.so'          [ Not found ]
[13:30:54]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[13:30:54]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[13:30:55]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[13:30:55] SHV5 Rootkit                                      [ Not found ]
[13:30:55]
[13:30:55] Checking for Sin Rootkit...
[13:30:55]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[13:30:55]   Checking for file '/dev/ttyoa'                  [ Not found ]
[13:30:55]   Checking for file '/dev/ttyof'                  [ Not found ]
[13:30:55]   Checking for file '/dev/ttyop'                  [ Not found ]
[13:30:55]   Checking for file '/dev/ttyos'                  [ Not found ]
[13:30:55]   Checking for file '/usr/lib/.lib'               [ Not found ]
[13:30:55]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[13:30:55]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[13:30:55]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[13:30:55]   Checking for file '/usr/man/man1/...'           [ Not found ]
[13:30:55]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[13:30:55]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[13:30:55]   Checking for directory '/usr/lib/sn'            [ Not found ]
[13:30:55]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[13:30:55]   Checking for directory '/dev/.haos'             [ Not found ]
[13:30:55] Sin Rootkit                                       [ Not found ]
[13:30:55]
[13:30:55] Checking for Slapper Worm...
[13:30:55]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[13:30:55]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[13:30:55]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[13:30:55]   Checking for file '/tmp/httpd'                  [ Not found ]
[13:30:55]   Checking for file '/tmp/.unlock'                [ Not found ]
[13:30:55]   Checking for file '/tmp/update'                 [ Not found ]
[13:30:55]   Checking for file '/tmp/.cinik'                 [ Not found ]
[13:30:55]   Checking for file '/tmp/.b'                     [ Not found ]
[13:30:55] Slapper Worm                                      [ Not found ]
[13:30:55]
[13:30:55] Checking for Sneakin Rootkit...
[13:30:55]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[13:30:55] Sneakin Rootkit                                   [ Not found ]
[13:30:55]
[13:30:55] Checking for 'Spanish' Rootkit...
[13:30:55]   Checking for file '/dev/ptyq'                   [ Not found ]
[13:30:55]   Checking for file '/bin/ad'                     [ Not found ]
[13:30:55]   Checking for file '/bin/ava'                    [ Not found ]
[13:30:55]   Checking for file '/bin/server'                 [ Not found ]
[13:30:55]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[13:30:55]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[13:30:55]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[13:30:55]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[13:30:55]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[13:30:55]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[13:30:56]   Checking for directory '/usr/share/...'         [ Not found ]
[13:30:56] 'Spanish' Rootkit                                 [ Not found ]
[13:30:56]
[13:30:56] Checking for Suckit Rootkit...
[13:30:56]   Checking for file '/sbin/initsk12'              [ Not found ]
[13:30:56]   Checking for file '/sbin/initxrk'               [ Not found ]
[13:30:56]   Checking for file '/usr/bin/null'               [ Not found ]
[13:30:56]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[13:30:56]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[13:30:56]   Checking for directory '/etc/.MG'               [ Not found ]
[13:30:56]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[13:30:56]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[13:30:56] Suckit Rootkit                                    [ Not found ]
[13:30:56]
[13:30:56] Checking for Superkit Rootkit...
[13:30:56]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[13:30:56]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[13:30:56]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[13:30:56]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[13:30:56]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[13:30:56] Superkit Rootkit                                  [ Not found ]
[13:30:56]
[13:30:56] Checking for TBD (Telnet BackDoor)...
[13:30:56]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[13:30:56] TBD (Telnet BackDoor)                             [ Not found ]
[13:30:56]
[13:30:56] Checking for TeLeKiT Rootkit...
[13:30:56]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[13:30:56]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[13:30:56]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[13:30:56]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[13:30:56]   Checking for file '/dev/ptyr'                   [ Not found ]
[13:30:56]   Checking for file '/dev/ptyp'                   [ Not found ]
[13:30:56]   Checking for file '/dev/ptyq'                   [ Not found ]
[13:30:56]   Checking for file '/dev/hda06'                  [ Not found ]
[13:30:56]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[13:30:56]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[13:30:56]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[13:30:56]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[13:30:56] TeLeKiT Rootkit                                   [ Not found ]
[13:30:56]
[13:30:56] Checking for T0rn Rootkit...
[13:30:56]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[13:30:56]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[13:30:57]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[13:30:57]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[13:30:57]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[13:30:57]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[13:30:57]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[13:30:57]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[13:30:57]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[13:30:57]   Checking for directory '/dev/.lib'              [ Not found ]
[13:30:57]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[13:30:57]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[13:30:57]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[13:30:57]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[13:30:57]   Checking for directory '/usr/src/.puta'         [ Not found ]
[13:30:57]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[13:30:57]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[13:30:57]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[13:30:57]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[13:30:57] T0rn Rootkit                                      [ Not found ]
[13:30:57]
[13:30:57] Checking for trNkit Rootkit...
[13:30:57]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[13:30:57]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[13:30:57]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[13:30:57] trNkit Rootkit                                    [ Not found ]
[13:30:57]
[13:30:57] Checking for Trojanit Kit...
[13:30:57]   Checking for file '/bin/.ls'                    [ Not found ]
[13:30:57]   Checking for file '/bin/.ps'                    [ Not found ]
[13:30:57]   Checking for file '/bin/.netstat'               [ Not found ]
[13:30:57]   Checking for file '/usr/bin/.nop'               [ Not found ]
[13:30:57]   Checking for file '/usr/bin/.who'               [ Not found ]
[13:30:58] Trojanit Kit                                      [ Not found ]
[13:30:58]
[13:30:58] Checking for Tuxtendo Rootkit...
[13:30:58]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[13:30:58]   Checking for file '/usr/bin/xchk'               [ Not found ]
[13:30:58]   Checking for file '/usr/bin/xsf'                [ Not found ]
[13:30:58]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.addr'              [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.cron'              [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.file'              [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.log'               [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.proc'              [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.iface'             [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.pw'                [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.df'                [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[13:30:58]   Checking for file '/dev/tux/.tux'               [ Not found ]
[13:30:58]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[13:30:58]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[13:30:58]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[13:30:58]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[13:30:58]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[13:30:58]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[13:30:58]   Checking for directory '/dev/tux'               [ Not found ]
[13:30:58]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[13:30:58]   Checking for directory '/dev/tux/backup'        [ Not found ]
[13:30:58] Tuxtendo Rootkit                                  [ Not found ]
[13:30:58]
[13:30:58] Checking for URK Rootkit...
[13:30:58]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[13:30:58]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[13:30:58]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[13:30:58]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[13:30:59]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[13:30:59]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[13:30:59]   Checking for file '/tmp/conf.inv'               [ Not found ]
[13:30:59]   Checking for directory '/dev/prom'              [ Not found ]
[13:30:59]   Checking for directory '/dev/pts/01'            [ Not found ]
[13:30:59]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[13:30:59]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[13:30:59] URK Rootkit                                       [ Not found ]
[13:30:59]
[13:30:59] Checking for Vampire Rootkit...
[13:30:59]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[13:30:59]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[13:30:59]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[13:30:59]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[13:30:59] Vampire Rootkit                                   [ Not found ]
[13:30:59]
[13:30:59] Checking for VcKit Rootkit...
[13:30:59]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[13:30:59]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[13:30:59] VcKit Rootkit                                     [ Not found ]
[13:30:59]
[13:30:59] Checking for Volc Rootkit...
[13:30:59]   Checking for file '/usr/bin/volc'               [ Not found ]
[13:30:59]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[13:30:59]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[13:30:59]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[13:30:59]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[13:31:00]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[13:31:00]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[13:31:00]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[13:31:00]   Checking for directory '/var/spool/.recent'     [ Not found ]
[13:31:00]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[13:31:00]   Checking for directory '/usr/lib/volc'          [ Not found ]
[13:31:00]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[13:31:00] Volc Rootkit                                      [ Not found ]
[13:31:00]
[13:31:00] Checking for Xzibit Rootkit...
[13:31:00]   Checking for file '/dev/dsx'                    [ Not found ]
[13:31:00]   Checking for file '/dev/caca'                   [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[13:31:00]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[13:31:00]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[13:31:00]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[13:31:00]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[13:31:00]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[13:31:00]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[13:31:00]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[13:31:00] Xzibit Rootkit                                    [ Not found ]
[13:31:00]
[13:31:00] Checking for zaRwT.KiT Rootkit...
[13:31:00]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[13:31:00]   Checking for file '/dev/ttyf'                   [ Not found ]
[13:31:00]   Checking for file '/dev/ttyp'                   [ Not found ]
[13:31:00]   Checking for file '/dev/ttyn'                   [ Not found ]
[13:31:00]   Checking for file '/rk/tulz'                    [ Not found ]
[13:31:00]   Checking for directory '/rk'                    [ Not found ]
[13:31:00]   Checking for directory '/dev/rd/s'              [ Not found ]
[13:31:00] zaRwT.KiT Rootkit                                 [ Not found ]
[13:31:00]
[13:31:00] Checking for ZK Rootkit...
[13:31:00]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[13:31:00]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[13:31:00]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[13:31:00]   Checking for file '/etc/1ssue.net'              [ Not found ]
[13:31:01]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[13:31:01]   Checking for directory '/usr/share/.zk'         [ Not found ]
[13:31:01]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[13:31:01] ZK Rootkit                                        [ Not found ]
[13:51:33]
[13:51:33] Info: Starting test name 'additional_rkts'
[13:51:33] Performing additional rootkit checks
[13:51:33]
[13:51:33]   Performing Suckit Rookit additional checks
[13:51:33]     Checking hard link count on '/sbin/init'      [ OK ]
[13:51:33]     Checking for hidden file extensions           [ None found ]
[13:51:33]     Running skdet command                         [ Skipped ]
[13:51:33] Info: Unable to find the 'skdet' command
[13:51:33]   Suckit Rookit additional checks                 [ OK ]
[13:51:33]
[13:51:33] Info: Starting test name 'possible_rkt_files'
[13:51:33]   Performing check of possible rootkit files and directories
[13:51:33]     Checking for file '/dev/sdr0'                 [ Not found ]
[13:51:33]     Checking for file '/dev/pisu'                 [ Not found ]
[13:51:33]     Checking for file '/dev/xdta'                 [ Not found ]
[13:51:33]     Checking for file '/dev/saux'                 [ Not found ]
[13:51:33]     Checking for file '/dev/hdx'                  [ Not found ]
[13:51:33]     Checking for file '/dev/hdx1'                 [ Not found ]
[13:51:33]     Checking for file '/dev/hdx2'                 [ Not found ]
[13:51:33]     Checking for file '/dev/ptyy'                 [ Not found ]
[13:51:33]     Checking for file '/dev/ptyu'                 [ Not found ]
[13:51:33]     Checking for file '/dev/ptyv'                 [ Not found ]
[13:51:33]     Checking for file '/dev/hdbb'                 [ Not found ]
[13:51:33]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[13:51:33]     Checking for file '/tmp/.bash_history'        [ Not found ]
[13:51:33]     Checking for file '/usr/info/.clib'           [ Not found ]
[13:51:33]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[13:51:34]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[13:51:34]     Checking for file '/sbin/create'              [ Not found ]
[13:51:34]     Checking for file '/dev/ttypz'                [ Not found ]
[13:51:34]     Checking for file '/var/log/tcp.log'          [ Not found ]
[13:51:34]     Checking for file '/usr/include/audit.h'      [ Not found ]
[13:51:34]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[13:51:34]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[13:51:34]     Checking for file '/dev/xmx'                  [ Not found ]
[13:51:34]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[13:51:34]     Checking for file '/bin/vobiscum'             [ Not found ]
[13:51:34]     Checking for file '/bin/psr'                  [ Not found ]
[13:51:34]     Checking for file '/dev/kdx'                  [ Not found ]
[13:51:34]     Checking for file '/dev/dkx'                  [ Not found ]
[13:51:34]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[13:51:34]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[13:51:34]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[13:51:34]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[13:51:34]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[13:51:34]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[13:51:34]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[13:51:34]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[13:51:34]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[13:51:34]     Checking for file '/tmp/.ush'                 [ Not found ]
[13:51:34]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[13:51:34]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[13:51:34]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[13:51:34]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[13:51:34]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[13:51:34]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[13:51:34]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[13:51:35]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[13:51:35]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[13:51:35]     Checking for file '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:35]     Checking for file '/etc/init.d/xfs3'          [ Not found ]
[13:51:35]     Checking for file '/usr/sbin/t.txt'           [ Not found ]
[13:51:35]     Checking for file '/usr/sbin/change'          [ Not found ]
[13:51:35]     Checking for file '/usr/sbin/s'               [ Not found ]
[13:51:35]     Checking for file '/bin/f'                    [ Not found ]
[13:51:35]     Checking for file '/bin/i'                    [ Not found ]
[13:51:35]     Checking for file '/lib/libncom.so.4.0.1'     [ Not found ]
[13:51:35]     Checking for file '/sbin/zinit'               [ Not found ]
[13:51:35]     Checking for file '/tmp/pass_ssh.log'         [ Not found ]
[13:51:35]     Checking for file '/usr/include/gpm2.h'       [ Not found ]
[13:51:35]     Checking for file '/etc/ssh/.sshd_auth'       [ Not found ]
[13:51:35]     Checking for file '/usr/lib/.sshd.h'          [ Not found ]
[13:51:35]     Checking for file '/var/run/.defunct'         [ Not found ]
[13:51:35]     Checking for file '/etc/httpd/run/.defunct'   [ Not found ]
[13:51:35]     Checking for file '/usr/share/pci.r'          [ Not found ]
[13:51:35]     Checking for file '/etc/cron.daily/dnsquery'  [ Not found ]
[13:51:35]     Checking for file '/usr/lib/libutil1.2.1.2.so' [ Not found ]
[13:51:35]     Checking for file '/bin/ceva'                 [ Not found ]
[13:51:35]     Checking for file '/sbin/syslogd '            [ Not found ]
[13:51:35]     Checking for file '/usr/include/shup.h'       [ Not found ]
[13:51:35]     Checking for file '/etc/rpm/sshdOLD'          [ Not found ]
[13:51:35]     Checking for file '/etc/rpm/sshOLD'           [ Not found ]
[13:51:35]     Checking for file '/usr/share/passwd.h'       [ Not found ]
[13:51:35]     Checking for file '/lib/.xsyslog'             [ Not found ]
[13:51:35]     Checking for file '/etc/.xsyslog'             [ Not found ]
[13:51:35]     Checking for file '/lib/.ssyslog'             [ Not found ]
[13:51:35]     Checking for file '/tmp/.sendmail'            [ Not found ]
[13:51:35]     Checking for file '/usr/share/sshd.sync'      [ Not found ]
[13:51:35]     Checking for file '/bin/zcut'                 [ Not found ]
[13:51:35]     Checking for file '/usr/bin/zmuie'            [ Not found ]
[13:51:36]     Checking for directory '/dev/ptyas'           [ Not found ]
[13:51:36]     Checking for directory '/usr/bin/take'        [ Not found ]
[13:51:36]     Checking for directory '/usr/src/.lib'        [ Not found ]
[13:51:36]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[13:51:36]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[13:51:36]     Checking for directory '/usr/sbin/...'        [ Not found ]
[13:51:36]     Checking for directory '/usr/share/.gun'      [ Not found ]
[13:51:36]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[13:51:36]     Checking for directory '/usr/man/man1/..  /.dir' [ Not found ]
[13:51:36]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[13:51:36]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[13:51:36]     Checking for directory '/tmp/.sys'            [ Not found ]
[13:51:36]     Checking for directory '/tmp/''               [ Not found ]
[13:51:36]     Checking for directory '/tmp/.,'              [ Not found ]
[13:51:36]     Checking for directory '/tmp/,.,'             [ Not found ]
[13:51:36]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[13:51:36]     Checking for directory '/var/tmp/.log'        [ Not found ]
[13:51:36]     Checking for directory '/tmp/zmeu/... '       [ Not found ]
[13:51:36]     Checking for directory '/var/log/ssh'         [ Not found ]
[13:51:36]     Checking for directory '/dev/ida'             [ Not found ]
[13:51:36]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[13:51:36]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[13:51:36]     Checking for directory '/usr/src/.poop'       [ Not found ]
[13:51:36]     Checking for directory '/dev/wd4'             [ Not found ]
[13:51:36]     Checking for directory '/var/run/.tmp'        [ Not found ]
[13:51:36]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[13:51:36]     Checking for directory '/dev/portd'           [ Not found ]
[13:51:36]     Checking for directory '/dev/...'             [ Not found ]
[13:51:36]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[13:51:37]     Checking for directory '/lib/.so'             [ Not found ]
[13:51:37]     Checking for directory '/lib/.sso'            [ Not found ]
[13:51:37]     Checking for directory '/usr/include/sslv3'   [ Not found ]
[13:51:37]     Checking for directory '/dev/shm/sshd'        [ Not found ]
[13:51:37]     Checking for directory '/usr/share/locale/mk/.dev/sk' [ Not found ]
[13:51:37]     Checking for directory '/usr/share/locale/mk/.dev' [ Not found ]
[13:51:37]     Checking for directory '/usr/include/netda.h' [ Not found ]
[13:51:37]     Checking for directory '/usr/include/.ssh'    [ Not found ]
[13:51:37]     Checking for directory '/usr/share/locale/jp/. ' [ Not found ]
[13:51:37]     Checking for directory '/usr/share/.sqe'      [ Not found ]
[13:51:37]   Checking for possible rootkit files and directories [ None found ]
[13:51:37]
[13:51:37] Info: Starting test name 'possible_rkt_strings'
[13:51:37]   Performing check for possible rootkit strings
[13:51:37] Info: Using system startup paths: /etc/rc.local /etc/init.d
[13:51:37]     Checking for string 'phalanx'                 [ Not found ]
[13:51:37]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:51:37]     Checking for string '****'                    [ Not found ]
[13:51:37]     Checking for string 'backdoor'                [ Not found ]
[13:51:37]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[13:51:37]     Checking for string '/usr/sbin/login'         [ Not found ]
[13:51:37]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:51:38]     Checking for string 'vt200'                   [ Not found ]
[13:51:38]     Checking for string '/usr/bin/xstat'          [ Not found ]
[13:51:38]     Checking for string '/bin/envpc'              [ Not found ]
[13:51:38]     Checking for string 'L4m3r0x'                 [ Not found ]
[13:51:38]     Checking for string '/lib/libext'             [ Not found ]
[13:51:38]     Checking for string '/usr/sbin/login'         [ Not found ]
[13:51:38]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:51:38]     Checking for string 'sendmail'                [ Not found ]
[13:51:38]     Checking for string 'cocacola'                [ Not found ]
[13:51:38]     Checking for string 'joao'                    [ Not found ]
[13:51:38]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:51:38]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:51:38]     Checking for string '/dev/sgk'                [ Not found ]
[13:51:38]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:51:38]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:51:39]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:51:39]     Checking for string '/lib/.sso'               [ Not found ]
[13:51:39]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:51:39]     Checking for string '/dev/caca'               [ Not found ]
[13:51:39]     Checking for string '/dev/ttyoa'              [ Not found ]
[13:51:39]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[13:51:39]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[13:51:39]     Checking for string 'syg'                     [ Not found ]
[13:51:39]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[13:51:39]     Checking for string '/dev/pts/01'             [ Not found ]
[13:51:39]     Checking for string 'tw33dl3'                 [ Not found ]
[13:51:39]     Checking for string 'psniff'                  [ Not found ]
[13:51:39]     Checking for string 'uconf.inv'               [ Not found ]
[13:51:39]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[13:51:39]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[13:51:40]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:40]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:51:40]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:51:40]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:40]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:41]     Checking for string '/bin/bash'               [ Not found ]
[13:51:42]     Checking for string '/dev/xdta'               [ Not found ]
[13:51:42]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[13:51:42]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[13:51:46]     Checking for string 'in.inetd'                [ Not found ]
[13:51:46]     Checking for string '#<HIDE_.*>'              [ Not found ]
[13:51:46]     Checking for string 'bin/xchk'                [ Not found ]
[13:51:47]     Checking for string 'bin/xsf'                 [ Not found ]
[13:51:47]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[13:51:47]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[13:51:47]     Checking for string 'ttyload'                 [ Not found ]
[13:51:47]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[13:51:47]     Checking for string 'usr/bin/xfss'            [ Not found ]
[13:51:48]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[13:51:48]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[13:51:48]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[13:51:48]     Checking for string '/ssh2d'                  [ Not found ]
[13:51:48]     Checking for string '/dev/kmod'               [ Not found ]
[13:51:48]     Checking for string '/crth.o'                 [ Not found ]
[13:51:49]     Checking for string '/crtz.o'                 [ Not found ]
[13:51:49]     Checking for string '/dev/dos'                [ Not found ]
[13:51:50]     Checking for string '/lpq'                    [ Not found ]
[13:51:50]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[13:51:50]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[13:51:50]     Checking for string '/volc'                   [ Not found ]
[13:51:50]     Checking for string 'sourcemask'              [ Not found ]
[13:51:50]     Checking for string '/bin/vobiscum'           [ Not found ]
[13:51:51]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[13:51:51]     Checking for string '/usr/bin/hdparm?-t1?-X53?-p' [ Not found ]
[13:51:51]     Checking for string '/lib/.xsyslog'           [ Not found ]
[13:51:51]     Checking for string '/etc/.xsyslog'           [ Not found ]
[13:51:52]     Checking for string '/lib/.ssyslog'           [ Not found ]
[13:51:52]     Checking for string '/tmp/.sendmail'          [ Not found ]
[13:51:52]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[13:51:52]     Checking for string 't0rnkit'                 [ Not found ]
[13:51:52]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[13:51:52]     Checking for string 'backdoor.h'              [ Not found ]
[13:51:52]     Checking for string 'backdoor_active'         [ Not found ]
[13:51:52]     Checking for string 'magic_pass_active'       [ Not found ]
[13:51:52]     Checking for string '/usr/include/gpm2.h'     [ Not found ]
[13:51:53]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:53]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:53]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:53]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[13:51:53]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[13:51:53]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[13:51:53]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[13:51:54]     Checking for string '/dev/ida/.inet'          [ Not found ]
[13:51:54]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:54]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:54]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:54]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:55]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:55]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[13:51:55]     Checking for string 'backconnect'             [ Not found ]
[13:51:55]     Checking for string 'magic?packet?received'   [ Not found ]
[13:51:55]   Checking for possible rootkit strings           [ None found ]
[13:51:55]
[13:51:55] Info: Starting test name 'malware'
[13:51:55] Performing malware checks
[13:51:55]
[13:51:55] Info: Test 'deleted_files' disabled at users request.
[13:51:55]
[13:51:55] Info: Starting test name 'running_procs'
[13:51:56]   Checking running processes for suspicious files [ None found ]
[13:51:56]
[13:51:56] Info: Test 'hidden_procs' disabled at users request.
[13:51:56]
[13:51:56] Info: Test 'suspscan' disabled at users request.
[13:51:56]
[13:51:56] Info: Starting test name 'other_malware'
[13:51:56]   Performing check for login backdoors
[13:51:56]     Checking for '/bin/.login'                    [ Not found ]
[13:51:56]     Checking for '/sbin/.login'                   [ Not found ]
[13:51:56]   Checking for login backdoors                    [ None found ]
[13:51:56]
[13:51:56]   Performing check for suspicious directories
[13:51:56]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[13:51:56]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[13:51:56]   Checking for suspicious directories             [ None found ]
[13:51:56]
[13:51:56]   Checking for software intrusions                [ Skipped ]
[13:51:56] Info: Check skipped - tripwire not installed
[13:51:56]
[13:51:56]   Performing check for sniffer log files
[13:51:56]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[13:51:56]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[13:51:56]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[13:51:56]   Checking for sniffer log files                  [ None found ]
[13:51:56]
[13:51:56] Info: Starting test name 'trojans'
[13:51:56] Performing trojan specific checks
[13:51:57]   Checking for enabled inetd services             [ Skipped ]
[13:51:57] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[13:51:57]
[13:51:57]   Performing check for enabled xinetd services
[13:51:57]   Checking for enabled xinetd services            [ Skipped ]
[13:51:57] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[13:51:57] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[13:51:57]
[13:51:57] Info: Starting test name 'os_specific'
[13:51:57] Performing Linux specific checks
[13:51:57]   Checking loaded kernel modules                  [ OK ]
[13:51:57] Info: Using modules pathname of '/lib/modules/3.2.0-29-generic'
[13:51:58]   Checking kernel module names                    [ OK ]
[13:52:18]
[13:52:18] Info: Starting test name 'network'
[13:52:18] Checking the network...
[13:52:18]
[13:52:18] Performing checks on the network ports
[13:52:18] Info: Starting test name 'ports'
[13:52:18]   Performing check for backdoor ports
[13:52:18]     Checking for TCP port 1524                    [ Not found ]
[13:52:18]     Checking for TCP port 1984                    [ Not found ]
[13:52:18]     Checking for UDP port 2001                    [ Not found ]
[13:52:18]     Checking for TCP port 2006                    [ Not found ]
[13:52:19]     Checking for TCP port 2128                    [ Not found ]
[13:52:19]     Checking for TCP port 6666                    [ Not found ]
[13:52:19]     Checking for TCP port 6667                    [ Not found ]
[13:52:19]     Checking for TCP port 6668                    [ Not found ]
[13:52:19]     Checking for TCP port 6669                    [ Not found ]
[13:52:19]     Checking for TCP port 7000                    [ Not found ]
[13:52:19]     Checking for TCP port 13000                   [ Not found ]
[13:52:19]     Checking for TCP port 14856                   [ Not found ]
[13:52:19]     Checking for TCP port 25000                   [ Not found ]
[13:52:19]     Checking for TCP port 29812                   [ Not found ]
[13:52:19]     Checking for TCP port 31337                   [ Not found ]
[13:52:19]     Checking for TCP port 32982                   [ Not found ]
[13:52:20]     Checking for TCP port 33369                   [ Not found ]
[13:52:20]     Checking for TCP port 47107                   [ Not found ]
[13:52:20]     Checking for TCP port 47018                   [ Not found ]
[13:52:20]     Checking for TCP port 60922                   [ Not found ]
[13:52:20]     Checking for TCP port 62883                   [ Not found ]
[13:52:20]     Checking for TCP port 65535                   [ Not found ]
[13:52:20]   Checking for backdoor ports                     [ None found ]
[13:52:20]
[13:52:20] Info: Starting test name 'hidden_ports'
[13:52:20] Info: Found the 'unhide-tcp' command: /usr/sbin/unhide-tcp
[13:52:20] Info: Found the 'awk' command: /usr/bin/awk
[13:52:21]   Checking for hidden ports                       [ None found ]
[13:52:21]
[13:52:21] Performing checks on the network interfaces
[13:52:21] Info: Starting test name 'promisc'
[13:52:21]   Checking for promiscuous interfaces             [ None found ]
[13:52:21]
[13:52:21] Info: Test 'packet_cap_apps' disabled at users request.
[13:52:21]
[13:52:21] Info: Starting test name 'local_host'
[13:52:21] Checking the local host...
[13:52:21]
[13:52:21] Info: Starting test name 'startup_files'
[13:52:21] Performing system boot checks
[13:52:21]   Checking for local host name                    [ Found ]
[13:52:22]
[13:52:22] Info: Starting test name 'startup_malware'
[13:52:22]   Checking for system startup files               [ Found ]
[13:52:22]   Checking system startup files for malware       [ None found ]
[13:52:22]
[13:52:22] Info: Starting test name 'group_accounts'
[13:52:22] Performing group and account checks
[13:52:22]   Checking for passwd file                        [ Found ]
[13:52:23] Info: Found password file: /etc/passwd
[13:52:23]   Checking for root equivalent (UID 0) accounts   [ None found ]
[13:52:23] Info: Found shadow file: /etc/shadow
[13:52:23]   Checking for passwordless accounts              [ None found ]
[13:52:23]
[13:52:23] Info: Starting test name 'passwd_changes'
[13:52:23]   Checking for passwd file changes                [ None found ]
[13:52:23]
[13:52:23] Info: Starting test name 'group_changes'
[13:52:23]   Checking for group file changes                 [ None found ]
[13:52:23]   Checking root account shell history files       [ None found ]
[13:52:23]
[13:52:23] Info: Starting test name 'system_configs'
[13:52:23] Performing system configuration file checks
[13:52:23]   Checking for SSH configuration file             [ Not found ]
[13:52:23]   Checking for running syslog daemon              [ Found ]
[13:52:23] Info: Found rsyslog configuration file: /etc/rsyslog.conf
[13:52:23]   Checking for syslog configuration file          [ Found ]
[13:52:23]   Checking if syslog remote logging is allowed    [ Not allowed ]
[13:52:23]
[13:52:23] Info: Starting test name 'filesystem'
[13:52:23] Performing filesystem checks
[13:52:23] Info: SCAN_MODE_DEV set to 'THOROUGH'
[13:52:23]   Checking /dev for suspicious file types         [ Warning ]
[13:52:23] Warning: Suspicious file types found in /dev:
[13:52:23]          /dev/.udev/rules.d/root.rules: ASCII text
[13:52:24]   Checking for hidden files and directories       [ Warning ]
[13:52:24] Warning: Hidden directory found: '/etc/.java'
[13:52:24] Warning: Hidden directory found: '/dev/.udev'
[13:52:24] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[13:52:27]
[13:52:27] Info: Test 'apps' disabled at users request.
[13:52:27]
[13:52:27] System checks summary
[13:52:27] =====================
[13:52:27]
[13:52:27] File properties checks...
[13:52:27] Required commands check failed
[13:52:27] Files checked: 139
[13:52:27] Suspect files: 131
[13:52:27]
[13:52:27] Rootkit checks...
[13:52:27] Rootkits checked : 292
[13:52:27] Possible rootkits: 0
[13:52:27]
[13:52:27] Applications checks...
[13:52:27] All checks skipped
[13:52:27]
[13:52:27] The system checks took: 26 minutes and 39 seconds
[13:52:27]
[13:52:27] Info: End date is Sat Sep  1 13:52:27 CEST 2012
```Thanks in advance! :)

---

### Post by cryptotheslow on 2012-09-01
No easy way as far as I'm aware.

You could download each package in turn from the Ubuntu site, extract the relevant file and then calculate its MD5 hash to compare e.g. [http://packages.ubuntu.com/source/precise/adduser](http://packages.ubuntu.com/source/precise/adduser)

That said your rkhunter is using sha1sum rather than MD5 as per your log here:
[i][13:25:47] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[13:25:47] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[13:25:47] Info: Stored hash values did not use a package manager
[13:25:48] Info: The hash function field index is set to 1
[13:25:48] Info: No package manager specified: using hash function '/usr/bin/sha1sum'[/i]

So you would need to calculate the MD5 hash for both the file you already have and the new one downloaded.

If you are only using the Ubuntu repositories for updates then it is very unlikely you'd end up with a "bad" script or binary as the repos are signed.

It seems from your log that you have upgraded from 11.10 to 12.04 since you last baselined rkhunter, so there will be a massive amount of differences.

If you have a real reason to suspect you have "bad" files then I'd suggest it is going to be quicker to do a clean install of 12.04.1 then baseline it immediately rather than manually check every discrepancy rkhunter has reported there.

---

### Post by FreedomOverdose on 2012-09-01
Thanks for your reply :). I have absolutely no reason to believe that my system is compromised. The only repos I've been using are the official ones and some open source ones which I assume to be safe (official banshee team, transmission, pidgin), and Getdeb. 

I wish there was an easier way to check the hashes directly from the Ubuntu site, and if there is a mismatch, automatically generate a diff between both files (if they're both shell scripts)

---

### Post by cryptotheslow on 2012-09-01
That would be nice for sure, it would probably be possible to script such a thing.

But that's the thing with rkhunter it needs keeping on top of to be of any realistic use. That takes time.

1. Don't allow automatic updates.
2. Run an rkhunter check before checking for and applying updates - nothing should flag.
3. Run the updates noting what has been updated.
4. Run another rkhunter check and verify the only things being flagged are those noted in step 3.
5. Re-baseline rkhunter.
6. Put rkhunter on a daily (or shorter if necessary) cron and actually read its logs or emails, nothing should flag up between the updates you do.

All this takes time and as with pretty much everything security related it's a trade off between convenience and paranoia. How you balance those two is always the dilemma :D

Certainly running rkhunter once every 6 months or so without keeping on top of it in the meantime is close to useless, not because it is deficient in what it does, it's just not how it was designed to be used.

---

