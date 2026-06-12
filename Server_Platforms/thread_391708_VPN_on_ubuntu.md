---
title: "VPN on ubuntu"
date: 2007-03-23
forum: Server Platforms
---

### Post by pixelis on 2007-03-23
Hello, sorry for my bad english , my question is how to set up a VPN server ?

i have a very poor expireance with ubuntu server , i know some few commands i know whre is the configs but i can't find the info about making VPN server on ubuntu server, latter there will be clients who are using windows so i need that they can connect to my ubuntu server .

P.S.
i know that my question sounds maybe different or stupid , anyway thx who will answer me !

I need help

---

### Post by Icidic on 2007-03-23
> **pixelis]Hello, sorry for my bad english[/quote]

Hehe... Don't worry mate, I've seen worse - from people that SPEAK English as their first language :eek:.

[quote=pixelis]my question is how to set up a VPN server ?

i have a very poor expireance with ubuntu server , i know some few commands i know whre is the configs but i can't find the info about making VPN server on ubuntu server, latter there will be clients who are using windows so i need that they can connect to my ubuntu server .[/quote]

Righto.  So you want to get a VPN Server running on Ubuntu Linux?  Well, firstly, what version of Ubuntu Linux are you running?  The reason I ask, is, if this VPN Server is going to be for production use, you might want to make sure you're running Ubuntu Linux Server Edition, and probably the Long Term Support release - Dapper Drake 6.06 LTS.

After that's all sorted out and installed, we need to find out what type of VPN you want to get going.  There are many different types - IPSec, L2TP, PPTP, OpenVPN to list a few.  However, thanks for mentioning you want Windows Clients to be able to connect - because that narrows it down a little bit :).

If you're going to have Windows (NT\2000\XP\Vista) Clients connecting (I'm excluding 9x based Windows, as no-one should be running those O\Ses anymore :p), the easiest way for them to VPN in, is using a VPN via technology called PPTP - or Point to Point Tunneling Protocol.  The reason for this is that Windows NT Based systems come with support for this built in.

The software you'd want to run on your Ubuntu Linux Server (Dapper Drake 6.06 LTS) would therefore be a Daemon called 'PoPToP', which is basically a PPTP VPN Server for Linux.  It's very easy to get going, and can intergrate with many different types of user databases (Active Directory on Windows 2000\2003 Server, MySQL, Local, LDAP, etc.).  You should be able to install it via Synaptic, but you're running Server Edition right  said:**
> 
[*]Searching these wonderful Ubuntu Forums
[*]Visiting the [Ubuntu Wiki]("http://wiki.ubuntu.com/") - more specifically pages on PoPToP w\ Ubuntu Linux
[*]Checking out the [PoPToP site]("http://www.poptop.org/") - there is a lot of useful information there
[*]And finally - Googling till the cows come home :D.
[/LIST]

One particular site which may be of help is HowToForge's 'How to install pptpd on Ubuntu Edgy'.  It's located [here]("http://www.howforge.com/how-to-install-pptpd-on-ubuntu-edgy").  Although it's Ubuntu Linux Edgy Eft (6.10), the instructions will most likely work for Ubuntu Linux Server Edition (Dapper Drake 6.06 LTS).

[quote=pixelis]P.S.
i know that my question sounds maybe different or stupid , anyway thx who will answer me !

Doesn't sound different\stupid at all.  Again, I've seen much stupider things on these and other forums :p.

[quote=pixelis]I need help[/quote]

I hope I've shed some light on the topic then :).

---

### Post by pixelis on 2007-03-24
Thx Icidic your helped me , now i don't have time but tommorov i will try to get cow home :D

yes you was right i am using ubuntu 6.06 with CLI.

:guitar:

---

### Post by StarLog on 2007-03-24
icidic,

I am running 6.10 with Beryl 0.2.0 and I am trying to use KVpnc which runs fine except for the following error.

error: The required daemon (ipsec) isn't available, connect will be disabled.

How or what will I need to get that daemon running, I loaded the ipsec tools, and that did not work.

Thanks in advance mate.

Tom

---

### Post by Sweet on 2007-03-24
I'm running Dapper 6.06 LTS - Server Edition and I'm trying to set up a pptp server (pptpd).

Upon first installing the server and entering the login details into /etc/ppp/chap-secrets the connection (from WinXP machine) would get to "Checking password" and then timeout.

I reinstalled it after trying a few things and now it does not even get to the "Checking password" stage. Though the syslogd messages are the same IIRC:

```
Mar 25 03:04:22 thomaspaine pptpd[5633]: CTRL: Client 87.112.29.126 control connection started
Mar 25 03:04:22 thomaspaine pptpd[5633]: CTRL: Starting call (launching pppd, opening GRE)
Mar 25 03:04:22 thomaspaine pptpd[5633]: GRE: socket() failed
Mar 25 03:06:32 thomaspaine pptpd[5633]: CTRL: Session timed out, ending call
Mar 25 03:06:32 thomaspaine pptpd[5633]: CTRL: Reaping child PPP[5634]

```

What on earth is "GRE: socket() failed", I looked about on the net and didn't find anything useful :( 

Thanks for your help.

Sweet

---

