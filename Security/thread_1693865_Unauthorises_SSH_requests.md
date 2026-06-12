---
title: "Unauthorises SSH requests"
date: 2011-02-23
forum: Security
---

### Post by bigmonmulgrew on 2011-02-23
Hi guys 
I've set up a web server using ubuntu 10.10

Since then I've noticed a lot of activity on my routers logs.
To be honest it may be a coincidence  as the logs dont go back very far.

The bulk of the connections all come from the same IP address. I must point out however that I'm not massivey familiar with the logs.

I'm just worried someone is trying to gain access to my server. How can I find out if someone has managed to access it and how do I stop them.

log below
```
Sat, 2000-01-01 00:01:08 - Send out NTP request to time-g.netgear.com
Sun, 2011-02-20 16:36:05 - Receive NTP Reply from time-g.netgear.com
Sun, 2011-02-20 16:36:39 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 16:36:39 - TCP Packet - Source:192.168.0.15,59997 Destination:74.125.77.100,80 - [HTTP rule not match]
Sun, 2011-02-20 16:36:40 - Administrator login successful - IP:192.168.0.15

Sun, 2011-02-20 16:34:56 - Router start up
Sun, 2011-02-20 16:52:47 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 16:59:41 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 17:09:42 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 17:21:10 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 17:38:32 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 17:56:04 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 18:11:46 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 18:24:45 - Administrator login successful - IP:192.168.0.15

Sun, 2011-02-20 18:34:11 - TCP Packet - Source:91.152.100.193,57030 Destination:78.86.140.13,22 - [SSH rule match]
Sun, 2011-02-20 18:34:17 - TCP Packet - Source:192.168.0.15,62312 Destination:78.86.140.13,21 - [FTP rule match]
Sun, 2011-02-20 18:35:46 - TCP Packet - Source:192.168.0.15,62332 Destination:78.86.140.13,22 - [SSH rule match]
Sun, 2011-02-20 18:44:30 - TCP Packet - Source:219.141.189.213,51930 Destination:78.86.140.13,22 - [SSH rule match]
Sun, 2011-02-20 18:44:52 - Administrator login successful - IP:192.168.0.15
Sun, 2011-02-20 18:46:01 - TCP Packet - Source:192.168.0.15,62496 Destination:78.86.140.13,8000 - [Open8000 rule match]
Sun, 2011-02-20 19:11:14 - TCP Packet - Source:192.168.0.15,62891 Destination:78.86.140.13,8000 - [Open8000 rule match]
Sun, 2011-02-20 19:11:38 - TCP Packet - Source:192.168.0.15,62895 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 07:11:08 - TCP Packet - Source:202.41.0.4,46413 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 09:23:01 - TCP Packet - Source:64.3.202.170,3799 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 09:48:26 - TCP Packet - Source:219.232.61.151,43268 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 11:53:26 - Administrator login successful - IP:192.168.0.15
Mon, 2011-02-21 12:16:40 - Administrator login successful - IP:192.168.0.15
Mon, 2011-02-21 12:41:50 - TCP Packet - Source:218.14.203.205,83 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 17:47:50 - TCP Packet - Source:81.255.130.187,45225 Destination:78.86.140.13,21 - [FTP rule match]
Mon, 2011-02-21 20:29:58 - TCP Packet - Source:174.142.130.220,28658 Destination:78.86.140.13,22 - [SSH rule match]
Mon, 2011-02-21 20:49:21 - TCP Packet - Source:113.11.194.83,26950 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:53:57 - TCP Packet - Source:218.14.203.205,45483 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:01 - TCP Packet - Source:218.14.203.205,45732 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:04 - TCP Packet - Source:218.14.203.205,45941 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:07 - TCP Packet - Source:218.14.203.205,46164 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:10 - TCP Packet - Source:218.14.203.205,46402 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:13 - TCP Packet - Source:218.14.203.205,46625 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:16 - TCP Packet - Source:218.14.203.205,46844 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:20 - TCP Packet - Source:218.14.203.205,47087 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:23 - TCP Packet - Source:218.14.203.205,47297 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:26 - TCP Packet - Source:218.14.203.205,47548 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:29 - TCP Packet - Source:218.14.203.205,47750 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:32 - TCP Packet - Source:218.14.203.205,48004 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:35 - TCP Packet - Source:218.14.203.205,48219 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:39 - TCP Packet - Source:218.14.203.205,48455 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:42 - TCP Packet - Source:218.14.203.205,48714 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:45 - TCP Packet - Source:218.14.203.205,48945 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:48 - TCP Packet - Source:218.14.203.205,49205 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:51 - TCP Packet - Source:218.14.203.205,49422 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:55 - TCP Packet - Source:218.14.203.205,49679 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:54:58 - TCP Packet - Source:218.14.203.205,49903 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:01 - TCP Packet - Source:218.14.203.205,50159 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:04 - TCP Packet - Source:218.14.203.205,50386 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:07 - TCP Packet - Source:218.14.203.205,50660 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:10 - TCP Packet - Source:218.14.203.205,56298 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:14 - TCP Packet - Source:218.14.203.205,56554 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:17 - TCP Packet - Source:218.14.203.205,56794 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:20 - TCP Packet - Source:218.14.203.205,57064 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:23 - TCP Packet - Source:218.14.203.205,57289 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:26 - TCP Packet - Source:218.14.203.205,57532 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:29 - TCP Packet - Source:218.14.203.205,57764 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:33 - TCP Packet - Source:218.14.203.205,58025 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:36 - TCP Packet - Source:218.14.203.205,58243 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:39 - TCP Packet - Source:218.14.203.205,58498 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:42 - TCP Packet - Source:218.14.203.205,58726 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:46 - TCP Packet - Source:218.14.203.205,58970 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:49 - TCP Packet - Source:218.14.203.205,59192 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:52 - TCP Packet - Source:218.14.203.205,59447 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:55 - TCP Packet - Source:218.14.203.205,59677 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 00:55:58 - TCP Packet - Source:218.14.203.205,59916 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 01:37:15 - TCP Packet - Source:124.205.128.170,47769 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 12:00:12 - TCP Packet - Source:173.0.48.166,17095 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 12:03:39 - TCP Packet - Source:81.3.138.118,57581 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:04 - TCP Packet - Source:218.14.203.205,35569 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:09 - TCP Packet - Source:218.14.203.205,35799 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:15 - TCP Packet - Source:218.14.203.205,36070 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:24 - TCP Packet - Source:218.14.203.205,36447 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:29 - TCP Packet - Source:218.14.203.205,36690 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:35 - TCP Packet - Source:218.14.203.205,36976 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:42 - TCP Packet - Source:218.14.203.205,37252 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:48 - TCP Packet - Source:218.14.203.205,37551 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:07:53 - TCP Packet - Source:218.14.203.205,37804 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:00 - TCP Packet - Source:218.14.203.205,38108 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:06 - TCP Packet - Source:218.14.203.205,38407 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:12 - TCP Packet - Source:218.14.203.205,38706 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:17 - TCP Packet - Source:218.14.203.205,38966 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:24 - TCP Packet - Source:218.14.203.205,39285 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:29 - TCP Packet - Source:218.14.203.205,39536 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:36 - TCP Packet - Source:218.14.203.205,39865 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:41 - TCP Packet - Source:218.14.203.205,40135 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:48 - TCP Packet - Source:218.14.203.205,40427 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:08:53 - TCP Packet - Source:218.14.203.205,40684 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:00 - TCP Packet - Source:218.14.203.205,40975 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:05 - TCP Packet - Source:218.14.203.205,41226 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:11 - TCP Packet - Source:218.14.203.205,41482 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:17 - TCP Packet - Source:218.14.203.205,41745 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:23 - TCP Packet - Source:218.14.203.205,41999 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:29 - TCP Packet - Source:218.14.203.205,42253 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:35 - TCP Packet - Source:218.14.203.205,42494 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:41 - TCP Packet - Source:218.14.203.205,42752 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:48 - TCP Packet - Source:218.14.203.205,43074 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:09:54 - TCP Packet - Source:218.14.203.205,43333 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:01 - TCP Packet - Source:218.14.203.205,43582 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:07 - TCP Packet - Source:218.14.203.205,36850 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:13 - TCP Packet - Source:218.14.203.205,37112 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:19 - TCP Packet - Source:218.14.203.205,37375 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:24 - TCP Packet - Source:218.14.203.205,37591 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:31 - TCP Packet - Source:218.14.203.205,37845 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:36 - TCP Packet - Source:218.14.203.205,38088 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:43 - TCP Packet - Source:218.14.203.205,38367 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:49 - TCP Packet - Source:218.14.203.205,38624 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 16:10:54 - TCP Packet - Source:218.14.203.205,38847 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 20:16:06 - TCP Packet - Source:219.129.239.118,33343 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 20:58:34 - TCP Packet - Source:219.129.239.118,54925 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 20:58:40 - TCP Packet - Source:219.129.239.118,55721 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 20:58:44 - TCP Packet - Source:219.129.239.118,56394 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 21:46:44 - TCP Packet - Source:217.172.179.114,35784 Destination:78.86.140.13,22 - [SSH rule match]
Tue, 2011-02-22 23:11:01 - TCP Packet - Source:67.137.238.164,46537 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:38 - TCP Packet - Source:217.172.179.114,57417 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:41 - TCP Packet - Source:217.172.179.114,57677 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:43 - TCP Packet - Source:217.172.179.114,57921 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:45 - TCP Packet - Source:217.172.179.114,58165 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:48 - TCP Packet - Source:217.172.179.114,58451 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:50 - TCP Packet - Source:217.172.179.114,58658 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:52 - TCP Packet - Source:217.172.179.114,58890 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:55 - TCP Packet - Source:217.172.179.114,59130 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:53:57 - TCP Packet - Source:217.172.179.114,59349 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:00 - TCP Packet - Source:217.172.179.114,59621 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:02 - TCP Packet - Source:217.172.179.114,59843 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:05 - TCP Packet - Source:217.172.179.114,60110 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:07 - TCP Packet - Source:217.172.179.114,60340 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:10 - TCP Packet - Source:217.172.179.114,60603 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:18 - TCP Packet - Source:217.172.179.114,33166 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:20 - TCP Packet - Source:217.172.179.114,33380 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:23 - TCP Packet - Source:217.172.179.114,33638 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:25 - TCP Packet - Source:217.172.179.114,33902 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:28 - TCP Packet - Source:217.172.179.114,34154 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:31 - TCP Packet - Source:217.172.179.114,34444 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:33 - TCP Packet - Source:217.172.179.114,34718 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:36 - TCP Packet - Source:217.172.179.114,35007 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 01:54:39 - TCP Packet - Source:217.172.179.114,35254 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 02:45:06 - TCP Packet - Source:87.106.63.254,48099 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 03:26:21 - TCP Packet - Source:87.106.63.254,42003 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 14:19:44 - TCP Packet - Source:212.33.238.199,36067 Destination:78.86.140.13,22 - [SSH rule match]
Wed, 2011-02-23 14:36:05 - Send out NTP request to time-g.netgear.com
Wed, 2011-02-23 14:36:02 - Receive NTP Reply from time-g.netgear.com
Wed, 2011-02-23 18:04:20 - Administrator login successful - IP:192.168.0.15
Wed, 2011-02-23 18:13:44 - Administrator login successful - IP:192.168.0.15


```

---

### Post by The Cog on 2011-02-23
Those are outgoing connection attempts, not incoming. They are to a server run by canonical - the providers of Ubuntu. It's almost certainly your system trying to check for the availability of security updates.

---

### Post by bigmonmulgrew on 2011-02-23
Ah perhaps I should have vetted the log.
I'm more concerned about the stuff at the bottom

Source:217.172.179.114

---

### Post by bodhi.zazen on 2011-02-23
If you are running a ssh server you will see tons of attempts to log in.

IMO you simply need to use ssh keys and disable password authentication.

If it really bothers you, use iptables, denyhost, fail2ban, or change the port but honestly as long as you disable password authentication you can just as easily disable the logs.

If you want to monitor your network, use snort, looking through  logs is extremely inefficient and prone to errors.

---

### Post by The Cog on 2011-02-24
Ah, sorry. I see now. Yes, I think that's some bot running a dictionary of usernames and passwords against you. What bodhi.zazen said is spot on.

---

