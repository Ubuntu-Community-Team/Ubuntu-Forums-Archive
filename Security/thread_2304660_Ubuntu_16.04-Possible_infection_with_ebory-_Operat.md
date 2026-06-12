---
title: "Ubuntu 16.04-Possible infection with ebory- Operation Windigo installetd"
date: 2015-11-28
forum: Security
---

### Post by Eriamieka on 2015-11-28
Hey all,

After the following checkups,
When I run:
sudo netstat -nap | grep "@/proc/udevd" 
  I get nothing, 
when I search for libns2.so, no result too. But when I run:
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected" 
the answer is system infected, 
and finally, when I then run:
sudo chkrootkit on Ebory's search it says: Possible Linux/Ebury - Operation Windigo installetd
Version of SSH:
ssh:
  Installed: 1:6.9p1-3
  Candidate: 1:6.9p1-3
  Version table:
 *** 1:6.9p1-3 0

There is quite alarming info on this trojan/virus

How can I make sure my system is infected or not? Already made a clean install to realize that the answers were the same.
Thanks in advance.

---

### Post by unspawn on 2015-11-30
> **Eriamieka said:**
> How can I make sure my system is infected or not? For Ebury to work root-owned binaries need to be replaced. So next to the commands in documents you've read on Ebury / Windigo you should do basic comparison of binaries and hashes (using a known safe, clean, incorruptible environment  if unsure, be it a workstation, virtual machine or CDROM) as the start of your basic forensic investigation. Be aware of false positives. Always double check Chkrootkit or Rootkit Hunter commands in debug mode if unsure. Please note that if your machine is infected that reinstalling from scratch only helps the perp by destroying evidence. Not a good practice. Also note commands change over time: where the "old" version of OpenSSH didn't recognize the "-G" switch the 7.n series does. Post verbose / debug output if unsure.

---

### Post by Eriamieka on 2015-12-01
Here is the chkrootkit result..
Sorry but I would need more precision on how to check the Hashes and the binaries, and I could not install ssh 7.0p1 or 7.1p1

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
 Checking `mail'...                                          not found
 Checking `mingetty'...                                      not found
 Checking `netstat'...                                       not infected
 Checking `named'...                                         not found
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
 Checking `tcpd'...                                          not infected
 Checking `tcpdump'...                                       not infected
 Checking `top'...                                           not infected
 Checking `telnetd'...                                       not found
 Checking `timed'...                                         not found
 Checking `traceroute'...                                    not found
 Checking `vdir'...                                          not infected
 Checking `w'...                                             not infected
 Checking `write'...                                         not infected
 Checking `aliens'...                                         
 /dev/shm/pulse-shm-1811059583
 Searching for sniffer's logs, it may take a while...        nothing found
 Searching for rootkit HiDrootkit's default files...         nothing found
 Searching for rootkit t0rn's default files...               nothing found
 Searching for t0rn's v8 defaults...                         nothing found
 Searching for rootkit Lion's default files...               nothing found
 Searching for rootkit RSHA's default files...               nothing found
 Searching for rootkit RH-Sharpe's default files...          nothing found
 Searching for Ambient's rootkit (ark) default files and dirs... nothing found
 Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:   
 /usr/lib/debug/.build-id /lib/modules/4.2.0-19-generic/vdso/.build-id
 /usr/lib/debug/.build-id /lib/modules/4.2.0-19-generic/vdso/.build-id
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
 enp5s0f2: PACKET SNIFFER(/sbin/dhclient[1258])
 virbr0: not promisc and no packet sniffer sockets
 tun0: not promisc and no packet sniffer sockets
 Checking `w55808'...                                        not infected
 Checking `wted'...                                          chkwtmp: nothing deleted
 Checking `scalper'...                                       not infected
 Checking `slapper'...                                       not infected
 Checking `z2'...                                            user albertdon deleted or never logged from lastlog!
 Checking `chkutmp'...                                        The tty of the following user process(es) were not found
  in /var/run/utmp !
 ! RUID          PID TTY    CMD
 ! root         1251 tty7   /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 ! albertd+     3738 pts/0  bash
 ! root        10530 pts/0  dbus-launch --autolaunch=36e5423a0be84ad381b72bb05074d4a9 --binary-syntax --close-stderr
 ! albertd+    10548 pts/2  bash
 ! albertd+    10816 pts/18 bash
 ! albertd+    11566 pts/19 bash
 ! root        22956 pts/19 /bin/sh /usr/sbin/chkrootkit
 ! root        23623 pts/19 ./chkutmp
 ! root        23625 pts/19 ps axk tty,ruser,args -o tty,pid,ruser,args
 ! root        23624 pts/19 sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
 ! root        22955 pts/19 sudo chkrootkit
 chkutmp: nothing deleted
 Checking `OSX_RSPLUG'...                                    not infected
```

