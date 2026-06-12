---
title: "Rootkit: RKHunter"
date: 2011-10-11
forum: Security
---

### Post by mxndrwgrdnr on 2011-10-11
New to Ubuntu, new to rootkits...was getting some persistent Google redirects yesterday until I deleted my cookies. Not sure if this counts as conclusive evidence of a rootkit or not. Anyways, I ran ClamAV, everything seemed ok. Same with CHKRootkit. Then I ran RKHunter and it found a few threats, but I'm not sure how to interpret them. ANY and all help will be greatly appreciated. Thank you! My RKHunter log is as follows:

```
[10:58:03] Running Rootkit Hunter version 1.3.6 on max-ThinkPad-T400
[10:58:03]
[10:58:03] Info: Start date is Tue Oct 11 10:58:03 PDT 2011
[10:58:03]
[10:58:03] Checking configuration file and command-line options...
[10:58:03] Info: Detected operating system is 'Linux'
[10:58:03] Info: Found O/S name: Ubuntu 11.04
[10:58:03] Info: Command line is /usr/bin/rkhunter -c
[10:58:03] Info: Environment shell is /bin/bash; rkhunter is using dash
[10:58:03] Info: Using configuration file '/etc/rkhunter.conf'
[10:58:03] Info: Installation directory is '/usr'
[10:58:03] Info: Using language 'en'
[10:58:03] Info: Using '/var/lib/rkhunter/db' as the database directory
[10:58:03] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[10:58:03] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[10:58:03] Info: Using '/' as the root directory by default
[10:58:03] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[10:58:03] Info: No mail-on-warning address configured
[10:58:03] Info: X will be automatically detected
[10:58:03] Info: Using second color set
[10:58:03] Info: Found the 'basename' command: /usr/bin/basename
[10:58:03] Info: Found the 'diff' command: /usr/bin/diff
[10:58:03] Info: Found the 'dirname' command: /usr/bin/dirname
[10:58:03] Info: Found the 'file' command: /usr/bin/file
[10:58:03] Info: Found the 'find' command: /usr/bin/find
[10:58:03] Info: Found the 'ifconfig' command: /sbin/ifconfig
[10:58:03] Info: Found the 'ip' command: /sbin/ip
[10:58:04] Info: Found the 'ldd' command: /usr/bin/ldd
[10:58:04] Info: Found the 'lsattr' command: /usr/bin/lsattr
[10:58:04] Info: Found the 'lsmod' command: /sbin/lsmod
[10:58:04] Info: Found the 'lsof' command: /usr/bin/lsof
[10:58:04] Info: Found the 'mktemp' command: /bin/mktemp
[10:58:04] Info: Found the 'netstat' command: /bin/netstat
[10:58:04] Info: Found the 'perl' command: /usr/bin/perl
[10:58:04] Info: Found the 'pgrep' command: /usr/bin/pgrep
[10:58:04] Info: Found the 'ps' command: /bin/ps
[10:58:04] Info: Found the 'pwd' command: /bin/pwd
[10:58:04] Info: Found the 'readlink' command: /bin/readlink
[10:58:04] Info: Found the 'sort' command: /usr/bin/sort
[10:58:04] Info: Found the 'stat' command: /usr/bin/stat
[10:58:04] Info: Found the 'strings' command: /usr/bin/strings
[10:58:04] Info: Found the 'uniq' command: /usr/bin/uniq
[10:58:04] Info: System is not using prelinking
[10:58:04] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[10:58:04] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[10:58:04] Info: Stored hash values did not use a package manager
[10:58:04] Info: The hash function field index is set to 1
[10:58:04] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[10:58:04] Info: Previous file attributes were stored
[10:58:04] Info: Enabled tests are: all
[10:58:04] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[10:58:04] Info: Found ksym file '/proc/kallsyms'
[10:58:04] Info: Using 'date' to process epoch second times.
[10:58:04]
[10:58:04] Checking if the O/S has changed since last time...
[10:58:04] Info: Nothing seems to have changed
[10:58:04] Info: Locking is not being used
[10:58:04]
[10:58:04] Starting system checks...
[10:58:04]
[10:58:04] Checking system commands...
[10:58:04] Info: Starting test name 'system_commands'
[10:58:04]
[10:58:04] Performing 'strings' command checks
[10:58:04] Info: Starting test name 'strings'
[10:58:04] Scanning for string /usr/sbin/ntpsx               [ OK ]
[10:58:04] Scanning for string /usr/sbin/.../bkit-ava        [ OK ]
[10:58:04] Scanning for string /usr/sbin/.../bkit-d          [ OK ]
[10:58:04] Scanning for string /usr/sbin/.../bkit-shd        [ OK ]
[10:58:05] Scanning for string /usr/sbin/.../bkit-f          [ OK ]
[10:58:05] Scanning for string /usr/include/.../proc.h       [ OK ]
[10:58:05] Scanning for string /usr/include/.../.bash_history [ OK ]
[10:58:05] Scanning for string /usr/include/.../bkit-get     [ OK ]
[10:58:05] Scanning for string /usr/include/.../bkit-dl      [ OK ]
[10:58:05] Scanning for string /usr/include/.../bkit-screen  [ OK ]
[10:58:05] Scanning for string /usr/include/.../bkit-sleep   [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-adore.o     [ OK ]
[10:58:05] Scanning for string /usr/lib/.../ls               [ OK ]
[10:58:05] Scanning for string /usr/lib/.../netstat          [ OK ]
[10:58:05] Scanning for string /usr/lib/.../lsof             [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[10:58:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[10:58:05] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[10:58:05] Scanning for string /usr/lib/.../psr              [ OK ]
[10:58:05] Scanning for string /usr/lib/.../find             [ OK ]
[10:58:05] Scanning for string /usr/lib/.../pstree           [ OK ]
[10:58:05] Scanning for string /usr/lib/.../slocate          [ OK ]
[10:58:05] Scanning for string /usr/lib/.../du               [ OK ]
[10:58:05] Scanning for string /usr/lib/.../top              [ OK ]
[10:58:05] Scanning for string /usr/sbin/...                 [ OK ]
[10:58:05] Scanning for string /usr/include/...              [ OK ]
[10:58:05] Scanning for string /usr/include/.../.tmp         [ OK ]
[10:58:05] Scanning for string /usr/lib/...                  [ OK ]
[10:58:05] Scanning for string /usr/lib/.../.ssh             [ OK ]
[10:58:06] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[10:58:06] Scanning for string /usr/lib/.bkit-               [ OK ]
[10:58:06] Scanning for string /tmp/.bkp                     [ OK ]
[10:58:06] Scanning for string /tmp/.cinik                   [ OK ]
[10:58:06] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[10:58:06] Scanning for string /lib/.sso                     [ OK ]
[10:58:06] Scanning for string /lib/.so                      [ OK ]
[10:58:06] Scanning for string /var/run/...dica/clean        [ OK ]
[10:58:06] Scanning for string /var/run/...dica/dxr          [ OK ]
[10:58:06] Scanning for string /var/run/...dica/read         [ OK ]
[10:58:06] Scanning for string /var/run/...dica/write        [ OK ]
[10:58:06] Scanning for string /var/run/...dica/lf           [ OK ]
[10:58:06] Scanning for string /var/run/...dica/xl           [ OK ]
[10:58:06] Scanning for string /var/run/...dica/xdr          [ OK ]
[10:58:06] Scanning for string /var/run/...dica/psg          [ OK ]
[10:58:06] Scanning for string /var/run/...dica/secure       [ OK ]
[10:58:06] Scanning for string /var/run/...dica/rdx          [ OK ]
[10:58:06] Scanning for string /var/run/...dica/va           [ OK ]
[10:58:06] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[10:58:06] Scanning for string /var/run/...dica/last.log     [ OK ]
[10:58:06] Scanning for string /usr/bin/.etc                 [ OK ]
[10:58:06] Scanning for string /etc/sshd_config              [ OK ]
[10:58:06] Scanning for string /etc/ssh_host_key             [ OK ]
[10:58:06] Scanning for string /etc/ssh_random_seed          [ OK ]
[10:58:06] Scanning for string /dev/ptyp                     [ OK ]
[10:58:06] Scanning for string /dev/ptyq                     [ OK ]
[10:58:06] Scanning for string /dev/ptyr                     [ OK ]
[10:58:07] Scanning for string /dev/ptys                     [ OK ]
[10:58:07] Scanning for string /dev/ptyt                     [ OK ]
[10:58:07] Scanning for string /dev/fd/.88/freshb-bsd        [ OK ]
[10:58:07] Scanning for string /dev/fd/.88/fresht            [ OK ]
[10:58:07] Scanning for string /dev/fd/.88/zxsniff           [ OK ]
[10:58:07] Scanning for string /dev/fd/.88/zxsniff.log       [ OK ]
[10:58:07] Scanning for string /dev/fd/.99/.ttyf00           [ OK ]
[10:58:07] Scanning for string /dev/fd/.99/.ttyp00           [ OK ]
[10:58:07] Scanning for string /dev/fd/.99/.ttyq00           [ OK ]
[10:58:07] Scanning for string /dev/fd/.99/.ttys00           [ OK ]
[10:58:07] Scanning for string /dev/fd/.99/.pwsx00           [ OK ]
[10:58:07] Scanning for string /etc/.acid                    [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/setrgrp.2        [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/TOHIDE           [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/adore/ava/ava    [ OK ]
[10:58:07] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[10:58:07] Scanning for string /bin/sysback                  [ OK ]
[10:58:07] Scanning for string /usr/local/bin/sysback        [ OK ]
[10:58:07] Scanning for string /usr/lib/.tbd                 [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[10:58:07] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[10:58:08] Scanning for string /usr/info/.torn/sh*           [ OK ]
[10:58:08] Scanning for string /usr/src/.puta/.1addr         [ OK ]
[10:58:08] Scanning for string /usr/src/.puta/.1file         [ OK ]
[10:58:08] Scanning for string /usr/src/.puta/.1proc         [ OK ]
[10:58:08] Scanning for string /usr/src/.puta/.1logz         [ OK ]
[10:58:08] Scanning for string /usr/info/.t0rn               [ OK ]
[10:58:08] Scanning for string /dev/.lib                     [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib                 [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib             [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[10:58:08] Scanning for string /dev/.lib/lib/scan            [ OK ]
[10:58:08] Scanning for string /usr/src/.puta                [ OK ]
[10:58:09] Scanning for string /usr/man/man1/man1            [ OK ]
[10:58:09] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[10:58:09] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[10:58:09] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[10:58:09]
[10:58:09] Performing 'shared libraries' checks
[10:58:09] Info: Starting test name 'shared_libs'
[10:58:09] Checking for preloading variables                 [ None found ]
[10:58:09] Checking for preloaded libraries                  [ None found ]
[10:58:09] Info: Starting test name 'shared_libs_path'
[10:58:09] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[10:58:09]
[10:58:09] Performing file properties checks
[10:58:09] Info: Starting test name 'properties'
[10:58:09] Checking for prerequisites                        [ OK ]
[10:58:09] /bin/bash                                         [ OK ]
[10:58:09] /bin/cat                                          [ OK ]
[10:58:09] /bin/chmod                                        [ OK ]
[10:58:10] /bin/chown                                        [ OK ]
[10:58:10] /bin/cp                                           [ OK ]
[10:58:10] /bin/date                                         [ OK ]
[10:58:10] /bin/df                                           [ OK ]
[10:58:10] /bin/dmesg                                        [ OK ]
[10:58:10] /bin/echo                                         [ OK ]
[10:58:10] /bin/ed                                           [ OK ]
[10:58:10] /bin/egrep                                        [ OK ]
[10:58:10] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[10:58:10] /bin/fgrep                                        [ OK ]
[10:58:10] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[10:58:11] /bin/fuser                                        [ OK ]
[10:58:11] /bin/grep                                         [ OK ]
[10:58:11] /bin/ip                                           [ OK ]
[10:58:11] /bin/kill                                         [ OK ]
[10:58:11] /bin/less                                         [ OK ]
[10:58:11] /bin/login                                        [ OK ]
[10:58:11] /bin/ls                                           [ OK ]
[10:58:11] /bin/lsmod                                        [ OK ]
[10:58:12] /bin/mktemp                                       [ OK ]
[10:58:12] /bin/more                                         [ OK ]
[10:58:12] /bin/mount                                        [ OK ]
[10:58:12] /bin/mv                                           [ OK ]
[10:58:12] /bin/netstat                                      [ OK ]
[10:58:12] /bin/ps                                           [ OK ]
[10:58:12] /bin/pwd                                          [ OK ]
[10:58:12] /bin/readlink                                     [ OK ]
[10:58:13] /bin/sed                                          [ OK ]
[10:58:13] /bin/sh                                           [ OK ]
[10:58:13] /bin/su                                           [ OK ]
[10:58:13] /bin/touch                                        [ OK ]
[10:58:13] /bin/uname                                        [ OK ]
[10:58:14] /bin/which                                        [ OK ]
[10:58:14] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[10:58:14] /bin/dash                                         [ OK ]
[10:58:14] /usr/bin/awk                                      [ OK ]
[10:58:14] /usr/bin/basename                                 [ OK ]
[10:58:14] /usr/bin/chattr                                   [ OK ]
[10:58:14] /usr/bin/cut                                      [ OK ]
[10:58:15] /usr/bin/diff                                     [ OK ]
[10:58:15] /usr/bin/dirname                                  [ OK ]
[10:58:15] /usr/bin/dpkg                                     [ OK ]
[10:58:15] /usr/bin/dpkg-query                               [ OK ]
[10:58:15] /usr/bin/du                                       [ OK ]
[10:58:15] /usr/bin/env                                      [ OK ]
[10:58:15] /usr/bin/file                                     [ OK ]
[10:58:15] /usr/bin/find                                     [ OK ]
[10:58:15] /usr/bin/GET                                      [ OK ]
[10:58:15] /usr/bin/groups                                   [ OK ]
[10:58:15] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[10:58:16] /usr/bin/head                                     [ OK ]
[10:58:16] /usr/bin/id                                       [ OK ]
[10:58:16] /usr/bin/killall                                  [ OK ]
[10:58:16] /usr/bin/last                                     [ OK ]
[10:58:16] /usr/bin/lastlog                                  [ OK ]
[10:58:16] /usr/bin/ldd                                      [ OK ]
[10:58:16] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[10:58:16] /usr/bin/less                                     [ OK ]
[10:58:16] /usr/bin/locate                                   [ OK ]
[10:58:16] /usr/bin/logger                                   [ OK ]
[10:58:16] /usr/bin/lsattr                                   [ OK ]
[10:58:17] /usr/bin/lsof                                     [ OK ]
[10:58:17] /usr/bin/mail                                     [ OK ]
[10:58:17] /usr/bin/md5sum                                   [ OK ]
[10:58:17] /usr/bin/mlocate                                  [ OK ]
[10:58:17] /usr/bin/newgrp                                   [ OK ]
[10:58:17] /usr/bin/passwd                                   [ OK ]
[10:58:17] /usr/bin/perl                                     [ OK ]
[10:58:17] /usr/bin/pgrep                                    [ OK ]
[10:58:17] /usr/bin/pstree                                   [ OK ]
[10:58:18] /usr/bin/rkhunter                                 [ Warning ]
[10:58:18] Warning: The file properties have changed:
[10:58:18]          File: /usr/bin/rkhunter
[10:58:18]          Current inode: 530548    Stored inode: 529637
[10:58:18] /usr/bin/rpm                                      [ OK ]
[10:58:18] /usr/bin/runcon                                   [ OK ]
[10:58:18] /usr/bin/sha1sum                                  [ OK ]
[10:58:18] /usr/bin/sha224sum                                [ OK ]
[10:58:18] /usr/bin/sha256sum                                [ OK ]
[10:58:18] /usr/bin/sha384sum                                [ OK ]
[10:58:18] /usr/bin/sha512sum                                [ OK ]
[10:58:19] /usr/bin/size                                     [ OK ]
[10:58:19] /usr/bin/sort                                     [ OK ]
[10:58:19] /usr/bin/stat                                     [ OK ]
[10:58:19] /usr/bin/strace                                   [ OK ]
[10:58:19] /usr/bin/strings                                  [ OK ]
[10:58:19] /usr/bin/sudo                                     [ OK ]
[10:58:19] /usr/bin/tail                                     [ OK ]
[10:58:19] /usr/bin/test                                     [ OK ]
[10:58:19] /usr/bin/top                                      [ OK ]
[10:58:19] /usr/bin/touch                                    [ OK ]
[10:58:20] /usr/bin/tr                                       [ OK ]
[10:58:20] /usr/bin/uniq                                     [ OK ]
[10:58:20] /usr/bin/users                                    [ OK ]
[10:58:20] /usr/bin/vmstat                                   [ OK ]
[10:58:20] /usr/bin/w                                        [ OK ]
[10:58:20] /usr/bin/watch                                    [ OK ]
[10:58:20] /usr/bin/wc                                       [ OK ]
[10:58:20] /usr/bin/wget                                     [ OK ]
[10:58:20] /usr/bin/whatis                                   [ OK ]
[10:58:20] /usr/bin/whereis                                  [ OK ]
[10:58:20] /usr/bin/which                                    [ OK ]
[10:58:20] /usr/bin/who                                      [ OK ]
[10:58:21] /usr/bin/whoami                                   [ OK ]
[10:58:21] /usr/bin/mawk                                     [ OK ]
[10:58:21] /usr/bin/lwp-request                              [ OK ]
[10:58:21] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[10:58:21] /usr/bin/bsd-mailx                                [ OK ]
[10:58:21] /usr/bin/w.procps                                 [ OK ]
[10:58:21] /sbin/depmod                                      [ OK ]
[10:58:22] /sbin/ifconfig                                    [ OK ]
[10:58:22] /sbin/ifdown                                      [ OK ]
[10:58:22] /sbin/ifup                                        [ OK ]
[10:58:22] /sbin/init                                        [ OK ]
[10:58:22] /sbin/insmod                                      [ OK ]
[10:58:22] /sbin/ip                                          [ OK ]
[10:58:22] /sbin/lsmod                                       [ OK ]
[10:58:23] /sbin/modinfo                                     [ OK ]
[10:58:23] /sbin/modprobe                                    [ OK ]
[10:58:23] /sbin/rmmod                                       [ OK ]
[10:58:23] /sbin/runlevel                                    [ OK ]
[10:58:23] /sbin/sulogin                                     [ OK ]
[10:58:24] /sbin/sysctl                                      [ OK ]
[10:58:24] /usr/sbin/adduser                                 [ OK ]
[10:58:24] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[10:58:24] /usr/sbin/chroot                                  [ OK ]
[10:58:24] /usr/sbin/cron                                    [ OK ]
[10:58:25] /usr/sbin/groupadd                                [ OK ]
[10:58:25] /usr/sbin/groupdel                                [ OK ]
[10:58:25] /usr/sbin/groupmod                                [ OK ]
[10:58:25] /usr/sbin/grpck                                   [ OK ]
[10:58:26] /usr/sbin/nologin                                 [ OK ]
[10:58:26] /usr/sbin/pwck                                    [ OK ]
[10:58:26] /usr/sbin/rsyslogd                                [ OK ]
[10:58:27] /usr/sbin/tcpd                                    [ OK ]
[10:58:27] /usr/sbin/useradd                                 [ OK ]
[10:58:27] /usr/sbin/userdel                                 [ OK ]
[10:58:27] /usr/sbin/usermod                                 [ OK ]
[10:58:27] /usr/sbin/vipw                                    [ OK ]
[10:58:27] /usr/sbin/unhide-linux26                          [ Warning ]
[10:58:27] Warning: The file properties have changed:
[10:58:27]          File: /usr/sbin/unhide-linux26
[10:58:27]          Current inode: 531946    Stored inode: 529638
[10:58:34]
[10:58:34] Checking for rootkits...
[10:58:34] Info: Starting test name 'rootkits'
[10:58:34]
[10:58:34] Performing check of known rootkit files and directories
[10:58:34] Info: Starting test name 'known_rkts'
[10:58:34]
[10:58:34] Checking for 55808 Trojan - Variant A...
[10:58:34]   Checking for file '/tmp/.../r'                  [ Not found ]
[10:58:34]   Checking for file '/tmp/.../a'                  [ Not found ]
[10:58:35] 55808 Trojan - Variant A                          [ Not found ]
[10:58:35]
[10:58:35] Checking for ADM Worm...
[10:58:35]   Checking for string 'w0rm'                      [ Not found ]
[10:58:35] ADM Worm                                          [ Not found ]
[10:58:35]
[10:58:35] Checking for AjaKit Rootkit...
[10:58:35]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:58:35]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:58:35]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:58:35]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[10:58:35]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[10:58:35]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[10:58:35]   Checking for directory '/dev/tux'               [ Not found ]
[10:58:35]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[10:58:35] AjaKit Rootkit                                    [ Not found ]
[10:58:35]
[10:58:35] Checking for Adore Rootkit...
[10:58:35]   Checking for file '/usr/secure'                 [ Not found ]
[10:58:35]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[10:58:35]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[10:58:35]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[10:58:35]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[10:58:35]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[10:58:35]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[10:58:35]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[10:58:35]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[10:58:35]   Checking for file '/var/log/ssh/old'            [ Not found ]
[10:58:35]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/kern'          [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/backup'        [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[10:58:35]   Checking for directory '/lib/backup'            [ Not found ]
[10:58:35]   Checking for directory '/lib/backup/txt'        [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/work'          [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/sys'           [ Not found ]
[10:58:35]   Checking for directory '/var/log/ssh'           [ Not found ]
[10:58:35]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[10:58:36]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[10:58:36] Adore Rootkit                                     [ Not found ]
[10:58:36]
[10:58:36] Checking for aPa Kit...
[10:58:36]   Checking for file '/usr/share/.aPa'             [ Not found ]
[10:58:36] aPa Kit                                           [ Not found ]
[10:58:36]
[10:58:36] Checking for Apache Worm...
[10:58:36]   Checking for file '/bin/.log'                   [ Not found ]
[10:58:36] Apache Worm                                       [ Not found ]
[10:58:36]
[10:58:36] Checking for Ambient (ark) Rootkit...
[10:58:36]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[10:58:36]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[10:58:36]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[10:58:36]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[10:58:36]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[10:58:36]   Checking for directory '/dev/ptyxx'             [ Not found ]
[10:58:36] Ambient (ark) Rootkit                             [ Not found ]
[10:58:36]
[10:58:36] Checking for Balaur Rootkit...
[10:58:36]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[10:58:36]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[10:58:36]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[10:58:36]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[10:58:36] Balaur Rootkit                                    [ Not found ]
[10:58:36]
[10:58:36] Checking for BeastKit Rootkit...
[10:58:36]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[10:58:36]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[10:58:36]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[10:58:36]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[10:58:36] BeastKit Rootkit                                  [ Not found ]
[10:58:36]
[10:58:36] Checking for beX2 Rootkit...
[10:58:36]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[10:58:37]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[10:58:37]   Checking for directory '/usr/include/bex'       [ Not found ]
[10:58:37] beX2 Rootkit                                      [ Not found ]
[10:58:37]
[10:58:37] Checking for BOBKit Rootkit...
[10:58:37]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[10:58:37]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[10:58:37]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[10:58:37]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[10:58:37]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[10:58:37]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../find'           [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../du'             [ Not found ]
[10:58:37]   Checking for file '/usr/lib/.../top'            [ Not found ]
[10:58:37]   Checking for directory '/usr/sbin/...'          [ Not found ]
[10:58:37]   Checking for directory '/usr/include/...'       [ Not found ]
[10:58:37]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[10:58:38]   Checking for directory '/usr/lib/...'           [ Not found ]
[10:58:38]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[10:58:38]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[10:58:38]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[10:58:38]   Checking for directory '/tmp/.bkp'              [ Not found ]
[10:58:38] BOBKit Rootkit                                    [ Not found ]
[10:58:38]
[10:58:38] Checking for cb Rootkit...
[10:58:38]   Checking for file '/dev/srd0'                   [ Not found ]
[10:58:38]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[10:58:38]   Checking for file '/dev/mounnt'                 [ Not found ]
[10:58:38]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /cl'       [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /.x.tgz'   [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /statdx'   [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /wted'     [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /write'    [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /scan'     [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /sc'       [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /sl2'      [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /wroot'    [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /wscan'    [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /wu'       [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /v'        [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /read'     [ Not found ]
[10:58:38]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[10:58:38]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[10:58:38]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[10:58:38]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[10:58:38]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[10:58:38]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[10:58:38]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[10:58:38]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.system/.. /tcp.log' [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /curatare/attrib' [ Not found ]
[10:58:38]   Checking for file '/usr/bin/.zeen/.. /curatare/chattr' [ Not found ]
[10:58:39]   Checking for file '/usr/bin/.zeen/.. /curatare/ps' [ Not found ]
[10:58:39]   Checking for file '/usr/bin/.zeen/.. /curatare/pstree' [ Not found ]
[10:58:39]   Checking for file '/usr/bin/.system/.. /.x/xC.o' [ Not found ]
[10:58:39]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[10:58:39]   Checking for directory '/usr/bin/.zeen/.. /curatare' [ Not found ]
[10:58:39]   Checking for directory '/usr/bin/.zeen/.. /scan' [ Not found ]
[10:58:39]   Checking for directory '/usr/bin/.system/.. '   [ Not found ]
[10:58:39] cb Rootkit                                        [ Not found ]
[10:58:39]
[10:58:39] Checking for CiNIK Worm (Slapper.B variant)...
[10:58:39]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:58:39]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[10:58:39] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[10:58:39]
[10:58:39] Checking for Danny-Boy's Abuse Kit...
[10:58:39]   Checking for file '/dev/mdev'                   [ Not found ]
[10:58:39]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[10:58:39] Danny-Boy's Abuse Kit                             [ Not found ]
[10:58:39]
[10:58:39] Checking for Devil RootKit...
[10:58:39]   Checking for file '/var/lib/games/.src'         [ Not found ]
[10:58:39]   Checking for file '/dev/dsx'                    [ Not found ]
[10:58:39]   Checking for file '/dev/caca'                   [ Not found ]
[10:58:39]   Checking for file '/dev/pro'                    [ Not found ]
[10:58:39]   Checking for file '/bin/bye'                    [ Not found ]
[10:58:39]   Checking for file '/bin/homedir'                [ Not found ]
[10:58:39]   Checking for file '/usr/bin/xfss'               [ Not found ]
[10:58:39]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[10:58:39]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[10:58:40]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[10:58:40]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[10:58:40] Devil RootKit                                     [ Not found ]
[10:58:40]
[10:58:40] Checking for Dica-Kit Rootkit...
[10:58:40]   Checking for file '/lib/.sso'                   [ Not found ]
[10:58:40]   Checking for file '/lib/.so'                    [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/read'       [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/write'      [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/va'         [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[10:58:40]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[10:58:40]   Checking for file '/usr/bin/.etc'               [ Not found ]
[10:58:40]   Checking for file '/etc/sshd_config'            [ Not found ]
[10:58:40]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[10:58:40]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[10:58:40]   Checking for directory '/var/run/...dica'       [ Not found ]
[10:58:40]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[10:58:40]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[10:58:41] Dica-Kit Rootkit                                  [ Not found ]
[10:58:41]
[10:58:41] Checking for Dreams Rootkit...
[10:58:41]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:58:41]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:58:41]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:58:41]   Checking for file '/usr/bin/sense'              [ Not found ]
[10:58:41]   Checking for file '/usr/bin/sl2'                [ Not found ]
[10:58:41]   Checking for file '/usr/bin/logclear'           [ Not found ]
[10:58:41]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[10:58:41]   Checking for file '/usr/bin/initrd'             [ Not found ]
[10:58:41]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[10:58:41]   Checking for file '/usr/bin/snfs'               [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libsss'             [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[10:58:41]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[10:58:41]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[10:58:41]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[10:58:41]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[10:58:41]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[10:58:41]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[10:58:41]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[10:58:41]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[10:58:41]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[10:58:41]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[10:58:41]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[10:58:41] Dreams Rootkit                                    [ Not found ]
[10:58:41]
[10:58:41] Checking for Duarawkz Rootkit...
[10:58:41]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[10:58:41]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[10:58:41] Duarawkz Rootkit                                  [ Not found ]
[10:58:41]
[10:58:41] Checking for Enye LKM...
[10:58:42]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[10:58:42]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[10:58:42] Enye LKM                                          [ Not found ]
[10:58:42]
[10:58:42] Checking for Flea Linux Rootkit...
[10:58:42]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:58:42]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[10:58:42]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[10:58:42]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[10:58:42]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[10:58:42]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:58:42]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[10:58:42]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[10:58:42]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[10:58:42]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[10:58:42]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[10:58:42]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:58:42]   Checking for directory '/dev/..0'               [ Not found ]
[10:58:42]   Checking for directory '/dev/..0/backup'        [ Not found ]
[10:58:42] Flea Linux Rootkit                                [ Not found ]
[10:58:42]
[10:58:42] Checking for FreeBSD Rootkit...
[10:58:42]   Checking for file '/dev/ptyp'                   [ Not found ]
[10:58:42]   Checking for file '/dev/ptyq'                   [ Not found ]
[10:58:42]   Checking for file '/dev/ptyr'                   [ Not found ]
[10:58:42]   Checking for file '/dev/ptys'                   [ Not found ]
[10:58:42]   Checking for file '/dev/ptyt'                   [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.88/freshb-bsd'      [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.88/fresht'          [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.88/zxsniff'         [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.88/zxsniff.log'     [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.99/.ttyf00'         [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.99/.ttyp00'         [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.99/.ttyq00'         [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.99/.ttys00'         [ Not found ]
[10:58:42]   Checking for file '/dev/fd/.99/.pwsx00'         [ Not found ]
[10:58:42]   Checking for file '/etc/.acid'                  [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/setrgrp.2'      [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/TOHIDE'         [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/adore/ava/ava'  [ Not found ]
[10:58:43]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[10:58:43]   Checking for file '/bin/sysback'                [ Not found ]
[10:58:43]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[10:58:43]   Checking for directory '/dev/fd/.88'            [ Not found ]
[10:58:43]   Checking for directory '/dev/fd/.99'            [ Not found ]
[10:58:43]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[10:58:43]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[10:58:43] FreeBSD Rootkit                                   [ Not found ]
[10:58:43]
[10:58:43] Checking for Fu Rootkit...
[10:58:43]   Checking for file '/sbin/xc'                    [ Not found ]
[10:58:43]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[10:58:43]   Checking for file '/bin/.lib'                   [ Not found ]
[10:58:43] Fu Rootkit                                        [ Not found ]
[10:58:43]
[10:58:43] Checking for ****`it Rootkit...
[10:58:43]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[10:58:43]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[10:58:43]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[10:58:43]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[10:58:43]   Checking for file '/dev/proc/fuckit/system-bins/init' [ Not found ]
[10:58:43]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[10:58:43]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[10:58:43]   Checking for directory '/dev/proc'              [ Not found ]
[10:58:44]   Checking for directory '/dev/proc/fuckit'       [ Not found ]
[10:58:44]   Checking for directory '/dev/proc/fuckit/system-bins' [ Not found ]
[10:58:44]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[10:58:44] ****`it Rootkit                                   [ Not found ]
[10:58:44]
[10:58:44] Checking for GasKit Rootkit...
[10:58:44]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[10:58:44]   Checking for directory '/dev/dev'               [ Not found ]
[10:58:44]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[10:58:44]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[10:58:44] GasKit Rootkit                                    [ Not found ]
[10:58:44]
[10:58:44] Checking for Heroin LKM...
[10:58:44]   Checking for kernel symbol 'heroin'             [ Not found ]
[10:58:44] Heroin LKM                                        [ Not found ]
[10:58:44]
[10:58:44] Checking for HjC Kit...
[10:58:44]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[10:58:44] HjC Kit                                           [ Not found ]
[10:58:44]
[10:58:44] Checking for ignoKit Rootkit...
[10:58:44]   Checking for file '/lib/defs/p'                 [ Not found ]
[10:58:44]   Checking for file '/lib/defs/q'                 [ Not found ]
[10:58:44]   Checking for file '/lib/defs/r'                 [ Not found ]
[10:58:44]   Checking for file '/lib/defs/s'                 [ Not found ]
[10:58:44]   Checking for file '/lib/defs/t'                 [ Not found ]
[10:58:44]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[10:58:44]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[10:58:44]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[10:58:44]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[10:58:44]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[10:58:44]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[10:58:44]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[10:58:44]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[10:58:44]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[10:58:44] ignoKit Rootkit                                   [ Not found ]
[10:58:44]
[10:58:44] Checking for iLLogiC Rootkit...
[10:58:44]   Checking for file '/dev/kmod'                   [ Not found ]
[10:58:45]   Checking for file '/dev/dos'                    [ Not found ]
[10:58:45]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[10:58:45]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[10:58:45]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:58:45]   Checking for file '/usr/bin/sia'                [ Not found ]
[10:58:45]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/iver'  [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/uconf.inv' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/ssh/sshport' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/ava'   [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/cleaner' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/sz'    [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/rcp'   [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/patcher' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/pg'    [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/crypt' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/utime' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/wget'  [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/instmod' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/find' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/du' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/ls' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/psr' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/netstat' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/su' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/ping' [ Not found ]
[10:58:45]   Checking for file '/lib/security/.config/bin/passwd' [ Not found ]
[10:58:45]   Checking for directory '/lib/security/.config'  [ Not found ]
[10:58:45]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:58:46]   Checking for directory '/lib/security/.config/bin' [ Not found ]
[10:58:46]   Checking for directory '/lib/security/.config/backup' [ Not found ]
[10:58:46]   Checking for directory '/root/   /.dir'         [ Not found ]
[10:58:46]   Checking for directory '/root/   /.dir/mass-scan' [ Not found ]
[10:58:46]   Checking for directory '/root/   /.dir/flood'   [ Not found ]
[10:58:46] iLLogiC Rootkit                                   [ Not found ]
[10:58:46]
[10:58:46] Checking for IntoXonia-NG Rootkit...
[10:58:46]   Checking for kernel symbol 'funces'             [ Not found ]
[10:58:46]   Checking for kernel symbol 'ixinit'             [ Not found ]
[10:58:46]   Checking for kernel symbol 'tricks'             [ Not found ]
[10:58:46]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[10:58:46]   Checking for kernel symbol 'rootme'             [ Not found ]
[10:58:46]   Checking for kernel symbol 'hide_module'        [ Not found ]
[10:58:46]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[10:58:46] IntoXonia-NG Rootkit                              [ Not found ]
[10:58:46]
[10:58:46] Checking for Irix Rootkit...
[10:58:46]   Checking for directory '/dev/pts/01'            [ Not found ]
[10:58:46]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[10:58:46]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[10:58:46]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[10:58:47] Irix Rootkit                                      [ Not found ]
[10:58:47]
[10:58:47] Checking for Kitko Rootkit...
[10:58:47]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[10:58:47] Kitko Rootkit                                     [ Not found ]
[10:58:47]
[10:58:47] Checking for Knark Rootkit...
[10:58:47]   Checking for file '/proc/knark/pids'            [ Not found ]
[10:58:47]   Checking for directory '/proc/knark'            [ Not found ]
[10:58:47] Knark Rootkit                                     [ Not found ]
[10:58:47]
[10:58:47] Checking for ld-linuxv.so Rootkit...
[10:58:47]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[10:58:47]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[10:58:47]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[10:58:47]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[10:58:47] ld-linuxv.so Rootkit                              [ Not found ]
[10:58:47]
[10:58:47] Checking for Li0n Worm...
[10:58:47]   Checking for file '/bin/in.telnetd'             [ Not found ]
[10:58:47]   Checking for file '/bin/mjy'                    [ Not found ]
[10:58:47]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[10:58:47]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[10:58:47]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[10:58:47]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[10:58:47] Li0n Worm                                         [ Not found ]
[10:58:48]
[10:58:48] Checking for Lockit / LJK2 Rootkit...
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[10:58:48]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[10:58:48]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[10:58:48] Lockit / LJK2 Rootkit                             [ Not found ]
[10:58:49]
[10:58:49] Checking for Mood-NT Rootkit...
[10:58:49]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[10:58:49]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[10:58:49]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[10:58:49]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[10:58:49]   Checking for directory '/_cthulhu'              [ Not found ]
[10:58:49] Mood-NT Rootkit                                   [ Not found ]
[10:58:49]
[10:58:49] Checking for MRK Rootkit...
[10:58:49]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[10:58:49]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[10:58:49]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[10:58:49]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[10:58:49]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[10:58:49]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[10:58:49] MRK Rootkit                                       [ Not found ]
[10:58:49]
[10:58:49] Checking for Ni0 Rootkit...
[10:58:49]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[10:58:49]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[10:58:49]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[10:58:49]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[10:58:49]   Checking for directory '/tmp/waza'              [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:58:49]   Checking for directory '/usr/sbin/es'           [ Not found ]
[10:58:49] Ni0 Rootkit                                       [ Not found ]
[10:58:49]
[10:58:49] Checking for Ohhara Rootkit...
[10:58:49]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[10:58:49]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[10:58:49] Ohhara Rootkit                                    [ Not found ]
[10:58:49]
[10:58:49] Checking for Optic Kit (Tux) Worm...
[10:58:49]   Checking for directory '/dev/tux'               [ Not found ]
[10:58:49]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[10:58:50]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[10:58:50]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[10:58:50] Optic Kit (Tux) Worm                              [ Not found ]
[10:58:50]
[10:58:50] Checking for Oz Rootkit...
[10:58:50]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[10:58:50]   Checking for directory '/dev/.oz'               [ Not found ]
[10:58:50] Oz Rootkit                                        [ Not found ]
[10:58:50]
[10:58:50] Checking for Phalanx Rootkit...
[10:58:50]   Checking for file '/uNFuNF'                     [ Not found ]
[10:58:50]   Checking for file '/etc/host.ph1'               [ Not found ]
[10:58:50]   Checking for file '/bin/host.ph1'               [ Not found ]
[10:58:50]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[10:58:50]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[10:58:50]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[10:58:50]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[10:58:50]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[10:58:50] Phalanx Rootkit                                   [ Not found ]
[10:58:50]
[10:58:50] Checking for Phalanx2 Rootkit...
[10:58:50]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[10:58:50]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[10:58:50]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[10:58:50]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[10:58:50]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[10:58:50]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[10:58:50]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[10:58:50]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[10:58:50]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[10:58:50]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[10:58:50]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[10:58:50]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[10:58:50]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[10:58:50]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[10:58:50] Phalanx2 Rootkit                                  [ Not found ]
[10:58:50]
[10:58:50] Checking for Phalanx2 Rootkit (extended tests)...
[10:58:50]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[10:58:50]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[10:58:50]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[10:58:51] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[10:58:51]
[10:58:51] Checking for Portacelo Rootkit...
[10:58:51]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../.p'             [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../getty'          [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../show'           [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[10:58:51]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[10:58:51]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[10:58:51] Portacelo Rootkit                                 [ Not found ]
[10:58:51]
[10:58:51] Checking for R3dstorm Toolkit...
[10:58:51]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[10:58:51]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[10:58:51]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[10:58:51]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[10:58:51]   Checking for file '/bin/.../see_all'            [ Not found ]
[10:58:51]   Checking for directory '/var/log/tk02'          [ Not found ]
[10:58:51]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[10:58:51]   Checking for directory '/bin/...'               [ Not found ]
[10:58:51] R3dstorm Toolkit                                  [ Not found ]
[10:58:51]
[10:58:51] Checking for RH-Sharpe's Rootkit...
[10:58:51]   Checking for file '/bin/lps'                    [ Not found ]
[10:58:51]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[10:58:51]   Checking for file '/usr/bin/ltop'               [ Not found ]
[10:58:51]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[10:58:51]   Checking for file '/usr/bin/ldu'                [ Not found ]
[10:58:51]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[10:58:52]   Checking for file '/usr/bin/wp'                 [ Not found ]
[10:58:52]   Checking for file '/usr/bin/shad'               [ Not found ]
[10:58:52]   Checking for file '/usr/bin/vadim'              [ Not found ]
[10:58:52]   Checking for file '/usr/bin/slice'              [ Not found ]
[10:58:52]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[10:58:52]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[10:58:52] RH-Sharpe's Rootkit                               [ Not found ]
[10:58:52]
[10:58:52] Checking for RSHA's Rootkit...
[10:58:52]   Checking for file '/bin/kr4p'                   [ Not found ]
[10:58:52]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[10:58:52]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[10:58:52]   Checking for file '/usr/bin/slice2'             [ Not found ]
[10:58:52]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[10:58:52]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[10:58:52]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[10:58:52]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[10:58:52] RSHA's Rootkit                                    [ Not found ]
[10:58:52]
[10:58:52] Checking for Scalper Worm...
[10:58:52]   Checking for file '/tmp/.a'                     [ Not found ]
[10:58:52]   Checking for file '/tmp/.uua'                   [ Not found ]
[10:58:52] Scalper Worm                                      [ Not found ]
[10:58:52]
[10:58:52] Checking for Sebek LKM...
[10:58:53]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[10:58:53] Sebek LKM                                         [ Not found ]
[10:58:53]
[10:58:53] Checking for Shutdown Rootkit...
[10:58:53]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[10:58:53]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[10:58:53]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[10:58:53]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[10:58:53]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[10:58:53]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[10:58:53]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[10:58:53]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[10:58:53] Shutdown Rootkit                                  [ Not found ]
[10:58:53]
[10:58:53] Checking for SHV4 Rootkit...
[10:58:53]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:58:53]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:58:53]   Checking for file '/lib/lidps1.so'              [ Not found ]
[10:58:53]   Checking for file '/lib/libproc.a'              [ Not found ]
[10:58:53]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[10:58:53]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[10:58:53]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[10:58:53]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[10:58:53]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[10:58:53]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[10:58:53]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[10:58:53]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[10:58:53]   Checking for file '/usr/include/file.h'         [ Not found ]
[10:58:53]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[10:58:53]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[10:58:53]   Checking for file '/usr/include/log.h'          [ Not found ]
[10:58:53]   Checking for file '/usr/include/proc.h'         [ Not found ]
[10:58:53]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[10:58:53]   Checking for file '/dev/srd0'                   [ Not found ]
[10:58:53]   Checking for directory '/lib/ldd.so'            [ Not found ]
[10:58:53]   Checking for directory '/lib/security/.config'  [ Not found ]
[10:58:53]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:58:54] SHV4 Rootkit                                      [ Not found ]
[10:58:54]
[10:58:54] Checking for SHV5 Rootkit...
[10:58:54]   Checking for file '/etc/sh.conf'                [ Not found ]
[10:58:54]   Checking for file '/lib/libproc.a'              [ Not found ]
[10:58:54]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[10:58:54]   Checking for file '/lib/lidps1.so'              [ Not found ]
[10:58:54]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[10:58:54]   Checking for file '/usr/include/file.h'         [ Not found ]
[10:58:54]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[10:58:54]   Checking for file '/usr/include/log.h'          [ Not found ]
[10:58:54]   Checking for file '/usr/include/proc.h'         [ Not found ]
[10:58:54]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[10:58:54]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[10:58:54]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[10:58:54]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[10:58:54]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[10:58:54]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[10:58:54]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[10:58:54]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[10:58:54]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[10:58:54]   Checking for file '/dev/srd0'                   [ Not found ]
[10:58:54]   Checking for directory '/lib/libsh.so'          [ Not found ]
[10:58:54]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[10:58:54]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[10:58:54]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[10:58:54] SHV5 Rootkit                                      [ Not found ]
[10:58:54]
[10:58:54] Checking for Sin Rootkit...
[10:58:54]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[10:58:54]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:58:54]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:58:54]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:58:54]   Checking for file '/dev/ttyos'                  [ Not found ]
[10:58:54]   Checking for file '/usr/lib/.lib'               [ Not found ]
[10:58:54]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[10:58:54]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[10:58:55]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[10:58:55]   Checking for file '/usr/man/man1/...'           [ Not found ]
[10:58:55]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[10:58:55]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[10:58:55]   Checking for directory '/usr/lib/sn'            [ Not found ]
[10:58:55]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[10:58:55]   Checking for directory '/dev/.haos'             [ Not found ]
[10:58:55] Sin Rootkit                                       [ Not found ]
[10:58:55]
[10:58:55] Checking for Slapper Worm...
[10:58:55]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[10:58:55]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[10:58:55]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[10:58:55]   Checking for file '/tmp/httpd'                  [ Not found ]
[10:58:55]   Checking for file '/tmp/.unlock'                [ Not found ]
[10:58:55]   Checking for file '/tmp/update'                 [ Not found ]
[10:58:55]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:58:55]   Checking for file '/tmp/.b'                     [ Not found ]
[10:58:55] Slapper Worm                                      [ Not found ]
[10:58:55]
[10:58:55] Checking for Sneakin Rootkit...
[10:58:55]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[10:58:55] Sneakin Rootkit                                   [ Not found ]
[10:58:55]
[10:58:55] Checking for 'Spanish' Rootkit...
[10:58:55]   Checking for file '/dev/ptyq'                   [ Not found ]
[10:58:55]   Checking for file '/bin/ad'                     [ Not found ]
[10:58:55]   Checking for file '/bin/ava'                    [ Not found ]
[10:58:55]   Checking for file '/bin/server'                 [ Not found ]
[10:58:55]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[10:58:55]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[10:58:56]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[10:58:56]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[10:58:56]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[10:58:56]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[10:58:56]   Checking for directory '/usr/share/...'         [ Not found ]
[10:58:56] 'Spanish' Rootkit                                 [ Not found ]
[10:58:56]
[10:58:56] Checking for Suckit Rootkit...
[10:58:56]   Checking for file '/sbin/initsk12'              [ Not found ]
[10:58:56]   Checking for file '/sbin/initxrk'               [ Not found ]
[10:58:56]   Checking for file '/usr/bin/null'               [ Not found ]
[10:58:56]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[10:58:56]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[10:58:56]   Checking for directory '/etc/.MG'               [ Not found ]
[10:58:56]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[10:58:56]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[10:58:56] Suckit Rootkit                                    [ Not found ]
[10:58:56]
[10:58:56] Checking for SunOS Rootkit...
[10:58:56]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:58:56]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:58:56]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:58:56]   Checking for file '/bin/xlogin'                 [ Not found ]
[10:58:56]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[10:58:56]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[10:58:56]   Checking for file '/sbin/login'                 [ Not found ]
[10:58:56]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[10:58:56]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[10:58:56]   Checking for file '/dev/kmod'                   [ Not found ]
[10:58:57]   Checking for file '/dev/dos'                    [ Not found ]
[10:58:57] SunOS Rootkit                                     [ Not found ]
[10:58:57]
[10:58:57] Checking for SunOS / NSDAP Rootkit...
[10:58:57]   Checking for file '/dev/pts/01/55su'            [ Not found ]
[10:58:57]   Checking for file '/dev/pts/01/55ps'            [ Not found ]
[10:58:57]   Checking for file '/dev/pts/01/55ping'          [ Not found ]
[10:58:57]   Checking for file '/dev/pts/01/55login'         [ Not found ]
[10:58:57]   Checking for file '/dev/pts/01/PATCHER_COMPLETED' [ Not found ]
[10:58:57]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[10:58:57]   Checking for file '/dev/prom/dos'               [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[10:58:57]   Checking for file '/usr/lib/lpset'              [ Not found ]
[10:58:57]   Checking for file '/usr/lib/lpstart'            [ Not found ]
[10:58:57]   Checking for file '/usr/bin/mc68000'            [ Not found ]
[10:58:57]   Checking for file '/usr/bin/mc68010'            [ Not found ]
[10:58:57]   Checking for file '/usr/bin/mc68020'            [ Not found ]
[10:58:57]   Checking for file '/usr/ucb/bin/ps'             [ Not found ]
[10:58:57]   Checking for file '/usr/bin/m68k'               [ Not found ]
[10:58:57]   Checking for file '/usr/bin/sun2'               [ Not found ]
[10:58:57]   Checking for file '/usr/bin/mc68030'            [ Not found ]
[10:58:57]   Checking for file '/usr/bin/mc68040'            [ Not found ]
[10:58:57]   Checking for file '/usr/bin/sun3'               [ Not found ]
[10:58:57]   Checking for file '/usr/bin/sun3x'              [ Not found ]
[10:58:57]   Checking for file '/usr/bin/lso'                [ Not found ]
[10:58:58]   Checking for file '/usr/bin/u370'               [ Not found ]
[10:58:58]   Checking for directory '/dev/pts/01'            [ Not found ]
[10:58:58]   Checking for directory '/dev/prom'              [ Not found ]
[10:58:58]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[10:58:58]   Checking for directory '/.pat'                  [ Not found ]
[10:58:58] SunOS / NSDAP Rootkit                             [ Not found ]
[10:58:58]
[10:58:58] Checking for Superkit Rootkit...
[10:58:58]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[10:58:58]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[10:58:58]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[10:58:58]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[10:58:58]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[10:58:58] Superkit Rootkit                                  [ Not found ]
[10:58:58]
[10:58:58] Checking for TBD (Telnet BackDoor)...
[10:58:58]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[10:58:58] TBD (Telnet BackDoor)                             [ Not found ]
[10:58:58]
[10:58:58] Checking for TeLeKiT Rootkit...
[10:58:58]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[10:58:58]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[10:58:58]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[10:58:58]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[10:58:58]   Checking for file '/dev/ptyr'                   [ Not found ]
[10:58:58]   Checking for file '/dev/ptyp'                   [ Not found ]
[10:58:58]   Checking for file '/dev/ptyq'                   [ Not found ]
[10:58:58]   Checking for file '/dev/hda06'                  [ Not found ]
[10:58:58]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[10:58:58]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[10:58:58]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[10:58:58]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[10:58:58] TeLeKiT Rootkit                                   [ Not found ]
[10:58:58]
[10:58:58] Checking for T0rn Rootkit...
[10:58:58]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[10:58:58]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[10:58:58]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[10:58:58]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[10:58:59]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[10:58:59]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[10:58:59]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[10:58:59]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[10:58:59]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[10:58:59]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[10:58:59]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[10:58:59]   Checking for directory '/dev/.lib'              [ Not found ]
[10:58:59]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[10:58:59]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[10:58:59]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[10:58:59]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[10:58:59]   Checking for directory '/usr/src/.puta'         [ Not found ]
[10:58:59]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[10:58:59]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[10:58:59]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[10:59:00]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[10:59:00] T0rn Rootkit                                      [ Not found ]
[10:59:00]
[10:59:00] Checking for trNkit Rootkit...
[10:59:00]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[10:59:00]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[10:59:00]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[10:59:00] trNkit Rootkit                                    [ Not found ]
[10:59:00]
[10:59:00] Checking for Trojanit Kit...
[10:59:00]   Checking for file '/bin/.ls'                    [ Not found ]
[10:59:00]   Checking for file '/bin/.ps'                    [ Not found ]
[10:59:00]   Checking for file '/bin/.netstat'               [ Not found ]
[10:59:00]   Checking for file '/usr/bin/.nop'               [ Not found ]
[10:59:00]   Checking for file '/usr/bin/.who'               [ Not found ]
[10:59:00] Trojanit Kit                                      [ Not found ]
[10:59:00]
[10:59:00] Checking for Tuxtendo Rootkit...
[10:59:00]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[10:59:00]   Checking for file '/usr/bin/xchk'               [ Not found ]
[10:59:00]   Checking for file '/usr/bin/xsf'                [ Not found ]
[10:59:00]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[10:59:00]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:59:00]   Checking for file '/dev/tux/.cron'              [ Not found ]
[10:59:00]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:59:00]   Checking for file '/dev/tux/.log'               [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.iface'             [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.pw'                [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.df'                [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[10:59:01]   Checking for file '/dev/tux/.tux'               [ Not found ]
[10:59:01]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[10:59:01]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[10:59:01]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[10:59:01]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[10:59:01]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[10:59:01]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[10:59:01]   Checking for directory '/dev/tux'               [ Not found ]
[10:59:01]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[10:59:01]   Checking for directory '/dev/tux/backup'        [ Not found ]
[10:59:01] Tuxtendo Rootkit                                  [ Not found ]
[10:59:01]
[10:59:01] Checking for URK Rootkit...
[10:59:01]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[10:59:01]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[10:59:01]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[10:59:01]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[10:59:02]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[10:59:02]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[10:59:02]   Checking for file '/tmp/conf.inv'               [ Not found ]
[10:59:02]   Checking for directory '/dev/prom'              [ Not found ]
[10:59:02]   Checking for directory '/dev/pts/01'            [ Not found ]
[10:59:02]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[10:59:02]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[10:59:02] URK Rootkit                                       [ Not found ]
[10:59:02]
[10:59:02] Checking for Vampire Rootkit...
[10:59:02]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[10:59:03]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[10:59:03]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[10:59:03]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[10:59:03] Vampire Rootkit                                   [ Not found ]
[10:59:03]
[10:59:03] Checking for VcKit Rootkit...
[10:59:03]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[10:59:03]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[10:59:03] VcKit Rootkit                                     [ Not found ]
[10:59:03]
[10:59:03] Checking for Volc Rootkit...
[10:59:03]   Checking for file '/usr/bin/volc'               [ Not found ]
[10:59:03]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[10:59:03]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[10:59:03]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[10:59:03]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[10:59:03]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[10:59:03]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[10:59:03]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[10:59:03]   Checking for directory '/var/spool/.recent'     [ Not found ]
[10:59:03]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[10:59:03]   Checking for directory '/usr/lib/volc'          [ Not found ]
[10:59:03]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[10:59:03] Volc Rootkit                                      [ Not found ]
[10:59:03]
[10:59:03] Checking for Xzibit Rootkit...
[10:59:03]   Checking for file '/dev/dsx'                    [ Not found ]
[10:59:03]   Checking for file '/dev/caca'                   [ Not found ]
[10:59:03]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[10:59:03]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[10:59:03]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[10:59:03]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[10:59:04]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[10:59:04]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[10:59:04]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[10:59:04]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[10:59:04]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[10:59:04]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[10:59:04]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[10:59:04] Xzibit Rootkit                                    [ Not found ]
[10:59:04]
[10:59:04] Checking for X-Org SunOS Rootkit...
[10:59:04]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[10:59:04]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[10:59:04]   Checking for file '/usr/bin/srload'             [ Not found ]
[10:59:04]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[10:59:04]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[10:59:04]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[10:59:04]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[10:59:04]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[10:59:04]   Checking for directory '/usr/share/man...'      [ Not found ]
[10:59:04] X-Org SunOS Rootkit                               [ Not found ]
[10:59:04]
[10:59:04] Checking for zaRwT.KiT Rootkit...
[10:59:04]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[10:59:04]   Checking for file '/dev/ttyf'                   [ Not found ]
[10:59:04]   Checking for file '/dev/ttyp'                   [ Not found ]
[10:59:04]   Checking for file '/dev/ttyn'                   [ Not found ]
[10:59:04]   Checking for file '/rk/tulz'                    [ Not found ]
[10:59:04]   Checking for directory '/rk'                    [ Not found ]
[10:59:04]   Checking for directory '/dev/rd/s'              [ Not found ]
[10:59:04] zaRwT.KiT Rootkit                                 [ Not found ]
[10:59:04]
[10:59:04] Checking for ZK Rootkit...
[10:59:04]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[10:59:05]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[10:59:05]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[10:59:05]   Checking for file '/etc/1ssue.net'              [ Not found ]
[10:59:05]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[10:59:05]   Checking for directory '/usr/share/.zk'         [ Not found ]
[10:59:05]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[10:59:05] ZK Rootkit                                        [ Not found ]
[10:59:05]
[10:59:05] Performing additional rootkit checks
[10:59:05] Info: Starting test name 'additional_rkts'
[10:59:05]
[10:59:05]   Performing Suckit Rookit additional checks
[10:59:05]     Checking hard link count on '/sbin/init'      [ OK ]
[10:59:05]     Checking for hidden file extensions           [ None found ]
[10:59:05]     Running skdet command                         [ Skipped ]
[10:59:05] Info: Unable to find the 'skdet' command
[10:59:05]   Suckit Rookit additional checks                 [ OK ]
[10:59:05]
[10:59:05]   Performing check of possible rootkit files and directories
[10:59:05] Info: Starting test name 'possible_rkt_files'
[10:59:05]     Checking for file '/dev/sdr0'                 [ Not found ]
[10:59:05]     Checking for file '/dev/pisu'                 [ Not found ]
[10:59:05]     Checking for file '/dev/xdta'                 [ Not found ]
[10:59:05]     Checking for file '/dev/saux'                 [ Not found ]
[10:59:05]     Checking for file '/dev/hdx'                  [ Not found ]
[10:59:05]     Checking for file '/dev/hdx1'                 [ Not found ]
[10:59:05]     Checking for file '/dev/hdx2'                 [ Not found ]
[10:59:05]     Checking for file '/dev/ptyy'                 [ Not found ]
[10:59:05]     Checking for file '/dev/ptyu'                 [ Not found ]
[10:59:05]     Checking for file '/dev/ptyv'                 [ Not found ]
[10:59:05]     Checking for file '/dev/hdbb'                 [ Not found ]
[10:59:05]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[10:59:05]     Checking for file '/tmp/.bash_history'        [ Not found ]
[10:59:06]     Checking for file '/usr/info/.clib'           [ Not found ]
[10:59:06]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[10:59:06]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[10:59:06]     Checking for file '/sbin/create'              [ Not found ]
[10:59:06]     Checking for file '/dev/ttypz'                [ Not found ]
[10:59:06]     Checking for file '/var/log/tcp.log'          [ Not found ]
[10:59:06]     Checking for file '/usr/include/audit.h'      [ Not found ]
[10:59:06]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[10:59:06]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[10:59:06]     Checking for file '/dev/xmx'                  [ Not found ]
[10:59:06]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[10:59:06]     Checking for file '/bin/vobiscum'             [ Not found ]
[10:59:06]     Checking for file '/bin/psr'                  [ Not found ]
[10:59:06]     Checking for file '/dev/kdx'                  [ Not found ]
[10:59:06]     Checking for file '/dev/dkx'                  [ Not found ]
[10:59:06]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[10:59:06]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[10:59:06]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[10:59:06]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[10:59:06]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[10:59:06]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[10:59:06]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[10:59:06]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[10:59:06]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[10:59:06]     Checking for file '/tmp/.ush'                 [ Not found ]
[10:59:06]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[10:59:06]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[10:59:06]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[10:59:07]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[10:59:07]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[10:59:07]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[10:59:07]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[10:59:07]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[10:59:07]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[10:59:07]     Checking for directory '/dev/ptyas'           [ Not found ]
[10:59:07]     Checking for directory '/usr/bin/take'        [ Not found ]
[10:59:07]     Checking for directory '/usr/src/.lib'        [ Not found ]
[10:59:07]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[10:59:07]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[10:59:07]     Checking for directory '/usr/sbin/...'        [ Not found ]
[10:59:07]     Checking for directory '/usr/share/.gun'      [ Not found ]
[10:59:07]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[10:59:07]     Checking for directory '/usr/man/man1/..  /.dir' [ Not found ]
[10:59:07]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[10:59:07]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[10:59:07]     Checking for directory '/tmp/.sys'            [ Not found ]
[10:59:07]     Checking for directory '/tmp/''               [ Not found ]
[10:59:07]     Checking for directory '/tmp/.,'              [ Not found ]
[10:59:07]     Checking for directory '/tmp/,.,'             [ Not found ]
[10:59:07]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[10:59:07]     Checking for directory '/var/tmp/.log'        [ Not found ]
[10:59:07]     Checking for directory '/tmp/zmeu/... '       [ Not found ]
[10:59:07]     Checking for directory '/var/log/ssh'         [ Not found ]
[10:59:07]     Checking for directory '/dev/ida'             [ Not found ]
[10:59:07]     Checking for directory '/lib/java'            [ Not found ]
[10:59:07]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[10:59:08]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[10:59:08]     Checking for directory '/usr/src/.poop'       [ Not found ]
[10:59:08]     Checking for directory '/dev/wd4'             [ Not found ]
[10:59:08]     Checking for directory '/var/run/.tmp'        [ Not found ]
[10:59:08]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[10:59:08]     Checking for directory '/dev/portd'           [ Not found ]
[10:59:08]     Checking for directory '/dev/...'             [ Not found ]
[10:59:08]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[10:59:08]     Checking for directory '/lib/.so'             [ Not found ]
[10:59:08]     Checking for directory '/lib/.sso'            [ Not found ]
[10:59:08]   Checking for possible rootkit files and directories [ None found ]
[10:59:08]
[10:59:08]   Performing check for possible rootkit strings
[10:59:08] Info: Starting test name 'possible_rkt_strings'
[10:59:08] Info: Using system startup paths: /etc/rc.local /etc/init.d
[10:59:08]     Checking for string 'phalanx'                 [ Not found ]
[10:59:08]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:59:08]     Checking for string '****'                    [ Not found ]
[10:59:08]     Checking for string 'backdoor'                [ Not found ]
[10:59:08]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[10:59:08]     Checking for string '/usr/sbin/login'         [ Not found ]
[10:59:08]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[10:59:08]     Checking for string 'vt200'                   [ Not found ]
[10:59:08]     Checking for string '/usr/bin/xstat'          [ Not found ]
[10:59:08]     Checking for string '/bin/envpc'              [ Not found ]
[10:59:09]     Checking for string 'L4m3r0x'                 [ Not found ]
[10:59:09]     Checking for string '/lib/libext'             [ Not found ]
[10:59:09]     Checking for string '/usr/sbin/login'         [ Not found ]
[10:59:09]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:59:09]     Checking for string 'sendmail'                [ Not found ]
[10:59:09]     Checking for string 'cocacola'                [ Not found ]
[10:59:09]     Checking for string 'joao'                    [ Not found ]
[10:59:09]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[10:59:09]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[10:59:09]     Checking for string '/dev/sgk'                [ Not found ]
[10:59:09]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:59:09]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:59:09]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:59:09]     Checking for string '/lib/.sso'               [ Not found ]
[10:59:09]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:59:09]     Checking for string '/dev/caca'               [ Not found ]
[10:59:09]     Checking for string '/dev/ttyoa'              [ Not found ]
[10:59:09]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[10:59:09]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[10:59:09]     Checking for string 'syg'                     [ Not found ]
[10:59:10]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:59:10]     Checking for string '/dev/pts/01'             [ Not found ]
[10:59:10]     Checking for string 'tw33dl3'                 [ Not found ]
[10:59:10]     Checking for string 'psniff'                  [ Not found ]
[10:59:10]     Checking for string 'uconf.inv'               [ Not found ]
[10:59:10]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[10:59:10]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[10:59:10]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:59:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:10]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[10:59:10]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[10:59:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:10]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:10]     Checking for string '/bin/bash'               [ Not found ]
[10:59:10]     Checking for string '/dev/xdta'               [ Not found ]
[10:59:10]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:59:10]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[10:59:11]     Checking for string 'in.inetd'                [ Not found ]
[10:59:11]     Checking for string '#<HIDE_.*>'              [ Not found ]
[10:59:12]     Checking for string 'bin/xchk'                [ Not found ]
[10:59:12]     Checking for string 'bin/xsf'                 [ Not found ]
[10:59:12]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[10:59:13]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[10:59:13]     Checking for string 'ttyload'                 [ Not found ]
[10:59:13]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[10:59:14]     Checking for string 'usr/bin/xfss'            [ Not found ]
[10:59:14]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[10:59:14]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[10:59:15]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[10:59:15]     Checking for string '/ssh2d'                  [ Not found ]
[10:59:15]     Checking for string '/dev/kmod'               [ Not found ]
[10:59:16]     Checking for string '/crth.o'                 [ Not found ]
[10:59:16]     Checking for string '/crtz.o'                 [ Not found ]
[10:59:17]     Checking for string '/dev/dos'                [ Not found ]
[10:59:17]     Checking for string '/lpq'                    [ Not found ]
[10:59:17]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[10:59:18]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[10:59:18]     Checking for string '/volc'                   [ Not found ]
[10:59:18]     Checking for string 'sourcemask'              [ Not found ]
[10:59:19]     Checking for string '/bin/vobiscum'           [ Not found ]
[10:59:19]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[10:59:19]     Checking for string 'hdparm'                  [ Not found ]
[10:59:19]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[10:59:19]     Checking for string 't0rnkit'                 [ Not found ]
[10:59:20]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:59:20]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:20]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:20]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:20]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[10:59:20]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[10:59:20]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[10:59:20]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[10:59:20]     Checking for string '/dev/ida/.inet'          [ Not found ]
[10:59:20]   Checking for possible rootkit strings           [ None found ]
[10:59:20]
[10:59:20] Performing malware checks
[10:59:20] Info: Starting test name 'malware'
[10:59:20]
[10:59:20] Info: Test 'deleted_files' disabled at users request.
[10:59:20] Info: Starting test name 'running_procs'
[10:59:21]   Checking running processes for suspicious files [ None found ]
[10:59:21]
[10:59:21] Info: Test 'hidden_procs' disabled at users request.
[10:59:21]
[10:59:21] Info: Test 'suspscan' disabled at users request.
[10:59:21]
[10:59:21]   Performing check for login backdoors
[10:59:21] Info: Starting test name 'other_malware'
[10:59:21]     Checking for '/bin/.login'                    [ Not found ]
[10:59:21]     Checking for '/sbin/.login'                   [ Not found ]
[10:59:21]   Checking for login backdoors                    [ None found ]
[10:59:21]
[10:59:21]   Performing check for suspicious directories
[10:59:21]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[10:59:21]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[10:59:21]   Checking for suspicious directories             [ None found ]
[10:59:21]
[10:59:21]   Checking for software intrusions                [ Skipped ]
[10:59:21] Info: Check skipped - tripwire not installed
[10:59:21]
[10:59:21]   Performing check for sniffer log files
[10:59:21]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[10:59:21]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[10:59:21]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[10:59:21]   Checking for sniffer log files                  [ None found ]
[10:59:21]
[10:59:21] Performing trojan specific checks
[10:59:21] Info: Starting test name 'trojans'
[10:59:21]   Checking for enabled inetd services             [ Skipped ]
[10:59:21] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[10:59:21]
[10:59:21]   Performing check for enabled xinetd services
[10:59:21]   Checking for enabled xinetd services            [ Skipped ]
[10:59:21] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[10:59:21] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[10:59:21]
[10:59:21] Performing Linux specific checks
[10:59:21] Info: Starting test name 'os_specific'
[10:59:21]   Checking loaded kernel modules                  [ OK ]
[10:59:22] Info: Using modules pathname of '/lib/modules/2.6.38-11-generic-pae'
[10:59:22]   Checking kernel module names                    [ OK ]
[10:59:28]
[10:59:28] Checking the network...
[10:59:28] Info: Starting test name 'network'
[10:59:28] Info: Starting test name 'ports'
[10:59:28]
[10:59:28] Performing check for backdoor ports
[10:59:28]   Checking for TCP port 1524                      [ Not found ]
[10:59:28]   Checking for TCP port 1984                      [ Not found ]
[10:59:28]   Checking for UDP port 2001                      [ Not found ]
[10:59:28]   Checking for TCP port 2006                      [ Not found ]
[10:59:28]   Checking for TCP port 2128                      [ Not found ]
[10:59:28]   Checking for TCP port 6666                      [ Not found ]
[10:59:29]   Checking for TCP port 6667                      [ Not found ]
[10:59:29]   Checking for TCP port 6668                      [ Not found ]
[10:59:29]   Checking for TCP port 6669                      [ Not found ]
[10:59:29]   Checking for TCP port 7000                      [ Not found ]
[10:59:29]   Checking for TCP port 13000                     [ Not found ]
[10:59:29]   Checking for TCP port 14856                     [ Not found ]
[10:59:29]   Checking for TCP port 25000                     [ Not found ]
[10:59:29]   Checking for TCP port 29812                     [ Not found ]
[10:59:29]   Checking for TCP port 31337                     [ Not found ]
[10:59:29]   Checking for TCP port 33369                     [ Not found ]
[10:59:29]   Checking for TCP port 47107                     [ Not found ]
[10:59:30]   Checking for TCP port 47018                     [ Not found ]
[10:59:30]   Checking for TCP port 60922                     [ Not found ]
[10:59:30]   Checking for TCP port 62883                     [ Not found ]
[10:59:30]   Checking for TCP port 65535                     [ Not found ]
[10:59:30]
[10:59:30] Performing checks on the network interfaces
[10:59:30] Info: Starting test name 'promisc'
[10:59:30]   Checking for promiscuous interfaces             [ None found ]
[10:59:30]
[10:59:30] Info: Test 'packet_cap_apps' disabled at users request.
[10:59:32]
[10:59:32] Checking the local host...
[10:59:32] Info: Starting test name 'local_host'
[10:59:32]
[10:59:32] Performing system boot checks
[10:59:32] Info: Starting test name 'startup_files'
[10:59:32]   Checking for local host name                    [ Found ]
[10:59:32] Info: Starting test name 'startup_malware'
[10:59:32]   Checking for system startup files               [ Found ]
[10:59:33]   Checking system startup files for malware       [ None found ]
[10:59:33]
[10:59:33] Performing group and account checks
[10:59:33] Info: Starting test name 'group_accounts'
[10:59:33]   Checking for passwd file                        [ Found ]
[10:59:33] Info: Found password file: /etc/passwd
[10:59:33]   Checking for root equivalent (UID 0) accounts   [ None found ]
[10:59:33] Info: Found shadow file: /etc/shadow
[10:59:33]   Checking for passwordless accounts              [ None found ]
[10:59:33] Info: Starting test name 'passwd_changes'
[10:59:33]   Checking for passwd file changes                [ Warning ]
[10:59:33] Warning: User 'clamav' has been added to the passwd file.
[10:59:33] Info: Starting test name 'group_changes'
[10:59:33]   Checking for group file changes                 [ Warning ]
[10:59:33] Warning: Group 'clamav' has been added to the group file.
[10:59:33]   Checking root account shell history files       [ None found ]
[10:59:33]
[10:59:33] Performing system configuration file checks
[10:59:33] Info: Starting test name 'system_configs'
[10:59:33]   Checking for SSH configuration file             [ Not found ]
[10:59:33]   Checking for running syslog daemon              [ Found ]
[10:59:33]   Checking for syslog configuration file          [ Found ]
[10:59:33] Info: Found syslog configuration file: /etc/rsyslog.conf
[10:59:33]   Checking if syslog remote logging is allowed    [ Not allowed ]
[10:59:33]
[10:59:33] Performing filesystem checks
[10:59:33] Info: Starting test name 'filesystem'
[10:59:33] Info: SCAN_MODE_DEV set to 'THOROUGH'
[10:59:34]   Checking /dev for suspicious file types         [ Warning ]
[10:59:34] Warning: Suspicious file types found in /dev:
[10:59:34]          /dev/shm/pulse-shm-2269265650: data
[10:59:34]          /dev/shm/pulse-shm-4087342566: data
[10:59:34]          /dev/shm/pulse-shm-160317889: data
[10:59:34]          /dev/shm/pulse-shm-3526516004: AmigaOS bitmap font
[10:59:34]          /dev/shm/pulse-shm-1996965821: data
[10:59:35]   Checking for hidden files and directories       [ Warning ]
[10:59:35] Warning: Hidden directory found: /etc/.java
[10:59:35] Warning: Hidden directory found: /dev/.udev
[10:59:35] Warning: Hidden directory found: /dev/.initramfs
[10:59:40]
[10:59:40] Info: Test 'apps' disabled at users request.
[10:59:40]
[10:59:40] System checks summary
[10:59:41] =====================
[10:59:41]
[10:59:41] File properties checks...
[10:59:41] Files checked: 133
[10:59:41] Suspect files: 2
[10:59:41]
[10:59:41] Rootkit checks...
[10:59:41] Rootkits checked : 242
[10:59:41] Possible rootkits: 0
[10:59:41]
[10:59:41] Applications checks...
[10:59:41] All checks skipped
[10:59:41]
[10:59:41] The system checks took: 1 minute and 36 seconds
[10:59:41]
[10:59:41] Info: End date is Tue Oct 11 10:59:41 PDT 2011
```

