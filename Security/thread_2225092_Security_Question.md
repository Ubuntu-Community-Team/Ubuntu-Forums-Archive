---
title: "Security Question"
date: 2014-05-19
forum: Security
---

### Post by cmac2 on 2014-05-19
After some sage advice from one of the community members I have decided to repost my question.  I apologize for the previous post.  It was incoherent and not making mucn sense.  I am new to Linux OS and reacted without thinking.  

Thank you ahead of time for your help.  


Background:  
A few weeks ago I asked one of my coworkers who happens to be the IT guy about hardening a linux os.  He asked me some basic questions and wasnt much help.  Said he just wasnt that famlar with linux and wouldnt be able to help.  3 days later I started to notice some issues with my computer.  The mouse cursor wouldnt respond, the webpages would sometimes show up in weird languages, my searches would have certain words/variables ommited, when I signed into webpages my auto sign in would be there even while running the live dvd. 
Thing just werent working right.  I started to suspect my coworker.  I did some asking around and he had been reprimanded in the past for remotely looging into another coworkers computer.  He is capable of doing this at work and it is his right.  The program he uses at work is F.O.G and PXE factors in somehow.  

So I was concerned that he was somehow remotely logging into my system.  I am currently running a live DVD with UbuntuGnome 64 bit.  

[SIZE=3][I]I forgot to add this part... a few days ago I checked my router and telnet was enabled.  I checked the port forwarding and found that the upnp feature was running and two divices were torrenting files.  I have since disabled Telnet and the upnp serive has not been used.  
[/I][/SIZE]
This is the results of rkhunter and chkrootkit.  


chkrootkit
```
ubuntu-gnome@ubuntu-gnome:~$ sudo chkrootkit 
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
Searching for suspicious files and dirs, it may take a while... nothing found 
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
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED 
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
-269    /usr/share 
-1    /usr/bin 
-1    /usr/sbin 
chkdirs: nothing detected 
Checking `rexedcs'...                                       not found 
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets 
eth0: PACKET SNIFFER(/sbin/dhclient[3116]) 
Checking `w55808'...                                        not infected 
Checking `wted'...                                          chkwtmp: nothing deleted 
Checking `scalper'...                                       not infected 
Checking `slapper'...                                       not infected 
Checking `z2'...                                            user root deleted or never logged from lastlog! 
user ubuntu-gnome deleted or never logged from lastlog! 
Checking `chkutmp'...                                        The tty of the following user process(es) were not found 
 in /var/run/utmp ! 
! RUID          PID TTY    CMD 
! root         4084 tty7   /usr/bin/X :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-yQdTmr/database -seat seat0 -nolisten tcp vt7 
chkutmp: nothing deleted 
Checking `OSX_RSPLUG'...                                    not infected 
```

rkhunter
                        ```
ubuntu-gnome@ubuntu-gnome:~$ sudo rkhunter -c --enable all --disable none --rwo 

 Warning: Checking for prerequisites               [ Warning ] 
          No output from the 'lsattr' command - all file immutable-bit checks will be skipped. 
 Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text 
 Warning: The following processes are using deleted files: 
          Process: /usr/sbin/cups-browsed    PID: 1498    File: /etc/passwd 
          Process: /usr/lib/libreoffice/program/soffice.bin    PID: 3940    File: /home/ubuntu-gnome/.execoooL7DBAu 
          Process: /usr/lib/evolution/evolution-calendar-factory    PID: 4742    File: /home/ubuntu-gnome/.local/share/gvfs-metadata/home 
          Process: /usr/lib/firefox/firefox    PID: 4857    File: /var/tmp/etilqs_s0PaSytuTwYLPHK 
          Process: /usr/bin/gnome-terminal    PID: 4980    File: /tmp/#36916 
 Warning: Process '/sbin/dhclient' (PID 3116) is listening on the network. 
 Warning: User 'postfix' has been added to the passwd file. 
 Warning: Group 'postfix' has been added to the group file. 
 Warning: Group 'postdrop' has been added to the group file. 
 Warning: Suspicious file types found in /dev: 

          /dev/.udev/rules.d/root.rules: ASCII text 
 Warning: Hidden directory found: '/dev/.udev: directory ' 
 Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'  
 ubuntu-gnome@ubuntu-gnome:~$  
  
```





