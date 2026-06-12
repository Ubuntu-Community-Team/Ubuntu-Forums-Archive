---
title: "Wireless Authentication to Samba PDC"
date: 2006-11-25
forum: Server Platforms
---

### Post by kahm007 on 2006-11-25
Hello everyone.  Having been throughly impressed with Ubuntu as a workstation I decided to try the Samba PDC solution that was available from [howtoforge]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")
This worked well for all my wired computers however I couldn't get the Wireless computers to connect to the domain.  I had to plug them up to the router and connect to my profiles.  And every time I try to connect through the wireless I can't connect.  Logically I suspect that its because the wireless software starts after you login into the domain so naturally.  No connection no login and it goes to a cached profile.  I have been beating my head against a wall trying to figure out how to get around this problem. I have found now explanation of my problem.  

From what I can gather, if I can get some form of authentication setup between my Ubuntu PDC and my Windows XP machines it should work.  I have been looking for a good guide for setting up a Radius server or even LDAP but the scope of them is larger then my need.  I have 2 laptops that I am trying to get connected.  Anybody have a suggestion or answer to this particular problem?

---

### Post by elst on 2006-11-26
There are a couple of potential issues here. If you post the contents of /etc/samba/smb.conf, and the specific operating systems that the clients and the server run, then it should be possible to work this out.

---

