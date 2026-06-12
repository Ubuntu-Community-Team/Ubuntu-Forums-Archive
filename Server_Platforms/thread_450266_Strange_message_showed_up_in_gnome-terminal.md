---
title: "Strange message showed up in gnome-terminal"
date: 2007-05-21
forum: Server Platforms
---

### Post by fakie_flip on 2007-05-21
I was pinging a computer, and out of no where I got this message in gnome-terminal.

```
xploit code for critical security vulnerabilities in Firefox was available for 9 days before Mozilla shipped a patch to remedy the problem.[35]

A 2006 Symantec
```Where did this message come from? Symantec? That is for windows, not Linux, and I hate it. I included a picture. I removed the computers ip from the picture to protect its anonymity. It already gets lots of brute force attacks for ssh.

---

### Post by mbradlcu on 2007-05-22
this is weird, the only time I've seen something like this what running konqueror (how ever it's spelled) from gnome.. if evoked from a terminal,, after it was closed, sometimes it would write to standard out a minute later... anyway I would install chkrootkit and rkhunter, and start looking at traffic and the logs to see if you have any un-invited guests.. please keep me posted,

---

### Post by fakie_flip on 2007-05-22
I've had chkrootkit for a while, and it gets run automatically by cron every day. Here is the results of me running it.

```
chris@ubuntu:~/Desktop$ sudo chkrootkit 
Password:
ROOTDIR is `/'
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
Checking `gpm'... not found
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
Checking `sendmail'... not found
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
/usr/lib/firefox/.autoreg
/usr/lib/ruby/gems/1.8/gems/actionpack-1.13.2/examples/.htaccess
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.5/examples/.htaccess
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/VMware/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/URI/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/VmdbPerl/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/VmPerl/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/HConfig/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/XML/Parser/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/XML/DOM/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/MIME/Base64/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/Authen/PAM/.packlist
/usr/lib/jvm/java-6-sun-1.6.0.00/.systemPrefs
/usr/lib/jvm/.java-6-sun.jinfo
/lib/modules/2.6.20-15-generic/volatile/.mounted

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
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
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
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[4145])
vmnet1: not promisc and no packet sniffer sockets
vmnet8: not promisc and no packet sniffer sockets
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted
chris@ubuntu:~/Desktop$ 
```

I didn't have rkhunter, but I installed it. Here are the results from it.

```
chris@ubuntu:~/Desktop$ sudo rkhunter --checkallPassword:


Rootkit Hunter 1.2.9 is running

Determining OS... Ready


Checking binaries
* Selftests
     Strings (command)                                        [ OK ]


