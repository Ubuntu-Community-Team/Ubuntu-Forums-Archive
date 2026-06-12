---
title: "Rootkit possible problem"
date: 2009-05-24
forum: Security
---

### Post by mi1k on 2009-05-24
So I am dual booting on a macbookpro with Mac and the new shiny ubuntu 9.04 SOUND WORKS, AWESOME!!! and I got a mac security program called "Rootkit Hunter" It is displaying that I have a rootkit. Here is the output of the scanner. any help? I'm going to bed in afew its 3:20 am right now in ontario Haha.



```
Plastik:~ plastik$ touch /tmp/rkhunter.0.log && echo OS X Rootkit Hunter needs to be started with administrator privileges, please authenticate first. > /tmp/rkhunter.0.log && clear && tail -f /tmp/rkhunter.0.log


















































OS X Rootkit Hunter needs to be started with administrator privileges, please authenticate first.
[ Rootkit Hunter version 1.3.0 ]
Running Rootkit Hunter version 1.3.0 on Plastik

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Skipped ]

  Performing file properties checks
    Checking for prerequisites                               [ Warning ]
The (command properties test) is not completly supported in this version of OSX rootkit hunter
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/csh                                                 [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/test                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/curl                                            [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/egrep                                           [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/fgrep                                           [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/grep                                            [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/login                                           [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/mktemp                                          [ OK ]
    /usr/bin/more                                            [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/readlink                                        [ OK ]
    /usr/bin/sed                                             [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/su                                              [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uname                                           [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /sbin/dmesg                                              [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/md5                                                [ OK ]
    /sbin/mount                                              [ OK ]
    /sbin/nologin                                            [ OK ]
    /usr/sbin/chown                                          [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/lsof                                           [ OK ]
    /usr/sbin/netstat                                        [ OK ]
    /usr/sbin/newsyslog                                      [ OK ]
    /usr/sbin/sysctl                                         [ OK ]
    /usr/sbin/syslogd                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /sw/bin/dpkg                                             [ OK ]
    /sw/bin/dpkg-query                                       [ OK ]
    /sw/bin/md5sum                                           [ OK ]
    /sw/bin/which                                            [ Warning ]
The command '/sw/bin/which' has been replaced by a script: /sw/bin/which: Bourne shell script text executable
    /sw/sbin/mktemp                                          [ OK ]
    /sw/sbin/readlink                                        [ OK ]
    /usr/libexec/tcpd                                        [ OK ]

Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
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
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Checking for possible rootkit files and directories      [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for hidden processes                            [ Skipped ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

Now we run an additional connection check, to inform you about used and listen tcp-ports
and their appropriate process/commands. - This additional check was created by Christian Hornung

There is a LISTEN tcp Port    localhost:60987    created by Process/Command:        aMSN
There is a LISTEN tcp Port    localhost:ipp    created by Process/Command:        launchd

FYI, named services are described in the file /etc/services

There is a CONNECTED tcp Port    http        used by the Process/Command:        firefox-b
There is a CONNECTED tcp Port    msnp        used by the Process/Command:        aMSN


  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ OK ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Warning ]
Syslog configuration file allows remote logging: install.*                        @127.0.0.1:32376

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]
Hidden file found: /usr/share/man/man5/.rhosts.5.gz: gzip compressed data, was ".rhosts.5", from Unix, last modified: Sat Nov 24 17:15:22 2007

Checking application versions...

    Checking version of Apache                               [ OK ]
    Checking version of Bind DNS                             [ OK ]
    Checking version of OpenSSL                              [ OK ]
    Checking version of PHP                                  [ OK ]
    Checking version of Procmail MTA                         [ OK ]
    Checking version of OpenSSH                              [ OK ]


System checks summary
=====================

File properties checks...
    Required commands check failed
    Files checked: 87
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 77
    Possible rootkits: 0

Applications checks...
    Applications checked: 6
    Suspect applications: 0

The system checks took: 2 minutes and 11 seconds

All results have been written to the logfile (/tmp/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/tmp/rkhunter.log)

Many thanks to the founder and developer of the original rootkit hunter:
Michael Boelen from [www.rootkit.nl]("http://www.rootkit.nl/")
```[]("http://www.rootkit.nl")

---

### Post by mi1k on 2009-05-24
Crap, there is a logfile I can go to sorry, I'll post that too. Anyone think its just the Refit GUI I'm using at bootup? I could cat the "which" file and put the code of the file there, I think i will do that too, the log will be in green. the code will be in red.

