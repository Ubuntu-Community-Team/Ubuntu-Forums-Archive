---
title: "Heavy Upload Issues-Web Server"
date: 2011-04-02
forum: Server Platforms
---

### Post by Hack.The.Pow. on 2011-04-02
Hello guys.  I have been having some issues with my web server recently.  I have been experiencing heavy upload data recently.  I set up this web server to just mess around with and work on my web development skills as well as Share some of my Movies and pictures and whatnot between me and my friends.

However since my roommates have been experiencing issues with our xbox having a weak signal I decided to check my routers bandwidth.  There I noticed that I had been uploading around 15 gigs a day which I feel is ridiculous because almost nobody besides me frequents my server.  I checked the logs on my router(it is running tomato) and saw this

```
Apr  2 10:16:01 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=60540 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  2 10:16:01 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=31727 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:05 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=39561 DF PROTO=TCP SPT=52422 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5156820000000001030306) 
Apr  2 10:16:08 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6f SRC=73.171.228.1 DST=255.255.255.255 LEN=367 TOS=0x00 PREC=0x00 TTL=255 ID=60589 PROTO=UDP SPT=67 DPT=68 LEN=347 
Apr  2 10:16:10 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=31847 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:10 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6f SRC=73.171.228.1 DST=255.255.255.255 LEN=367 TOS=0x00 PREC=0x00 TTL=255 ID=60604 PROTO=UDP SPT=67 DPT=68 LEN=347 
Apr  2 10:16:12 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=31870 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:12 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29381 DF PROTO=TCP SPT=52701 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A515CC40000000001030306) 
Apr  2 10:16:14 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=31901 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:17 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=30511 DF PROTO=TCP SPT=52941 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A51621A0000000001030306) 
Apr  2 10:16:22 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32016 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:23 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=19633 DF PROTO=TCP SPT=53211 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5168050000000001030306) 
Apr  2 10:16:24 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32042 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:26 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32067 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:29 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=179 DF PROTO=TCP SPT=53485 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A516E000000000001030306) 
Apr  2 10:16:35 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32214 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:36 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=47359 DF PROTO=TCP SPT=53760 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5174220000000001030306) 
Apr  2 10:16:37 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32238 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:39 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32265 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:41 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=55880 DF PROTO=TCP SPT=54012 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A51799B0000000001030306) 
Apr  2 10:16:47 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=54954 DF PROTO=TCP SPT=54252 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A517F2A0000000001030306) 
Apr  2 10:16:47 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32369 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:49 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32399 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:51 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32428 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:16:52 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=38090 DF PROTO=TCP SPT=54488 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5184360000000001030306) 
Apr  2 10:16:57 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=36387 DF PROTO=TCP SPT=54717 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5189050000000001030306) 
Apr  2 10:16:59 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=60769 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  2 10:17:00 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32561 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:02 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32590 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:03 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=34430 DF PROTO=TCP SPT=54977 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A518EF50000000001030306) 
Apr  2 10:17:04 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32631 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:08 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=40783 DF PROTO=TCP SPT=55196 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5193DB0000000001030306) 
Apr  2 10:17:12 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=32767 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:13 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=14325 DF PROTO=TCP SPT=55423 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A5198C30000000001030306) 
Apr  2 10:17:14 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=29 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:16 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=68 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:19 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=65416 DF PROTO=TCP SPT=55656 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A519E210000000001030306) 
Apr  2 10:17:25 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=185 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:26 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=17913 DF PROTO=TCP SPT=55998 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A51A5950000000001030306) 
Apr  2 10:17:27 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:50 SRC=202.63.230.28 DST=98.229.4.15 LEN=80 TOS=0x00 PREC=0x20 TTL=113 ID=207 PROTO=UDP SPT=23223 DPT=59590 LEN=60 
Apr  2 10:17:31 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=17979 DF PROTO=TCP SPT=56200 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A51AA2C0000000001030306) 
Apr  2 10:17:36 unknown user.warn kernel: ACCEPT IN=vlan1 OUT=br0 SRC=202.175.83.126 DST=192.168.1.170 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=12456 DF PROTO=TCP SPT=56429 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40402080A3A51AF510000000001030306) 
```