* System tools
  Performing 'known bad' check...
   /bin/cat                                                   [ OK ]
   /bin/chmod                                                 [ OK ]
   /bin/chown                                                 [ OK ]
   /bin/date                                                  [ OK ]
   /bin/df                                                    [ OK ]
   /bin/dmesg                                                 [ OK ]
   /bin/echo                                                  [ OK ]
   /bin/ed                                                    [ OK ]
   /bin/egrep                                                 [ OK ]
   /bin/fgrep                                                 [ OK ]
   /bin/grep                                                  [ OK ]
   /bin/kill                                                  [ OK ]
   /bin/login                                                 [ OK ]
   /bin/ls                                                    [ OK ]
   /bin/more                                                  [ OK ]
   /bin/mount                                                 [ OK ]
   /bin/netstat                                               [ OK ]
   /bin/ps                                                    [ OK ]
   /bin/sh                                                    [ OK ]
   /bin/su                                                    [ OK ]
   /sbin/depmod                                               [ OK ]
   /sbin/ifconfig                                             [ OK ]
   /sbin/ifdown                                               [ OK ]
   /sbin/ifup                                                 [ OK ]
   /sbin/init                                                 [ OK ]
   /sbin/insmod                                               [ OK ]
   /sbin/ip                                                   [ OK ]
   /sbin/lsmod                                                [ OK ]
   /sbin/modinfo                                              [ OK ]
   /sbin/modprobe                                             [ OK ]
   /sbin/rmmod                                                [ OK ]
   /sbin/runlevel                                             [ OK ]
   /sbin/sulogin                                              [ OK ]
   /sbin/sysctl                                               [ OK ]
   /sbin/syslogd                                              [ OK ]
   /usr/bin/basename                                          [ OK ]
   /usr/bin/chattr                                            [ OK ]
   /usr/bin/du                                                [ OK ]
   /usr/bin/file                                              [ OK ]
   /usr/bin/find                                              [ OK ]
   /usr/bin/groups                                            [ OK ]
   /usr/bin/head                                              [ OK ]
   /usr/bin/killall                                           [ OK ]
   /usr/bin/last                                              [ OK ]
   /usr/bin/lastlog                                           [ OK ]
   /usr/bin/less                                              [ OK ]
   /usr/bin/locate                                            [ OK ]
   /usr/bin/logger                                            [ OK ]
   /usr/bin/lsattr                                            [ OK ]
   /usr/bin/md5sum                                            [ OK ]
   /usr/bin/passwd                                            [ OK ]
   /usr/bin/pstree                                            [ OK ]
   /usr/bin/sha1sum                                           [ OK ]
   /usr/bin/size                                              [ OK ]
   /usr/bin/slocate                                           [ OK ]
   /usr/bin/sort                                              [ OK ]
   /usr/bin/stat                                              [ OK ]
   /usr/bin/strace                                            [ OK ]
   /usr/bin/strings                                           [ OK ]
   /usr/bin/test                                              [ OK ]
   /usr/bin/top                                               [ OK ]
   /usr/bin/touch                                             [ OK ]
   /usr/bin/users                                             [ OK ]
   /usr/bin/vmstat                                            [ OK ]
   /usr/bin/w                                                 [ OK ]
   /usr/bin/watch                                             [ OK ]
   /usr/bin/wc                                                [ OK ]
   /usr/bin/wget                                              [ OK ]
   /usr/bin/whatis                                            [ OK ]
   /usr/bin/whereis                                           [ OK ]
   /usr/bin/which                                             [ OK ]
   /usr/bin/who                                               [ OK ]
   /usr/bin/whoami                                            [ OK ]
   /usr/sbin/adduser                                          [ OK ]
   /usr/sbin/chroot                                           [ OK ]
   /usr/sbin/cron                                             [ OK ]
   /usr/sbin/tcpd                                             [ OK ]
   /usr/sbin/useradd                                          [ OK ]
   /usr/sbin/usermod                                          [ OK ]
   /usr/sbin/vipw                                             [ OK ]
   /usr/sbin/xinetd                                           [ OK ]
  Performing 'known good' check...
Info: Check skipped - no hashes available

[Press <ENTER> to continue]



Check rootkits
* Default files and directories
   Rootkit '55808 Trojan - Variant A'...                      [ OK ]
   ADM Worm...                                                [ OK ]
   Rootkit 'AjaKit'...                                        [ OK ]
   Rootkit 'aPa Kit'...                                       [ OK ]
   Rootkit 'Apache Worm'...                                   [ OK ]
   Rootkit 'Ambient (ark) Rootkit'...                         [ OK ]
   Rootkit 'Balaur Rootkit'...                                [ OK ]
   Rootkit 'BeastKit'...                                      [ OK ]
   Rootkit 'beX2'...                                          [ OK ]
   Rootkit 'BOBKit'...                                        [ OK ]
   Rootkit 'CiNIK Worm (Slapper.B variant)'...                [ OK ]
   Rootkit 'Danny-Boy's Abuse Kit'...                         [ OK ]
   Rootkit 'Devil RootKit'...                                 [ OK ]
   Rootkit 'Dica'...                                          [ OK ]
   Rootkit 'Dreams Rootkit'...                                [ OK ]
   Rootkit 'Duarawkz'...                                      [ OK ]
   Rootkit 'Flea Linux Rootkit'...                            [ OK ]
   Rootkit 'FreeBSD Rootkit'...                               [ OK ]
   Rootkit '****`it Rootkit'...                               [ OK ]
   Rootkit 'GasKit'...                                        [ OK ]
   Rootkit 'Heroin LKM'...                                    [ OK ]
   Rootkit 'HjC Kit'...                                       [ OK ]
   Rootkit 'ignoKit'...                                       [ OK ]
   Rootkit 'ImperalsS-FBRK'...                                [ OK ]
   Rootkit 'Irix Rootkit'...                                  [ OK ]
   Rootkit 'Kitko'...                                         [ OK ]
   Rootkit 'Knark'...                                         [ OK ]
   Rootkit 'Li0n Worm'...                                     [ OK ]
   Rootkit 'Lockit / LJK2'...                                 [ OK ]
   Rootkit 'MRK'...                                           [ OK ]
   Rootkit 'Ni0 Rootkit'...                                   [ OK ]
   Rootkit 'RootKit for SunOS / NSDAP'...                     [ OK ]
   Rootkit 'Optic Kit (Tux)'...                               [ OK ]
   Rootkit 'Oz Rootkit'...                                    [ OK ]
   Rootkit 'Portacelo'...                                     [ OK ]
   Rootkit 'R3dstorm Toolkit'...                              [ OK ]
   Rootkit 'RH-Sharpe's rootkit'...                           [ OK ]
   Rootkit 'RSHA's rootkit'...                                [ OK ]
   Sebek LKM...                                               [ OK ]
   Rootkit 'Scalper Worm'...                                  [ OK ]
   Rootkit 'Shutdown'...                                      [ OK ]
   Rootkit 'SHV4'...                                          [ OK ]
   Rootkit 'SHV5'...                                          [ OK ]
   Rootkit 'Sin Rootkit'...                                   [ OK ]
   Rootkit 'Slapper'...                                       [ OK ]
   Rootkit 'Sneakin Rootkit'...                               [ OK ]
   Rootkit 'Suckit Rootkit'...                                [ OK ]
   Rootkit 'SunOS Rootkit'...                                 [ OK ]
   Rootkit 'Superkit'...                                      [ OK ]
   Rootkit 'TBD (Telnet BackDoor)'...                         [ OK ]
   Rootkit 'TeLeKiT'...                                       [ OK ]
   Rootkit 'T0rn Rootkit'...                                  [ OK ]
   Rootkit 'Trojanit Kit'...                                  [ OK ]
   Rootkit 'Tuxtendo'...                                      [ OK ]
   Rootkit 'URK'...                                           [ OK ]
   Rootkit 'VcKit'...                                         [ OK ]
   Rootkit 'Volc Rootkit'...                                  [ OK ]
   Rootkit 'X-Org SunOS Rootkit'...                           [ OK ]
   Rootkit 'zaRwT.KiT Rootkit'...                             [ OK ]