If anyone can suggest another tool to figure this out I would really appreciate it.  

Thanks

---

### Post by CharlesA on 2014-05-19
Looks normal to me. Both those programs are notorious for false positives and as each system is different, they will give you different results depending on your system.

Run this and see what it spits out:

```
sudo netstat -nlpu
```

---

### Post by cmac2 on 2014-05-19
```
ubuntu-gnome@ubuntu-gnome:~$ sudo netstat -nlpu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:13882           0.0.0.0:*                           3116/dhclient   
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1498/cups-browsed
udp        0      0 0.0.0.0:35712           0.0.0.0:*                           1081/avahi-daemon: 
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1999/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3116/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1081/avahi-daemon: 
udp6       0      0 :::5662                 :::*                                3116/dhclient   
udp6       0      0 :::53853                :::*                                1081/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1081/avahi-daemon: 
ubuntu-gnome@ubuntu-gnome:~$
```

Im not trying to be overly difficult...just trying to make sure I am all good.  

In my previouas thread the results from rkhunter didnt mention these warnings.  

Warning: User 'postfix' has been added to the passwd file. 
 Warning: Group 'postfix' has been added to the group file. 
 Warning: Group 'postdrop' has been added to the group file. 

Any reason for this discrepancy?  Does it have to do with how I set rkhunter up?  

Thank you for your help.

---

### Post by CharlesA on 2014-05-19
That looks normal too. I doubt any of the problems you are seeing are from your coworker.

---

### Post by cmac2 on 2014-05-19
I found this command while checking other threads.  I am running a live DVD and havent used the root account as root.  Only as sudo.  

Is this still normal?  Is the root account accessed each time you start the live DVD?  

```
ubuntu-gnome@ubuntu-gnome:~$ stat -c%y /etc/passwd
2014-05-19 22:56:31.095881310 +0000
ubuntu-gnome@ubuntu-gnome:~$ 
```

I also noticed I had a lot of active internet connections.  At the time of the screenshot I think there were 127.  Here is the screeshot.  Is this common?  Is it due to old connections not being flushed?  

