---
title: "Analyze this rootkit analysis"
date: 2011-08-29
forum: Security
---

### Post by TheHistorian on 2011-08-29
```
[17:21:04] Running Rootkit Hunter version 1.3.6 on jack-System-Product-Name
[17:21:04]
[17:21:04] Info: Start date is Mon Aug 29 17:21:04 EST 2011
[17:21:04]
[17:21:04] Checking configuration file and command-line options...
[17:21:04] Info: Detected operating system is 'Linux'
[17:21:04] Info: Found O/S name: Ubuntu 11.04
[17:21:04] Info: Command line is /usr/bin/rkhunter --check
[17:21:04] Info: Environment shell is /bin/bash; rkhunter is using dash
[17:21:04] Info: Using configuration file '/etc/rkhunter.conf'
[17:21:04] Info: Installation directory is '/usr'
[17:21:04] Info: Using language 'en'
[17:21:04] Info: Using '/var/lib/rkhunter/db' as the database directory
[17:21:04] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[17:21:04] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[17:21:04] Info: Using '/' as the root directory by default
[17:21:04] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[17:21:04] Info: No mail-on-warning address configured
[17:21:04] Info: X will be automatically detected
[17:21:04] Info: Using second color set
[17:21:04] Info: Found the 'basename' command: /usr/bin/basename
[17:21:04] Info: Found the 'diff' command: /usr/bin/diff
[17:21:04] Info: Found the 'dirname' command: /usr/bin/dirname
[17:21:04] Info: Found the 'file' command: /usr/bin/file
[17:21:04] Info: Found the 'find' command: /usr/bin/find
[17:21:04] Info: Found the 'ifconfig' command: /sbin/ifconfig
[17:21:04] Info: Found the 'ip' command: /sbin/ip
[17:21:05] Info: Found the 'ldd' command: /usr/bin/ldd
[17:21:05] Info: Found the 'lsattr' command: /usr/bin/lsattr
[17:21:05] Info: Found the 'lsmod' command: /sbin/lsmod
[17:21:05] Info: Found the 'lsof' command: /usr/bin/lsof
[17:21:05] Info: Found the 'mktemp' command: /bin/mktemp
[17:21:05] Info: Found the 'netstat' command: /bin/netstat
[17:21:05] Info: Found the 'perl' command: /usr/bin/perl
[17:21:05] Info: Found the 'pgrep' command: /usr/bin/pgrep
[17:21:05] Info: Found the 'ps' command: /bin/ps
[17:21:05] Info: Found the 'pwd' command: /bin/pwd
[17:21:05] Info: Found the 'readlink' command: /bin/readlink
[17:21:05] Info: Found the 'sort' command: /usr/bin/sort
[17:21:05] Info: Found the 'stat' command: /usr/bin/stat
[17:21:05] Info: Found the 'strings' command: /usr/bin/strings
[17:21:05] Info: Found the 'uniq' command: /usr/bin/uniq
[17:21:05] Info: System is not using prelinking
[17:21:05] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[17:21:05] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[17:21:05] Info: Stored hash values did not use a package manager
[17:21:05] Info: The hash function field index is set to 1
[17:21:05] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[17:21:05] Info: Previous file attributes were stored
[17:21:05] Info: Enabled tests are: all
[17:21:05] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[17:21:05] Info: Found ksym file '/proc/kallsyms'
[17:21:05] Info: Using 'date' to process epoch second times.
[17:21:05]
[17:21:05] Checking if the O/S has changed since last time...
[17:21:05] Info: Nothing seems to have changed
[17:21:05] Info: Locking is not being used
[17:21:05]
[17:21:05] Starting system checks...
[17:21:05]
[17:21:05] Checking system commands...
[17:21:05] Info: Starting test name 'system_commands'
[17:21:05]
[17:21:05] Performing 'strings' command checks
[17:21:05] Info: Starting test name 'strings'
[17:21:05] Scanning for string /usr/sbin/ntpsx               [ OK ]
[17:21:06] Scanning for string /usr/sbin/.../bkit-ava        [ OK ]
[17:21:06] Scanning for string /usr/sbin/.../bkit-d          [ OK ]
[17:21:06] Scanning for string /usr/sbin/.../bkit-shd        [ OK ]
[17:21:06] Scanning for string /usr/sbin/.../bkit-f          [ OK ]
[17:21:06] Scanning for string /usr/include/.../proc.h       [ OK ]
[17:21:06] Scanning for string /usr/include/.../.bash_history [ OK ]
[17:21:06] Scanning for string /usr/include/.../bkit-get     [ OK ]
[17:21:06] Scanning for string /usr/include/.../bkit-dl      [ OK ]
[17:21:06] Scanning for string /usr/include/.../bkit-screen  [ OK ]
[17:21:06] Scanning for string /usr/include/.../bkit-sleep   [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-adore.o     [ OK ]
[17:21:06] Scanning for string /usr/lib/.../ls               [ OK ]
[17:21:06] Scanning for string /usr/lib/.../netstat          [ OK ]
[17:21:06] Scanning for string /usr/lib/.../lsof             [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[17:21:06] Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[17:21:06] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[17:21:06] Scanning for string /usr/lib/.../psr              [ OK ]
[17:21:06] Scanning for string /usr/lib/.../find             [ OK ]
[17:21:06] Scanning for string /usr/lib/.../pstree           [ OK ]
[17:21:07] Scanning for string /usr/lib/.../slocate          [ OK ]
[17:21:07] Scanning for string /usr/lib/.../du               [ OK ]
[17:21:07] Scanning for string /usr/lib/.../top              [ OK ]
[17:21:07] Scanning for string /usr/sbin/...                 [ OK ]
[17:21:07] Scanning for string /usr/include/...              [ OK ]
[17:21:07] Scanning for string /usr/include/.../.tmp         [ OK ]
[17:21:07] Scanning for string /usr/lib/...                  [ OK ]
[17:21:07] Scanning for string /usr/lib/.../.ssh             [ OK ]
[17:21:07] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[17:21:07] Scanning for string /usr/lib/.bkit-               [ OK ]
[17:21:07] Scanning for string /tmp/.bkp                     [ OK ]
[17:21:07] Scanning for string /tmp/.cinik                   [ OK ]
[17:21:07] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[17:21:07] Scanning for string /lib/.sso                     [ OK ]
[17:21:07] Scanning for string /lib/.so                      [ OK ]
[17:21:07] Scanning for string /var/run/...dica/clean        [ OK ]
[17:21:07] Scanning for string /var/run/...dica/dxr          [ OK ]
[17:21:07] Scanning for string /var/run/...dica/read         [ OK ]
[17:21:07] Scanning for string /var/run/...dica/write        [ OK ]
[17:21:07] Scanning for string /var/run/...dica/lf           [ OK ]
[17:21:07] Scanning for string /var/run/...dica/xl           [ OK ]
[17:21:07] Scanning for string /var/run/...dica/xdr          [ OK ]
[17:21:07] Scanning for string /var/run/...dica/psg          [ OK ]
[17:21:08] Scanning for string /var/run/...dica/secure       [ OK ]
[17:21:08] Scanning for string /var/run/...dica/rdx          [ OK ]
[17:21:08] Scanning for string /var/run/...dica/va           [ OK ]
[17:21:08] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[17:21:08] Scanning for string /var/run/...dica/last.log     [ OK ]
[17:21:08] Scanning for string /usr/bin/.etc                 [ OK ]
[17:21:08] Scanning for string /etc/sshd_config              [ OK ]
[17:21:08] Scanning for string /etc/ssh_host_key             [ OK ]
[17:21:08] Scanning for string /etc/ssh_random_seed          [ OK ]
[17:21:08] Scanning for string /dev/ptyp                     [ OK ]
[17:21:08] Scanning for string /dev/ptyq                     [ OK ]
[17:21:08] Scanning for string /dev/ptyr                     [ OK ]
[17:21:08] Scanning for string /dev/ptys                     [ OK ]
[17:21:08] Scanning for string /dev/ptyt                     [ OK ]
[17:21:08] Scanning for string /dev/fd/.88/freshb-bsd        [ OK ]
[17:21:08] Scanning for string /dev/fd/.88/fresht            [ OK ]
[17:21:08] Scanning for string /dev/fd/.88/zxsniff           [ OK ]
[17:21:08] Scanning for string /dev/fd/.88/zxsniff.log       [ OK ]
[17:21:08] Scanning for string /dev/fd/.99/.ttyf00           [ OK ]
[17:21:08] Scanning for string /dev/fd/.99/.ttyp00           [ OK ]
[17:21:08] Scanning for string /dev/fd/.99/.ttyq00           [ OK ]
[17:21:08] Scanning for string /dev/fd/.99/.ttys00           [ OK ]
[17:21:08] Scanning for string /dev/fd/.99/.pwsx00           [ OK ]
[17:21:09] Scanning for string /etc/.acid                    [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/setrgrp.2        [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/TOHIDE           [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/adore/ava/ava    [ OK ]
[17:21:09] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[17:21:09] Scanning for string /bin/sysback                  [ OK ]
[17:21:09] Scanning for string /usr/local/bin/sysback        [ OK ]
[17:21:09] Scanning for string /usr/lib/.tbd                 [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[17:21:09] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[17:21:10] Scanning for string /usr/info/.torn/sh*           [ OK ]
[17:21:10] Scanning for string /usr/src/.puta/.1addr         [ OK ]
[17:21:10] Scanning for string /usr/src/.puta/.1file         [ OK ]
[17:21:10] Scanning for string /usr/src/.puta/.1proc         [ OK ]
[17:21:10] Scanning for string /usr/src/.puta/.1logz         [ OK ]
[17:21:10] Scanning for string /usr/info/.t0rn               [ OK ]
[17:21:10] Scanning for string /dev/.lib                     [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib                 [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib             [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[17:21:10] Scanning for string /dev/.lib/lib/scan            [ OK ]
[17:21:10] Scanning for string /usr/src/.puta                [ OK ]
[17:21:10] Scanning for string /usr/man/man1/man1            [ OK ]
[17:21:11] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[17:21:11] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[17:21:11] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[17:21:11]
[17:21:11] Performing 'shared libraries' checks
[17:21:11] Info: Starting test name 'shared_libs'
[17:21:11] Checking for preloading variables                 [ None found ]
[17:21:11] Checking for preloaded libraries                  [ None found ]
[17:21:11] Info: Starting test name 'shared_libs_path'
[17:21:11] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[17:21:11]
[17:21:11] Performing file properties checks
[17:21:11] Info: Starting test name 'properties'
[17:21:11] Checking for prerequisites                        [ OK ]
[17:21:11] /bin/bash                                         [ OK ]
[17:21:11] /bin/cat                                          [ OK ]
[17:21:12] /bin/chmod                                        [ OK ]
[17:21:12] /bin/chown                                        [ OK ]
[17:21:12] /bin/cp                                           [ OK ]
[17:21:12] /bin/date                                         [ OK ]
[17:21:12] /bin/df                                           [ OK ]
[17:21:12] /bin/dmesg                                        [ OK ]
[17:21:12] /bin/echo                                         [ OK ]
[17:21:12] /bin/ed                                           [ OK ]
[17:21:12] /bin/egrep                                        [ OK ]
[17:21:12] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[17:21:13] /bin/fgrep                                        [ OK ]
[17:21:13] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[17:21:13] /bin/fuser                                        [ OK ]
[17:21:13] /bin/grep                                         [ OK ]
[17:21:13] /bin/ip                                           [ OK ]
[17:21:13] /bin/kill                                         [ OK ]
[17:21:14] /bin/less                                         [ OK ]
[17:21:14] /bin/login                                        [ OK ]
[17:21:14] /bin/ls                                           [ OK ]
[17:21:14] /bin/lsmod                                        [ OK ]
[17:21:14] /bin/mktemp                                       [ OK ]
[17:21:14] /bin/more                                         [ OK ]
[17:21:14] /bin/mount                                        [ OK ]
[17:21:14] /bin/mv                                           [ OK ]
[17:21:15] /bin/netstat                                      [ OK ]
[17:21:15] /bin/ps                                           [ OK ]
[17:21:15] /bin/pwd                                          [ OK ]
[17:21:15] /bin/readlink                                     [ OK ]
[17:21:15] /bin/sed                                          [ OK ]
[17:21:15] /bin/sh                                           [ OK ]
[17:21:16] /bin/su                                           [ OK ]
[17:21:16] /bin/touch                                        [ OK ]
[17:21:16] /bin/uname                                        [ OK ]
[17:21:16] /bin/which                                        [ OK ]
[17:21:16] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[17:21:17] /bin/dash                                         [ OK ]
[17:21:17] /usr/bin/awk                                      [ OK ]
[17:21:17] /usr/bin/basename                                 [ OK ]
[17:21:17] /usr/bin/chattr                                   [ OK ]
[17:21:17] /usr/bin/cut                                      [ OK ]
[17:21:17] /usr/bin/diff                                     [ OK ]
[17:21:17] /usr/bin/dirname                                  [ OK ]
[17:21:18] /usr/bin/dpkg                                     [ OK ]
[17:21:18] /usr/bin/dpkg-query                               [ OK ]
[17:21:18] /usr/bin/du                                       [ OK ]
[17:21:18] /usr/bin/env                                      [ OK ]
[17:21:18] /usr/bin/file                                     [ OK ]
[17:21:18] /usr/bin/find                                     [ OK ]
[17:21:18] /usr/bin/GET                                      [ OK ]
[17:21:18] /usr/bin/groups                                   [ OK ]
[17:21:18] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[17:21:19] /usr/bin/head                                     [ OK ]
[17:21:19] /usr/bin/id                                       [ OK ]
[17:21:19] /usr/bin/killall                                  [ OK ]
[17:21:19] /usr/bin/last                                     [ OK ]
[17:21:19] /usr/bin/lastlog                                  [ OK ]
[17:21:19] /usr/bin/ldd                                      [ OK ]
[17:21:19] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[17:21:19] /usr/bin/less                                     [ OK ]
[17:21:19] /usr/bin/locate                                   [ OK ]
[17:21:20] /usr/bin/logger                                   [ OK ]
[17:21:20] /usr/bin/lsattr                                   [ OK ]
[17:21:20] /usr/bin/lsof                                     [ OK ]
[17:21:20] /usr/bin/mail                                     [ Warning ]
[17:21:20] Warning: The file '/usr/bin/mail' exists on the system, but it is not present in the rkhunter.dat file.
[17:21:20] /usr/bin/md5sum                                   [ OK ]
[17:21:20] /usr/bin/mlocate                                  [ OK ]
[17:21:20] /usr/bin/newgrp                                   [ OK ]
[17:21:20] /usr/bin/passwd                                   [ OK ]
[17:21:21] /usr/bin/perl                                     [ OK ]
[17:21:21] /usr/bin/pgrep                                    [ OK ]
[17:21:21] /usr/bin/pstree                                   [ OK ]
[17:21:21] /usr/bin/rkhunter                                 [ OK ]
[17:21:21] /usr/bin/runcon                                   [ OK ]
[17:21:21] /usr/bin/sha1sum                                  [ OK ]
[17:21:21] /usr/bin/sha224sum                                [ OK ]
[17:21:22] /usr/bin/sha256sum                                [ OK ]
[17:21:22] /usr/bin/sha384sum                                [ OK ]
[17:21:22] /usr/bin/sha512sum                                [ OK ]
[17:21:22] /usr/bin/size                                     [ OK ]
[17:21:22] /usr/bin/sort                                     [ OK ]
[17:21:22] /usr/bin/stat                                     [ OK ]
[17:21:22] /usr/bin/strace                                   [ OK ]
[17:21:22] /usr/bin/strings                                  [ OK ]
[17:21:22] /usr/bin/sudo                                     [ OK ]
[17:21:23] /usr/bin/tail                                     [ OK ]
[17:21:23] /usr/bin/test                                     [ OK ]
[17:21:23] /usr/bin/top                                      [ OK ]
[17:21:23] /usr/bin/touch                                    [ OK ]
[17:21:23] /usr/bin/tr                                       [ OK ]
[17:21:23] /usr/bin/uniq                                     [ OK ]
[17:21:23] /usr/bin/users                                    [ OK ]
[17:21:23] /usr/bin/vmstat                                   [ OK ]
[17:21:23] /usr/bin/w                                        [ OK ]
[17:21:24] /usr/bin/watch                                    [ OK ]
[17:21:24] /usr/bin/wc                                       [ OK ]
[17:21:24] /usr/bin/wget                                     [ OK ]
[17:21:24] /usr/bin/whatis                                   [ OK ]
[17:21:24] /usr/bin/whereis                                  [ OK ]
[17:21:24] /usr/bin/which                                    [ OK ]
[17:21:24] /usr/bin/who                                      [ OK ]
[17:21:24] /usr/bin/whoami                                   [ OK ]
[17:21:24] /usr/bin/mawk                                     [ OK ]
[17:21:24] /usr/bin/lwp-request                              [ OK ]
[17:21:25] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[17:21:25] /usr/bin/bsd-mailx                                [ Warning ]
[17:21:25] Warning: The file '/usr/bin/bsd-mailx' exists on the system, but it is not present in the rkhunter.dat file.
[17:21:25] /usr/bin/w.procps                                 [ OK ]
[17:21:25] /sbin/depmod                                      [ OK ]
[17:21:26] /sbin/ifconfig                                    [ OK ]
[17:21:26] /sbin/ifdown                                      [ OK ]
[17:21:26] /sbin/ifup                                        [ OK ]
[17:21:26] /sbin/init                                        [ OK ]
[17:21:26] /sbin/insmod                                      [ OK ]
[17:21:26] /sbin/ip                                          [ OK ]
[17:21:26] /sbin/lsmod                                       [ OK ]
[17:21:27] /sbin/modinfo                                     [ OK ]
[17:21:27] /sbin/modprobe                                    [ OK ]
[17:21:27] /sbin/rmmod                                       [ OK ]
[17:21:27] /sbin/runlevel                                    [ OK ]
[17:21:28] /sbin/sulogin                                     [ OK ]
[17:21:28] /sbin/sysctl                                      [ OK ]
[17:21:28] /usr/sbin/adduser                                 [ OK ]
[17:21:28] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[17:21:29] /usr/sbin/chroot                                  [ OK ]
[17:21:29] /usr/sbin/cron                                    [ OK ]
[17:21:29] /usr/sbin/groupadd                                [ OK ]
[17:21:29] /usr/sbin/groupdel                                [ OK ]
[17:21:30] /usr/sbin/groupmod                                [ OK ]
[17:21:30] /usr/sbin/grpck                                   [ OK ]
[17:21:30] /usr/sbin/nologin                                 [ OK ]
[17:21:31] /usr/sbin/pwck                                    [ OK ]
[17:21:31] /usr/sbin/rsyslogd                                [ OK ]
[17:21:31] /usr/sbin/tcpd                                    [ OK ]
[17:21:32] /usr/sbin/useradd                                 [ OK ]
[17:21:32] /usr/sbin/userdel                                 [ OK ]
[17:21:32] /usr/sbin/usermod                                 [ OK ]
[17:21:32] /usr/sbin/vipw                                    [ OK ]
[17:21:32] /usr/sbin/unhide-linux26                          [ OK ]
```I've got two warnings - need I be worried?

