---
title: "Possibly Comprimised, Advice?"
date: 2007-10-23
forum: Server Platforms
---

### Post by Falcorian on 2007-10-23
So we run linux at work, and our main processing machine isl WORKMAIN, which I ssh to from my desk on WORKTERM. I run Ubuntu 7.10 64AMD at home, on HOME.

Today, the IT guys at work sent out an email saying some of the following things:

> 
From forensics on disk of WORKMAIN, I believe the following additional accounts to be compromised:

Myaccount

at various systems, some not at work.

rd.c was used to crudely encrypt the credentials stolen via trojan sshd & ssh installed by the hackers - it can be used to decrypt the stolen credentials as well.


To be more precise, the following credentials were sniffed from WORKMAIN (some inbound, some outbound, difficult to be sure which is which, since both ssh & sshd were trojaned):

Myaccount@WORKTERM
Myaccount@HOME
Myaccount@some_random_university_computer_I_used


So, I use an RSA key on WORKMAIN to ssh to HOME, which I -- out of laziness -- I used the same password for as for the log ons for HOME, WORKMAIN, and WORKTERM. So, if someone got my work password, they can get root on my home box. (Yeah... I won't be doing that again...)

Obviously I've nuked the RSA key, but... What now? Anything I should ask the IT guys for clarification? Anything I should check here (and what about my seldom used Windows partition, which Linux has full RW on)? Is a full reformat the only sure way, and if so, what stuff can I keep?

Thanks all, I could really use the advice. :(

---

### Post by Falcorian on 2007-10-23
I loaded up a trusted Live CD, mounted my / from my machine and ran rkhunter, which gave me as follows:

```
[05:44:32] Running Rootkit Hunter version 1.3.0 on ubuntu
[05:44:32]
[05:44:32] Info: Start date is Tue Oct 23 05:44:32 UTC 2007
[05:44:32]
[05:44:32] Checking configuration file and command-line options...
[05:44:32] Info: Detected operating system is 'Linux'
[05:44:32] Info: Found O/S name: Ubuntu 7.10
[05:44:32] Info: Command line is /usr/bin/rkhunter --rootdir /media/root/ -c
[05:44:32] Info: Environment shell is /bin/bash; rkhunter is using dash
[05:44:32] Info: Using configuration file '/etc/rkhunter.conf'
[05:44:32] Info: Installation directory is '/usr'
[05:44:32] Info: Using language 'en'
[05:44:32] Info: Using '/var/lib/rkhunter/db' as the database directory
[05:44:32] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[05:44:32] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/games /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[05:44:32] Info: Using '/media/root/' as the root directory
[05:44:32] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[05:44:32] Info: No mail-on-warning address configured
[05:44:32] Info: X will automatically be detected
[05:44:32] Info: Using second color set
[05:44:32] Info: Found the 'diff' command: /usr/bin/diff
[05:44:32] Info: Found the 'file' command: /usr/bin/file
[05:44:32] Info: Found the 'find' command: /usr/bin/find
[05:44:32] Info: Found the 'ifconfig' command: /sbin/ifconfig
[05:44:32] Info: Found the 'ip' command: /sbin/ip
[05:44:32] Info: Found the 'ldd' command: /usr/bin/ldd
[05:44:32] Info: Found the 'lsattr' command: /usr/bin/lsattr
[05:44:32] Info: Found the 'lsmod' command: /sbin/lsmod
[05:44:32] Info: Found the 'lsof' command: /usr/bin/lsof
[05:44:32] Info: Found the 'mktemp' command: /bin/mktemp
[05:44:32] Info: Found the 'netstat' command: /bin/netstat
[05:44:32] Info: Found the 'perl' command: /usr/bin/perl
[05:44:32] Info: Found the 'ps' command: /bin/ps
[05:44:32] Info: Found the 'pwd' command: /bin/pwd
[05:44:32] Info: Found the 'readlink' command: /bin/readlink
[05:44:32] Info: Found the 'sort' command: /usr/bin/sort
[05:44:32] Info: Found the 'stat' command: /usr/bin/stat
[05:44:32] Info: Found the 'strings' command: /usr/bin/strings
[05:44:32] Info: Found the 'uniq' command: /usr/bin/uniq
[05:44:32] Info: System is not using prelinking
[05:44:32] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[05:44:32] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[05:44:32] Info: Stored hash values did not use a package manager
[05:44:32] Info: The hash function field index is set to 1
[05:44:32] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[05:44:32] Info: Previous file attributes were stored
[05:44:32] Info: Enabled tests are: all
[05:44:32] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[05:44:32] Info: All ksyms and kallsyms checks will be skipped - neither file is present on the system.
[05:44:32]
[05:44:32] Checking if the O/S has changed since last time...
[05:44:32] Info: Nothing seems to have changed
[05:44:33]
[05:44:33] Starting system checks...
[05:44:33]
[05:44:33] Checking system commands...
[05:44:33] Info: Starting test name 'system_commands'
[05:44:33]
[05:44:33] Performing 'strings' command checks
[05:44:33] Info: Starting test name 'strings'
[05:44:33] Scanning for string /usr/sbin/ntpsx               [ OK ]
[05:44:33] Scanning for string /usr/lib/.../ls               [ OK ]
[05:44:33] Scanning for string /usr/lib/.../netstat          [ OK ]
[05:44:33] Scanning for string /usr/lib/.../lsof             [ OK ]
[05:44:33] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[05:44:33] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[05:44:33] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[05:44:33] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[05:44:33] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[05:44:33] Scanning for string /usr/lib/.../psr              [ OK ]
[05:44:33] Scanning for string /usr/lib/.../find             [ OK ]
[05:44:33] Scanning for string /usr/lib/.../pstree           [ OK ]
[05:44:33] Scanning for string /usr/lib/.../slocate          [ OK ]
[05:44:33] Scanning for string /usr/lib/.../du               [ OK ]
[05:44:33] Scanning for string /usr/lib/.../top              [ OK ]
[05:44:33] Scanning for string /usr/lib/...                  [ OK ]
[05:44:33] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[05:44:33] Scanning for string /usr/lib/.bkit-               [ OK ]
[05:44:33] Scanning for string /tmp/.bkp                     [ OK ]
[05:44:33] Scanning for string /tmp/.cinik                   [ OK ]
[05:44:33] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[05:44:33] Scanning for string /lib/.sso                     [ OK ]
[05:44:33] Scanning for string /lib/.so                      [ OK ]
[05:44:33] Scanning for string /var/run/...dica/clean        [ OK ]
[05:44:33] Scanning for string /var/run/...dica/xl           [ OK ]
[05:44:33] Scanning for string /var/run/...dica/xdr          [ OK ]
[05:44:33] Scanning for string /var/run/...dica/psg          [ OK ]
[05:44:33] Scanning for string /var/run/...dica/secure       [ OK ]
[05:44:33] Scanning for string /var/run/...dica/rdx          [ OK ]
[05:44:33] Scanning for string /var/run/...dica/va           [ OK ]
[05:44:33] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[05:44:33] Scanning for string /usr/bin/.etc                 [ OK ]
[05:44:33] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[05:44:33] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[05:44:33] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[05:44:33] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[05:44:33] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[05:44:33] Scanning for string /bin/sysback                  [ OK ]
[05:44:33] Scanning for string /usr/local/bin/sysback        [ OK ]
[05:44:33] Scanning for string /usr/lib/.tbd                 [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[05:44:33] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[05:44:34] Scanning for string /usr/info/.torn/sh*           [ OK ]
[05:44:34] Scanning for string /usr/src/.****/.1addr         [ OK ]
[05:44:34] Scanning for string /usr/src/.****/.1file         [ OK ]
[05:44:34] Scanning for string /usr/src/.****/.1proc         [ OK ]
[05:44:34] Scanning for string /usr/src/.****/.1logz         [ OK ]
[05:44:34] Scanning for string /usr/info/.t0rn               [ OK ]
[05:44:34] Scanning for string /dev/.lib                     [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib                 [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib             [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[05:44:34] Scanning for string /dev/.lib/lib/scan            [ OK ]
[05:44:34] Scanning for string /usr/src/.****                [ OK ]
[05:44:34] Scanning for string /usr/man/man1/man1            [ OK ]
[05:44:34] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[05:44:34] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[05:44:34] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[05:44:34]
[05:44:34] Performing 'shared libraries' checks
[05:44:34] Info: Starting test name 'shared_libs'
[05:44:34] Checking for preloading variables                 [ None found ]
[05:44:34] Checking for preload file                         [ Not found ]
[05:44:34] Info: Starting test name 'shared_libs_path'
[05:44:34] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[05:44:34]
[05:44:34] Performing file properties checks
[05:44:34] Info: Starting test name 'properties'
[05:44:34] Checking for prerequisites                        [ OK ]
[05:44:34] /media/root//bin/bash                             [ Warning ]
[05:44:34] Warning: The file properties have changed:
[05:44:34]          File: /media/root//bin/bash
[05:44:34]          Current inode: 640229    Stored inode: 200
[05:44:34] /media/root//bin/cat                              [ Warning ]
[05:44:34] Warning: The file properties have changed:
[05:44:34]          File: /media/root//bin/cat
[05:44:34]          Current inode: 640242    Stored inode: 359
[05:44:34] /media/root//bin/chmod                            [ Warning ]
[05:44:34] Warning: The file properties have changed:
[05:44:34]          File: /media/root//bin/chmod
[05:44:34]          Current inode: 640245    Stored inode: 227
[05:44:34] /media/root//bin/chown                            [ Warning ]
[05:44:34] Warning: The file properties have changed:
[05:44:34]          File: /media/root//bin/chown
[05:44:34]          Current inode: 640246    Stored inode: 226
[05:44:34] /media/root//bin/cp                               [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/cp
[05:44:35]          Current inode: 640247    Stored inode: 1444
[05:44:35] /media/root//bin/date                             [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/date
[05:44:35]          Current inode: 640250    Stored inode: 1422
[05:44:35] /media/root//bin/df                               [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/df
[05:44:35]          Current inode: 640253    Stored inode: 1669
[05:44:35] /media/root//bin/dmesg                            [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/dmesg
[05:44:35]          Current inode: 640255    Stored inode: 1708
[05:44:35] /media/root//bin/echo                             [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/echo
[05:44:35]          Current inode: 640257    Stored inode: 894
[05:44:35] /media/root//bin/ed                               [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/ed
[05:44:35]          Current inode: 640258    Stored inode: 14408
[05:44:35] /media/root//bin/egrep                            [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/egrep
[05:44:35]          Current inode: 640259    Stored inode: 1022
[05:44:35] Info: Found file '/media/root//bin/egrep': it is whitelisted for the 'script replacement' check.
[05:44:35] /media/root//bin/fgrep                            [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/fgrep
[05:44:35]          Current inode: 640262    Stored inode: 1027
[05:44:35] Info: Found file '/media/root//bin/fgrep': it is whitelisted for the 'script replacement' check.
[05:44:35] /media/root//bin/grep                             [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/grep
[05:44:35]          Current inode: 640266    Stored inode: 228
[05:44:35] /media/root//bin/ip                               [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/ip
[05:44:35]          Current inode: 640272    Stored inode: 2030
[05:44:35] /media/root//bin/kill                             [ Warning ]
[05:44:35] Warning: The file properties have changed:
[05:44:35]          File: /media/root//bin/kill
[05:44:36]          Current inode: 640274    Stored inode: 14409
[05:44:36] /media/root//bin/login                            [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/login
[05:44:36]          Current inode: 640280    Stored inode: 1724
[05:44:36] /media/root//bin/ls                               [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/ls
[05:44:36]          Current inode: 640281    Stored inode: 1622
[05:44:36] /media/root//bin/lsmod                            [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/lsmod
[05:44:36]          Current inode: 640282    Stored inode: 1763
[05:44:36] /media/root//bin/mktemp                           [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/mktemp
[05:44:36]          Current inode: 640288    Stored inode: 14405
[05:44:36] /media/root//bin/more                             [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/more
[05:44:36]          Current inode: 640289    Stored inode: 14410
[05:44:36] /media/root//bin/mount                            [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/mount
[05:44:36]          Current inode: 640290    Stored inode: 1295
[05:44:36] /media/root//bin/mv                               [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/mv
[05:44:36]          Current inode: 640294    Stored inode: 803
[05:44:36] /media/root//bin/netstat                          [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/netstat
[05:44:36]          Current inode: 640298    Stored inode: 1815
[05:44:36] /media/root//bin/ps                               [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/ps
[05:44:36]          Current inode: 640308    Stored inode: 14406
[05:44:36] /media/root//bin/pwd                              [ Warning ]
[05:44:36] Warning: The file properties have changed:
[05:44:36]          File: /media/root//bin/pwd
[05:44:36]          Current inode: 640309    Stored inode: 10253
[05:44:37] /media/root//bin/readlink                         [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/readlink
[05:44:37]          Current inode: 640311    Stored inode: 987
[05:44:37] /media/root//bin/sed                              [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/sed
[05:44:37]          Current inode: 640318    Stored inode: 551
[05:44:37] /media/root//bin/sh                               [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/sh
[05:44:37]          Current inode: 640323    Stored inode: 183
[05:44:37]          Current file modification time: 1192728578
[05:44:37]          Stored file modification time : 1192490257
[05:44:37] /media/root//bin/su                               [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/su
[05:44:37]          Current inode: 640328    Stored inode: 10236
[05:44:37] /media/root//bin/touch                            [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/touch
[05:44:37]          Current inode: 640334    Stored inode: 1348
[05:44:37] /media/root//bin/uname                            [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/uname
[05:44:37]          Current inode: 640338    Stored inode: 1293
[05:44:37] /media/root//bin/which                            [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/which
[05:44:37]          Current inode: 640343    Stored inode: 904
[05:44:37] Info: Found file '/media/root//bin/which': it is whitelisted for the 'script replacement' check.
[05:44:37] /media/root//bin/dash                             [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//bin/dash
[05:44:37]          Current inode: 640249    Stored inode: 184
[05:44:37] /media/root//usr/bin/awk                          [ Warning ]
[05:44:37] Warning: The file properties have changed:
[05:44:37]          File: /media/root//usr/bin/awk
[05:44:37]          Current inode: 2084905    Stored inode: 896
[05:44:37]          Current file modification time: 1192728601
[05:44:37]          Stored file modification time : 1192490224
[05:44:37] /media/root//usr/bin/basename                     [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/basename
[05:44:38]          Current inode: 2084907    Stored inode: 1710
[05:44:38] /media/root//usr/bin/chattr                       [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/chattr
[05:44:38]          Current inode: 2084977    Stored inode: 14411
[05:44:38] /media/root//usr/bin/curl                         [ Warning ]
[05:44:38] Warning: The file '/media/root//usr/bin/curl' exists on the system, but it is not present in the rkhunter.dat file.
[05:44:38] /media/root//usr/bin/cut                          [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/cut
[05:44:38]          Current inode: 2085019    Stored inode: 229
[05:44:38] /media/root//usr/bin/diff                         [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/diff
[05:44:38]          Current inode: 2085061    Stored inode: 1791
[05:44:38] /media/root//usr/bin/dirname                      [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/dirname
[05:44:38]          Current inode: 2085066    Stored inode: 1712
[05:44:38] /media/root//usr/bin/dpkg                         [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/dpkg
[05:44:38]          Current inode: 2085072    Stored inode: 946
[05:44:38] /media/root//usr/bin/dpkg-query                   [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/dpkg-query
[05:44:38]          Current inode: 2085074    Stored inode: 922
[05:44:38] /media/root//usr/bin/du                           [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/du
[05:44:38]          Current inode: 2085078    Stored inode: 1793
[05:44:38] /media/root//usr/bin/env                          [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/env
[05:44:38]          Current inode: 2085098    Stored inode: 1814
[05:44:38] /media/root//usr/bin/file                         [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/file
[05:44:38]          Current inode: 2085131    Stored inode: 14402
[05:44:38] /media/root//usr/bin/find                         [ Warning ]
[05:44:38] Warning: The file properties have changed:
[05:44:38]          File: /media/root//usr/bin/find
[05:44:38]          Current inode: 2085133    Stored inode: 269
[05:44:39] /media/root//usr/bin/GET                          [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/GET
[05:44:39]          Current inode: 2084853    Stored inode: 14412
[05:44:39]          Current file modification time: 1192728600
[05:44:39]          Stored file modification time : 1192490481
[05:44:39] /media/root//usr/bin/groups                       [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/groups
[05:44:39]          Current inode: 2085350    Stored inode: 1741
[05:44:39] Info: Found file '/media/root//usr/bin/groups': it is whitelisted for the 'script replacement' check.
[05:44:39] /media/root//usr/bin/head                         [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/head
[05:44:39]          Current inode: 2085389    Stored inode: 1009
[05:44:39] /media/root//usr/bin/id                           [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/id
[05:44:39]          Current inode: 2085425    Stored inode: 1743
[05:44:39] /media/root//usr/bin/killall                      [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/killall
[05:44:39]          Current inode: 2085448    Stored inode: 9862
[05:44:39] /media/root//usr/bin/last                         [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/last
[05:44:39]          Current inode: 2085451    Stored inode: 14414
[05:44:39] /media/root//usr/bin/lastlog                      [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/lastlog
[05:44:39]          Current inode: 2085453    Stored inode: 14415
[05:44:39] /media/root//usr/bin/ldd                          [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/ldd
[05:44:39]          Current inode: 2085458    Stored inode: 1813
[05:44:39] Info: Found file '/media/root//usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[05:44:39] /media/root//usr/bin/less                         [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/less
[05:44:39]          Current inode: 2085459    Stored inode: 1797
[05:44:39] /media/root//usr/bin/locate                       [ Warning ]
[05:44:39] Warning: The file properties have changed:
[05:44:39]          File: /media/root//usr/bin/locate
[05:44:39]          Current inode: 2085478    Stored inode: 14416
[05:44:39]          Current file modification time: 1192728605
[05:44:39]          Stored file modification time : 1192490843
[05:44:40] /media/root//usr/bin/logger                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/logger
[05:44:40]          Current inode: 2085480    Stored inode: 14418
[05:44:40] /media/root//usr/bin/lsattr                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/lsattr
[05:44:40]          Current inode: 2085491    Stored inode: 14403
[05:44:40] /media/root//usr/bin/lsof                         [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/lsof
[05:44:40]          Current inode: 2085495    Stored inode: 14404
[05:44:40] /media/root//usr/bin/md5sum                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/md5sum
[05:44:40]          Current inode: 2085518    Stored inode: 806
[05:44:40] /media/root//usr/bin/newgrp                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/newgrp
[05:44:40]          Current inode: 2085556    Stored inode: 14419
[05:44:40] /media/root//usr/bin/passwd                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/passwd
[05:44:40]          Current inode: 2085614    Stored inode: 14420
[05:44:40] /media/root//usr/bin/perl                         [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/perl
[05:44:40]          Current inode: 2085633    Stored inode: 14
[05:44:40] /media/root//usr/bin/pstree                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/pstree
[05:44:40]          Current inode: 2085691    Stored inode: 14421
[05:44:40] /media/root//usr/bin/rkhunter                     [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/rkhunter
[05:44:40]          Current inode: 2088075    Stored inode: 12897
[05:44:40] /media/root//usr/bin/runcon                       [ Warning ]
[05:44:40] Warning: The file properties have changed:
[05:44:40]          File: /media/root//usr/bin/runcon
[05:44:40]          Current inode: 2085742    Stored inode: 14422
[05:44:40] /media/root//usr/bin/sha1sum                      [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/sha1sum
[05:44:41]          Current inode: 2085794    Stored inode: 1808
[05:44:41] /media/root//usr/bin/size                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/size
[05:44:41]          Current inode: 2085804    Stored inode: 14423
[05:44:41] /media/root//usr/bin/slocate                      [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/slocate
[05:44:41]          Current inode: 2085807    Stored inode: 14417
[05:44:41] /media/root//usr/bin/sort                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/sort
[05:44:41]          Current inode: 2085822    Stored inode: 545
[05:44:41] /media/root//usr/bin/stat                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/stat
[05:44:41]          Current inode: 2085838    Stored inode: 1681
[05:44:41] /media/root//usr/bin/strace                       [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/strace
[05:44:41]          Current inode: 2085839    Stored inode: 14424
[05:44:41] /media/root//usr/bin/strings                      [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/strings
[05:44:41]          Current inode: 2085841    Stored inode: 14407
[05:44:41] /media/root//usr/bin/sudo                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/sudo
[05:44:41]          Current inode: 2085843    Stored inode: 1057
[05:44:41] /media/root//usr/bin/tail                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/tail
[05:44:41]          Current inode: 2085854    Stored inode: 1811
[05:44:41] /media/root//usr/bin/test                         [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/test
[05:44:41]          Current inode: 2085861    Stored inode: 14425
[05:44:41] /media/root//usr/bin/top                          [ Warning ]
[05:44:41] Warning: The file properties have changed:
[05:44:41]          File: /media/root//usr/bin/top
[05:44:41]          Current inode: 2085874    Stored inode: 14426
[05:44:42] /media/root//usr/bin/touch                        [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/touch
[05:44:42]          Current inode: 2085878    Stored inode: 1713
[05:44:42]          Current file modification time: 1192728610
[05:44:42]          Stored file modification time : 1192490226
[05:44:42] /media/root//usr/bin/tr                           [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/tr
[05:44:42]          Current inode: 2085880    Stored inode: 895
[05:44:42] /media/root//usr/bin/uniq                         [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/uniq
[05:44:42]          Current inode: 2085910    Stored inode: 1010
[05:44:42] /media/root//usr/bin/users                        [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/users
[05:44:42]          Current inode: 2085925    Stored inode: 14427
[05:44:42] /media/root//usr/bin/vmstat                       [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/vmstat
[05:44:42]          Current inode: 2085939    Stored inode: 14428
[05:44:42] /media/root//usr/bin/w                            [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/w
[05:44:42]          Current inode: 2085944    Stored inode: 14429
[05:44:42]          Current file modification time: 1192728610
[05:44:42]          Stored file modification time : 1192490264
[05:44:42] /media/root//usr/bin/watch                        [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/watch
[05:44:42]          Current inode: 2085949    Stored inode: 14432
[05:44:42] /media/root//usr/bin/wc                           [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/wc
[05:44:42]          Current inode: 2085950    Stored inode: 1008
[05:44:42] /media/root//usr/bin/wget                         [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/wget
[05:44:42]          Current inode: 2085952    Stored inode: 1817
[05:44:42] /media/root//usr/bin/whatis                       [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/whatis
[05:44:42]          Current inode: 2085953    Stored inode: 14433
[05:44:42] /media/root//usr/bin/whereis                      [ Warning ]
[05:44:42] Warning: The file properties have changed:
[05:44:42]          File: /media/root//usr/bin/whereis
[05:44:42]          Current inode: 2085954    Stored inode: 14434
[05:44:43] /media/root//usr/bin/which                        [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/which
[05:44:43]          Current inode: 2085955    Stored inode: 903
[05:44:43]          Current file modification time: 1192728610
[05:44:43]          Stored file modification time : 1192490228
[05:44:43] /media/root//usr/bin/who                          [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/who
[05:44:43]          Current inode: 2085957    Stored inode: 1799
[05:44:43] /media/root//usr/bin/whoami                       [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/whoami
[05:44:43]          Current inode: 2085958    Stored inode: 7807
[05:44:43] /media/root//usr/bin/mawk                         [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/mawk
[05:44:43]          Current inode: 2085514    Stored inode: 898
[05:44:43] /media/root//usr/bin/lwp-request                  [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/lwp-request
[05:44:43]          Current inode: 2085502    Stored inode: 14413
[05:44:43] Info: Found file '/media/root//usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[05:44:43] /media/root//usr/bin/w.procps                     [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//usr/bin/w.procps
[05:44:43]          Current inode: 2085945    Stored inode: 14431
[05:44:43] /media/root//sbin/depmod                          [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//sbin/depmod
[05:44:43]          Current inode: 2528084    Stored inode: 14435
[05:44:43] /media/root//sbin/ifconfig                        [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//sbin/ifconfig
[05:44:43]          Current inode: 2528113    Stored inode: 1428
[05:44:43] /media/root//sbin/ifdown                          [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//sbin/ifdown
[05:44:43]          Current inode: 2528114    Stored inode: 14436
[05:44:43] /media/root//sbin/ifup                            [ Warning ]
[05:44:43] Warning: The file properties have changed:
[05:44:43]          File: /media/root//sbin/ifup
[05:44:44]          Current inode: 2528115    Stored inode: 1423
[05:44:44] /media/root//sbin/init                            [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/init
[05:44:44]          Current inode: 2528116    Stored inode: 1264
[05:44:44] /media/root//sbin/insmod                          [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/insmod
[05:44:44]          Current inode: 2528118    Stored inode: 14437
[05:44:44] /media/root//sbin/ip                              [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/ip
[05:44:44]          Current inode: 2528120    Stored inode: 2029
[05:44:44]          Current file modification time: 1192728600
[05:44:44]          Stored file modification time : 1192490279
[05:44:44] /media/root//sbin/lsmod                           [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/lsmod
[05:44:44]          Current inode: 2528155    Stored inode: 1762
[05:44:44]          Current file modification time: 1192728600
[05:44:44]          Stored file modification time : 1192490294
[05:44:44] /media/root//sbin/modinfo                         [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/modinfo
[05:44:44]          Current inode: 2528175    Stored inode: 9427
[05:44:44] /media/root//sbin/modprobe                        [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/modprobe
[05:44:44]          Current inode: 2528176    Stored inode: 953
[05:44:44] /media/root//sbin/rmmod                           [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/rmmod
[05:44:44]          Current inode: 2528201    Stored inode: 1765
[05:44:44] /media/root//sbin/runlevel                        [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/runlevel
[05:44:44]          Current inode: 2528206    Stored inode: 1278
[05:44:44] /media/root//sbin/sulogin                         [ Warning ]
[05:44:44] Warning: The file properties have changed:
[05:44:44]          File: /media/root//sbin/sulogin
[05:44:45]          Current inode: 2528216    Stored inode: 14440
[05:44:45] /media/root//sbin/sysctl                          [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//sbin/sysctl
[05:44:45]          Current inode: 2528219    Stored inode: 1309
[05:44:45] /media/root//sbin/syslogd                         [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//sbin/syslogd
[05:44:45]          Current inode: 2528220    Stored inode: 1947
[05:44:45] /media/root//usr/sbin/adduser                     [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/adduser
[05:44:45]          Current inode: 2086945    Stored inode: 235
[05:44:45] Info: Found file '/media/root//usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[05:44:45] /media/root//usr/sbin/chroot                      [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/chroot
[05:44:45]          Current inode: 2086961    Stored inode: 14441
[05:44:45] /media/root//usr/sbin/cron                        [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/cron
[05:44:45]          Current inode: 2086967    Stored inode: 2514
[05:44:45] /media/root//usr/sbin/groupadd                    [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/groupadd
[05:44:45]          Current inode: 2087011    Stored inode: 250
[05:44:45] /media/root//usr/sbin/groupdel                    [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/groupdel
[05:44:45]          Current inode: 2087012    Stored inode: 14442
[05:44:45] /media/root//usr/sbin/groupmod                    [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/groupmod
[05:44:45]          Current inode: 2087013    Stored inode: 14443
[05:44:45] /media/root//usr/sbin/grpck                       [ Warning ]
[05:44:45] Warning: The file properties have changed:
[05:44:45]          File: /media/root//usr/sbin/grpck
[05:44:45]          Current inode: 2087014    Stored inode: 210
[05:44:46] /media/root//usr/sbin/nologin                     [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/nologin
[05:44:46]          Current inode: 2087063    Stored inode: 14444
[05:44:46] /media/root//usr/sbin/pwck                        [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/pwck
[05:44:46]          Current inode: 2087084    Stored inode: 204
[05:44:46] /media/root//usr/sbin/tcpd                        [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/tcpd
[05:44:46]          Current inode: 2087106    Stored inode: 14445
[05:44:46] /media/root//usr/sbin/useradd                     [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/useradd
[05:44:46]          Current inode: 2087142    Stored inode: 256
[05:44:46] /media/root//usr/sbin/userdel                     [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/userdel
[05:44:46]          Current inode: 2087143    Stored inode: 14446
[05:44:46] /media/root//usr/sbin/usermod                     [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/usermod
[05:44:46]          Current inode: 2087144    Stored inode: 278
[05:44:46] /media/root//usr/sbin/vipw                        [ Warning ]
[05:44:46] Warning: The file properties have changed:
[05:44:46]          File: /media/root//usr/sbin/vipw
[05:44:46]          Current inode: 2087150    Stored inode: 14447
[05:44:49]
[05:44:49] Checking for rootkits...
[05:44:49] Info: Starting test name 'rootkits'
[05:44:49]
[05:44:49] Performing check of known rootkit files and directories
[05:44:49] Info: Starting test name 'known_rkts'
[05:44:49]
[05:44:49] Checking for 55808 Trojan - Variant A...
[05:44:49]   Checking for file '/media/root//tmp/.../r'      [ Not found ]
[05:44:49]   Checking for file '/media/root//tmp/.../a'      [ Not found ]
[05:44:49] 55808 Trojan - Variant A                          [ Not found ]
[05:44:49]
[05:44:49] Checking for ADM Worm...
[05:44:49]   Checking for string 'w0rm'                      [ Not found ]
[05:44:49] ADM Worm                                          [ Not found ]
[05:44:49]
[05:44:49] Checking for AjaKit Rootkit...
[05:44:49]   Checking for file '/media/root//dev/tux/.addr'  [ Not found ]
[05:44:49]   Checking for file '/media/root//dev/tux/.proc'  [ Not found ]
[05:44:49]   Checking for file '/media/root//dev/tux/.file'  [ Not found ]
[05:44:49]   Checking for file '/media/root//lib/.libgh-gh/cleaner' [ Not found ]
[05:44:49]   Checking for file '/media/root//lib/.libgh-gh/Patch/patch' [ Not found ]
[05:44:49]   Checking for file '/media/root//lib/.libgh-gh/sb0k' [ Not found ]
[05:44:49]   Checking for directory '/media/root//dev/tux'   [ Not found ]
[05:44:49]   Checking for directory '/media/root//lib/.libgh-gh' [ Not found ]
[05:44:49] AjaKit Rootkit                                    [ Not found ]
[05:44:49]
[05:44:49] Checking for aPa Kit...
[05:44:50]   Checking for file '/media/root//usr/share/.aPa' [ Not found ]
[05:44:50] aPa Kit                                           [ Not found ]
[05:44:50]
[05:44:50] Checking for Apache Worm...
[05:44:50]   Checking for file '/media/root//bin/.log'       [ Not found ]
[05:44:50] Apache Worm                                       [ Not found ]
[05:44:50]
[05:44:50] Checking for Ambient (ark) Rootkit...
[05:44:50]   Checking for file '/media/root//usr/lib/.ark?'  [ Not found ]
[05:44:50]   Checking for file '/media/root//dev/ptyxx/.log' [ Not found ]
[05:44:50]   Checking for file '/media/root//dev/ptyxx/.file' [ Not found ]
[05:44:50]   Checking for directory '/media/root//dev/ptyxx' [ Not found ]
[05:44:50] Ambient (ark) Rootkit                             [ Not found ]
[05:44:50]
[05:44:50] Checking for Balaur Rootkit...
[05:44:50]   Checking for file '/media/root//usr/lib/liblog.o' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/.kinetic' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/.egcs' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/.wormie' [ Not found ]
[05:44:50] Balaur Rootkit                                    [ Not found ]
[05:44:50]
[05:44:50] Checking for BeastKit Rootkit...
[05:44:50]   Checking for file '/media/root//usr/sbin/arobia' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/sbin/idrun' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/hk' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/sc' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/sdco' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/elm/arobia/elm/srsd' [ Not found ]
[05:44:50]   Checking for directory '/media/root//lib/ldd.so/bktools' [ Not found ]
[05:44:50] BeastKit Rootkit                                  [ Not found ]
[05:44:50]
[05:44:50] Checking for beX2 Rootkit...
[05:44:50]   Checking for directory '/media/root//usr/include/bex' [ Not found ]
[05:44:50] beX2 Rootkit                                      [ Not found ]
[05:44:50]
[05:44:50] Checking for BOBKit Rootkit...
[05:44:50]   Checking for file '/media/root//usr/sbin/ntpsx' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../ls' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../netstat' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../lsof' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../uconf.inv' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../psr' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../find' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../pstree' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../slocate' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../du' [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/.../top' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/...' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/.../bkit-ssh' [ Not found ]
[05:44:50]   Checking for directory '/media/root//usr/lib/.bkit-' [ Not found ]
[05:44:50]   Checking for directory '/media/root//tmp/.bkp'  [ Not found ]
[05:44:50] BOBKit Rootkit                                    [ Not found ]
[05:44:50]
[05:44:50] Checking for CiNIK Worm (Slapper.B variant)...
[05:44:50]   Checking for file '/media/root//tmp/.cinik'     [ Not found ]
[05:44:50]   Checking for directory '/media/root//tmp/.font-unix/.cinik' [ Not found ]
[05:44:50] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[05:44:50]
[05:44:50] Checking for Danny-Boy's Abuse Kit...
[05:44:50]   Checking for file '/media/root//dev/mdev'       [ Not found ]
[05:44:50]   Checking for file '/media/root//usr/lib/libX.a' [ Not found ]
[05:44:50] Danny-Boy's Abuse Kit                             [ Not found ]
[05:44:51]
[05:44:51] Checking for Devil RootKit...
[05:44:51]   Checking for file '/media/root//var/lib/games/.src' [ Not found ]
[05:44:51]   Checking for file '/media/root//dev/dsx'        [ Not found ]
[05:44:51]   Checking for file '/media/root//dev/caca'       [ Not found ]
[05:44:51] Devil RootKit                                     [ Not found ]
[05:44:51]
[05:44:51] Checking for Dica-Kit Rootkit...
[05:44:51]   Checking for file '/media/root//lib/.sso'       [ Not found ]
[05:44:51]   Checking for file '/media/root//lib/.so'        [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/clean' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/xl' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/xdr' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/psg' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/secure' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/rdx' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/va' [ Not found ]
[05:44:51]   Checking for file '/media/root//var/run/...dica/cl.sh' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/.etc'   [ Not found ]
[05:44:51]   Checking for directory '/media/root//var/run/...dica' [ Not found ]
[05:44:51]   Checking for directory '/media/root//var/run/...dica/mh' [ Not found ]
[05:44:51]   Checking for directory '/media/root//var/run/...dica/scan' [ Not found ]
[05:44:51] Dica-Kit Rootkit                                  [ Not found ]
[05:44:51]
[05:44:51] Checking for Dreams Rootkit...
[05:44:51]   Checking for file '/media/root//dev/ttyoa'      [ Not found ]
[05:44:51]   Checking for file '/media/root//dev/ttyof'      [ Not found ]
[05:44:51]   Checking for file '/media/root//dev/ttyop'      [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/sense'  [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/sl2'    [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/logclear' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/(swapd)' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/snfs'   [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/libsss' [ Not found ]
[05:44:51]   Checking for directory '/media/root//dev/ida/.hpd' [ Not found ]
[05:44:51] Dreams Rootkit                                    [ Not found ]
[05:44:51]
[05:44:51] Checking for Duarawkz Rootkit...
[05:44:51]   Checking for file '/media/root//usr/bin/duarawkz/loginpass' [ Not found ]
[05:44:51]   Checking for directory '/media/root//usr/bin/duarawkz' [ Not found ]
[05:44:51] Duarawkz Rootkit                                  [ Not found ]
[05:44:51]
[05:44:51] Checking for Enye LKM...
[05:44:51]   Checking for file '/media/root//etc/.enyelkmHIDE^IT.ko' [ Not found ]
[05:44:51] Enye LKM                                          [ Not found ]
[05:44:51]
[05:44:51] Checking for Flea Linux Rootkit...
[05:44:51]   Checking for file '/media/root//etc/ld.so.hash' [ Not found ]
[05:44:51]   Checking for file '/media/root//lib/security/.config/ssh/ssh_host_key' [ Not found ]
[05:44:51]   Checking for file '/media/root//lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[05:44:51]   Checking for file '/media/root//lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/bin/ssh2d'  [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/ldlibns.so' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/ldlibpst.so' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/ldlibdu.so' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/ldlibct.so' [ Not found ]
[05:44:51]   Checking for directory '/media/root//lib/security/.config/ssh' [ Not found ]
[05:44:51]   Checking for directory '/media/root//dev/..0'   [ Not found ]
[05:44:51]   Checking for directory '/media/root//dev/..0/backup' [ Not found ]
[05:44:51] Flea Linux Rootkit                                [ Not found ]
[05:44:51]
[05:44:51] Checking for FreeBSD Rootkit...
[05:44:51]   Checking for file '/media/root//usr/lib/.fx/sched_host.2' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/.fx/random_d.2' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/.fx/set_pid.2' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/.fx/cons.saver' [ Not found ]
[05:44:51]   Checking for file '/media/root//usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[05:44:51]   Checking for file '/media/root//bin/sysback'    [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/local/bin/sysback' [ Not found ]
[05:44:52]   Checking for directory '/media/root//usr/lib/.fx' [ Not found ]
[05:44:52]   Checking for directory '/media/root//usr/lib/.fx/adore' [ Not found ]
[05:44:52] FreeBSD Rootkit                                   [ Not found ]
[05:44:52]
[05:44:52] Checking for ****`it Rootkit...
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/hax0r' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/hax0rshell' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/config/lports' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/config/rports' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/config/rkconf' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/config/password' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/fuckit/config/progs' [ Not found ]
[05:44:52]   Checking for file '/media/root//dev/proc/system-bins/init' [ Not found ]
[05:44:52] ****`it Rootkit                                   [ Not found ]
[05:44:52]
[05:44:52] Checking for GasKit Rootkit...
[05:44:52]   Checking for file '/media/root//dev/dev/gaskit/sshd/sshdd' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/dev'   [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/dev/gaskit' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/dev/gaskit/sshd' [ Not found ]
[05:44:52] GasKit Rootkit                                    [ Not found ]
[05:44:52]
[05:44:52] Checking for Heroin LKM...
[05:44:52]   Checking for kernel symbol 'heroin'             [ Skipped ]
[05:44:52] Heroin LKM                                        [ Not found ]
[05:44:52]
[05:44:52] Checking for HjC Kit...
[05:44:52]   Checking for directory '/media/root//dev/.hijackerz' [ Not found ]
[05:44:52] HjC Kit                                           [ Not found ]
[05:44:52]
[05:44:52] Checking for ignoKit Rootkit...
[05:44:52]   Checking for file '/media/root//lib/defs/p'     [ Not found ]
[05:44:52]   Checking for file '/media/root//lib/defs/q'     [ Not found ]
[05:44:52]   Checking for file '/media/root//lib/defs/r'     [ Not found ]
[05:44:52]   Checking for file '/media/root//lib/defs/s'     [ Not found ]
[05:44:52]   Checking for file '/media/root//lib/defs/t'     [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/defs/p' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/defs/q' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/defs/r' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/defs/s' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/defs/t' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/.libigno/pkunsec' [ Not found ]
[05:44:52]   Checking for file '/media/root//usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[05:44:52]   Checking for directory '/media/root//usr/lib/.libigno' [ Not found ]
[05:44:52]   Checking for directory '/media/root//usr/lib/.libigno/.igno' [ Not found ]
[05:44:52] ignoKit Rootkit                                   [ Not found ]
[05:44:52]
[05:44:52] Checking for ImperalsS-FBRK Rootkit...
[05:44:52]   Checking for directory '/media/root//dev/fd/.88' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/fd/.99' [ Not found ]
[05:44:52] ImperalsS-FBRK Rootkit                            [ Not found ]
[05:44:52]
[05:44:52] Checking for Irix Rootkit...
[05:44:52]   Checking for directory '/media/root//dev/pts/01' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/pts/01/backup' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/pts/01/etc' [ Not found ]
[05:44:52]   Checking for directory '/media/root//dev/pts/01/tmp' [ Not found ]
[05:44:52] Irix Rootkit                                      [ Not found ]
[05:44:52]
[05:44:52] Checking for Kitko Rootkit...
[05:44:52]   Checking for directory '/media/root//usr/src/redhat/SRPMS/...' [ Not found ]
[05:44:52] Kitko Rootkit                                     [ Not found ]
[05:44:52]
[05:44:52] Checking for Knark Rootkit...
[05:44:52]   Checking for file '/media/root//proc/knark/pids' [ Not found ]
[05:44:52]   Checking for directory '/media/root//proc/knark' [ Not found ]
[05:44:52] Knark Rootkit                                     [ Not found ]
[05:44:52]
[05:44:52] Checking for Li0n Worm...
[05:44:52]   Checking for file '/media/root//bin/in.telnetd' [ Not found ]
[05:44:53]   Checking for file '/media/root//bin/mjy'        [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/1i0n.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/hack.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/bind' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/randb' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/scan.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/pscan' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/star.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/bindx.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/scan/bindname.log' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/1i0n.sh' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/lib/netstat' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[05:44:53]   Checking for file '/media/root//dev/.lib/lib/lib/dev/.1file' [ Not found ]
[05:44:53] Li0n Worm                                         [ Not found ]
[05:44:53]
[05:44:53] Checking for Lockit / LJK2 Rootkit...
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[05:44:53]   Checking for file '/media/root//usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[05:44:53]   Checking for directory '/media/root//usr/lib/libmen.oo/.LJK2' [ Not found ]
[05:44:53] Lockit / LJK2 Rootkit                             [ Not found ]
[05:44:53]
[05:44:53] Checking for Mood-NT Rootkit...
[05:44:53]   Checking for file '/media/root//sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[05:44:53]   Checking for file '/media/root//_cthulhu/mood-nt.init' [ Not found ]
[05:44:53]   Checking for file '/media/root//_cthulhu/mood-nt.conf' [ Not found ]
[05:44:53]   Checking for file '/media/root//_cthulhu/mood-nt.sniff' [ Not found ]
[05:44:53]   Checking for directory '/media/root//_cthulhu'  [ Not found ]
[05:44:53] Mood-NT Rootkit                                   [ Not found ]
[05:44:53]
[05:44:53] Checking for MRK Rootkit...
[05:44:54]   Checking for file '/media/root//dev/ida/.inet/pid' [ Not found ]
[05:44:54]   Checking for file '/media/root//dev/ida/.inet/ssh_host_key' [ Not found ]
[05:44:54]   Checking for file '/media/root//dev/ida/.inet/ssh_random_seed' [ Not found ]
[05:44:54]   Checking for file '/media/root//dev/ida/.inet/tcp.log' [ Not found ]
[05:44:54]   Checking for directory '/media/root//dev/ida/.inet' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/spool/cron/.sh' [ Not found ]
[05:44:54] MRK Rootkit                                       [ Not found ]
[05:44:54]
[05:44:54] Checking for Ni0 Rootkit...
[05:44:54]   Checking for file '/media/root//var/lock/subsys/...datafile.../...net...' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lock/subsys/...datafile.../...port...' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lock/subsys/...datafile.../...ps...' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lock/subsys/...datafile.../...file...' [ Not found ]
[05:44:54]   Checking for directory '/media/root//tmp/waza'  [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile...' [ Not found ]
[05:44:54]   Checking for directory '/media/root//usr/sbin/es' [ Not found ]
[05:44:54] Ni0 Rootkit                                       [ Not found ]
[05:44:54]
[05:44:54] Checking for Ohhara Rootkit...
[05:44:54]   Checking for file '/media/root//var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile...' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[05:44:54]   Checking for directory '/media/root//var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[05:44:54] Ohhara Rootkit                                    [ Not found ]
[05:44:54]
[05:44:54] Checking for Optic Kit (Tux) Worm...
[05:44:54]   Checking for directory '/media/root//dev/tux'   [ Not found ]
[05:44:54]   Checking for directory '/media/root//usr/bin/xchk' [ Not found ]
[05:44:54]   Checking for directory '/media/root//usr/bin/xsf' [ Not found ]
[05:44:54]   Checking for directory '/media/root//usr/bin/ssh2d' [ Not found ]
[05:44:54] Optic Kit (Tux) Worm                              [ Not found ]
[05:44:54]
[05:44:54] Checking for Oz Rootkit...
[05:44:54]   Checking for file '/media/root//dev/.oz/.nap/rkit/terror' [ Not found ]
[05:44:54]   Checking for directory '/media/root//dev/.oz'   [ Not found ]
[05:44:54] Oz Rootkit                                        [ Not found ]
[05:44:54]
[05:44:54] Checking for Phalanx Rootkit...
[05:44:54]   Checking for file '/media/root//usr/share/.home.ph1/cb' [ Not found ]
[05:44:54]   Checking for file '/media/root//etc/host.ph1'   [ Not found ]
[05:44:54]   Checking for file '/media/root//bin/host.ph1'   [ Not found ]
[05:44:54]   Checking for file '/media/root//usr/share/.home.ph1/phalanx' [ Not found ]
[05:44:54]   Checking for directory '/media/root//usr/share/.home.ph1' [ Not found ]
[05:44:54] Phalanx Rootkit                                   [ Not found ]
[05:44:54]
[05:44:54] Checking for Phalanx Rootkit (strings)...
[05:44:54]   Checking for string 'phalanx'                   [ Not found ]
[05:44:54] Phalanx Rootkit (strings)                         [ Not found ]
[05:44:54]
[05:44:54] Checking for Portacelo Rootkit...
[05:44:54]   Checking for file '/media/root//var/lib/.../.ak' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../.hk' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../.rs' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../.p' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../getty' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../lkt.o' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../show' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../nlkt.o' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../ssshrc' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../sssh_equiv' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../sssh_known_hosts' [ Not found ]
[05:44:54]   Checking for file '/media/root//var/lib/.../sssh_pid' [ Not found ]
[05:44:54]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[05:44:54] Portacelo Rootkit                                 [ Not found ]
[05:44:54]
[05:44:54] Checking for R3dstorm Toolkit...
[05:44:54]   Checking for file '/media/root//var/log/tk02/see_all' [ Not found ]
[05:44:55]   Checking for file '/media/root//bin/.../sshd/sbin/sshd1' [ Not found ]
[05:44:55]   Checking for file '/media/root//bin/.../hate/sk' [ Not found ]
[05:44:55]   Checking for file '/media/root//bin/.../see_all' [ Not found ]
[05:44:55]   Checking for directory '/media/root//var/log/tk02' [ Not found ]
[05:44:55]   Checking for directory '/media/root//var/log/tk02/old' [ Not found ]
[05:44:55]   Checking for directory '/media/root//bin/...'   [ Not found ]
[05:44:55] R3dstorm Toolkit                                  [ Not found ]
[05:44:55]
[05:44:55] Checking for RH-Sharpe's Rootkit...
[05:44:55]   Checking for file '/media/root//bin/lps'        [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/lpstree' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/ltop'   [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/lkillall' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/ldu'    [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/lnetstat' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/wp'     [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/shad'   [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/vadim'  [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/slice'  [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/cleaner' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/include/rpcsvc/du' [ Not found ]
[05:44:55] RH-Sharpe's Rootkit                               [ Not found ]
[05:44:55]
[05:44:55] Checking for RSHA's Rootkit...
[05:44:55]   Checking for file '/media/root//bin/kr4p'       [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/n3tstat' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/chsh2'  [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/bin/slice2' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[05:44:55]   Checking for file '/media/root//etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[05:44:55]   Checking for directory '/media/root//etc/rc.d/rsha' [ Not found ]
[05:44:55]   Checking for directory '/media/root//etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[05:44:55] RSHA's Rootkit                                    [ Not found ]
[05:44:55]
[05:44:55] Checking for Scalper Worm...
[05:44:55]   Checking for file '/media/root//tmp/.a'         [ Not found ]
[05:44:55]   Checking for file '/media/root//tmp/.uua'       [ Not found ]
[05:44:55] Scalper Worm                                      [ Not found ]
[05:44:55]
[05:44:55] Checking for Sebek LKM...
[05:44:55]   Checking for kernel symbol 'adore or sebek'     [ Skipped ]
[05:44:55] Sebek LKM                                         [ Not found ]
[05:44:55]
[05:44:55] Checking for Shutdown Rootkit...
[05:44:55]   Checking for file '/media/root//usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/man/man5/.. /.dir/see' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/man/man5/.. /.dir/nscd' [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/man/man5/.. /.dir/alpd' [ Not found ]
[05:44:55]   Checking for file '/media/root//etc/rc.d/rc.local ' [ Not found ]
[05:44:55]   Checking for directory '/media/root//usr/man/man5/.. /.dir' [ Not found ]
[05:44:55]   Checking for directory '/media/root//usr/man/man5/.. /.dir/scannah' [ Not found ]
[05:44:55]   Checking for directory '/media/root//etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[05:44:55] Shutdown Rootkit                                  [ Not found ]
[05:44:55]
[05:44:55] Checking for SHV4 Rootkit...
[05:44:55]   Checking for file '/media/root//etc/ld.so.hash' [ Not found ]
[05:44:55]   Checking for file '/media/root//lib/libext-2.so.7' [ Not found ]
[05:44:55]   Checking for file '/media/root//lib/lidps1.so'  [ Not found ]
[05:44:55]   Checking for file '/media/root//usr/sbin/xntps' [ Not found ]
[05:44:55]   Checking for directory '/media/root//lib/security/.config' [ Not found ]
[05:44:55]   Checking for directory '/media/root//lib/security/.config/ssh' [ Not found ]
[05:44:55] SHV4 Rootkit                                      [ Not found ]
[05:44:55]
[05:44:55] Checking for SHV5 Rootkit...
[05:44:55]   Checking for file '/media/root//etc/sh.conf'    [ Not found ]
[05:44:55]   Checking for file '/media/root//dev/srd0'       [ Not found ]
[05:44:55]   Checking for directory '/media/root//usr/lib/libsh' [ Not found ]
[05:44:55] SHV5 Rootkit                                      [ Not found ]
[05:44:56]
[05:44:56] Checking for Sin Rootkit...
[05:44:56]   Checking for file '/media/root//dev/.haos/haos1/.f/Denyed' [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/ttyoa'      [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/ttyof'      [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/ttyop'      [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/ttyos'      [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/.lib'   [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/sn/.X'  [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/sn/.sys' [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/ld/.X'  [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/man/man1/...' [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/man/man1/.../.m' [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/man/man1/.../.w' [ Not found ]
[05:44:56]   Checking for directory '/media/root//usr/lib/sn' [ Not found ]
[05:44:56]   Checking for directory '/media/root//usr/lib/man1/...' [ Not found ]
[05:44:56]   Checking for directory '/media/root//dev/.haos' [ Not found ]
[05:44:56] Sin Rootkit                                       [ Not found ]
[05:44:56]
[05:44:56] Checking for Slapper Worm...
[05:44:56]   Checking for file '/media/root//tmp/.bugtraq'   [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/.uubugtraq' [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/.bugtraq.c' [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/httpd'      [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/.unlock'    [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/update'     [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/.cinik'     [ Not found ]
[05:44:56]   Checking for file '/media/root//tmp/.b'         [ Not found ]
[05:44:56] Slapper Worm                                      [ Not found ]
[05:44:56]
[05:44:56] Checking for Sneakin Rootkit...
[05:44:56]   Checking for directory '/media/root//tmp/.X11-unix/.../rk' [ Not found ]
[05:44:56] Sneakin Rootkit                                   [ Not found ]
[05:44:56]
[05:44:56] Checking for Suckit Rootkit...
[05:44:56]   Checking for file '/media/root//sbin/initsk12'  [ Not found ]
[05:44:56]   Checking for file '/media/root//sbin/initxrk'   [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/bin/null'   [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/share/locale/sk/.sk12/sk' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc0.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc1.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc2.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc3.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc4.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc5.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for file '/media/root//etc/rc.d/rc6.d/S23kmdac' [ Not found ]
[05:44:56]   Checking for directory '/media/root//dev/sdhu0/tehdrakg' [ Not found ]
[05:44:56]   Checking for directory '/media/root//etc/.MG'   [ Not found ]
[05:44:56]   Checking for directory '/media/root//usr/share/locale/sk/.sk12' [ Not found ]
[05:44:56]   Checking for directory '/media/root//usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[05:44:56] Suckit Rootkit                                    [ Not found ]
[05:44:56]
[05:44:56] Checking for SunOS Rootkit...
[05:44:56]   Checking for file '/media/root//etc/ld.so.hash' [ Not found ]
[05:44:56]   Checking for file '/media/root//lib/libext-2.so.7' [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/bin/ssh2d'  [ Not found ]
[05:44:56]   Checking for file '/media/root//bin/xlogin'     [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/crth.o' [ Not found ]
[05:44:56]   Checking for file '/media/root//usr/lib/crtz.o' [ Not found ]
[05:44:56]   Checking for file '/media/root//sbin/login'     [ Not found ]
[05:44:56]   Checking for file '/media/root//lib/security/.config/sn' [ Not found ]
[05:44:56]   Checking for file '/media/root//lib/security/.config/lpsched' [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/kmod'       [ Not found ]
[05:44:56]   Checking for file '/media/root//dev/dos'        [ Not found ]
[05:44:56] SunOS Rootkit                                     [ Not found ]
[05:44:56]
[05:44:56] Checking for SunOS / NSDAP Rootkit...
[05:44:56]   Checking for file '/media/root//usr/lib/vold/nsdap/.kit' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/defines' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/patcher' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/pg' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/cleaner' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/utime' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/crypt' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/findkit' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/sn2' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/sniffload' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/vold/nsdap/runsniff' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/lib/lpset'  [ Not found ]
[05:44:57]   Checking for directory '/media/root//usr/lib/vold/nsdap' [ Not found ]
[05:44:57] SunOS / NSDAP Rootkit                             [ Not found ]
[05:44:57]
[05:44:57] Checking for Superkit Rootkit...
[05:44:57]   Checking for file '/media/root//usr/man/.sman/sk' [ Not found ]
[05:44:57] Superkit Rootkit                                  [ Not found ]
[05:44:57]
[05:44:57] Checking for TBD (Telnet BackDoor)...
[05:44:57]   Checking for file '/media/root//usr/lib/.tbd'   [ Not found ]
[05:44:57] TBD (Telnet BackDoor)                             [ Not found ]
[05:44:57]
[05:44:57] Checking for TeLeKiT Rootkit...
[05:44:57]   Checking for file '/media/root//usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/man/man3/.../cl' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/ptyr'       [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/ptyp'       [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/ptyq'       [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/hda06'      [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/info/libc1.so' [ Not found ]
[05:44:57]   Checking for directory '/media/root//usr/man/man3/...' [ Not found ]
[05:44:57]   Checking for directory '/media/root//usr/man/man3/.../lsniff' [ Not found ]
[05:44:57]   Checking for directory '/media/root//usr/man/man3/.../TeLeKiT' [ Not found ]
[05:44:57] TeLeKiT Rootkit                                   [ Not found ]
[05:44:57]
[05:44:57] Checking for T0rn Rootkit...
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/t0rns' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/du' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/ls' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/t0rnsb' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/ps' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/t0rnp' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/find' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/ifconfig' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/pg' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/ssh.tgz' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/top' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/sz' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/login' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/in.fingerd' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/1i0n.sh' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/pstree' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/in.telnetd' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/mjy' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/sush' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/tfn' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/name' [ Not found ]
[05:44:57]   Checking for file '/media/root//dev/.lib/lib/lib/getip.sh' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/info/.torn/sh*' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/src/.****/.1addr' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/src/.****/.1file' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/src/.****/.1proc' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/src/.****/.1logz' [ Not found ]
[05:44:57]   Checking for file '/media/root//usr/info/.t0rn' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/.lib'  [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/.lib/lib' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/.lib/lib/lib' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/.lib/lib/lib/dev' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/.lib/lib/scan' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/src/.****' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/man/man1/man1' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/man/man1/man1/lib' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/man/man1/man1/lib/.lib' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[05:44:58] T0rn Rootkit                                      [ Not found ]
[05:44:58]
[05:44:58] Checking for Trojanit Kit...
[05:44:58]   Checking for file '/media/root//bin/.ls'        [ Not found ]
[05:44:58]   Checking for file '/media/root//bin/.ps'        [ Not found ]
[05:44:58]   Checking for file '/media/root//bin/.netstat'   [ Not found ]
[05:44:58]   Checking for file '/media/root//usr/bin/.nop'   [ Not found ]
[05:44:58]   Checking for file '/media/root//usr/bin/.who'   [ Not found ]
[05:44:58] Trojanit Kit                                      [ Not found ]
[05:44:58]
[05:44:58] Checking for Tuxtendo Rootkit...
[05:44:58]   Checking for file '/media/root//dev/tux/.addr'  [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/.cron'  [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/.file'  [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/.log'   [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/.proc'  [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/crontab' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/df' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/dir' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/find' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/ifconfig' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/locate' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/netstat' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/ps' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/pstree' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/syslogd' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/tcpd' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/top' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/updatedb' [ Not found ]
[05:44:58]   Checking for file '/media/root//dev/tux/backup/vdir' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/tux'   [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/tux/ssh2' [ Not found ]
[05:44:58]   Checking for directory '/media/root//dev/tux/backup' [ Not found ]
[05:44:58] Tuxtendo Rootkit                                  [ Not found ]
[05:44:58]
[05:44:58] Checking for URK Rootkit...
[05:44:58]   Checking for file '/media/root//usr/man/man1/xxxxxxbin/find' [ Not found ]
[05:44:58]   Checking for file '/media/root//usr/man/man1/xxxxxxbin/du' [ Not found ]
[05:44:58]   Checking for file '/media/root//usr/man/man1/xxxxxxbin/ps' [ Not found ]
[05:44:58]   Checking for file '/media/root//tmp/conf.inf'   [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/man/man1/xxxxxxbin' [ Not found ]
[05:44:58] URK Rootkit                                       [ Not found ]
[05:44:58]
[05:44:58] Checking for VcKit Rootkit...
[05:44:58]   Checking for directory '/media/root//usr/include/linux/modules/lib.so' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/include/linux/modules/lib.so/bin' [ Not found ]
[05:44:58] VcKit Rootkit                                     [ Not found ]
[05:44:58]
[05:44:58] Checking for Volc Rootkit...
[05:44:58]   Checking for directory '/media/root//var/spool/.recent' [ Not found ]
[05:44:58]   Checking for directory '/media/root//var/spool/.recent/.files' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/lib/volc' [ Not found ]
[05:44:58]   Checking for directory '/media/root//usr/lib/volc/backup' [ Not found ]
[05:44:58] Volc Rootkit                                      [ Not found ]
[05:44:58]
[05:44:58] Checking for X-Org SunOS Rootkit...
[05:44:58]   Checking for file '/media/root//usr/lib/libX.a/bin/tmpfl' [ Not found ]
[05:44:58]   Checking for file '/media/root//usr/lib/libX.a/bin/rps' [ Not found ]
[05:44:59]   Checking for file '/media/root//usr/bin/srload' [ Not found ]
[05:44:59]   Checking for file '/media/root//usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[05:44:59]   Checking for file '/media/root//usr/sbin/modcheck' [ Not found ]
[05:44:59]   Checking for directory '/media/root//usr/lib/libX.a' [ Not found ]
[05:44:59]   Checking for directory '/media/root//usr/lib/libX.a/bin' [ Not found ]
[05:44:59]   Checking for directory '/media/root//usr/lib/libX.a/bin/sparcv7' [ Not found ]
[05:44:59]   Checking for directory '/media/root//usr/share/man...' [ Not found ]
[05:44:59] X-Org SunOS Rootkit                               [ Not found ]
[05:44:59]
[05:44:59] Checking for zaRwT.KiT Rootkit...
[05:44:59]   Checking for file '/media/root//dev/rd/s/sendmeil' [ Not found ]
[05:44:59]   Checking for file '/media/root//dev/ttyf'       [ Not found ]
[05:44:59]   Checking for file '/media/root//dev/ttyp'       [ Not found ]
[05:44:59]   Checking for file '/media/root//dev/ttyn'       [ Not found ]
[05:44:59]   Checking for file '/media/root//rk/tulz'        [ Not found ]
[05:44:59]   Checking for directory '/media/root//rk'        [ Not found ]
[05:44:59]   Checking for directory '/media/root//dev/rd/s'  [ Not found ]
[05:44:59] zaRwT.KiT Rootkit                                 [ Not found ]
[05:44:59]
[05:44:59] Performing additional rootkit checks
[05:44:59] Info: Starting test name 'additional_rkts'
[05:44:59]
[05:44:59]   Performing Suckit Rookit additional checks
[05:44:59]     Checking /sbin/init link count                [ OK ]
[05:44:59]     Checking for hidden file extensions           [ None found ]
[05:44:59]     Running skdet command                         [ Skipped ]
[05:44:59] Info: Unable to find the 'skdet' command
[05:44:59]   Suckit Rookit additional checks                 [ OK ]
[05:44:59]
[05:44:59]   Performing check of possible rootkit files and directories
[05:44:59] Info: Starting test name 'possible_rkt_files'
[05:44:59]     Checking for file '/media/root//dev/sdr0'     [ Not found ]
[05:44:59]     Checking for file '/media/root//tmp/.syshackfile' [ Not found ]
[05:44:59]     Checking for file '/media/root//tmp/.bash_history' [ Not found ]
[05:44:59]     Checking for file '/media/root//usr/info/.clib' [ Not found ]
[05:44:59]     Checking for file '/media/root//usr/sbin/tcp.log' [ Not found ]
[05:44:59]     Checking for file '/media/root//usr/bin/take/pid' [ Not found ]
[05:44:59]     Checking for file '/media/root//sbin/create'  [ Not found ]
[05:44:59]     Checking for file '/media/root//dev/ttypz'    [ Not found ]
[05:44:59]     Checking for directory '/media/root//usr/bin/take' [ Not found ]
[05:44:59]     Checking for directory '/media/root//usr/src/.lib' [ Not found ]
[05:44:59]     Checking for directory '/media/root//usr/share/man/man1/.1c' [ Not found ]
[05:44:59]     Checking for directory '/media/root//lib/lblip.tk' [ Not found ]
[05:44:59]     Checking for directory '/media/root//usr/sbin/...' [ Not found ]
[05:44:59]     Checking for directory '/media/root//usr/share/.gun' [ Not found ]
[05:44:59]   Checking for possible rootkit files and directories [ None found ]
[05:44:59]
[05:44:59]   Performing check for possible rootkit strings
[05:44:59] Info: Starting test name 'possible_rkt_strings'
[05:44:59] Info: Found local startup file: /media/root//etc/rc.local
[05:44:59]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[05:44:59]     Checking for string '****'                    [ Not found ]
[05:44:59]     Checking for string 'backdoor'                [ Not found ]
[05:44:59]     Checking for string 'vt200'                   [ Not found ]
[05:44:59]     Checking for string '/usr/bin/xstat'          [ Not found ]
[05:44:59]     Checking for string '/bin/envpc'              [ Not found ]
[05:44:59]     Checking for string 'L4m3r0x'                 [ Not found ]
[05:44:59]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:44:59]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[05:45:00]     Checking for string '/dev/sgk'                [ Not found ]
[05:45:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:45:00]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:45:00]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[05:45:00]     Checking for string '/lib/.sso'               [ Not found ]
[05:45:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:45:00]     Checking for string '/dev/caca'               [ Not found ]
[05:45:00]     Checking for string '/dev/ttyoa'              [ Not found ]
[05:45:00]     Checking for string 'syg'                     [ Not found ]
[05:45:00]     Checking for string '/dev/pts/01'             [ Not found ]
[05:45:00]     Checking for string 'tw33dl3'                 [ Not found ]
[05:45:00]     Checking for string 'psniff'                  [ Not found ]
[05:45:00]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:45:00]     Checking for string '/dev/ptyxx'              [ Not found ]
[05:45:00]     Checking for string 'promiscuous'             [ Not found ]
[05:45:00]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:45:00]     Checking for string '/dev/xdta'               [ Not found ]
[05:45:00]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:45:00]     Checking for string 'in.inetd'                [ Not found ]
[05:45:00]     Checking for string '#<HIDE_.*>'              [ Not found ]
[05:45:00]     Checking for string 'bin/xchk'                [ Not found ]
[05:45:00]     Checking for string 'bin/xsf'                 [ Not found ]
[05:45:00]   Checking for possible rootkit strings           [ None found ]
[05:45:00]
[05:45:00] Performing malware checks
[05:45:00] Info: Starting test name 'malware'
[05:45:00]
[05:45:00] Info: Test 'deleted_files' disabled at users request.
[05:45:00] Info: Starting test name 'running_procs'
[05:45:00]   Checking running processes for suspicious files [ None found ]
[05:45:00]
[05:45:00] Info: Test 'hidden_procs' disabled at users request.
[05:45:00]
[05:45:00] Info: Test 'suspscan' disabled at users request.
[05:45:00]
[05:45:00]   Performing check for login backdoors
[05:45:00] Info: Starting test name 'other_malware'
[05:45:00]     Checking for '/media/root//bin/.login'        [ Not found ]
[05:45:00]     Checking for '/media/root//sbin/.login'       [ Not found ]
[05:45:00]   Checking for login backdoors                    [ None found ]
[05:45:00]
[05:45:00]   Performing check for suspicious directories
[05:45:00]     Checking for directory '/media/root//usr/X11R6/bin/.,/copy' [ Not found ]
[05:45:01]     Checking for directory '/media/root//dev/rd/cdb' [ Not found ]
[05:45:01]   Checking for suspicious directories             [ None found ]
[05:45:01]
[05:45:01]   Checking for software intrusions                [ Skipped ]
[05:45:01] Info: Check skipped - tripwire not installed
[05:45:01]
[05:45:01]   Performing check for sniffer log files
[05:45:01]     Checking for file '/media/root//usr/lib/libice.log' [ Not found ]
[05:45:01]   Checking for sniffer log files                  [ None found ]
[05:45:01]
[05:45:01] Performing trojan specific checks
[05:45:01] Info: Starting test name 'trojans'
[05:45:01] Info: Using inetd configuration file '/etc/inetd.conf'
[05:45:01]   Checking for enabled inetd services             [ OK ]
[05:45:01]
[05:45:01]   Performing check for enabled xinetd services
[05:45:01]   Checking for enabled xinetd services            [ Skipped ]
[05:45:01] Info: Check skipped - file '/media/root//etc/xinetd.conf' does not exist.
[05:45:01] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[05:45:01]
[05:45:01] Performing Linux specific checks
[05:45:01] Info: Starting test name 'os_specific'
[05:45:01]   Checking kernel module commands                 [ Warning ]
[05:45:01] Warning: The modules file '/media/root//proc/modules' is missing.
[05:45:01] Info: Using modules pathname of '/media/root//lib/modules'
[05:45:01]   Checking kernel module names                    [ OK ]
[05:45:03]
[05:45:03] Checking the network...
[05:45:03] Info: Starting test name 'network'
[05:45:03] Info: Starting test name 'ports'
[05:45:03]
[05:45:03] Performing check for backdoor ports
[05:45:03]   Checking for UDP port 2001                      [ Not found ]
[05:45:04]   Checking for TCP port 2006                      [ Not found ]
[05:45:04]   Checking for TCP port 2128                      [ Not found ]
[05:45:04]   Checking for TCP port 14856                     [ Not found ]
[05:45:04]   Checking for TCP port 47107                     [ Not found ]
[05:45:04]   Checking for TCP port 60922                     [ Not found ]
[05:45:04]
[05:45:04] Performing checks on the network interfaces
[05:45:04] Info: Starting test name 'promisc'
[05:45:04]   Checking for promiscuous interfaces             [ None found ]
[05:45:04]
[05:45:04] Info: Test 'packet_cap_apps' disabled at users request.
[05:45:05]
[05:45:05] Checking the local host...
[05:45:05] Info: Starting test name 'local_host'
[05:45:05]
[05:45:05] Performing system boot checks
[05:45:05] Info: Starting test name 'startup_files'
[05:45:05]   Checking for local host name                    [ Found ]
[05:45:05] Info: Starting test name 'startup_malware'
[05:45:05] Info: Found local startup file: /media/root//etc/rc.local
[05:45:05]   Checking for local startup files                [ Found ]
[05:45:05]   Checking local startup files for malware        [ None found ]
[05:45:05] Info: Found system startup directory: /media/root//etc/init.d
[05:45:05]   Checking system startup files for malware       [ None found ]
[05:45:05]
[05:45:05] Performing group and account checks
[05:45:05] Info: Starting test name 'group_accounts'
[05:45:05]   Checking for passwd file                        [ Found ]
[05:45:06] Info: Found password file: /media/root//etc/passwd
[05:45:06]   Checking for root equivalent (UID 0) accounts   [ None found ]
[05:45:06] Info: Found shadow file: /media/root//etc/shadow
[05:45:06]   Checking for passwordless accounts              [ None found ]
[05:45:06] Info: Starting test name 'passwd_changes'
[05:45:06]   Checking for passwd file changes                [ None found ]
[05:45:06] Info: Starting test name 'group_changes'
[05:45:06]   Checking for group file changes                 [ None found ]
[05:45:06]   Checking root account shell history files       [ None found ]
[05:45:06]
[05:45:06] Performing system configuration file checks
[05:45:06] Info: Starting test name 'system_configs'
[05:45:06]   Checking for SSH configuration file             [ Found ]
[05:45:06] Info: Found SSH configuration file: /media/root//etc/ssh/sshd_config
[05:45:06] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[05:45:06]   Checking if SSH root access is allowed          [ Not allowed ]
[05:45:06]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[05:45:06]   Checking for running syslog daemon              [ Found ]
[05:45:06]   Checking for syslog configuration file          [ Found ]
[05:45:06] Info: Found syslog configuration file: /media/root//etc/syslog.conf
[05:45:06]   Checking if syslog remote logging is allowed    [ Not allowed ]
[05:45:06]
[05:45:06] Performing filesystem checks
[05:45:06] Info: Starting test name 'filesystem'
[05:45:06] Info: SCAN_MODE_DEV set to 'THOROUGH'
[05:45:07]   Checking /dev for suspicious file types         [ None found ]
[05:45:07] Info: Found hidden directory '/media/root//etc/.java': it is whitelisted.
[05:45:07]   Checking for hidden files and directories       [ None found ]
[05:45:08]
[05:45:08] Checking application versions...
[05:45:08] Info: Starting test name 'apps'
[05:45:13]   Checking version of Exim MTA                    [ OK ]
[05:45:13] Info: Application 'exim' version '4.67' found.
[05:45:13]   Checking version of GnuPG                       [ OK ]
[05:45:13] Info: Application 'gpg' version '1.4.6' found.
[05:45:13] Info: Application 'httpd' not found.
[05:45:13] Info: Application 'named' not found.
[05:45:13]   Checking version of OpenSSL                     [ OK ]
[05:45:13] Info: Application 'openssl' version '0.9.8e' found.
[05:45:13] Info: Application 'php' not found.
[05:45:13] Info: Application 'procmail' not found.
[05:45:13] Info: Application 'proftpd' not found.
[05:45:13] Info: Application 'sshd' not found.
[05:45:13] Info: Applications checked: 3 out of 9
[05:45:13]
[05:45:13] System checks summary
[05:45:13] =====================
[05:45:13]
[05:45:13] File properties checks...
[05:45:13] Files checked: 123
[05:45:13] Suspect files: 123
[05:45:13]
[05:45:13] Rootkit checks...
[05:45:13] Rootkits checked : 110
[05:45:13] Possible rootkits: 0
[05:45:13]
[05:45:13] Applications checks...
[05:45:13] Applications checked: 3
[05:45:13] Suspect applications: 0
[05:45:13]
[05:45:13] The system checks took: 40 seconds
[05:45:13]
[05:45:13] Info: End date is Tue Oct 23 05:45:13 UTC 2007
```

Doesn't look like anything bad... The md5sums on the bad files match the Live CD versions, so I think that's a "They're not in the right place!" issue.

Running chkrootkit gave the following:

```
ROOTDIR is `/media/root/'
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
Checking `gpm'... not infected
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
Checking `mail'... not found
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
/media/root/usr/lib/jvm/.java-7-icedtea.jinfo
/media/root/usr/lib/firefox/.autoreg
/media/root/lib/linux-restricted-modules/.nvidia_new_installed

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
Searching for OBSD rk v1... /media/root/usr/lib/security
/media/root/usr/lib/security/classpath.security
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
Checking `bindshell'... not tested
Checking `lkm'... chkproc: not tested
Checking `rexedcs'... not found
Checking `sniffer'... not tested
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted
```

Again, looks good? Any thing else I should look at?

---

### Post by Imamoomoocow on 2007-10-25
I have to say you should take this up with the IT people at your school. I doubt you could have compromised your work or home computers. Connecting to a remote server from a public computer is a bad idea, Especially if the computer is running Windows.

---

### Post by Falcorian on 2007-10-25
> **Imamoomoocow said:**
> I have to say you should take this up with the IT people at your school. I doubt you could have compromised your work or home computers. Connecting to a remote server from a public computer is a bad idea, Especially if the computer is running Windows.

Yeah, that's the plan. Although I may have given the wrong impression as to the problem, which is as follows:

The work computers were compromised through some hole in a 64bit program that didn't get patched by the admins in time. The attacker then installed a modified ssh and sshd. From these compromised machines, when no one knew they were compromised, I sshed home.

So I'm worried my machine is also compromised, because I logged into it from a machine who's ssh had been taken over. (I just cut all the other names out of the email... Which may make it look like I was the only one. In reality everyone who used the work machine was on the list.)

---

### Post by bodhi.zazen on 2007-10-25
I would disconnect from the internet, image your partition for later analysis, and re-install.

But then again, I am paranoid that way.

---

### Post by Falcorian on 2007-10-25
> **bodhi.zazen said:**
> I would disconnect from the internet, image your partition for later analysis, and re-install.

But then again, I am paranoid that way.
Yeah, after not getting replies I reinstalled from trusted backups... Even probing around with the LiveCD didn't give me enough peace of mind.

---

### Post by Chayak on 2007-10-27
To be honest the standard procedure at many levels of corporate and government for a machine that is even suspected to be compromised is to image the disk forensically and reinstall.  You can pull your personal files off the image later.  If the workstation gets a virus, spyware, or anything it'll get slicked and reimaged.  It's better not to take chances with such things.  Most of the time it's windows machines but there has been two occasions where it was a *nix machine.

---

### Post by htdnet on 2008-05-16
# NOTE: If the hash function is changed then you MUST run rkhunter with
#       the '--propupd' option to rebuild the file properties database.
#
#HASH_FUNC=?????

Make sure your hash function is not enabled manually. I reproduced this problem several times that is why you get the warning errors. Or you just didn't run a 

$ rkhunter --propupd

After you updated your rkhunter.conf run the above command should fix the problem.

---

### Post by htdnet on 2008-05-16
I feel bad for you too because you probably already reimaged your stuff and just missed the directions right there...eeks. Oh well we are all here to learn. I spent a good part of the day upgrading my RootKit Hunter to the latest and getting it to run smoothly with Plesk 8.4 :) hoorah!  :popcorn:

---