I'm assuming that there is some web crawler or something trying to access my server for some reason?  I recently password protected the directories that had all of my videos and documents to cut down on what everybody could access.  That cut down on the uploads.  However there is still a consistent 250 KB/S  being uploaded from my server at all times.  It is really annoying because my total data usage per day is still around 7 gigs of data(Pretty much all upload data)

Can anybody suggest something to combat this?  I would like to get this resolved ASAP

---

### Post by Joe of loath on 2011-04-02
What's the output of netstat when the server is uploading?

---

### Post by Doug S on 2011-04-02
[FONT=Calibri][SIZE=3]I think many forum readers would be willing to help, but we would need a lot more information before being able to give useful suggestions. In addition to the previous posters request for netstat output, I would ask:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Have you reviewed your apache log files (/var/log/apache2/access.log) to see who is looking at things?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Do you have a good robots.txt file (/var/www/robots.txt) that instructs web crawlers as to what you want indexed or not, or even disabling some webcrawlers?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Are you even certain that the high traffic volume is web server related (port 80) or is it on some other port?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]From your router log fragment, it is not clear which is your web server IP address. I do see some port 22 activity, but from always different source ports, which has the appearance of an SSH attack.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The netstat output will show a connection snapshot. Perhaps running tcpdump for an hour might reveal more detail. I would run the following command for maybe an hour (assumes your externally facing NIC card is eth0, and the options are just what I prefer):[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]sudo tcpdump –i eth0 –n –nn –tttt >capture.txt[/SIZE][/FONT]

---

### Post by BkkBonanza on 2011-04-02
Those look like firewall log messages from some source on an internal vlan. You might have a look at vlan config on the router and see if you have something wrong. If you're not using a vlan then it should probably be disabled as maybe spurious traffic is being caught and logged. Look also for some settings for remote logging in case all your log messges are trying to get uploaded elsewhere to be logged. That would cause a side effect of a secondary stream of useless data.

A lot of those log entries seem to be SYN packets (starting a new connection) being dropped. Is there something in your network that may be generating spurious outgoing data that is being blocked, eg. torrent client mistakenly trying something that's blocked. I would review all router settings for something odd. 

And maybe run wireshark inside your network to see if you can find some weird stuff happening (though you're likely to see some stuff you don't understand anyway).

---

### Post by Hack.The.Pow. on 2011-04-03
> **Doug S said:**
> [FONT=Calibri][SIZE=3]I think many forum readers would be willing to help, but we would need a lot more information before being able to give useful suggestions. In addition to the previous posters request for netstat output, I would ask:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Have you reviewed your apache log files (/var/log/apache2/access.log) to see who is looking at things?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Do you have a good robots.txt file (/var/www/robots.txt) that instructs web crawlers as to what you want indexed or not, or even disabling some webcrawlers?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Are you even certain that the high traffic volume is web server related (port 80) or is it on some other port?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]From your router log fragment, it is not clear which is your web server IP address. I do see some port 22 activity, but from always different source ports, which has the appearance of an SSH attack.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The netstat output will show a connection snapshot. Perhaps running tcpdump for an hour might reveal more detail. I would run the following command for maybe an hour (assumes your externally facing NIC card is eth0, and the options are just what I prefer):[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]sudo tcpdump –i eth0 –n –nn –tttt >capture.txt[/SIZE][/FONT]

Thank you for the detailed response.  I think your suggestion of using a robots.txt file solved the problem.  After learning about that I started it and restricted it from my images and media folders.  The upload data is very low now.  Hopefully it stays that way.

However I am still getting that unknown user warning in my router logs.  I was wondering if you believed that was serious or not. In regards to the port 22 activity I occasionally use ssh from other locations but not very frequently.  As for my server IP I use dyndns to keep track of my ip so that might be why you always see it changing. Will the netstat output still be relevant?

---

### Post by Hack.The.Pow. on 2011-04-04
> **BkkBonanza said:**
> Those look like firewall log messages from some source on an internal vlan. You might have a look at vlan config on the router and see if you have something wrong. If you're not using a vlan then it should probably be disabled as maybe spurious traffic is being caught and logged. Look also for some settings for remote logging in case all your log messges are trying to get uploaded elsewhere to be logged. That would cause a side effect of a secondary stream of useless data.