---

### Post by Steam. on 2011-10-11
Please put it in code tags so people won't have to scroll down?

---

### Post by Dangertux on 2011-10-11
Based on that I would say there is nothing conclusive to say your system has a rootkit on it. 

However if I am reading the error correctly the LD_PRELOAD variable is set to a path that is not present. LD_PRELOAD can be used by rootkits to hook certain system calls. That being said the LD_PRELOAD variable may just not be set, or set to a library that no longer exists. Suspicion arises in that a rootkit would likely hide the path for whatever library was being preloaded. So you should verify it manually.

You can verify where it is pointing by doing the following and looking for LD_PRELOAD=

```

printenv | grep LD_PRELOAD=

```

Hope that helps

---

### Post by mxndrwgrdnr on 2011-10-11
@steam. sorry about the lack of code tags.

@dangertux thanks for the help...maybe I'm missing something, though. I entered your code into the terminal, but I'm not sure how to look for the file. The ubuntu Search for File GUI doesn't seem to be able to find anything but I'm not sure it's doing a thorough search of my whole machine. Is there an easier way to search in the command line?

---

### Post by conundrumx on 2011-10-11
What was the output from Dangertux's command?

Your system looks clean, I doubt you have a rootkit.

---

### Post by mxndrwgrdnr on 2011-10-11
was no output. 

