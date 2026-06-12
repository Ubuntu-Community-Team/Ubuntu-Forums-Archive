---
title: "Firewall Setup With Free Chat &amp; Voice Comm Server"
date: 2008-03-11
forum: Security Discussions
---

### Post by ricardohf on 2008-03-11
Dear friends,

I am a network system administrator and I use Kernel 2.6 and iptables as a firewall and NAT.  My company decided to install a Windows application called CYF (CALL YOU FREE) in all the desktops of the customer support and sales department.   CALL YOU FREE is a communications application to answer incoming webcalls and chat contacts from our company’s website and we are using its freeware version.

The issue is that when I tested the application with my computer connected directly to the internet (public IP) it works fine.  But when I connected my computer in a private IP behind the NAT I cannot even login to the system.

I conclude that there must be a firewall problem, so I opened all ports in the firewall and it works fine.

I would like to know how I can find out what port(s) does the application try to access.   It seems to be an Asterisk based application using IAX protocol so I tried opening port 4569 but nothing happened.

I would appreciate your help because I really don’t know how to find out what port should I open, unless I try one by one, or it may use yet more than one port.

Thanks,
Ricardo Houssef.

---

### Post by Oldsoldier2003 on 2008-03-11
> **ricardohf said:**
> Dear friends,

I am a network system administrator and I use Kernel 2.6 and iptables as a firewall and NAT.  My company decided to install a Windows application called CYF (CALL YOU FREE) in all the desktops of the customer support and sales department.   CALL YOU FREE is a communications application to answer incoming webcalls and chat contacts from our company’s website and we are using its freeware version.

The issue is that when I tested the application with my computer connected directly to the internet (public IP) it works fine.  But when I connected my computer in a private IP behind the NAT I cannot even login to the system.

I conclude that there must be a firewall problem, so I opened all ports in the firewall and it works fine.

I would like to know how I can find out what port(s) does the application try to access.   It seems to be an Asterisk based application using IAX protocol so I tried opening port 4569 but nothing happened.

I would appreciate your help because I really don’t know how to find out what port should I open, unless I try one by one, or it may use yet more than one port.

Thanks,
Ricardo Houssef.
check the docs from the vendor?

---

### Post by mcomotti on 2008-03-13
This may help too. I tried to run the “cyf.exe” on a Windows Vista and it didn’t run because of permission problems, but It run well as administrator (right button on the program icon and click “run as administrator”).

Note that only the application has to be run as administrator, not the webphone.

---

