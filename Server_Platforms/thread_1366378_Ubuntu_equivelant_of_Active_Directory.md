---
title: "Ubuntu equivelant of Active Directory"
date: 2009-12-28
forum: Server Platforms
---

### Post by jhy2a on 2009-12-28
I am the I.T. Director at a church and we are looking into a complete overhaul of our I.T. infrastructure. We are moving over to a centralized network from an ad-hoc network. We are adding a couple of new machines to our network at this time as well. One question that the Senior pastor has brought up is security. Currently only 2 machines even require a password. I am putting in a Linux file server but was wondering if anyone knew of a Linux equivelant to Active Directory (since this is a small church with a limited budget, we can't afford to purchase Active Directory)? It would be nice to tell the pastor that we have a security solution that we can actually afford in our budget.

---

### Post by gradinaruvasile on 2009-12-28
There is samba 4. We did a test in our office and succesfully managed to authenticate a Windows machine against samba 4 (CentOS server). I know that our admin used the samba 4 wiki with default settings without any other modification to the config files and it was working in about 2 hours.

Samba4 is not ready for production use, but we found it quite stable. I dont know about advanced settings, we just created 2 active directory users, one admin, one restricted and logged in with them. It was working.

See the wiki:

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by msw on 2009-12-28
It really depends on what your goal is with AD. If you are simply looking for domain authentication then any version of Samba can be a Domain Controller. As for replacing MS's AD in terms of extensive AD policies etc, Samba is not there, and to be frank will probably never have the capability in the same depth as MS....not to mention 99.99% of the AD sofware tools are Windows based.

In any case, having your pc's on a domain network, whether that be MS or Samba based, does not imply security as there is a lot more work involved in achieving real security. To quote Bruce Schneier "Security is a process not a product".

---

### Post by jhy2a on 2009-12-28
> **msw said:**
> It really depends on what your goal is with AD.
 
Simple authentication is not our only goal here although it is one of them. We are looking for access controls, group policies, etc... things of this nature. I will check out Samba4 but I think you are correct in that it may not be all that we are looking for, but it might put us in the ballpark at least. Thanks for your input fellows.

---

### Post by Fire_Chief on 2009-12-28
Not one to sing praises of Microsoft but they do offer a Charity Open License for Server 2008 R2 for $110. Suspect you're probably a qualifying non-profit organization. This was found at CDW. [http://www.cdw.com/shop/products/default.aspx?EDC=1826198]("http://www.cdw.com/shop/products/default.aspx?EDC=1826198")

Cheers!

NOTE: This does not included media or documentation

---

### Post by jhy2a on 2009-12-29
> **Fire_Chief said:**
> Not one to sing praises of Microsoft but they do offer a Charity Open License for Server 2008 R2 for $110. Suspect you're probably a qualifying non-profit organization. This was found at CDW. [http://www.cdw.com/shop/products/default.aspx?EDC=1826198](http://www.cdw.com/shop/products/default.aspx?EDC=1826198)
 
Cheers!
 
NOTE: This does not included media or documentation
 
 
 
Hmmm.... that is something I might need to look into. I was hoping for a inexpensive (as in free) alternative, but the pastor might agree to $110. Thanks for the feedback guys!!!

---

### Post by ReverendKnoxville on 2009-12-30
Hi,

This is my first post, hope it helps.

Manually setting up Samba as a Linux/Unix rookie is not fun (particularly if you want to do fancy stuff like connect to LDAP). Your best bet is to go with ebox 1.2, it will handle authentication and file sharing quite well between windows XP desktops and it's Ubuntu base. It essentially combines ldap, samba, mail server (dovecot?), jabber, etc. It will do pretty much anything a small to medium sized church wants to do and is absolutely rock solid. I will never again install a winserver because I have happy users with ebox and let's be frank: nobody likes CAL's. :)

I use it for a 200 person NGO in Kunming, China. Most of my guests are ubuntu guests so I also modify the default e-box slightly to accomodate linux clients:

I share /home/samba/users via NFS and mount it in the clients as the same.

I modify /etc/ebox/80samba.conf to give a bash login instead of /bin/false (login_shell = /bin/bash)

I also open up OpenLDAP to be seen by the outside network by changing from loopback (127.0.0.1) to 0.0.0.0 (do be aware that leaves your LDAP directory COMPLETELY OPEN and do be careful with it)

Now you can connect all manner of clients: XP, OpenSuse, Mac, Ubuntu, etc

There is also an expiremental client package for Ubuntu 9.04 last I checked that will automate things like e-mail setup if you use evolution, but I confess I've not used it yet because I'm old school and have an install server and scripts to setup my clients.

Samba4 looks cool, but I haven't tried it and don't recommend alpha/beta for production environments. I'll probably jump a school that I also administer (all XP clients attached to ebox 1.2) to it when it becomes stable though.

Good luck & God bless,

-Knoxville

---