Thank you for your help

---

### Post by Bucky Ball on 2015-12-01
*Thread moved to **Ubuntu Development Version**.*

Just wondering why you are using 16.04 LTS. It is not released until next April. If you are aware you are running a testing version and are quite happy with the unpredictablity of that, then all good.

If not, install a supported release, 14.04 LTS or 15.10, both of which can be 'net' upgraded to 16.04 LTS when it comes out, and try again. There are plenty of things that may or may not work on 16.04 LTS.

---

### Post by QIII on 2015-12-01
Do chkrootkit on your install media in a Live session.  There is an [active bug]("https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/1508248") regarding this in 15.10.  16.04 may be the same.

If you get a positive or possible on this in a live session, I'd say the bug still exists in Xenial.

---

### Post by Eriamieka on 2015-12-01
Hey QIII,

Thank you for your help

Yes the result is possibly infected, here is the result from the live session:

```
ubuntu@ubuntu:~$ sudo chkrootkit
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
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
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
Checking `sendmail'...                                      not found
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
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /lib/modules/4.2.0-19-generic/vdso/.build-id
/lib/modules/4.2.0-19-generic/vdso/.build-id
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
-290    /usr/share
-1    /usr/sbin
-26    /lib
chkdirs: Warning: Possible LKM Trojan installed
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
enp5s0f2: PACKET SNIFFER(/sbin/dhclient[4619])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user ubuntu deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         3573 tty7   /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
! root         6021 pts/1  /bin/sh /usr/sbin/chkrootkit
! root         6676 pts/1  ./chkutmp
! root         6678 pts/1  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         6677 pts/1  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root         6020 pts/1  sudo chkrootkit
! ubuntu       4351 pts/1  bash
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
```

Same result as above "system infected" for :
```
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
```

I configured ssh following this:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)    which apparently gives a little bit more security

---

### Post by deadflowr on 2015-12-01
Please use [code tags ]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")when posting terminal output.

It makes the output more readable.

---

### Post by Eriamieka on 2015-12-01
Hey Bucky Ball,

Thanks for the advice, but

I believe I  contribute a little bit to Ubuntu, and I enjoy trying to sort out the  mess I put myself in.  I am also a Linux Ubuntu apprentice and other  distros on other partitions since Ubuntu 12.04..

---

### Post by Eriamieka on 2015-12-01
Hey deadflowr,

Thanks, 
I knew something was not OK with the answer window, got it now

---

### Post by Eriamieka on 2015-12-01
Sorry for spelling mistake it is Ebury and not Ebory
Done a few other checks and most seem positive, got the document here:
[URL="http://www.welivesecurity.com/wp-content/uploads/2014/03/operation_windigo.pdf"]http://www.welivesecurity.com/wp-content/uploads/2014/03/operation_windigo.pdf


[/URL]

---

### Post by Bucky Ball on 2015-12-01
> **Eriamieka said:**
> Hey Bucky Ball,

Thanks for the advice, but

I believe I  contribute a little bit to Ubuntu, and I enjoy trying to sort out the  mess I put myself in.  I am also a Linux Ubuntu apprentice and other  distros on other partitions since Ubuntu 12.04..

Excellent! All 16.04 and future development release issues go here, then. Enjoy. :)

---

### Post by Eriamieka on 2015-12-01
Where is the best place to deal with this issue? My post was moved. I am particularly concerned with this issue.

---

### Post by Bucky Ball on 2015-12-01
> **Eriamieka said:**
> Where is the best place to deal with this issue? My post was moved. I am particularly concerned with this issue.

... and thread moved back to Security. Apologies, my mistake. Cariboo's advice to you to post in Security has just been pointed out to me, so as it's his call, I'll follow that lead. Good luck.

---

### Post by philhughes on 2015-12-01
As QIII pointed out, most likely a false positive.See also:

[https://bugzilla.redhat.com/show_bug.cgi?id=1234436](https://bugzilla.redhat.com/show_bug.cgi?id=1234436)

---

### Post by QIII on 2015-12-01
My guess is a false positive, since there is a bug against Wily that is not fixed.

Anyway, the next step would be to go to a known clean machine (one that is running a release earlier than Wily that has been checked with chkrootkit) and try a live session.  If it shows positive, then this is probably a false positive.  It would be worth reporting against Xenial, with a note referencing the Wily bug.

---