[SIZE=2][COLOR=SeaGreen]Sorry I didnt know about the code wrapper, I'm pretty new to forums.
[/COLOR][/SIZE]```
-e [03:20:43] Running Rootkit Hunter version 1.3.0 on Plastik
[03:20:43]
-e [03:20:43] Info: Start date is Sun May 24 03:20:43 EDT 2009
[03:20:43]
-e [03:20:43] Checking configuration file and command-line options...
-e [03:20:43] Info: Detected operating system is 'Darwin'
-e [03:20:43] Info: Uname output is 'Darwin Plastik.local 9.7.0 Darwin Kernel Version 9.7.0: Tue Mar 31 22:52:17 PDT 2009; root:xnu-1228.12.14~1/RELEASE_I386 i386'
-e [03:20:43] Info: Command line is /Applications/OSXrkhunter/bin/rkhunter -c -sk
-e [03:20:43] Info: Environment shell is /bin/bash; rkhunter is using sh
-e [03:20:43] Info: Using configuration file '/Applications/OSXrkhunter/etc/rkhunter.conf'
-e [03:20:43] Info: Installation directory is '/Applications/OSXrkhunter'
-e [03:20:43] Info: Using language 'en'
-e [03:20:43] Info: Using '/Applications/OSXrkhunter/var/lib/rkhunter/db' as the database directory
-e [03:20:43] Info: Using '/Applications/OSXrkhunter/lib/rkhunter/scripts' as the support script directory
-e [03:20:43] Info: Using '/usr/bin /bin /usr/sbin /sbin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /sw/bin /sw/sbin /opt/local/bin /opt/local/sbin /usr/libexec /usr/local/libexec' as the command directories
-e [03:20:43] Info: Using '/' as the root directory
-e [03:20:43] Info: Using '/Applications/OSXrkhunter/var/lib/rkhunter/tmp' as the temporary directory
-e [03:20:43] Info: No mail-on-warning address configured
-e [03:20:43] Info: X will automatically be detected
-e [03:20:43] Info: Using second color set
-e [03:20:43] Info: Found the 'diff' command: /usr/bin/diff
-e [03:20:43] Info: Found the 'file' command: /usr/bin/file
-e [03:20:43] Info: Found the 'find' command: /usr/bin/find
-e [03:20:43] Info: Found the 'ifconfig' command: /sbin/ifconfig
-e [03:20:43] Info: Unable to find the 'ip' command
-e [03:20:43] Info: Unable to find the 'ldd' command
-e [03:20:43] Info: Unable to find the 'lsattr' command
-e [03:20:43] Info: Unable to find the 'lsmod' command
-e [03:20:43] Info: Found the 'lsof' command: /usr/sbin/lsof
-e [03:20:43] Info: Found the 'mktemp' command: /usr/bin/mktemp
-e [03:20:43] Info: Found the 'netstat' command: /usr/sbin/netstat
-e [03:20:43] Info: Found the 'perl' command: /usr/bin/perl
-e [03:20:43] Info: Found the 'ps' command: /bin/ps
-e [03:20:43] Info: Found the 'pwd' command: /bin/pwd
-e [03:20:43] Info: Found the 'readlink' command: /Applications/OSXrkhunter/lib/rkhunter/scripts/readlink.sh
-e [03:20:43] Info: Found the 'sort' command: /usr/bin/sort
-e [03:20:43] Info: Found the 'stat' command: /usr/bin/stat
-e [03:20:43] Info: Found the 'strings' command: /usr/bin/strings
-e [03:20:43] Info: Found the 'uniq' command: /usr/bin/uniq
-e [03:20:43] Info: System is not using prelinking
-e [03:20:43] Info: Using the perl SHA1 module for the file hash checks
-e [03:20:43] Info: The hash function field index is set to 1
-e [03:20:43] Info: No package manager specified: using hash function '/usr/bin/perl /Applications/OSXrkhunter/lib/rkhunter/scripts/filehashsha1.pl'
-e [03:20:43] Info: Previous file attributes were stored
-e [03:20:43] Info: Enabled tests are: all
-e [03:20:43] Info: Disabled tests are: suspscan deleted_files packet_cap_apps possible_rkt_strings startup_files startup_malware
-e [03:20:43] Info: All ksyms and kallsyms checks will be skipped - neither file is present on the system.
[03:20:43]
-e [03:20:43] Starting system checks...
[03:20:43]
-e [03:20:43] Checking system commands...
-e [03:20:43] Info: Starting test name 'system_commands'
[03:20:44]
-e [03:20:44] Performing 'strings' command checks
-e [03:20:44] Info: Starting test name 'strings'
-e [03:20:44] Scanning for string /usr/sbin/ntpsx               [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../ls               [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../netstat          [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../lsof             [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../psr              [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../find             [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../pstree           [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../slocate          [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../du               [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../top              [ OK ]
-e [03:20:44] Scanning for string /usr/lib/...                  [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
-e [03:20:44] Scanning for string /usr/lib/.bkit-               [ OK ]
-e [03:20:44] Scanning for string /tmp/.bkp                     [ OK ]
-e [03:20:44] Scanning for string /tmp/.cinik                   [ OK ]
-e [03:20:44] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
-e [03:20:44] Scanning for string /lib/.sso                     [ OK ]
-e [03:20:44] Scanning for string /lib/.so                      [ OK ]
-e [03:20:44] Scanning for string /var/run/...dica/clean        [ OK ]
-e [03:20:44] Scanning for string /var/run/...dica/xl           [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/xdr          [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/psg          [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/secure       [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/rdx          [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/va           [ OK ]
-e [03:20:45] Scanning for string /var/run/...dica/cl.sh        [ OK ]
-e [03:20:45] Scanning for string /usr/bin/.etc                 [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
-e [03:20:45] Scanning for string /bin/sysback                  [ OK ]
-e [03:20:45] Scanning for string /usr/local/bin/sysback        [ OK ]
-e [03:20:45] Scanning for string /usr/lib/.tbd                 [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
-e [03:20:45] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
-e [03:20:46] Scanning for string /usr/info/.torn/sh*           [ OK ]
-e [03:20:46] Scanning for string /usr/src/.****/.1addr         [ OK ]
-e [03:20:46] Scanning for string /usr/src/.****/.1file         [ OK ]
-e [03:20:46] Scanning for string /usr/src/.****/.1proc         [ OK ]
-e [03:20:46] Scanning for string /usr/src/.****/.1logz         [ OK ]
-e [03:20:46] Scanning for string /usr/info/.t0rn               [ OK ]
-e [03:20:46] Scanning for string /dev/.lib                     [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib                 [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib             [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
-e [03:20:46] Scanning for string /dev/.lib/lib/scan            [ OK ]
-e [03:20:46] Scanning for string /usr/src/.****                [ OK ]
-e [03:20:46] Scanning for string /usr/man/man1/man1            [ OK ]
-e [03:20:46] Scanning for string /usr/man/man1/man1/lib        [ OK ]
-e [03:20:46] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
-e [03:20:47] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[03:20:47]
-e [03:20:47] Performing 'shared libraries' checks
-e [03:20:47] Info: Starting test name 'shared_libs'
-e [03:20:47] Checking for preloading variables                 [ None found ]
-e [03:20:47] Checking for preload file                         [ Not found ]
-e [03:20:47] Info: Starting test name 'shared_libs_path'
-e [03:20:47] Checking LD_LIBRARY_PATH variable                 [ Skipped ]
-e [03:20:47] Info: Unable to find the 'ldd' command
[03:20:47]
-e [03:20:47] Performing file properties checks
-e [03:20:47] Info: Starting test name 'properties'
-e [03:20:47] Info: Skipping all immutable-bit checks. This check is only available for Linux systems.
-e [03:20:47] Warning: Checking for prerequisites               [ Warning ]
-e [03:20:47]          The file of stored file properties (rkhunter.dat) does not exist, and so must be created. To do this type in 'rkhunter --propupd'.
[03:20:47]
-e [03:20:47] Warning: WARNING! It is the users responsibility to ensure that when the '--propupd' option
-e            is used, all the files on their system are known to be genuine, and installed from a
-e            reliable source. The rkhunter '--check' option will compare the current file properties
-e            against previously stored values, and report if any values differ. However, rkhunter
-e            cannot determine what has caused the change, that is for the user to do.
-e [03:20:47] /bin/bash                                         [ OK ]
-e [03:20:47] /bin/cat                                          [ OK ]
-e [03:20:47] /bin/chmod                                        [ OK ]
-e [03:20:47] /bin/cp                                           [ OK ]
-e [03:20:47] /bin/csh                                          [ OK ]
-e [03:20:47] /bin/date                                         [ OK ]
-e [03:20:47] /bin/df                                           [ OK ]
-e [03:20:47] /bin/echo                                         [ OK ]
-e [03:20:47] /bin/ed                                           [ OK ]
-e [03:20:47] /bin/kill                                         [ OK ]
-e [03:20:48] /bin/ls                                           [ OK ]
-e [03:20:48] /bin/mv                                           [ OK ]
-e [03:20:48] /bin/ps                                           [ OK ]
-e [03:20:48] /bin/pwd                                          [ OK ]
-e [03:20:48] /bin/sh                                           [ OK ]
-e [03:20:48] /bin/test                                         [ OK ]
-e [03:20:48] /usr/bin/awk                                      [ OK ]
-e [03:20:48] /usr/bin/basename                                 [ OK ]
-e [03:20:48] /usr/bin/curl                                     [ OK ]
-e [03:20:48] /usr/bin/cut                                      [ OK ]
-e [03:20:48] /usr/bin/diff                                     [ OK ]
-e [03:20:48] /usr/bin/dirname                                  [ OK ]
-e [03:20:48] /usr/bin/du                                       [ OK ]
-e [03:20:48] /usr/bin/egrep                                    [ OK ]
-e [03:20:48] /usr/bin/env                                      [ OK ]
-e [03:20:48] /usr/bin/fgrep                                    [ OK ]
-e [03:20:48] /usr/bin/file                                     [ OK ]
-e [03:20:48] /usr/bin/find                                     [ OK ]
-e [03:20:48] /usr/bin/grep                                     [ OK ]
-e [03:20:48] /usr/bin/groups                                   [ OK ]
-e [03:20:49] /usr/bin/head                                     [ OK ]
-e [03:20:49] /usr/bin/id                                       [ OK ]
-e [03:20:49] /usr/bin/killall                                  [ OK ]
-e [03:20:49] /usr/bin/last                                     [ OK ]
-e [03:20:49] /usr/bin/less                                     [ OK ]
-e [03:20:49] /usr/bin/locate                                   [ OK ]
-e [03:20:49] /usr/bin/logger                                   [ OK ]
-e [03:20:49] /usr/bin/login                                    [ OK ]
-e [03:20:49] /usr/bin/mail                                     [ OK ]
-e [03:20:49] /usr/bin/mktemp                                   [ OK ]
-e [03:20:49] /usr/bin/more                                     [ OK ]
-e [03:20:49] /usr/bin/newgrp                                   [ OK ]
-e [03:20:49] /usr/bin/passwd                                   [ OK ]
-e [03:20:49] /usr/bin/perl                                     [ OK ]
-e [03:20:49] /usr/bin/readlink                                 [ OK ]
-e [03:20:49] /usr/bin/sed                                      [ OK ]
-e [03:20:49] /usr/bin/size                                     [ OK ]
-e [03:20:49] /usr/bin/sort                                     [ OK ]
-e [03:20:50] /usr/bin/stat                                     [ OK ]
-e [03:20:50] /usr/bin/strings                                  [ OK ]
-e [03:20:50] /usr/bin/su                                       [ OK ]
-e [03:20:50] /usr/bin/sudo                                     [ OK ]
-e [03:20:50] /usr/bin/tail                                     [ OK ]
-e [03:20:50] /usr/bin/top                                      [ OK ]
-e [03:20:50] /usr/bin/touch                                    [ OK ]
-e [03:20:50] /usr/bin/tr                                       [ OK ]
-e [03:20:50] /usr/bin/uname                                    [ OK ]
-e [03:20:50] /usr/bin/uniq                                     [ OK ]
-e [03:20:50] /usr/bin/users                                    [ OK ]
-e [03:20:50] /usr/bin/w                                        [ OK ]
-e [03:20:50] /usr/bin/wc                                       [ OK ]
-e [03:20:50] /usr/bin/whatis                                   [ OK ]
-e [03:20:50] Info: Found file '/usr/bin/whatis': it is whitelisted for the 'script replacement' check.
-e [03:20:50] /usr/bin/whereis                                  [ OK ]
-e [03:20:50] /usr/bin/which                                    [ OK ]
-e [03:20:50] /usr/bin/who                                      [ OK ]
-e [03:20:50] /usr/bin/whoami                                   [ OK ]
-e [03:20:51] /sbin/dmesg                                       [ OK ]
-e [03:20:51] /sbin/ifconfig                                    [ OK ]
-e [03:20:51] /sbin/md5                                         [ OK ]
-e [03:20:51] /sbin/mount                                       [ OK ]
-e [03:20:51] /sbin/nologin                                     [ OK ]
-e [03:20:51] Info: Found file '/sbin/nologin': it is whitelisted for the 'script replacement' check.
-e [03:20:51] /usr/sbin/chown                                   [ OK ]
-e [03:20:51] /usr/sbin/chroot                                  [ OK ]
-e [03:20:51] /usr/sbin/cron                                    [ OK ]
-e [03:20:51] /usr/sbin/lsof                                    [ OK ]
-e [03:20:51] /usr/sbin/netstat                                 [ OK ]
-e [03:20:51] /usr/sbin/newsyslog                               [ OK ]
-e [03:20:51] /usr/sbin/sysctl                                  [ OK ]
-e [03:20:51] /usr/sbin/syslogd                                 [ OK ]
-e [03:20:51] /usr/sbin/vipw                                    [ OK ]
-e [03:20:51] /sw/bin/dpkg                                      [ OK ]
-e [03:20:51] /sw/bin/dpkg-query                                [ OK ]
-e [03:20:51] /sw/bin/md5sum                                    [ OK ]
-e [03:20:52] /sw/bin/which                                     [ Warning ]
-e [03:20:52] Warning: The command '/sw/bin/which' has been replaced by a script: /sw/bin/which: Bourne shell script text executable
-e [03:20:52] /sw/sbin/mktemp                                   [ OK ]
-e [03:20:52] /sw/sbin/readlink                                 [ OK ]
-e [03:20:52] /usr/libexec/tcpd                                 [ OK ]
[03:20:52]
-e [03:20:52] Checking for rootkits...
-e [03:20:52] Info: Starting test name 'rootkits'
[03:20:52]
-e [03:20:52] Performing check of known rootkit files and directories
-e [03:20:52] Info: Starting test name 'known_rkts'
[03:20:52]
-e [03:20:52] Checking for 55808 Trojan - Variant A...
-e [03:20:52]   Checking for file '/tmp/.../r'                  [ Not found ]
-e [03:20:52]   Checking for file '/tmp/.../a'                  [ Not found ]
-e [03:20:52] 55808 Trojan - Variant A                          [ Not found ]
[03:20:52]
-e [03:20:52] Checking for ADM Worm...
-e [03:20:52]   Checking for string 'w0rm'                      [ Not found ]
-e [03:20:52] ADM Worm                                          [ Not found ]
[03:20:52]
-e [03:20:52] Checking for AjaKit Rootkit...
-e [03:20:52]   Checking for file '/dev/tux/.addr'              [ Not found ]
-e [03:20:52]   Checking for file '/dev/tux/.proc'              [ Not found ]
-e [03:20:52]   Checking for file '/dev/tux/.file'              [ Not found ]
-e [03:20:52]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
-e [03:20:52]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
-e [03:20:52]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
-e [03:20:52]   Checking for directory '/dev/tux'               [ Not found ]
-e [03:20:52]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
-e [03:20:52] AjaKit Rootkit                                    [ Not found ]
[03:20:52]
-e [03:20:52] Checking for aPa Kit...
-e [03:20:53]   Checking for file '/usr/share/.aPa'             [ Not found ]
-e [03:20:53] aPa Kit                                           [ Not found ]
[03:20:53]
-e [03:20:53] Checking for Apache Worm...
-e [03:20:53]   Checking for file '/bin/.log'                   [ Not found ]
-e [03:20:53] Apache Worm                                       [ Not found ]
[03:20:53]
-e [03:20:53] Checking for Ambient (ark) Rootkit...
-e [03:20:53]   Checking for file '/usr/lib/.ark?'              [ Not found ]
-e [03:20:53]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
-e [03:20:53]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
-e [03:20:53]   Checking for directory '/dev/ptyxx'             [ Not found ]
-e [03:20:53] Ambient (ark) Rootkit                             [ Not found ]
[03:20:53]
-e [03:20:53] Checking for Balaur Rootkit...
-e [03:20:53]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
-e [03:20:53]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
-e [03:20:53]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
-e [03:20:53]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
-e [03:20:53] Balaur Rootkit                                    [ Not found ]
[03:20:53]
-e [03:20:53] Checking for BeastKit Rootkit...
-e [03:20:53]   Checking for file '/usr/sbin/arobia'            [ Not found ]
-e [03:20:53]   Checking for file '/usr/sbin/idrun'             [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
-e [03:20:53]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
-e [03:20:54]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
-e [03:20:54] BeastKit Rootkit                                  [ Not found ]
[03:20:54]
-e [03:20:54] Checking for beX2 Rootkit...
-e [03:20:54]   Checking for directory '/usr/include/bex'       [ Not found ]
-e [03:20:54] beX2 Rootkit                                      [ Not found ]
[03:20:54]
-e [03:20:54] Checking for BOBKit Rootkit...
-e [03:20:54]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../ls'             [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../psr'            [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../find'           [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../du'             [ Not found ]
-e [03:20:54]   Checking for file '/usr/lib/.../top'            [ Not found ]
-e [03:20:54]   Checking for directory '/usr/lib/...'           [ Not found ]
-e [03:20:54]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
-e [03:20:54]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
-e [03:20:54]   Checking for directory '/tmp/.bkp'              [ Not found ]
-e [03:20:54] BOBKit Rootkit                                    [ Not found ]
[03:20:54]
-e [03:20:54] Checking for CiNIK Worm (Slapper.B variant)...
-e [03:20:54]   Checking for file '/tmp/.cinik'                 [ Not found ]
-e [03:20:55]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
-e [03:20:55] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[03:20:55]
-e [03:20:55] Checking for Danny-Boy's Abuse Kit...
-e [03:20:55]   Checking for file '/dev/mdev'                   [ Not found ]
-e [03:20:55]   Checking for file '/usr/lib/libX.a'             [ Not found ]
-e [03:20:55] Danny-Boy's Abuse Kit                             [ Not found ]
[03:20:55]
-e [03:20:55] Checking for Devil RootKit...
-e [03:20:55]   Checking for file '/var/lib/games/.src'         [ Not found ]
-e [03:20:55]   Checking for file '/dev/dsx'                    [ Not found ]
-e [03:20:55]   Checking for file '/dev/caca'                   [ Not found ]
-e [03:20:55] Devil RootKit                                     [ Not found ]
[03:20:55]
-e [03:20:55] Checking for Dica-Kit Rootkit...
-e [03:20:55]   Checking for file '/lib/.sso'                   [ Not found ]
-e [03:20:55]   Checking for file '/lib/.so'                    [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/clean'      [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/xl'         [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/psg'        [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/secure'     [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/va'         [ Not found ]
-e [03:20:55]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
-e [03:20:55]   Checking for file '/usr/bin/.etc'               [ Not found ]
-e [03:20:55]   Checking for directory '/var/run/...dica'       [ Not found ]
-e [03:20:55]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
-e [03:20:55]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
-e [03:20:56] Dica-Kit Rootkit                                  [ Not found ]
[03:20:56]
-e [03:20:56] Checking for Dreams Rootkit...
-e [03:20:56]   Checking for file '/dev/ttyoa'                  [ Not found ]
-e [03:20:56]   Checking for file '/dev/ttyof'                  [ Not found ]
-e [03:20:56]   Checking for file '/dev/ttyop'                  [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/sense'              [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/sl2'                [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/logclear'           [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/snfs'               [ Not found ]
-e [03:20:56]   Checking for file '/usr/lib/libsss'             [ Not found ]
-e [03:20:56]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
-e [03:20:56] Dreams Rootkit                                    [ Not found ]
[03:20:56]
-e [03:20:56] Checking for Duarawkz Rootkit...
-e [03:20:56]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
-e [03:20:56]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
-e [03:20:56] Duarawkz Rootkit                                  [ Not found ]
[03:20:56]
-e [03:20:56] Checking for Enye LKM...
-e [03:20:56]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
-e [03:20:56] Enye LKM                                          [ Not found ]
[03:20:56]
-e [03:20:56] Checking for Flea Linux Rootkit...
-e [03:20:56]   Checking for file '/etc/ld.so.hash'             [ Not found ]
-e [03:20:56]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
-e [03:20:56]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
-e [03:20:56]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
-e [03:20:56]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
-e [03:20:56]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
-e [03:20:56]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
-e [03:20:57]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
-e [03:20:57]   Checking for directory '/dev/..0'               [ Not found ]
-e [03:20:57]   Checking for directory '/dev/..0/backup'        [ Not found ]
-e [03:20:57] Flea Linux Rootkit                                [ Not found ]
[03:20:57]
-e [03:20:57] Checking for FreeBSD Rootkit...
-e [03:20:57]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
-e [03:20:57]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
-e [03:20:57]   Checking for file '/bin/sysback'                [ Not found ]
-e [03:20:57]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
-e [03:20:57]   Checking for directory '/usr/lib/.fx'           [ Not found ]
-e [03:20:57]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
-e [03:20:57] FreeBSD Rootkit                                   [ Not found ]
[03:20:57]
-e [03:20:57] Checking for ****`it Rootkit...
-e [03:20:57]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
-e [03:20:57]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
-e [03:20:57] ****`it Rootkit                                   [ Not found ]
[03:20:58]
-e [03:20:58] Checking for GasKit Rootkit...
-e [03:20:58]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
-e [03:20:58]   Checking for directory '/dev/dev'               [ Not found ]
-e [03:20:58]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
-e [03:20:58]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
-e [03:20:58] GasKit Rootkit                                    [ Not found ]
[03:20:58]
-e [03:20:58] Checking for Heroin LKM...
-e [03:20:58]   Checking for kernel symbol 'heroin'             [ Skipped ]
-e [03:20:58] Heroin LKM                                        [ Not found ]
[03:20:58]
-e [03:20:58] Checking for HjC Kit...
-e [03:20:58]   Checking for directory '/dev/.hijackerz'        [ Not found ]
-e [03:20:58] HjC Kit                                           [ Not found ]
[03:20:58]
-e [03:20:58] Checking for ignoKit Rootkit...
-e [03:20:58]   Checking for file '/lib/defs/p'                 [ Not found ]
-e [03:20:58]   Checking for file '/lib/defs/q'                 [ Not found ]
-e [03:20:58]   Checking for file '/lib/defs/r'                 [ Not found ]
-e [03:20:58]   Checking for file '/lib/defs/s'                 [ Not found ]
-e [03:20:58]   Checking for file '/lib/defs/t'                 [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/defs/p'             [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/defs/q'             [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/defs/r'             [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/defs/s'             [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/defs/t'             [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
-e [03:20:58]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
-e [03:20:58]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
-e [03:20:58]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
-e [03:20:59] ignoKit Rootkit                                   [ Not found ]
[03:20:59]
-e [03:20:59] Checking for ImperalsS-FBRK Rootkit...
-e [03:20:59]   Checking for directory '/dev/fd/.88'            [ Not found ]
-e [03:20:59]   Checking for directory '/dev/fd/.99'            [ Not found ]
-e [03:20:59] ImperalsS-FBRK Rootkit                            [ Not found ]
[03:20:59]
-e [03:20:59] Checking for Irix Rootkit...
-e [03:20:59]   Checking for directory '/dev/pts/01'            [ Not found ]
-e [03:20:59]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
-e [03:20:59]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
-e [03:20:59]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
-e [03:20:59] Irix Rootkit                                      [ Not found ]
[03:20:59]
-e [03:20:59] Checking for Kitko Rootkit...
-e [03:20:59]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
-e [03:20:59] Kitko Rootkit                                     [ Not found ]
[03:20:59]
-e [03:20:59] Checking for Knark Rootkit...
-e [03:20:59]   Checking for file '/proc/knark/pids'            [ Not found ]
-e [03:20:59]   Checking for directory '/proc/knark'            [ Not found ]
-e [03:20:59] Knark Rootkit                                     [ Not found ]
[03:20:59]
-e [03:20:59] Checking for Li0n Worm...
-e [03:20:59]   Checking for file '/bin/in.telnetd'             [ Not found ]
-e [03:20:59]   Checking for file '/bin/mjy'                    [ Not found ]
-e [03:20:59]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
-e [03:20:59]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
-e [03:20:59]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
-e [03:20:59]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
-e [03:21:00]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
-e [03:21:00] Li0n Worm                                         [ Not found ]
[03:21:00]
-e [03:21:00] Checking for Lockit / LJK2 Rootkit...
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
-e [03:21:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
-e [03:21:01]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
-e [03:21:01]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
-e [03:21:01] Lockit / LJK2 Rootkit                             [ Not found ]
[03:21:01]
-e [03:21:01] Checking for Mood-NT Rootkit...
-e [03:21:01]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
-e [03:21:01]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
-e [03:21:02]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
-e [03:21:02]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
-e [03:21:02]   Checking for directory '/_cthulhu'              [ Not found ]
-e [03:21:02] Mood-NT Rootkit                                   [ Not found ]
[03:21:02]
-e [03:21:02] Checking for MRK Rootkit...
-e [03:21:02]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
-e [03:21:02]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
-e [03:21:02]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
-e [03:21:02]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
-e [03:21:02]   Checking for directory '/dev/ida/.inet'         [ Not found ]
-e [03:21:02]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
-e [03:21:02] MRK Rootkit                                       [ Not found ]
[03:21:02]
-e [03:21:02] Checking for Ni0 Rootkit...
-e [03:21:02]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
-e [03:21:02]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
-e [03:21:02]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
-e [03:21:02]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
-e [03:21:02]   Checking for directory '/tmp/waza'              [ Not found ]
-e [03:21:02]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
-e [03:21:02]   Checking for directory '/usr/sbin/es'           [ Not found ]
-e [03:21:02] Ni0 Rootkit                                       [ Not found ]
[03:21:02]
-e [03:21:02] Checking for Ohhara Rootkit...
-e [03:21:02]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
-e [03:21:02]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
-e [03:21:02]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
-e [03:21:02]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
-e [03:21:02]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
-e [03:21:03]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
-e [03:21:03]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
-e [03:21:03] Ohhara Rootkit                                    [ Not found ]
[03:21:03]
-e [03:21:03] Checking for Optic Kit (Tux) Worm...
-e [03:21:03]   Checking for directory '/dev/tux'               [ Not found ]
-e [03:21:03]   Checking for directory '/usr/bin/xchk'          [ Not found ]
-e [03:21:03]   Checking for directory '/usr/bin/xsf'           [ Not found ]
-e [03:21:03]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
-e [03:21:03] Optic Kit (Tux) Worm                              [ Not found ]
[03:21:03]
-e [03:21:03] Checking for Oz Rootkit...
-e [03:21:03]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
-e [03:21:03]   Checking for directory '/dev/.oz'               [ Not found ]
-e [03:21:03] Oz Rootkit                                        [ Not found ]
[03:21:03]
-e [03:21:03] Checking for Phalanx Rootkit...
-e [03:21:03]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
-e [03:21:03]   Checking for file '/etc/host.ph1'               [ Not found ]
-e [03:21:03]   Checking for file '/bin/host.ph1'               [ Not found ]
-e [03:21:03]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
-e [03:21:03]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
-e [03:21:03] Phalanx Rootkit                                   [ Not found ]
[03:21:03]
-e [03:21:03] Checking for Portacelo Rootkit...
-e [03:21:03]   Checking for file '/var/lib/.../.ak'            [ Not found ]
-e [03:21:03]   Checking for file '/var/lib/.../.hk'            [ Not found ]
-e [03:21:03]   Checking for file '/var/lib/.../.rs'            [ Not found ]
-e [03:21:03]   Checking for file '/var/lib/.../.p'             [ Not found ]
-e [03:21:03]   Checking for file '/var/lib/.../getty'          [ Not found ]
-e [03:21:03]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../show'           [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
-e [03:21:04]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
-e [03:21:04]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
-e [03:21:04] Portacelo Rootkit                                 [ Not found ]
[03:21:04]
-e [03:21:04] Checking for R3dstorm Toolkit...
-e [03:21:04]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
-e [03:21:04]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
-e [03:21:04]   Checking for file '/bin/.../hate/sk'            [ Not found ]
-e [03:21:04]   Checking for file '/bin/.../see_all'            [ Not found ]
-e [03:21:04]   Checking for directory '/var/log/tk02'          [ Not found ]
-e [03:21:04]   Checking for directory '/var/log/tk02/old'      [ Not found ]
-e [03:21:04]   Checking for directory '/bin/...'               [ Not found ]
-e [03:21:04] R3dstorm Toolkit                                  [ Not found ]
[03:21:04]
-e [03:21:04] Checking for RH-Sharpe's Rootkit...
-e [03:21:04]   Checking for file '/bin/lps'                    [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/lpstree'            [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/ltop'               [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/lkillall'           [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/ldu'                [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/wp'                 [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/shad'               [ Not found ]
-e [03:21:04]   Checking for file '/usr/bin/vadim'              [ Not found ]
-e [03:21:05]   Checking for file '/usr/bin/slice'              [ Not found ]
-e [03:21:05]   Checking for file '/usr/bin/cleaner'            [ Not found ]
-e [03:21:05]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
-e [03:21:05] RH-Sharpe's Rootkit                               [ Not found ]
[03:21:05]
-e [03:21:05] Checking for RSHA's Rootkit...
-e [03:21:05]   Checking for file '/bin/kr4p'                   [ Not found ]
-e [03:21:05]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
-e [03:21:05]   Checking for file '/usr/bin/chsh2'              [ Not found ]
-e [03:21:05]   Checking for file '/usr/bin/slice2'             [ Not found ]
-e [03:21:05]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
-e [03:21:05]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
-e [03:21:05]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
-e [03:21:05]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
-e [03:21:05] RSHA's Rootkit                                    [ Not found ]
[03:21:05]
-e [03:21:05] Checking for Scalper Worm...
-e [03:21:05]   Checking for file '/tmp/.a'                     [ Not found ]
-e [03:21:05]   Checking for file '/tmp/.uua'                   [ Not found ]
-e [03:21:05] Scalper Worm                                      [ Not found ]
[03:21:05]
-e [03:21:05] Checking for Sebek LKM...
-e [03:21:05]   Checking for kernel symbol 'adore or sebek'     [ Skipped ]
-e [03:21:05] Sebek LKM                                         [ Not found ]
[03:21:05]
-e [03:21:05] Checking for Shutdown Rootkit...
-e [03:21:05]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
-e [03:21:05]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
-e [03:21:05]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
-e [03:21:05]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
-e [03:21:05]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
-e [03:21:06]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
-e [03:21:06]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
-e [03:21:06]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
-e [03:21:06] Shutdown Rootkit                                  [ Not found ]
[03:21:06]
-e [03:21:06] Checking for SHV4 Rootkit...
-e [03:21:06]   Checking for file '/etc/ld.so.hash'             [ Not found ]
-e [03:21:06]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
-e [03:21:06]   Checking for file '/lib/lidps1.so'              [ Not found ]
-e [03:21:06]   Checking for file '/usr/sbin/xntps'             [ Not found ]
-e [03:21:06]   Checking for directory '/lib/security/.config'  [ Not found ]
-e [03:21:06]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
-e [03:21:06] SHV4 Rootkit                                      [ Not found ]
[03:21:06]
-e [03:21:06] Checking for SHV5 Rootkit...
-e [03:21:06]   Checking for file '/etc/sh.conf'                [ Not found ]
-e [03:21:06]   Checking for file '/dev/srd0'                   [ Not found ]
-e [03:21:06]   Checking for directory '/usr/lib/libsh'         [ Not found ]
-e [03:21:06] SHV5 Rootkit                                      [ Not found ]
[03:21:06]
-e [03:21:06] Checking for Sin Rootkit...
-e [03:21:06]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
-e [03:21:06]   Checking for file '/dev/ttyoa'                  [ Not found ]
-e [03:21:06]   Checking for file '/dev/ttyof'                  [ Not found ]
-e [03:21:06]   Checking for file '/dev/ttyop'                  [ Not found ]
-e [03:21:06]   Checking for file '/dev/ttyos'                  [ Not found ]
-e [03:21:06]   Checking for file '/usr/lib/.lib'               [ Not found ]
-e [03:21:06]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
-e [03:21:06]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
-e [03:21:06]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
-e [03:21:07]   Checking for file '/usr/man/man1/...'           [ Not found ]
-e [03:21:07]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
-e [03:21:07]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
-e [03:21:07]   Checking for directory '/usr/lib/sn'            [ Not found ]
-e [03:21:07]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
-e [03:21:07]   Checking for directory '/dev/.haos'             [ Not found ]
-e [03:21:07] Sin Rootkit                                       [ Not found ]
[03:21:07]
-e [03:21:07] Checking for Slapper Worm...
-e [03:21:07]   Checking for file '/tmp/.bugtraq'               [ Not found ]
-e [03:21:07]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
-e [03:21:07]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
-e [03:21:07]   Checking for file '/tmp/httpd'                  [ Not found ]
-e [03:21:07]   Checking for file '/tmp/.unlock'                [ Not found ]
-e [03:21:07]   Checking for file '/tmp/update'                 [ Not found ]
-e [03:21:07]   Checking for file '/tmp/.cinik'                 [ Not found ]
-e [03:21:07]   Checking for file '/tmp/.b'                     [ Not found ]
-e [03:21:07] Slapper Worm                                      [ Not found ]
[03:21:07]
-e [03:21:07] Checking for Sneakin Rootkit...
-e [03:21:07]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
-e [03:21:07] Sneakin Rootkit                                   [ Not found ]
[03:21:07]
-e [03:21:07] Checking for Suckit Rootkit...
-e [03:21:07]   Checking for file '/sbin/initsk12'              [ Not found ]
-e [03:21:07]   Checking for file '/sbin/initxrk'               [ Not found ]
-e [03:21:07]   Checking for file '/usr/bin/null'               [ Not found ]
-e [03:21:07]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
-e [03:21:07]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
-e [03:21:07]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
-e [03:21:08]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
-e [03:21:08]   Checking for directory '/etc/.MG'               [ Not found ]
-e [03:21:08]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
-e [03:21:08]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
-e [03:21:08] Suckit Rootkit                                    [ Not found ]
[03:21:08]
-e [03:21:08] Checking for SunOS Rootkit...
-e [03:21:08]   Checking for file '/etc/ld.so.hash'             [ Not found ]
-e [03:21:08]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
-e [03:21:08]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
-e [03:21:08]   Checking for file '/bin/xlogin'                 [ Not found ]
-e [03:21:08]   Checking for file '/usr/lib/crth.o'             [ Not found ]
-e [03:21:08]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
-e [03:21:08]   Checking for file '/sbin/login'                 [ Not found ]
-e [03:21:08]   Checking for file '/lib/security/.config/sn'    [ Not found ]
-e [03:21:08]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
-e [03:21:08]   Checking for file '/dev/kmod'                   [ Not found ]
-e [03:21:08]   Checking for file '/dev/dos'                    [ Not found ]
-e [03:21:08] SunOS Rootkit                                     [ Not found ]
[03:21:08]
-e [03:21:08] Checking for SunOS / NSDAP Rootkit...
-e [03:21:08]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
-e [03:21:09]   Checking for file '/usr/lib/lpset'              [ Not found ]
-e [03:21:09]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
-e [03:21:09] SunOS / NSDAP Rootkit                             [ Not found ]
[03:21:09]
-e [03:21:09] Checking for Superkit Rootkit...
-e [03:21:09]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
-e [03:21:09] Superkit Rootkit                                  [ Not found ]
[03:21:09]
-e [03:21:09] Checking for TBD (Telnet BackDoor)...
-e [03:21:09]   Checking for file '/usr/lib/.tbd'               [ Not found ]
-e [03:21:09] TBD (Telnet BackDoor)                             [ Not found ]
[03:21:09]
-e [03:21:09] Checking for TeLeKiT Rootkit...
-e [03:21:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
-e [03:21:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
-e [03:21:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
-e [03:21:09]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
-e [03:21:09]   Checking for file '/dev/ptyr'                   [ Not found ]
-e [03:21:09]   Checking for file '/dev/ptyp'                   [ Not found ]
-e [03:21:09]   Checking for file '/dev/ptyq'                   [ Not found ]
-e [03:21:10]   Checking for file '/dev/hda06'                  [ Not found ]
-e [03:21:10]   Checking for file '/usr/info/libc1.so'          [ Not found ]
-e [03:21:10]   Checking for directory '/usr/man/man3/...'      [ Not found ]
-e [03:21:10]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
-e [03:21:10]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
-e [03:21:10] TeLeKiT Rootkit                                   [ Not found ]
[03:21:10]
-e [03:21:10] Checking for T0rn Rootkit...
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
-e [03:21:10]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
-e [03:21:11]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
-e [03:21:11]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
-e [03:21:11]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
-e [03:21:11]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
-e [03:21:11]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
-e [03:21:11]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
-e [03:21:11]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
-e [03:21:11]   Checking for file '/usr/info/.t0rn'             [ Not found ]
-e [03:21:11]   Checking for directory '/dev/.lib'              [ Not found ]
-e [03:21:11]   Checking for directory '/dev/.lib/lib'          [ Not found ]
-e [03:21:11]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
-e [03:21:11]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
-e [03:21:11]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
-e [03:21:11]   Checking for directory '/usr/src/.****'         [ Not found ]
-e [03:21:11]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
-e [03:21:11]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
-e [03:21:11]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
-e [03:21:11]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
-e [03:21:11] T0rn Rootkit                                      [ Not found ]
[03:21:11]
-e [03:21:11] Checking for Trojanit Kit...
-e [03:21:11]   Checking for file '/bin/.ls'                    [ Not found ]
-e [03:21:11]   Checking for file '/bin/.ps'                    [ Not found ]
-e [03:21:11]   Checking for file '/bin/.netstat'               [ Not found ]
-e [03:21:11]   Checking for file '/usr/bin/.nop'               [ Not found ]
-e [03:21:11]   Checking for file '/usr/bin/.who'               [ Not found ]
-e [03:21:11] Trojanit Kit                                      [ Not found ]
[03:21:12]
-e [03:21:12] Checking for Tuxtendo Rootkit...
-e [03:21:12]   Checking for file '/dev/tux/.addr'              [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/.cron'              [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/.file'              [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/.log'               [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/.proc'              [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/df'          [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/find'        [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/top'         [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
-e [03:21:12]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
-e [03:21:12]   Checking for directory '/dev/tux'               [ Not found ]
-e [03:21:12]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
-e [03:21:12]   Checking for directory '/dev/tux/backup'        [ Not found ]
-e [03:21:12] Tuxtendo Rootkit                                  [ Not found ]
[03:21:12]
-e [03:21:12] Checking for URK Rootkit...
-e [03:21:12]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
-e [03:21:12]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
-e [03:21:13]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
-e [03:21:13]   Checking for file '/tmp/conf.inf'               [ Not found ]
-e [03:21:13]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
-e [03:21:13] URK Rootkit                                       [ Not found ]
[03:21:13]
-e [03:21:13] Checking for VcKit Rootkit...
-e [03:21:13]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
-e [03:21:13]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
-e [03:21:13] VcKit Rootkit                                     [ Not found ]
[03:21:13]
-e [03:21:13] Checking for Volc Rootkit...
-e [03:21:13]   Checking for directory '/var/spool/.recent'     [ Not found ]
-e [03:21:13]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
-e [03:21:13]   Checking for directory '/usr/lib/volc'          [ Not found ]
-e [03:21:13]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
-e [03:21:13] Volc Rootkit                                      [ Not found ]
[03:21:13]
-e [03:21:13] Checking for X-Org SunOS Rootkit...
-e [03:21:13]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
-e [03:21:13]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
-e [03:21:13]   Checking for file '/usr/bin/srload'             [ Not found ]
-e [03:21:13]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
-e [03:21:13]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
-e [03:21:13]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
-e [03:21:13]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
-e [03:21:13]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
-e [03:21:13]   Checking for directory '/usr/share/man...'      [ Not found ]
-e [03:21:13] X-Org SunOS Rootkit                               [ Not found ]
[03:21:13]
-e [03:21:13] Checking for zaRwT.KiT Rootkit...
-e [03:21:13]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
-e [03:21:13]   Checking for file '/dev/ttyf'                   [ Not found ]
-e [03:21:14]   Checking for file '/dev/ttyp'                   [ Not found ]
-e [03:21:14]   Checking for file '/dev/ttyn'                   [ Not found ]
-e [03:21:14]   Checking for file '/rk/tulz'                    [ Not found ]
-e [03:21:14]   Checking for directory '/rk'                    [ Not found ]
-e [03:21:14]   Checking for directory '/dev/rd/s'              [ Not found ]
-e [03:21:14] zaRwT.KiT Rootkit                                 [ Not found ]
[03:21:14]
-e [03:21:14] Performing additional rootkit checks
-e [03:21:14] Info: Starting test name 'additional_rkts'
[03:21:14]
-e [03:21:14]   Performing check of possible rootkit files and directories
-e [03:21:14] Info: Starting test name 'possible_rkt_files'
-e [03:21:14]     Checking for file '/dev/sdr0'                 [ Not found ]
-e [03:21:14]     Checking for file '/tmp/.syshackfile'         [ Not found ]
-e [03:21:14]     Checking for file '/tmp/.bash_history'        [ Not found ]
-e [03:21:14]     Checking for file '/usr/info/.clib'           [ Not found ]
-e [03:21:14]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
-e [03:21:14]     Checking for file '/usr/bin/take/pid'         [ Not found ]
-e [03:21:14]     Checking for file '/sbin/create'              [ Not found ]
-e [03:21:14]     Checking for file '/dev/ttypz'                [ Not found ]
-e [03:21:14]     Checking for directory '/usr/bin/take'        [ Not found ]
-e [03:21:14]     Checking for directory '/usr/src/.lib'        [ Not found ]
-e [03:21:14]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
-e [03:21:14]     Checking for directory '/lib/lblip.tk'        [ Not found ]
-e [03:21:14]     Checking for directory '/usr/sbin/...'        [ Not found ]
-e [03:21:15]     Checking for directory '/usr/share/.gun'      [ Not found ]
-e [03:21:15]   Checking for possible rootkit files and directories [ None found ]
[03:21:15]
-e [03:21:15] Info: Test 'possible_rkt_strings' disabled at users request.
[03:21:15]
-e [03:21:15] Performing malware checks
-e [03:21:15] Info: Starting test name 'malware'
[03:21:15]
-e [03:21:15] Info: Test 'deleted_files' disabled at users request.
-e [03:21:15] Info: Starting test name 'running_procs'
-e [03:21:16]   Checking running processes for suspicious files [ None found ]
-e [03:21:16] Info: Starting test name 'hidden_procs'
-e [03:21:16]   Checking for hidden processes                   [ Skipped ]
-e [03:21:16] Info: Unable to find the 'unhide' command
[03:21:16]
-e [03:21:16] Info: Test 'suspscan' disabled at users request.
[03:21:16]
-e [03:21:16]   Performing check for login backdoors
-e [03:21:16] Info: Starting test name 'other_malware'
-e [03:21:16]     Checking for '/bin/.login'                    [ Not found ]
-e [03:21:16]     Checking for '/sbin/.login'                   [ Not found ]
-e [03:21:16]   Checking for login backdoors                    [ None found ]
[03:21:16]
-e [03:21:16]   Performing check for suspicious directories
-e [03:21:16]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
-e [03:21:16]     Checking for directory '/dev/rd/cdb'          [ Not found ]
-e [03:21:16]   Checking for suspicious directories             [ None found ]
[03:21:16]
-e [03:21:16]   Checking for software intrusions                [ Skipped ]
-e [03:21:16] Info: Check skipped - tripwire not installed
[03:21:16]
-e [03:21:16]   Performing check for sniffer log files
-e [03:21:16]     Checking for file '/usr/lib/libice.log'       [ Not found ]
-e [03:21:16]   Checking for sniffer log files                  [ None found ]
[03:21:16]
-e [03:21:16] Performing trojan specific checks
-e [03:21:16] Info: Starting test name 'trojans'
-e [03:21:16]   Checking for enabled inetd services             [ Skipped ]
-e [03:21:16] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[03:21:16]
-e [03:21:16]   Performing check for enabled xinetd services
-e [03:21:16]   Checking for enabled xinetd services            [ Skipped ]
-e [03:21:16] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
-e [03:21:16] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[03:21:16]
-e [03:21:16] Performing Darwin specific checks
-e [03:21:16] Info: Starting test name 'os_specific'
-e [03:21:17] Info: No specific tests available
[03:21:17]
-e [03:21:17] Checking the network...
-e [03:21:17] Info: Starting test name 'network'
-e [03:21:17] Info: Starting test name 'ports'
[03:21:17]
-e [03:21:17] Performing check for backdoor ports
-e [03:21:17]   Checking for UDP port 2001                      [ Not found ]
-e [03:21:17]   Checking for TCP port 2006                      [ Not found ]
-e [03:21:17]   Checking for TCP port 2128                      [ Not found ]
-e [03:21:17]   Checking for TCP port 14856                     [ Not found ]
-e [03:21:17]   Checking for TCP port 47107                     [ Not found ]
-e [03:21:17]   Checking for TCP port 60922                     [ Not found ]
[03:22:49]
-e [03:22:49] Performing checks on the network interfaces
-e [03:22:49] Info: Starting test name 'promisc'
-e [03:22:49]   Checking for promiscuous interfaces             [ None found ]
-e [03:22:49] Info: Test 'packet_cap_apps' skipped due to O/S: /proc/net/packet required
[03:22:49]
-e [03:22:49] Checking the local host...
-e [03:22:49] Info: Starting test name 'local_host'
[03:22:49]
-e [03:22:49] Info: Test 'startup_files' disabled at users request.
[03:22:49]
-e [03:22:49] Performing group and account checks
-e [03:22:49] Info: Starting test name 'group_accounts'
-e [03:22:49]   Checking for passwd file                        [ Found ]
-e [03:22:49] Info: Found password file: /etc/passwd
-e [03:22:49]   Checking for root equivalent (UID 0) accounts   [ None found ]
-e [03:22:49] Info: Found shadow file: /private/etc/passwd
-e [03:22:49]   Checking for passwordless accounts              [ None found ]
-e [03:22:49] Info: Starting test name 'passwd_changes'
-e [03:22:49]   Checking for passwd file changes                [ None found ]
-e [03:22:49] Info: Starting test name 'group_changes'
-e [03:22:49]   Checking for group file changes                 [ None found ]
-e [03:22:49]   Checking root account shell history files       [ None found ]
[03:22:49]
-e [03:22:49] Performing system configuration file checks
-e [03:22:49] Info: Starting test name 'system_configs'
-e [03:22:49]   Checking for SSH configuration file             [ Found ]
-e [03:22:49] Info: Found SSH configuration file: /etc/sshd_config
-e [03:22:49] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'yes'.
-e [03:22:49]   Checking if SSH root access is allowed          [ OK ]
-e [03:22:50]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
-e [03:22:50]   Checking for running syslog daemon              [ Found ]
-e [03:22:50]   Checking for syslog configuration file          [ Found ]
-e [03:22:50] Info: Found syslog configuration file: /etc/syslog.conf
-e [03:22:50]   Checking if syslog remote logging is allowed    [ Warning ]
-e [03:22:50] Warning: Syslog configuration file allows remote logging: install.*                        @127.0.0.1:32376
[03:22:50]
-e [03:22:50] Performing filesystem checks
-e [03:22:50] Info: Starting test name 'filesystem'
-e [03:22:50] Info: SCAN_MODE_DEV set to 'THOROUGH'
-e [03:22:50] Info: Found file '/dev/fd/3': it is whitelisted.
-e [03:22:50] Info: Found file '/dev/fd/4': it is whitelisted.
-e [03:22:50] Info: Found file '/dev/fd/5': it is whitelisted.
-e [03:22:53]   Checking /dev for suspicious file types         [ None found ]
-e [03:22:53]   Checking for hidden files and directories       [ Warning ]
-e [03:22:53] Warning: Hidden file found: /usr/share/man/man5/.rhosts.5.gz: gzip compressed data, was ".rhosts.5", from Unix, last modified: Sat Nov 24 17:15:22 2007
[03:22:53]
-e [03:22:53] Checking application versions...
-e [03:22:53] Info: Starting test name 'apps'
-e [03:22:54] Info: Application 'exim' not found.
-e [03:22:54] Info: Application 'gpg' not found.
-e [03:22:54]   Checking version of Apache                      [ OK ]
-e [03:22:54] Info: Application 'httpd' version '2.2.11' found.
-e [03:22:54]   Checking version of Bind DNS                    [ OK ]
-e [03:22:54] Info: Application 'named' version '9.4.3' found.
-e [03:22:54]   Checking version of OpenSSL                     [ OK ]
-e [03:22:54] Info: Application 'openssl' version '0.9.7l' found.
-e [03:22:54]   Checking version of PHP                         [ OK ]
-e [03:22:54] Info: Application 'php' version '5.2.8' found.
-e [03:22:54]   Checking version of Procmail MTA                [ OK ]
-e [03:22:54] Info: Application 'procmail' version '3.22' found.
-e [03:22:54] Info: Application 'proftpd' not found.
-e [03:22:54]   Checking version of OpenSSH                     [ OK ]
-e [03:22:54] Info: Application 'sshd' version '5.1p1' found.
-e [03:22:54] Info: Applications checked: 6 out of 9
[03:22:54]
-e [03:22:54] System checks summary
-e [03:22:54] =====================
[03:22:54]
-e [03:22:54] File properties checks...
-e [03:22:54] Required commands check failed
-e [03:22:55] Files checked: 87
-e [03:22:55] Suspect files: 1
[03:22:55]
-e [03:22:55] Rootkit checks...
-e [03:22:55] Rootkits checked : 77
-e [03:22:55] Possible rootkits: 0
[03:22:55]
-e [03:22:55] Applications checks...
-e [03:22:55] Applications checked: 6
-e [03:22:55] Suspect applications: 0
[03:22:55]
-e [03:22:55] The system checks took: 2 minutes and 11 seconds
[03:22:55]
-e [03:22:55] Info: End date is Sun May 24 03:22:55 EDT 2009
```[COLOR=Red](I also noticed it said there were other problems in it too. Could this all just be from the Refit?

And now running cat command on the which file[/COLOR]

```
#! /bin/sh
set -ef

if [ "$#" = "0" ]; then
 ALLRET=1
else
 ALLRET=0
fi
case $PATH in
 *::) : "not *DIR:" ;;
  *:) PATH="$PATH:" ;;
esac
for PROGRAM in "$@"; do
 RET=1
 IFS_SAVE="$IFS"
 IFS=:
 case $PROGRAM in
  */*)
   if [ -f "$PROGRAM" ] && [ -x "$PROGRAM" ]; then
    printf '%s\n' "$PROGRAM"
    RET=0
   fi
   ;;
  *)
   for ELEMENT in $PATH; do
    if [ -z "$ELEMENT" ]; then
     ELEMENT=.
    fi
    if [ -f "$ELEMENT/$PROGRAM" ] && [ -x "$ELEMENT/$PROGRAM" ]; then
     printf '%s\n' "$ELEMENT/$PROGRAM"
     RET=0
     break
    fi
   done
   ;;
 esac
 IFS="$IFS_SAVE"
 if [ "$RET" != "0" ]; then
  ALLRET=1
 fi
done

exit "$ALLRET"

```

---

