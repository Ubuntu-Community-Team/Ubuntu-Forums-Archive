---
title: "Help closing a connection"
date: 2010-11-21
forum: Security
---

### Post by michaelmurkers on 2010-11-21
need help closing a connection to bd67f301.virtua.com.br 

I am using the firestarter firewall utility and I have no idea where to begin. 

please help

---

### Post by michaelmurkers on 2010-11-21
now the host-name has changed to unallocated.barefruit.co.uk the service is unknown 

what is this I have heard of barefruit.co.uk providing tiscali service users with certain error systems and what not but why am I connected to them? and how do I stop this

---

### Post by HermanAB on 2010-11-22
$ sudo iptables -i eth0 -s bd67f301.virtua.com.br -j DROP

---

### Post by michaelmurkers on 2010-11-22
> **HermanAB said:**
> $ sudo iptables -i eth0 -s bd67f301.virtua.com.br -j DROP

I wouldnt be that because i am using a wireless device but its already taken a turn for the worse Ive now got a suspected trojan on my system almost 

ashley@ashley-Satellite-C650:~$ chkrootkit
The program 'chkrootkit' is currently not installed.  You can install it by typing:
sudo apt-get install chkrootkit
ashley@ashley-Satellite-C650:~$ sudo apt-get install chkrootkit
[sudo] password for ashley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  chkrootkit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 357kB of archives.
After this operation, 995kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main chkrootkit amd64 0.49-4 [357kB]
Fetched 357kB in 0s (887kB/s)    
Preconfiguring packages ...
Selecting previously deselected package chkrootkit.
(Reading database ... 137131 files and directories currently installed.)
Unpacking chkrootkit (from .../chkrootkit_0.49-4_amd64.deb) ...
Processing triggers for man-db ...
Setting up chkrootkit (0.49-4) ...
ashley@ashley-Satellite-C650:~$ chkrootkit
/usr/sbin/chkrootkit need root privileges
ashley@ashley-Satellite-C650:~$ sudo chkrootkit
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
Checking `rpcinfo'...                                       not infected
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
/usr/lib/xulrunner-1.9.2.12/.autoreg /usr/lib/firefox-3.6.12/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/jvm/.java-6-openjdk.jinfo

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
Checking `lkm'...                                           You have     3 process hidden for readdir command
You have     3 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1002], /sbin/dhclient3[1792])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user ashley deleted or never logged from lastlog!
Checking `chkutmp'...                                       chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected

---

### Post by michaelmurkers on 2010-11-22
do you think this calls for a cd boot and installation

---

### Post by HermanAB on 2010-11-22
```
$ sudo iptables -i wlan0 -s bd67f301.virtua.com.br -j DROP
```

BTW, chrootkit is quite useless.

---

### Post by michaelmurkers on 2010-11-22
are there rootkits for ubuntu out there? what do you think i should do next?

---

### Post by OpSecShellshock on 2010-11-22
Really doubt it's a rootkit. Was the connection initiated from an external network, or is something that you're using connecting out? What network applications, if any, are you using aside from the browser? Have you tried shutting off the network connection temporarily?

---

### Post by michaelmurkers on 2010-11-22
netstat -pantu
ashley@ashley-Satellite-C650:~$ sudo netstat -pantu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1285/cupsd      
tcp        0      0 127.0.0.1:42441         0.0.0.0:*               LISTEN      4711/beam.smp   
tcp        1      0 192.168.1.77:58055      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:48237      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56651      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56648      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:36880      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:40463      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:60987      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34001      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:48239      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56649      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp       38      0 192.168.1.77:60925      91.189.89.106:443       CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:46471      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34004      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:60990      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:36879      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:58058      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33990      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:48234      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:48238      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:57073      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:40457      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:60989      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:57075      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33992      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56138      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34000      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:36881      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:46472      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:57074      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:58060      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33994      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56643      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:58057      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        0      0 192.168.1.77:41484      209.85.229.100:80       ESTABLISHED 4783/firefox-bin
tcp        1      0 192.168.1.77:46473      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56645      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:58061      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:40462      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34002      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33996      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34006      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33997      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:33998      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:48241      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34005      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:56653      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp        1      0 192.168.1.77:34007      91.189.89.31:80         CLOSE_WAIT  4466/gvfsd-http 
tcp6       0      0 ::1:631                 :::*                    LISTEN      1285/cupsd      
udp        0      0 0.0.0.0:54222           0.0.0.0:*                           987/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           987/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           13724/dhclient  
udp6       0      0 :::43966                :::*                                987/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                987/avahi-daemon: r

---

### Post by michaelmurkers on 2010-11-22
> **OpSecShellshock said:**
> Really doubt it's a rootkit. Was the connection initiated from an external network, or is something that you're using connecting out? What network applications, if any, are you using aside from the browser? Have you tried shutting off the network connection temporarily?

transmission downloading alot of torrents

also im getting around 10 blocked hits in firestarter every minuiite

---

### Post by HermanAB on 2010-11-22
So stop the torrent cruft, then relax and enjoy your system.

---

### Post by michaelmurkers on 2010-11-22
what do you actually think i should do then?

---

### Post by OpSecShellshock on 2010-11-22
The connections were almost certainly happening due to the torrent downloads, so all you need to do is stop those and exit out of Transmission.

---

### Post by a quarter past seven on 2010-11-22
in the future if you do want to stop a connection in fire starter press the padlock button in the top left and it will block all connections

---