A lot of those log entries seem to be SYN packets (starting a new connection) being dropped. Is there something in your network that may be generating spurious outgoing data that is being blocked, eg. torrent client mistakenly trying something that's blocked. I would review all router settings for something odd. 

And maybe run wireshark inside your network to see if you can find some weird stuff happening (though you're likely to see some stuff you don't understand anyway).

Thanks for the help.  I've been running wireshark for a while now and from what I can see pretty much the only traffic there is between my server(192.168.1.170) and my router (192.168.1.1) .  It happens extremely frequently but I'm assuming that is normal?

Also after starring at the router logs more I noticed that the mac address is pretty much always the mac of my router.  The dest is always my outside ip address with gets forwarded to my server at 192.168.1.170 on ports 80 and 22.  The src however is always weird ip addresses from random countries(Indonesia, Sri Lanka, Romania, etc).

I have noticed however that the uploads seem to start and stop at random times.  If I could provide any more helpful info I would be glad to.  Thank You

---

### Post by BkkBonanza on 2011-04-04
Traffic to your port 80 (web server) is pretty unavoidable. But for port 22 (ssh) you have options. Having unknown user entries in the log is not in itself a problem as there are always random hackers out there trying to break in and as long as you ahve a strong password it's unlikely they accomplish anything. One common semi-solution is to move your ssh onto some high port number (>1024) as this makes it less likely to be found and targetted. That will get rid of the log entries mostly but doesn't inherently make it more secure.

If port 22 is being forwarded to your server for outside access and you need that then you'll probably want to keep it, or move it to a high port. If port 22 is just used for your router only then I'd reconsider if you really need to admin your router from outside very often. Usually we don't adjust the router too often and it's better to not have that port open to the internet if at all possible. And of course if you don't have a srong password then fix that right away, or use key authentication if you can.

Regarding your high upload usage: what method do you use for making the files available - how do you or friends access the content? Via web page links or ssh/sftp or other ways?

---

### Post by Hack.The.Pow. on 2011-04-04
> **BkkBonanza said:**
> Traffic to your port 80 (web server) is pretty unavoidable. But for port 22 (ssh) you have options. Having unknown user entries in the log is not in itself a problem as there are always random hackers out there trying to break in and as long as you ahve a strong password it's unlikely they accomplish anything. One common semi-solution is to move your ssh onto some high port number (>1024) as this makes it less likely to be found and targetted. That will get rid of the log entries mostly but doesn't inherently make it more secure.

If port 22 is being forwarded to your server for outside access and you need that then you'll probably want to keep it, or move it to a high port. If port 22 is just used for your router only then I'd reconsider if you really need to admin your router from outside very often. Usually we don't adjust the router too often and it's better to not have that port open to the internet if at all possible. And of course if you don't have a srong password then fix that right away, or use key authentication if you can.

Regarding your high upload usage: what method do you use for making the files available - how do you or friends access the content? Via web page links or ssh/sftp or other ways?

Thanks for the reply.

Access to SSH from an outside network is rarely used so I did decide to disable that on my router.  

The files are accessed via web links.  I have a folder called Media which has links to my documents, videos, pictures, and music folders in my home folder.  I password protected that media folder so only me and a couple select friends can access that.  There is only one password and it is relatively strong.

It still seems odd though that it would some random hackers though because the bandwidth is pretty constant at like 200-300 KB/s .....

---

### Post by BkkBonanza on 2011-04-04
That's pretty severe upload bw for a home connection. Since your files are served using http you should be able to look in the server logs and get a good idea of what IPs the uploads are going to. If you see a few that are constantly hitting your files then maybe make note of them and do a reverse dns lookup to see what networks they come from. 

If you and your friends are all in one ISP's network then you could easily add an IP block for any IPs outside that network. But you would have to figure out how much you can block or not block. If they are actually getting past a password control then either the password block isn't correctly set up or maybe there has been a breach that has already allowed them access.

---

### Post by Vegan on 2011-04-04
I see lots of random traffic on my network. I only provide basic services on my Linux box, http, ftp and dns

rest are closed to plug & pray users

---