i agree it looks like i'm clean, but there's really no way to know for sure is there without doing a complete re-install?

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> was no output. 

i agree it looks like i'm clean, but there's really no way to know for sure is there without doing a complete re-install?

If there was no output it just means that the LD_PRELOAD variable is not set in your environment. This is fine, if you would like a more broad view of the environment to make sure that no other odd variables are set just do the following

```

printenv

```

You may also want to do it for your root environment by prepending sudo to the command, also you may wish to check the following file /etc/ld.so.conf and /etc/ld.so.conf.d/libc.conf if there seems to be anything out of place or recent modifications to any files you may wish to let us know.

On another note what exactly do you mean by a google redirect? 

Hope that helps

---

### Post by mxndrwgrdnr on 2011-10-11
you've been very helpful, dangertux. printev outputs the following:
```
max@max-ThinkPad-T400:~$ printenv
ORBIT_SOCKETDIR=/tmp/orbit-max
SSH_AGENT_PID=1362
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=79c3318659f73fded88617990000000a-1318302469.621251-1841676489
WINDOWID=73433305
GNOME_KEYRING_CONTROL=/tmp/keyring-oykQWl
GTK_MODULES=canberra-gtk-module
USER=max
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
SSH_AUTH_SOCK=/tmp/keyring-oykQWl/ssh
SESSION_MANAGER=local/max-ThinkPad-T400:@/tmp/.ICE-unix/1327,unix/max-ThinkPad-T400:/tmp/.ICE-unix/1327
USERNAME=max
DEFAULTS_PATH=/usr/share/gconf/gnome-classic.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-classic:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=gnome-classic
PWD=/home/max
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GDM_LANG=en_US.utf8
MANDATORY_PATH=/usr/share/gconf/gnome-classic.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
GDMSESSION=gnome-classic
SHLVL=1
HOME=/home/max
LANGUAGE=en_US:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=max
XDG_DATA_DIRS=/usr/share/gnome-classic:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-UoGT1krY7L,guid=d983540f668ee27cfffb717b00000018
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-max-hMmpnE/database
_=/usr/bin/printenv
```