* Suspicious files and malware
   Scanning for known rootkit strings                         [ OK ]
   Scanning for known rootkit files                           [ OK ]
   Testing running processes...                               [ OK ]
   Miscellaneous Login backdoors                              [ OK ]
   Miscellaneous directories                                  [ OK ]
   Software related files                                     [ OK ]
   Sniffer logs                                               [ OK ]

[Press <ENTER> to continue]


* Trojan specific characteristics
   shv4
     Checking /etc/rc.d/rc.sysinit                            [ Not found ]
     Checking /etc/inetd.conf                                 [ Clean ]
     Checking /etc/xinetd.conf                                [ Clean ]

* Suspicious file properties
   chmod properties
     Checking /bin/ps                                         [ Clean ]
     Checking /bin/ls                                         [ Clean ]
     Checking /usr/bin/w                                      [ Clean ]
     Checking /usr/bin/who                                    [ Clean ]
     Checking /bin/netstat                                    [ Clean ]
     Checking /bin/login                                      [ Clean ]
   Script replacements
     Checking /bin/ps                                         [ Clean ]
     Checking /bin/ls                                         [ Clean ]
     Checking /usr/bin/w                                      [ Clean ]
     Checking /usr/bin/who                                    [ Clean ]
     Checking /bin/netstat                                    [ Clean ]
     Checking /bin/login                                      [ Clean ]

* OS dependant tests

   Linux
     Checking loaded kernel modules...                        [ OK ]
     Checking file attributes                                 [ OK ]
     Checking LKM module path                                 [ OK ]


Networking
* Check: frequently used backdoors
  Port 2001: Scalper Rootkit                                  [ OK ]
  Port 2006: CB Rootkit                                       [ OK ]
  Port 2128: MRK                                              [ OK ]
  Port 14856: Optic Kit (Tux)                                 [ OK ]
  Port 47107: T0rn Rootkit                                    [ OK ]
  Port 60922: zaRwT.KiT                                       [ OK ]

* Interfaces
     Scanning for promiscuous interfaces...                   [ OK ]

[Press <ENTER> to continue]



System checks
* Allround tests
   Checking hostname... Found. Hostname is ubuntu
   Checking for passwordless user accounts... OK
   Checking for differences in user accounts...                    [ NA ]
   Checking for differences in user groups... Creating file It seems this is your first time.
   Checking boot.local/rc.local file... 
     - /etc/rc.local                                          [ OK ]
     - /etc/rc.d/rc.local                                     [ Not found ]
     - /usr/local/etc/rc.local                                [ Not found ]
     - /usr/local/etc/rc.d/rc.local                           [ Not found ]
     - /etc/conf.d/local.start                                [ Not found ]
     - /etc/init.d/boot.local                                 [ Not found ]
   Checking rc.d files...                                     [ Not found ]
   Checking history files
     Bourne Shell                                             [ OK ]

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock
/etc/.java /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

