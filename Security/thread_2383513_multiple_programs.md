---
title: "multiple programs"
date: 2018-01-26
forum: Security
---

### Post by b4dmofo on 2018-01-26
hi,
after browser crash my whole system started to act weird.
every program runs like 3~4 times under different PID's.
when i try to kill one of the PID's all instances closing.
chkrootkit gives me pretty strange results:
```
bl4ck@5un:~$ sudo chkrootkit
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
Checking `rpcinfo'...                                       not found
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
Checking `traceroute'...                                    not infected
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
/usr/lib/debug/.build-id /lib/modules/4.4.0-109-generic/vdso/.build-id /lib/modules/4.4.0-112-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.4.0-109-generic/vdso/.build-id /lib/modules/4.4.0-112-generic/vdso/.build-id
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
eth0: PACKET SNIFFER(/usr/sbin/nethogs[1842])
tun0: PACKET SNIFFER(/usr/sbin/nethogs[1842])
Checking `w55808'...                                        not infected
Checking `wted'...                                          2 deletion(s) between Fri Jan 26 06:30:09 2018 and Fri Jan 26 06:33:23 2018
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user bl4ck deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! &#65533;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l       0 &#65533;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8261;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l &#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l
! &#65533;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l       0 &#65533;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8261;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l &#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l
! &#65533;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l       0 &#65533;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8261;&#65533;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l &#9585;&#10742;&#10744;&#11003;&#11005;&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;&#42889;&#65044;&#65045;&#65087;&#65117;&#65118;?&#65294;&#65295;&#65377;&#65440;???&#65532;&#65533;|155:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/l
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected


```
htop shows:
[ATTACH=CONFIG]278326[/ATTACH]
kind regards

---

### Post by oldos2er on 2018-01-26
What exactly does "start to act weird" mean? Your htop screen looks normal to me.

Which Ubuntu version are you using? Which version of chkrootkit? Have you checked chkrootkit's results against a previous run's results?

See [https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/1508248](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/1508248)

---

### Post by b4dmofo on 2018-01-27
all programs been on the last version, doing updates every day.
btw over the day nearly every program wasn't usable. like firefox just startet after remove and reinstall.
 i just been able to made the most important backups. after that i just wiped away the system and set a new fresh one up.
thanks for the response anyway
regards

---

### Post by b4dmofo on 2018-01-27
feel free to delete the thread

---

### Post by oldos2er on 2018-01-27
> **b4dmofo said:**
> feel free to delete the thread

That would defeat the purpose of the 'Solved' tag, even though an OS reinstall is in my opinion a bit extreme. But for a potential rootkit it's probably the best course to take.

---

