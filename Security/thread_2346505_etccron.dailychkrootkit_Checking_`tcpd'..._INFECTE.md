---
title: "/etc/cron.daily/chkrootkit: Checking `tcpd'... INFECTED,  Is this true or a bug?"
date: 2016-12-15
forum: Security
---

### Post by MechaMechanism on 2016-12-15
Got the following; /etc/cron.daily/chkrootkit:
Checking `tcpd'... INFECTED

Am I really infected?

---

### Post by kpatz on 2016-12-15
What version of Ubuntu are you running?

Run these commands and post the results:

```
sudo find / -name tcpd -ls
sudo sha1sum /usr/sbin/tcpd
```

On both my 14.04 and 16.04, I get this for the sha1sum:```
cd9cfc19df7f0e4b7f9adfa4fe8c5d74caa53d86  /usr/sbin/tcpd
```

If yours is different, it could be infected.

---

### Post by MechaMechanism on 2016-12-15
> **kpatz said:**
> What version of Ubuntu are you running?

Run these commands and post the results:

```
sudo find / -name tcpd -ls
sudo sha1sum /usr/sbin/tcpd
```

On both my 14.04 and 16.04, I get this for the sha1sum:```
cd9cfc19df7f0e4b7f9adfa4fe8c5d74caa53d86  /usr/sbin/tcpd
```

If yours is different, it could be infected.

Ubuntu 16.10 desktop.  Upgraded from 15.10 to 16.04 to 16.10.
```
sudo find / -name tcpd -ls
[sudo] password for nate: 
   141460      0 lrwxrwxrwx   1 root     root            8 Nov 30  2015 /usr/share/doc/tcpd -> libwrap0
  6296010     12 -rwxr-xr-x   1 root     root        10456 Jan 12  2014 /usr/sbin/tcpd
find: ‘/run/user/1000/gvfs’: Permission denied
```

```
sudo sha1sum /usr/sbin/tcpd
cd9cfc19df7f0e4b7f9adfa4fe8c5d74caa53d86  /usr/sbin/tcpd
```

Looks like a false positive.  sha1sums look same.  What you think.

---

### Post by kpatz on 2016-12-15
It probably is a false positive.  Your size, date stamp and sha1 is the same as on mine.  I installed and ran chkrootkit on my 16.04 system and it found no infections.  If you run it manually with 'sudo chkrootkit' what do you get?

---

### Post by MechaMechanism on 2016-12-15
> **kpatz said:**
> It probably is a false positive.  Your size, date stamp and sha1 is the same as on mine.  I installed and ran chkrootkit on my 16.04 system and it found no infections.  If you run it manually with 'sudo chkrootkit' what do you get?

```
sudo chkrootkit
[sudo] password for nate: 
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
Checking `named'...                                         not infected
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not found
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not infected
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          INFECTED
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
/usr/lib/debug/.build-id /usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /lib/modules/4.8.0-30-generic/vdso/.build-id /lib/modules/4.8.0-28-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.8.0-30-generic/vdso/.build-id /lib/modules/4.8.0-28-generic/vdso/.build-id
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
Searching for Linux/Ebury - Operation Windigo ssh...        Possible Linux/Ebury - Operation Windigo installetd
Searching for 64-bit Linux Rootkit ...                      nothing found
Searching for 64-bit Linux Rootkit modules...               nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
enp0s31f6: not promisc and no packet sniffer sockets
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            chklastlog: nothing deleted
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! nate        10925 pts/2  bash
! root        11450 pts/2  /bin/sh /usr/sbin/chkrootkit
! root        12125 pts/2  ./chkutmp
! root        12127 pts/2  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        12126 pts/2  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        11447 pts/2  sudo chkrootkit
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
```

---

### Post by kpatz on 2016-12-15
What version of chkrootkit do you have?  Run```
chkrootkit -V
```My 16.04 system has 0.50.  I'll load 16.10 in a VM and see what version that has.

EDIT: something else I thought of... if you do have a rootkit perhaps it's returning a fake/unaltered version of tcpd when querying it with sha1sum.  Try booting from a live CD/USB, mounting the root partition to /mnt and then running sha1sum on /mnt/usr/sbin/tcpd and see what you get.

---

### Post by MechaMechanism on 2016-12-15
> **kpatz said:**
> What version of chkrootkit do you have?  Run```
chkrootkit -V
```My 16.04 system has 0.50.  I'll load 16.10 in a VM and see what version that has.

```
chkrootkit -V
chkrootkit version 0.50
```  Same as yours.

---

### Post by kpatz on 2016-12-15
Aha!  I just ran it in a freshly installed VM of 16.10 and got:```
kpatz@vmtest1610:~$ sudo chkrootkit -q
[sudo] password for kpatz: 
**Checking `tcpd'... INFECTED**

/usr/lib/debug/.build-id /lib/modules/4.8.0-22-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.8.0-22-generic/vdso/.build-id
Possible Linux/Ebury - Operation Windigo installetd
enp0s3: PACKET SNIFFER(/sbin/dhclient[839])
user kpatz deleted or never logged from lastlog!
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! kpatz        2207 pts/6  bash
! root         2230 pts/6  /bin/sh /usr/sbin/chkrootkit -q
! root         2784 pts/6  ./chkutmp
! root         2786 pts/6  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         2785 pts/6  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root         2220 pts/6  sudo chkrootkit -q
kpatz@vmtest1610:~$ 

```
Looks like a false positive in 16.10.

---

### Post by MechaMechanism on 2016-12-15
> **kpatz said:**
> Aha!  I just ran it in a freshly installed VM of 16.10 and got:```
kpatz@vmtest1610:~$ sudo chkrootkit -q
[sudo] password for kpatz: 
**Checking `tcpd'... INFECTED**

/usr/lib/debug/.build-id /lib/modules/4.8.0-22-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.8.0-22-generic/vdso/.build-id
Possible Linux/Ebury - Operation Windigo installetd
enp0s3: PACKET SNIFFER(/sbin/dhclient[839])
user kpatz deleted or never logged from lastlog!
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! kpatz        2207 pts/6  bash
! root         2230 pts/6  /bin/sh /usr/sbin/chkrootkit -q
! root         2784 pts/6  ./chkutmp
! root         2786 pts/6  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         2785 pts/6  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root         2220 pts/6  sudo chkrootkit -q
kpatz@vmtest1610:~$ 

```
Looks like a false positive in 16.10.

Thanks for your help buddy.  Appreciate it.

---