and sudo printev outputs the following:
```
max@max-ThinkPad-T400:~$ sudo printenv
[sudo] password for max: 
TERM=xterm
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
LANG=en_US.UTF-8
HOME=/home/max
LANGUAGE=en_US:en
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-max-hMmpnE/database
SHELL=/bin/bash
LOGNAME=root
USER=root
USERNAME=root
MAIL=/var/mail/root
SUDO_COMMAND=/usr/bin/printenv
SUDO_USER=max
SUDO_UID=1000
SUDO_GID=1000
```

ld.so.conf.d (this is a directory, there is no file named ld.so.conf in /etc/) contains only 4 files: GL.conf, i686-linux-gnu.conf, libasound2.conf, and libc.conf. And libc.conf reads ```
# libc default configuration
/usr/local/lib
```Seems normal to me, but I wouldn't know what abnormal would look like either.

The google redirect I was referring to was an issue I was having where any time I attempted to use a google service, either the search in my chromium address bar, or by manually entering [http://www.google.com](http://www.google.com) in the address bar, or clicking my gmail bookmark, I would either be redirected to some "wikimedia" website or would receive a 404 error. These were the only symptoms of a virus I had, and after doing research it seemed like the Google redirects were typically associated with a rootkit infection.

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> you've been very helpful, dangertux. printev outputs the following:
```
max@max-ThinkPad-T400:~$ printenv
ORBIT_SOCKETDIR=/tmp/orbit-max
SSH_AGENT_PID=1362
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=79c3318659f73fded88617990000000a-1318302469.621251-1841676489
WINDOWID=73433305
GNOME_KEYRING_CONTROL=/tmp/keyring-oykQWl
GTK_MODULES=canberra-gtk-module
USER=max
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
SSH_AUTH_SOCK=/tmp/keyring-oykQWl/ssh
SESSION_MANAGER=local/max-ThinkPad-T400:@/tmp/.ICE-unix/1327,unix/max-ThinkPad-T400:/tmp/.ICE-unix/1327
USERNAME=max
DEFAULTS_PATH=/usr/share/gconf/gnome-classic.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-classic:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=gnome-classic
PWD=/home/max
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GDM_LANG=en_US.utf8
MANDATORY_PATH=/usr/share/gconf/gnome-classic.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
GDMSESSION=gnome-classic
SHLVL=1
HOME=/home/max
LANGUAGE=en_US:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=max
XDG_DATA_DIRS=/usr/share/gnome-classic:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-UoGT1krY7L,guid=d983540f668ee27cfffb717b00000018
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-max-hMmpnE/database
_=/usr/bin/printenv
```and sudo printev outputs the following:
```
max@max-ThinkPad-T400:~$ sudo printenv
[sudo] password for max: 
TERM=xterm
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
LANG=en_US.UTF-8
HOME=/home/max
LANGUAGE=en_US:en
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-max-hMmpnE/database
SHELL=/bin/bash
LOGNAME=root
USER=root
USERNAME=root
MAIL=/var/mail/root
SUDO_COMMAND=/usr/bin/printenv
SUDO_USER=max
SUDO_UID=1000
SUDO_GID=1000
```ld.so.conf.d (this is a directory, there is no file named ld.so.conf in /etc/) contains only 4 files: GL.conf, i686-linux-gnu.conf, libasound2.conf, and libc.conf. And libc.conf reads ```
# libc default configuration
/usr/local/lib
```Seems normal to me, but I wouldn't know what abnormal would look like either.

The google redirect I was referring to was an issue I was having where any time I attempted to use a google service, either the search in my chromium address bar, or by manually entering [http://www.google.com](http://www.google.com) in the address bar, or clicking my gmail bookmark, I would either be redirected to some "wikimedia" website or would receive a 404 error. These were the only symptoms of a virus I had, and after doing research it seemed like the Google redirects were typically associated with a rootkit infection.

That output looks fine, odd the symptoms you are describing are related to a Windows based browser jacking method. It is known in the Windows version of Google Chrome.

Could you post the contents of /etc/hosts?

---

### Post by mxndrwgrdnr on 2011-10-11
```
max@max-ThinkPad-T400:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	max-ThinkPad-T400

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> ```
max@max-ThinkPad-T400:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    max-ThinkPad-T400

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Ok that's fine , next question are you using Google Chrome or Chromium?

If you are using chromium ; I would recommend backing up any bookmarks you may have and removing it via 

```

sudo apt-get remove -f --purge chromium-browser

```then reinstalling.

If you are using chrome you can simply uninstall it then insure the files in /home/username/.config/chrome are removed.

Alternatively you can go through the files in /home/username/.config/chrome(chromium) particularly 

Local State
/Default/Web Data
/Default/Preferences

*substitute default for your profile name.

to see if there are any oddities there. (Do not post their contents).

I would just choose the reinstall of Chrome/ium 

Also you may wish to make sure you're using version : [FONT=Arial]14.0.835.202[/FONT]
hope this helps.

---

### Post by mxndrwgrdnr on 2011-10-11
Checked in those directories for anything suspicious and nothing really stood out...again, I could just not know what to look for. Anyways I then removed and re-installed chromium to be safe, although somehow the new chromium found the bookmarks from my last chromium without me directing it there? Is that possible? I saved the bookmarks.html file to my desktop before removing chromium.

Anyways, I guess it would seem as though I'm in the clear. Still a bit nervous though about entering passwords, etc into my machine if there's a risk that I do in fact have a rootkit. Think it's going overboard to wipe the hdd just because of the problems I was having with Google?

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> Checked in those directories for anything suspicious and nothing really stood out...again, I could just not know what to look for. Anyways I then removed and re-installed chromium to be safe, although somehow the new chromium found the bookmarks from my last chromium without me directing it there? Is that possible? I saved the bookmarks.html file to my desktop before removing chromium.

Anyways, I guess it would seem as though I'm in the clear. Still a bit nervous though about entering passwords, etc into my machine if there's a risk that I do in fact have a rootkit. Think it's going overboard to wipe the hdd just because of the problems I was having with Google?

Without having access to your system myself I can't speak with 100% certainty to say you're safe however I can say with a decent amount of certainty that what you experienced was not a rootkit but a browser jacking method addressed in recent security patches (~oct 4thish).

I really don't believe your system is rooted, if anything Chromium may still be compromised. However the only way to be certain is completely wipe.

I personally wouldn't -- however, it is ultimately your decision. If you don't have a ton of data to back up , and it would be relatively quick (couple of hours or so) I would do it just to give yourself peace of mind.

---

### Post by mxndrwgrdnr on 2011-10-11
OK, I guess I'm going to leave it be for now. But you bring up an interesting question, which is if I DID wan't to wipe a possibly compromised hdd, but also back up my files, how can I be sure that the data I'm backing up doesn't contain an element of the rootkit as well? Thanks for all of the help, though, really.

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> OK, I guess I'm going to leave it be for now. But you bring up an interesting question, which is if I DID wan't to wipe a possibly compromised hdd, but also back up my files, how can I be sure that the data I'm backing up doesn't contain an element of the rootkit as well? Thanks for all of the help, though, really.

As I stated already I don't believe there is a root kit. A root kit is a very specific thing, not another generic term like malware. That being said we will assume for a minute that there is a root kit.

Which brings you into root kit methodology , which requires you understand a little about a root kit's priorities , and what it must do.  These are the goals of most root kits in order of importance.


1 - Make sure it survives a reboot. Either by hooking system calls, or the kernel itself. Also rc.local is often hooked. 

2 - Backdoor the system allowing access to the owner of the root kit, or whatever else knows about it.

3 - Hide itself, from AV, anti-malware, IDS and anything else that might be trying to find it.

4 - Download or install auxilliary code ,  usually along the lines of keyloggers, or an application that recovers SSH keys or other types of credentials.

What you will notice MOST root kits do not do, is mess with your browser. The reason is, that is a REALLY good way to get noticed, a root kit doesn't want to be noticed. Once it's noticed game is over, root kit will be removed. 

IF you did have a rootkit installed on your system, it will be affecting very specific files, and will not be messing with anything that isn't executable, and or a share object/library. So ultimately as long as you're backing up your data and not executable files you shouldn't have to worry about a rootkit persisting through a complete wipe.

That being said, the only way to be sure is to destroy it all. Again, I reiterate, this is probably NOT what happened to you, so I wouldn't go destroying all your data out of fear.

---

### Post by mxndrwgrdnr on 2011-10-11
Got it. Thanks for all the help. You, sir, are a gentleman.

---

### Post by Dangertux on 2011-10-11
> **mxndrwgrdnr said:**
> Got it. Thanks for all the help. You, sir, are a gentleman.

Well , thank you for the very flattering words. Glad I could be helpful :-)

---