[Press <ENTER> to continue]



Application advisories
* Application scan
   Checking Apache2 modules ...                               [ OK ]
   Checking Apache configuration ...                          [ OK ]

* Application version scan
   - Exim MTA 4.63                                            [ Unknown ]
gpg: WARNING: unsafe ownership on configuration file `/home/chris/.gnupg/gpg.conf'
   - GnuPG 1.4.6                                              [ Unknown ]
   - OpenSSL 0.9.8c                                           [ Unknown ]

Your system contains some unknown version numbers. Please run Rootkit Hunter
with the --update parameter or contact us through the Rootkit Hunter mailinglist
at rkhunter-users@lists.sourceforge.net.


Security advisories
* Check: Groups and Accounts
   Searching for /etc/passwd...                               [ Found ]
   Checking users with UID '0' (root)...                      [ OK ]

* Check: SSH
   Searching for sshd_config... 
   Found /etc/ssh/sshd_config
   Checking for allowed root login... Watch out Root login possible. Possible risk!
    info: "PermitRootLogin yes" found in file /etc/ssh/sshd_config
    Hint: See logfile for more information about this issue
   Checking for allowed protocols...                          [ OK (Only SSH2 allowed) ]

* Check: Events and Logging
   Search for syslog configuration...                         [ OK ]
   Checking for running syslog slave...                       [ OK ]
   Checking for logging to remote system...                   [ OK (no remote logging) ]

[Press <ENTER> to continue]



---------------------------- Scan results ----------------------------

MD5 scan
Scanned files: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 1445 seconds

-----------------------------------------------------------------------

Do you have some problems, undetected rootkits, false positives, ideas
or suggestions? Please e-mail us through the Rootkit Hunter mailinglist
at rkhunter-users@lists.sourceforge.net.

-----------------------------------------------------------------------
chris@ubuntu:~/Desktop$ 
```

I also have the protection of a router. What do you think?

---

### Post by falcon15500 on 2007-05-22
Without having a lot to base it on - I suspect an overflow condition.

falc

---

### Post by fakie_flip on 2007-05-22
What is an overflow condition? What do you mean?

---

### Post by battleshipterry on 2007-05-22
I have similer results I will post them for you. just posted the warning part down everything above was ok or clean. I run fiesty. wish I could be more help just new at this thanks for posting question I am also curious.




* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock
/etc/.java /dev/.tmp-22-0
/dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /etc/.java (directory)  /dev/.tmp-22-0 (block special (22/0))  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

[Press <ENTER> to continue]



Application advisories
* Application scan
   Checking Apache2 modules ...                               [ OK ]
   Checking Apache configuration ...                          [ OK ]

* Application version scan
   - Exim MTA 4.63                                            [ Unknown ]
   - GnuPG 1.4.6                                              [ Unknown ]
   - OpenSSL 0.9.8c                                           [ Unknown ]

Your system contains some unknown version numbers. Please run Rootkit Hunter
with the --update parameter or contact us through the Rootkit Hunter mailinglist
at [email]rkhunter-users@lists.sourceforge.net[/email].


Security advisories
* Check: Groups and Accounts
   Searching for /etc/passwd...                               [ Found ]
   Checking users with UID '0' (root)...                      [ OK ]

* Check: SSH
   Searching for sshd_config... 

* Check: Events and Logging
   Search for syslog configuration...                         [ OK ]
   Checking for running syslog slave...                       [ OK ]
   Checking for logging to remote system...                   [ OK (no remote logging) ]

[Press <ENTER> to continue]



---------------------------- Scan results ----------------------------

MD5 scan
Scanned files: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 82 seconds

-----------------------------------------------------------------------

Do you have some problems, undetected rootkits, false positives, ideas
or suggestions? Please e-mail us through the Rootkit Hunter mailinglist
at [email]rkhunter-users@lists.sourceforge.net[/email].

-----------------------------------------------------------------------
root@ski-desktop:~#

---

### Post by falcon15500 on 2007-05-23
> **fakie_flip said:**
> What is an overflow condition? What do you mean?

A memory overflow.  Bascially one of the programs in use may be reading from or writing to memory that belongs to another program.  As I said, without a lot to base it on - that's what it looks like.  It doesn't look like a hack attempt to me - more likely a program bug.

falc

---

### Post by battleshipterry on 2007-05-23
I have seen memory leakage and video slows down. if it is the same as memory overflow a reboot will solve it and run another scan it should clear up results I cannot explain memory leakage other then over time video slows.a device I repair that runs in a linux OS has this problem.just reboot and recheck results memory overflow should be similar.

---

