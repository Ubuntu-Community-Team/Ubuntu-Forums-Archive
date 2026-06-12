---
title: "Honeypot Keylogger for Compromised Box?"
date: 2010-05-12
forum: Server Platforms
---

### Post by victorhooi on 2010-05-12
heya,

We have a Ubuntu 9.04 box running out of Amazon's EC2 cloud that we're pretty sure has been compromised.

When I ran top, I get:

```
top: error while loading shared libraries: libncurses.so.4: cannot open shared object file: No such file or directory

```

I thought, that's a bit weird, so I installed chkrootkit, and ran that:

```
sudo chkrootkit 
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
Checking `ifconfig'...                                      INFECTED
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not infected
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       INFECTED
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        INFECTED
Checking `rpcinfo'...                                       not infected
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not infected
Checking `syslogd'...                                       not infected
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           INFECTED
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        /etc/ld.so.hash 
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         Possible t0rn v8 (or variation) rootkit installed
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/lib/init/rw/.ramfs

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
Searching for Showtee...                                    Warning: Possible Showtee Rootkit installed
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                            /usr/include/file.h /usr/include/proc.h
Searching for Suckit rootkit...                             nothing found
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       Possible ShKit rootkit installed
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[1180])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            chklastlog: nothing deleted

```

Anyhow, in terms of using this box, the safest way is probably just to blow it away, and re-install from scratch.

However, I'm still curious as to how exactly the box got compromised, or what exactly the attacker is using the box for.

Is there some kind of keylogger I can install, to set it up as a honeypot, to find out what exactly they're doing with this box? I know of lkl and uberkey ([http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux]("http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux")), however, I'm not sure if either of those would log SSH sessions - I thought they only log the physical keyboard port? Or log any other remote-access method they've installed. There is a external firewall, that only allows, from memory, port 22, 80, 443, and 8080, so the backdoor would have to traverse one of those ports.

What's a good way of basically logging everything done and every keystroke on this box? I know, we don't own this box anymore, but either way, I'd at least like to install something to try.

Also, I should add I did try THC Vlogger ([http://freeworld.thc.org/releases.php?q=logger&x=0&y=0]("http://freeworld.thc.org/releases.php?q=logger&x=0&y=0")), however, I suspect it's not compatible with Linux 2.6, gave an error:
```
./configure: 27: cannot open /proc/ksyms: No such file
```

and the make after that failed as well.

It actually looks like pretty much what I want, I just need something more recent, and that's compatible with Ubuntu. Anybody know of anything, or any other way of achieving this?


Cheers,
Victor

---