### Post by Hack.The.Pow. on 2011-04-05
> **BkkBonanza said:**
> That's pretty severe upload bw for a home connection. Since your files are served using http you should be able to look in the server logs and get a good idea of what IPs the uploads are going to. If you see a few that are constantly hitting your files then maybe make note of them and do a reverse dns lookup to see what networks they come from. 

If you and your friends are all in one ISP's network then you could easily add an IP block for any IPs outside that network. But you would have to figure out how much you can block or not block. If they are actually getting past a password control then either the password block isn't correctly set up or maybe there has been a breach that has already allowed them access.

By server logs I assume you mean the apache logs(/var/log/apache2)

Here is the latest access.log 
```
127.0.0.1 - - [03/Apr/2011:23:03:59 -0400] "GET / HTTP/1.1" 200 1537 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
127.0.0.1 - - [03/Apr/2011:23:03:59 -0400] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
127.0.0.1 - - [03/Apr/2011:23:10:48 -0400] "GET / HTTP/1.1" 200 1538 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
127.0.0.1 - - [03/Apr/2011:23:10:49 -0400] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
98.229.4.15 - - [04/Apr/2011:09:43:51 -0400] "GET / HTTP/1.1" 200 1538 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
98.229.4.15 - - [04/Apr/2011:09:43:51 -0400] "GET /favicon.ico HTTP/1.1" 404 510 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.27 (KHTML, like Gecko) Chrome/12.0.712.0 Safari/534.27"
183.15.134.141 - - [04/Apr/2011:13:52:21 -0400] "GET / HTTP/1.0" 200 2721 "http://help.sina.com.cn/" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; TencentTraveler 4.0; QQPinyin 730; QQDownload 638; Foxy/1; .NET CLR 1.1.4322)"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "POST http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:23:36 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "POST http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:25:12 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "POST http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:28:02 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "POST http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:30:39 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:36 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:36 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:36 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:36 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:37 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:37 -0400] "POST http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:33:37 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:34:00 -0400] "GET http://vlad-tepes.bofh.it/freenode-proxy-checker.txt HTTP/1.0" 404 511 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:34:00 -0400] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 2721 "-" "-"
85.190.0.3 - - [04/Apr/2011:21:34:00 -0400] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 2721 "-" "-"
211.28.207.46 - - [04/Apr/2011:22:19:00 -0400] "^\x8a\x82\xbc\xcf\xbe\x05\xf2\x12\xb4\xf1\x07!b\x91NsL\xe8A\x8f\b\xe8\xb9" 200 2508 "-" "-"
211.28.207.46 - - [04/Apr/2011:22:21:16 -0400] "\xbf\x17\xca\xd8%\x1f\x8c\xc3\x81\x06\xf4\x98\x16\xa76\xf8\xbf\xbd]\xd3\xc7\x16\xb3\x07!\xfe\x8b+%\xe6" 200 2508 "-" "-"
211.28.207.46 - - [04/Apr/2011:22:22:25 -0400] "\x10\x86/\x82\x904" 200 2508 "-" "-"
211.28.207.46 - - [04/Apr/2011:22:23:45 -0400] "\xaeXg\xc6\xd7\xbd\x9fn\x199\x1e4\xdc\xe4\x0f\b8\xa4\xb5\xc2t\xd4^\x9a\xeb3\x80\xa1\r\x87\x9e?\xb1\xa1\xcb\xf1|\x04\xd0\x0c\xf3\xcb" 400 518 "-" "-"
211.28.207.46 - - [04/Apr/2011:22:28:21 -0400] "\x0c\xbd\x11\x92K\xd1@P\xbbr\xfc\x7fi\vg\xbb\x1b\xa2\x82>\x1e\xd8\xbe\xf7\x99\xd7\x16\xb3\xeeDA\xbe&Jl\xa9;\xc2 y\xfc@\xd3_\xa9\xcc\xdc\xd9\xa3\xc7\xf2\xf5X\xbd\x06X\x015\x96(H\x01\xc3\xd2y\xfb\xb1`/\xd2\xba\x11\xc1\xf3|\xcfky\x12\x1f\xe4!S\xe0\xeb\xc1\x84\x83$?" 400 518 "-" "-"
93.81.1.211 - - [05/Apr/2011:04:25:32 -0400] "\v\x93\xf9L\xe6\xbb\xf8\xb3y\xf3c\x06\xc0%|\x1e\xa2j\xbe\xb9\x14;l@\xbcu\xb9'\xb4\x1eP\x8a\x18!\xa1{\b\xac\xe57\xc2(\xc5?\x86\xb2\x8d\xcf\xa9\x15\xd0\x85\xfb\x01\xfb\xb8\x01$\x0cz\x95\xfb\xb7\xa0\xd2\x9c\xd5a#\xb6W\xda+\x9f*\xd1\xdd\x84K\xf4r)\x11U\xd3\x1do'\xfe\xb8\xb9~\xfc\xf3\xc8\x17\x82\x91mx" 400 518 "-" "-"
74.54.205.122 - - [05/Apr/2011:06:24:36 -0400] "GET /cube/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:37 -0400] "GET /round/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:37 -0400] "GET /roundcube-0.2/README HTTP/1.1" 404 473 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:38 -0400] "GET /roundcube-0.1/README HTTP/1.1" 404 473 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:39 -0400] "GET /roundcubemail-0.1/README HTTP/1.1" 404 476 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:39 -0400] "GET /roundcubemail-0.2/README HTTP/1.1" 404 476 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:40 -0400] "GET /wm/README HTTP/1.1" 404 466 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:40 -0400] "GET /webmail2/README HTTP/1.1" 404 470 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:40 -0400] "GET /rms/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:41 -0400] "GET /mail2/README HTTP/1.1" 404 468 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:41 -0400] "GET /mss2/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:42 -0400] "GET /mss/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:42 -0400] "GET /roundcubemail/README HTTP/1.1" 404 473 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:43 -0400] "GET /rc/README HTTP/1.1" 404 466 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:43 -0400] "GET /webmail/README HTTP/1.1" 404 470 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:44 -0400] "GET /roundcube/README HTTP/1.1" 404 470 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:44 -0400] "GET /mail/README HTTP/1.1" 404 468 "-" "Morfeus strikes again."
74.54.205.122 - - [05/Apr/2011:06:24:45 -0400] "GET /README HTTP/1.1" 404 464 "-" "Morfeus strikes again."
```

So it seems some hacker "morfeus" is trying to get in.  However when looking at the errors all the files he tried to access showed up in the error.log file as well because they are not there.  So it looks like he was unsuccessful.

Now the strangest thing.  I disable port 80 on my forwarding and even shutdown apache and the uploads are still there on my router.  After checking the logs yet again the dest ip is either my servers ip or 255.255.255.255.  Could it be some other program on my computer that is causing all this upload data.  If so what is the best way to find out?

---

### Post by SeijiSensei on 2011-04-05
That's a "script kiddie" running a canned exploitation script that tests to see if any of a large number of known exploits can be found on your server.  It looks like the attacker is hoping to find a way to turn your server into a proxy.  All those 404 errors are a good indication that you're not playing along.

The real Morpheus would be doing a better job, or else asking Trinity for some help using nmap.

---

### Post by Joe of loath on 2011-04-05
Ah, script kiddies. Their uselessness never fails to amuse me.

"TROLOLOLO HOW I CAN HACK WIFI ON VISTA PLZ?" Etc.

---

### Post by Hack.The.Pow. on 2011-04-06
> **SeijiSensei said:**
> That's a "script kiddie" running a canned exploitation script that tests to see if any of a large number of known exploits can be found on your server.  It looks like the attacker is hoping to find a way to turn your server into a proxy.  All those 404 errors are a good indication that you're not playing along.

The real Morpheus would be doing a better job, or else asking Trinity for some help using nmap.

Ahh thats what I figured.  Good to know I'm keeping him out :)

Anyways as far as the uploads it turns out that my idiot friend had like 4 seasons of a tv show running in a torrent so thats what was hogging all the bandwidth.  

I would like to know however what the unknown user warn kernel messages are in my router logs.  They are still showing up but not as frequently.  Here is a snipit.

```
Apr  6 14:33:08 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46345 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:33:37 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46530 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:33:49 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46655 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:34:10 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46827 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:34:18 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:28 SRC=221.192.199.46 DST=98.229.4.15 LEN=40 TOS=0x00 PREC=0x20 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
Apr  6 14:34:20 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46928 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:34:27 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=46978 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:35:09 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47291 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:35:12 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47326 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:35:18 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:2c SRC=113.197.74.12 DST=98.229.4.15 LEN=44 TOS=0x00 PREC=0x20 TTL=244 ID=8092 PROTO=TCP SPT=80 DPT=31666 WINDOW=8190 RES=0x00 ACK SYN URGP=0 OPT (020402
Apr  6 14:35:39 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47531 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:36:07 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47749 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:36:20 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47831 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:36:33 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=47947 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:36:38 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:86 SRC=85.159.130.144 DST=98.229.4.15 LEN=134 TOS=0x00 PREC=0x20 TTL=43 ID=57051 PROTO=UDP SPT=51396 DPT=3799 LEN=114 
Apr  6 14:36:40 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:86 SRC=85.159.130.144 DST=98.229.4.15 LEN=134 TOS=0x00 PREC=0x20 TTL=43 ID=39626 PROTO=UDP SPT=51396 DPT=3799 LEN=114 
Apr  6 14:36:44 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=00:1c:10:5a:b8:4d:00:24:c4:27:ad:e2:08:00:45:20:00:86 SRC=85.159.130.144 DST=98.229.4.15 LEN=134 TOS=0x00 PREC=0x20 TTL=43 ID=11769 PROTO=UDP SPT=51396 DPT=3799 LEN=114 
Apr  6 14:37:10 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4f SRC=73.171.228.1 DST=255.255.255.255 LEN=335 TOS=0x00 PREC=0x00 TTL=255 ID=48229 PROTO=UDP SPT=67 DPT=68 LEN=315 
Apr  6 14:37:10 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4f SRC=73.171.228.1 DST=255.255.255.255 LEN=335 TOS=0x00 PREC=0x00 TTL=255 ID=48234 PROTO=UDP SPT=67 DPT=68 LEN=315 
Apr  6 14:37:40 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=48420 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:37:54 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=48518 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:38:32 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=48873 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:38:32 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=48878 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:38:54 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=49034 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:38:56 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=49043 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:39:07 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=49123 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:40:26 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:59 SRC=73.171.228.1 DST=255.255.255.255 LEN=345 TOS=0x00 PREC=0x00 TTL=255 ID=50042 PROTO=UDP SPT=67 DPT=68 LEN=325 
Apr  6 14:40:35 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:57 SRC=73.171.228.1 DST=255.255.255.255 LEN=343 TOS=0x00 PREC=0x00 TTL=255 ID=50098 PROTO=UDP SPT=67 DPT=68 LEN=323 
Apr  6 14:40:35 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:57 SRC=73.171.228.1 DST=255.255.255.255 LEN=343 TOS=0x00 PREC=0x00 TTL=255 ID=50102 PROTO=UDP SPT=67 DPT=68 LEN=323 
Apr  6 14:41:17 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:67 SRC=73.171.228.1 DST=255.255.255.255 LEN=359 TOS=0x00 PREC=0x00 TTL=255 ID=50452 PROTO=UDP SPT=67 DPT=68 LEN=339 
Apr  6 14:41:20 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:67 SRC=73.171.228.1 DST=255.255.255.255 LEN=359 TOS=0x00 PREC=0x00 TTL=255 ID=50479 PROTO=UDP SPT=67 DPT=68 LEN=339 
Apr  6 14:41:49 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:49 SRC=73.171.228.1 DST=255.255.255.255 LEN=329 TOS=0x00 PREC=0x00 TTL=255 ID=50699 PROTO=UDP SPT=67 DPT=68 LEN=309 
Apr  6 14:41:49 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:49 SRC=73.171.228.1 DST=255.255.255.255 LEN=329 TOS=0x00 PREC=0x00 TTL=255 ID=50702 PROTO=UDP SPT=67 DPT=68 LEN=309 
Apr  6 14:41:52 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=50717 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:42:08 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:63 SRC=73.171.228.1 DST=255.255.255.255 LEN=355 TOS=0x00 PREC=0x00 TTL=255 ID=50816 PROTO=UDP SPT=67 DPT=68 LEN=335 
Apr  6 14:42:12 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:63 SRC=73.171.228.1 DST=255.255.255.255 LEN=355 TOS=0x00 PREC=0x00 TTL=255 ID=50852 PROTO=UDP SPT=67 DPT=68 LEN=335 
Apr  6 14:42:33 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51032 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:42:34 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51050 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:43:08 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51328 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:43:49 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:71 SRC=73.171.228.1 DST=255.255.255.255 LEN=369 TOS=0x00 PREC=0x00 TTL=255 ID=51614 PROTO=UDP SPT=67 DPT=68 LEN=349 
Apr  6 14:43:51 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:71 SRC=73.171.228.1 DST=255.255.255.255 LEN=369 TOS=0x00 PREC=0x00 TTL=255 ID=51627 PROTO=UDP SPT=67 DPT=68 LEN=349 
Apr  6 14:43:58 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=51693 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:44:00 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=51720 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:44:16 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51855 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:44:19 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51885 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:44:19 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51890 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:44:23 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:49 SRC=73.171.228.1 DST=255.255.255.255 LEN=329 TOS=0x00 PREC=0x00 TTL=255 ID=51913 PROTO=UDP SPT=67 DPT=68 LEN=309 
Apr  6 14:44:24 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:49 SRC=73.171.228.1 DST=255.255.255.255 LEN=329 TOS=0x00 PREC=0x00 TTL=255 ID=51929 PROTO=UDP SPT=67 DPT=68 LEN=309 
Apr  6 14:44:28 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=51965 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:44:30 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:6d SRC=73.171.228.1 DST=255.255.255.255 LEN=365 TOS=0x00 PREC=0x00 TTL=255 ID=51985 PROTO=UDP SPT=67 DPT=68 LEN=345 
Apr  6 14:44:31 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=51994 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:44:32 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=52014 PROTO=UDP SPT=67 DPT=68 LEN=311 
Apr  6 14:44:33 unknown user.warn kernel: DROP IN=vlan1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:c4:27:ad:e2:08:00:45:00:01:4b SRC=73.171.228.1 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=255 ID=52021 PROTO=UDP SPT=67 DPT=68 LEN=311 
```

---

### Post by Doug S on 2011-04-06
[FONT=Calibri][SIZE=3]Without the raw packet it is not certain what is going on. I am also not familiar with this particular type of request (or I didn't look through my stuff hard enough). My best guess is that 73.171.228.1 is sending some form of BOOTP/DHCP request ( ports 67 and 68 ) . It doesn't know the actual mac address or IP address, which is quite normal until things get going.[/SIZE][/FONT]

---

### Post by BkkBonanza on 2011-04-06
Those appear to be broadcast packets trying to obtain an IP address by DHCP. Not sure why they are marked unknown as they seem to be DROP messages from iptables or some firewall using iptables. And not sure why they have a src IP already. Mis-configured network device?

It says it's coming in on vlan1, which seem odd. Have you configured a vlan on your router? Maybe some device on your network is misconfigured to use a vlan.

---

### Post by Hack.The.Pow. on 2011-04-07
> **BkkBonanza said:**
> Those appear to be broadcast packets trying to obtain an IP address by DHCP. Not sure why they are marked unknown as they seem to be DROP messages from iptables or some firewall using iptables. And not sure why they have a src IP already. Mis-configured network device?

It says it's coming in on vlan1, which seem odd. Have you configured a vlan on your router? Maybe some device on your network is misconfigured to use a vlan.

the vlan1 interface is my router's(running tomato) interface for traffic coming into or out the internet.  Tomato uses a firewall automatically to keep out unwanted traffic.  I believe the firmware is based on linux somehow so that may appear to be DROP messages from iptables.

I checked on the ip that occurred most frequently and it was Comcast which is my internet service provider.  They just checking up on me?

---

### Post by Doug S on 2011-04-07
[SIZE=3][FONT=Calibri]Again, without the raw packet it is hard to know for sure, so I am guessing a little here. I think that 73.171.228.1 is the BOOTP/DHCP server ( port 67 ) asking any client ( port 68 ) to please register via asking for a DHCP license. For reasons that I do not know, your router DROPs those packets. Perhaps it should not. Maybe your router is setup with a static IP address and doesn't use DHCP. Maybe your ISP still wants you to get even a static ip address via DHCP (mine does). I think it becomes a matter between you and your ISP. However, if things are working perhaps don't worry about it.[/FONT][/SIZE]

---