Update:

I ran...

rkhunter --propupd
These were the results (notice the two application warnings - must I be worried)
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
    /usr/bin/mawk                                            [ OK ]
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
    Files checked: 132
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 2 minutes and 7 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

Chrootkit says:
```
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
Checking `mail'...                                          not infected
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
/usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.7/.path /usr/lib/pymodules/python2.7/PyQt4/uic/widget-plugins/.noinit /usr/lib/xulrunner-1.9.2.18/.autoreg /usr/lib/byobu/.notify_osd

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
eth0: PACKET SNIFFER(/sbin/dhclient[1109])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user jack deleted or never logged from lastlog!
Checking `chkutmp'...                                       chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
```
Is anything out of the ordinary?

---

### Post by cariboo on 2011-08-29
Why did you run all those programs if there is nothing wrong?

---

### Post by snip3r8 on 2011-08-30
I think you should only be worried about rootkits if you stole emails from HB>Gary

---

### Post by FatalMessenger on 2011-08-30
No, by the looks of it, there is nothing wrong. It looks like you installed some mail related program, and the didn't update the rkhunter database of allowed programs, so rkhunter flagged it because it wasn't in it's approved programs database.

As for the to warnings at the bottom, rkhunter flags any hidden files with warnings, probably nothing to worry about.

---

### Post by Dangertux on 2011-08-30
LOL@ the HB Gary email thing

But these warnings are typical in Ubuntu they are caused by the fact that the files in question are symlinks. This is because ubuntu doesnt use them the same way other distros do and the symlinks are there to maintain compatibility for cross platform scripts. I wouldn't worry.

---

