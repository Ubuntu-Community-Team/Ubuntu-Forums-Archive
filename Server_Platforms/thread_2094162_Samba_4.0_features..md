---
title: "Samba 4.0 features."
date: 2012-12-13
forum: Server Platforms
---

### Post by honey_bee on 2012-12-13
[SIZE=2]hi,
The samba 4.0 has finally been released.I was reading its features at [/SIZE][_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]https://www.samba.org/samba/news/releases/4.0.0.html_[/COLOR][/SIZE][/COLOR][/SIZE]]("https://www.samba.org/samba/news/releases/4.0.0.html")[SIZE=2] .One thing which is confusing me is (as the release says ).[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana]"Samba 4.0 provides everything needed to serve as an Active Directory Compatible Domain Controller for all versions of Microsoft Windows clients currently supported by Microsoft, including the recently released Windows 8."[/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE] 
[SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]So for a new small/medium size network we can use samba 4.0 instead of MS windows server to authenticate windows clients ?

2- What is the minimum requirement for samba 4.0 using Ubuntu version ?

thanks
honey.[/FONT][/COLOR][/FONT][/COLOR][/SIZE]
[/FONT][/COLOR] 
[/SIZE]

---

### Post by Cheesemill on 2012-12-13
[SIZE=2]> **honey_bee said:**
> [COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]So for a new small/medium size network we can use samba 4.0 instead of MS windows server to authenticate windows clients ?
Ye[SIZE=2]s, you can replace the DC role on a Windows Server with a Ubuntu server running Sam[SIZE=2]ba 4.

[/SIZE][/SIZE] > 2- What is the minimum requirement for samba 4.0 using Ubuntu version ?
This all depends on the type of environment you are serving.[SIZE=2] The DC role isn't very CPU or disk intensive though so pretty much any modern hardware will run Ubuntu Server + Samba 4. [SIZE=2]Obviously[/SIZE] authenticating thousands of clients will need better hardware than serving tens of clients though[/SIZE][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR].
[/SIZE]

---

### Post by volkswagner on 2012-12-13
One thing to know about SAMBA4:  It does not have NetBIOS discovery.  So your windows clients won't be able to see the SAMBA4 server in "network neighborhood" or "Network" from Explorer file browser. 

You will need to manually specify the address in the address bar or simply create mapped network drives so you only need to do it once.

As far as requirements, you will see that you need to have DNS server on the SAMBA machine.  You can use the internal DNS or configure Bind9.

According to the how to on [SAMBA4 Wiki]("http://wiki.samba.org/index.php/Samba4/HOWTO"), it is best to use GIT to install.

If you follow the how to, you should have little or no issues.  The only issue I ran into was properly setting up my router DHCP options to forward DNS requests to SAMBA4

on router config for DNS options, I used option 6:
```
6,192.168.7.20,192.168.7.1
```

Plus point DNS at my routers ip in smb.conf.
```
dns forwarder = 192.168.7.1
```

---

### Post by honey_bee on 2012-12-13
thanks for your replies. We are going to make a fresh medium size network in which we will have 100 to 150 windows clients. All needs authentication. We not want to purchase windows server for our windows xp,win7 and win 8 clients machines. 
 
"Cheesemill" as you said that 
 
>  
"[SIZE=2][FONT=Verdana]Yes, you can replace the DC role on a Windows Server with a Ubuntu server running Samba 4."[/FONT][/SIZE]


[FONT=Verdana][SIZE=2]So I decise to install samba 4.0 as a Domain Controller and as "volkswagner" said that[/SIZE][/FONT]

> 
[SIZE=2][FONT=Verdana][FONT=Verdana][SIZE=2]"In the Samba 4.0 does not have NetBIOS discovery and need to manually specify the address in the address bar or simply create mapped network drives so you only need to do it once[/SIZE][/FONT]
[/FONT][/SIZE][SIZE=2][FONT=Verdana]
[/FONT][/SIZE]
[FONT=Verdana][SIZE=2]> [FONT=Verdana][SIZE=2]I can configure DNS as well in samba 4 box as well.[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Verdana][SIZE=2]So using these parameters I am sure that with samba 4 it will be a good achievement for us to use Linux as a domain controller.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Any more suggestion please must share.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]thanks[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]honey.[/SIZE][/FONT]

---