[[IMG]http://i138.photobucket.com/albums/q268/cmacfarlane77/Screenshotfrom2014-05-19234047_zpsd3cbf571.png[/IMG]]("http://s138.photobucket.com/user/cmacfarlane77/media/Screenshotfrom2014-05-19234047_zpsd3cbf571.png.html")


I apologize for all the questions.  Just wanted to get your opinion and learn about it

---

### Post by cariboo on 2014-05-19
I'm assuming the ip address of your system is 192.168.1.129, and the ip address of your router is 192.168.1.1, so the established connections are between your system and router. 

You can use whois to check foreign ip addresses that aren't in your netblock eg:

```
whois 97.94.152.ii5
```

---

### Post by cmac2 on 2014-05-19
When I run IP chicken it shows my address as 97.94.152.115

I talked to my ISP and last time I checked IP chicken matched the ISP.  

Sorry for the basic questions...just trying to get a handle on it.  

So if I am the 97 address is the 192.168.1.129 number an internal IP address?

---

### Post by CharlesA on 2014-05-20
The 192.168.x.y number is your internal address, the 97.x.y.z is your external address.

---

### Post by cmac2 on 2014-05-20
Ok so based on the screen shot tcp 34 has a remote IP address...23.61.194.251 running through my local IP address which is 192.168.1.129.  It is an established connection.  

Its port 80 so I figure that is the normal port for internet traffic.  Is there a way to figure out which process is using that webaddress?  

Can I draw any conclusions from this information?

Ok I did another check on the router.  I had 700+active internet connections on the router.  Is this some type of torrent?

So this what I got from the whois command.

```
ubuntu-gnome@ubuntu-gnome:~$ sudo whois 23.61.194.195

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: [https://www.arin.net/whois_tou.html](https://www.arin.net/whois_tou.html)
#


#
# The following results may also be obtained via:
# [http://whois.arin.net/rest/nets;q=23.61.194.195?showDetails=true&showARIN=false&ext=netref2](http://whois.arin.net/rest/nets;q=23.61.194.195?showDetails=true&showARIN=false&ext=netref2)
#

NetRange:       23.32.0.0 - 23.67.255.255
CIDR:           23.64.0.0/14, 23.32.0.0/11
OriginAS:       
NetName:        AKAMAI
NetHandle:      NET-23-32-0-0-1
Parent:         NET-23-0-0-0-0
NetType:        Direct Allocation
RegDate:        2011-05-16
Updated:        2012-03-02
Ref:            [http://whois.arin.net/rest/net/NET-23-32-0-0-1](http://whois.arin.net/rest/net/NET-23-32-0-0-1)

OrgName:        Akamai Technologies, Inc.
OrgId:          AKAMAI
Address:        8 Cambridge Center
City:           Cambridge
StateProv:      MA
PostalCode:     02142
Country:        US
RegDate:        1999-01-21
Updated:        2014-03-19
Ref:            [http://whois.arin.net/rest/org/AKAMAI](http://whois.arin.net/rest/org/AKAMAI)

OrgTechHandle: ZIPKI-ARIN
OrgTechName:   Zipkin, Justin 
OrgTechPhone:  +1-617-444-9713 
OrgTechEmail:  [email]ip-admin@akamai.com[/email]
OrgTechRef:    [http://whois.arin.net/rest/poc/ZIPKI-ARIN](http://whois.arin.net/rest/poc/ZIPKI-ARIN)

OrgAbuseHandle: MHA379-ARIN
OrgAbuseName:   Hannigan, Martin 
OrgAbusePhone:  +1-617-444-2535 
OrgAbuseEmail:  [email]ip-admin@akamai.com[/email]
OrgAbuseRef:    [http://whois.arin.net/rest/poc/MHA379-ARIN](http://whois.arin.net/rest/poc/MHA379-ARIN)

OrgTechHandle: SJS98-ARIN
OrgTechName:   Schecter, Steven Jay
OrgTechPhone:  +1-617-274-7134 
OrgTechEmail:  [email]ip-admin@akamai.com[/email]
OrgTechRef:    [http://whois.arin.net/rest/poc/SJS98-ARIN](http://whois.arin.net/rest/poc/SJS98-ARIN)

OrgTechHandle: MHA379-ARIN
OrgTechName:   Hannigan, Martin 
OrgTechPhone:  +1-617-444-2535 
OrgTechEmail:  [email]ip-admin@akamai.com[/email]
OrgTechRef:    [http://whois.arin.net/rest/poc/MHA379-ARIN](http://whois.arin.net/rest/poc/MHA379-ARIN)


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: [https://www.arin.net/whois_tou.html](https://www.arin.net/whois_tou.html)
#

ubuntu-gnome@ubuntu-gnome:~$
```

---

### Post by CharlesA on 2014-05-20
Akamai is a CDN, so it's likely something you are browsing is being served by them.

As far as 700+ connections, no idea. I checked my home router and it was sitting at around 200 connections, but I also only had one machine running at the time.

---

### Post by cmac2 on 2014-05-20
This a a screenshot of the app_profile folder in a gufw file. 

I did not add any of these files. Anyone know how they could get there?  


[[IMG]http://i138.photobucket.com/albums/q268/cmacfarlane77/Screenshotfrom2014-05-20062657_zps98d382a4.png[/IMG]]("http://s138.photobucket.com/user/cmacfarlane77/media/Screenshotfrom2014-05-20062657_zps98d382a4.png.html")

This is a typical file in this folder.  

[0verkill]
title=0verkill
description=An ASCII-art 2D deathmatch game
ports=6666
categories=Games;Action;
reference=[[http://artax.karlin.mff.cuni.cz/~brain/0verkill/index.cgi?mainpage](http://artax.karlin.mff.cuni.cz/~brain/0verkill/index.cgi?mainpage) 0verkill mainpage]

Is the purpose of the app_profile folder to bypass the guwf firewall?

---

### Post by coffeecat on 2014-05-20
They got there because they are part of a default installation. The contents of /etc/gufw/app_profiles are predefined rules - profiles for apps - which are provided as a convenience for when configuring gufw.

---

### Post by cmac2 on 2014-05-20
Thanks for explaining that.  I really appreciate your guys insights and help.  I must have been making something out of nothing.  

From reading past threads I know this happens a lot and it is most likely a major pain in the butt.  I apologize for all of the questions and thank you for taking the time to help me out.

---

