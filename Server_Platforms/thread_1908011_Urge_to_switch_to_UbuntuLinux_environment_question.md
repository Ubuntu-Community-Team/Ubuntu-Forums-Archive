---
title: "Urge to switch to Ubuntu/Linux environment questions"
date: 2012-01-12
forum: Server Platforms
---

### Post by morgue888 on 2012-01-12
I have done some searching for the situation I will present in a moment but most of the articles I have found are rather dated. Any help or pointers in the right direction will be greatly appreciated. 

Running a small shop off ESXi 4.1 (free) the needs are very basic.
(small shop being about 5 local 1-2 remote users)
Prior to migration I plan to update ESXi to 5.0.
I am aware of limitations in regards to specialized software IE: Peachtree and Quickbooks.
There will inherently still be a need to keep a few windows based machines around.
I would like to migrate to a more Linux based environment overall.

The reasons I would like to migrate:
Reduce software upgrade/update costs.
Enhance security by updating existing software. 
(running server 2003 exchange 2003 currently w/ xp clients running office 2k-2k3)

The goals I wish to accomplish are as follows:
Centralized login capability for windows and Linux clients/server
(is this possible?)
Account bound access restrictions to a centralized file storage
(for windows and linux client/servers)
Email server w/ AV & Spam filtering
(what are the top choices and perhaps a comparison)
VPN+RDP access from a windows client 
(Teamviewer or VNC are the best options I know of for Remote desktop sessions)

Note: I may add to this list but this is all I can think of off the top of my head.


Thanks in advance!

P.S. If there is a recent answer to a similar post as this somewhere I have not seen, I apologize.
If the above is true kindly point me in the right direction.

---

### Post by rubylaser on 2012-01-12
[Zentyal]("http://www.zentyal.com/") is a good, easy solution to much of this.

---

### Post by CharlesA on 2012-01-12
You can do SSO (single-sign on) with LDAP. I would recommend checking out some of the [turnkey appliances]("http://www.turnkeylinux.org/") for that task since LDAP isn't exactly super easy to configure.

---

### Post by rubylaser on 2012-01-12
> **CharlesA said:**
> You can do SSO (single-sign on) with LDAP. I would recommend checking out some of the [turnkey appliances]("http://www.turnkeylinux.org/") for that task since LDAP isn't exactly super easy to configure.

Turnkey appliances are also a great idea, and work VERY well.

---

### Post by morgue888 on 2012-01-17
Thank you for the suggestions. 
I will look into these.

I remember looking at turnkey a while back for their wordpress turnkey solution.
It worked really well.
I nearly forgot about turnkey though. Thanks for the reminder!

---

### Post by morgue888 on 2012-01-26
I had some misc issues with the turnkey PDC.
(Strange interface issues with browsers and I found it easier to config samba the old fashioned way)
I also just prefer to do things the hard way to better understand it.

I ended up going with setting everything up manually.
It is working great in my test environment.
There is still a lot of work to do but I figured I would post some info I found useful.

Good Tutorial for DNS basic config.
[http://www.youtube.com/user/cgermany77/search?query=ubuntu+dns](http://www.youtube.com/user/cgermany77/search?query=ubuntu+dns)

Good Tutorial for Sama PDC basic config.
[http://www.youtube.com/user/ReicheltAcademy](http://www.youtube.com/user/ReicheltAcademy)

---

