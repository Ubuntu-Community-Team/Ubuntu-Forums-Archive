---
title: "Domain controller?"
date: 2009-03-19
forum: Server Platforms
---

### Post by don bohrer on 2009-03-19
At work I am entirely windows based and that's not an entirely bad thing! However... that little voice... you know the one that leaves you glassy eyed with a grin on your face was asking me is it possible to replace my windows dc and all my windows workstations with ubuntu?

Is it possible to replace the windows DC hosting SAM db with an Ubuntu server doing the same thing? What's ubuntus equiv of Active Directory? 

thanks

---

### Post by koenn on 2009-03-20
> **don bohrer said:**
> ? What's ubuntus equiv of Active Directory? 


MS AD is basically Kerberos with some modifications by MS + LDAP implemented the Microsoft way + and some additional stuff, like for gpo's etc.

You can come pretty close by running Kerberos, OpenLDAP, and Samba (for file sharing stuff most people associate with AD, such as logon scripts and home directories) + soem tweaks to mimic GPO's etc.

I don't know whether these come bundled with Ubuntu Server, you may have to look up some docs.

There are also Directory Services other than MS Active Directory, mainly by IBM, Novell, ...  They'lll run on Linux, but probably aren't in the ubuntu repos

---

### Post by don bohrer on 2009-03-20
I would be nice to have ubuntu have default server roles that minic what MS does. It would make implementing an Ubuntu server much easier.

thanks koenn

---

### Post by jamesrfla on 2009-03-20
I know you can connect a Ubuntu desktop to a domain using [http://www.likewise.com/](http://www.likewise.com/) I don't think Ubuntu has a server version of active directory yet. I hear that they are working on one. They call it Ubuntu Directory Server.

---

### Post by HermanAB on 2009-03-21
There are two types of MS Active Directory: Win2000 and Win2003.

The Samba project provides a Domain server for the older Win2000 type.  The newer Win2003 type of ADS is still under development: 
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Cheers,

Herman

---

### Post by koenn on 2009-03-21
> **HermanAB said:**
> There are two types of MS Active Directory: Win2000 and Win2003.

The Samba project provides a Domain server for the older Win2000 type.  The newer Win2003 type of ADS is still under development: 
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Cheers,

Herman

Not exactly. Microsoft had the "NT4 domain" and, since Win2000, the Active Directory domain. 
Samba is capable of being an NT4-style domain controller, or can be a member of an Active Directory domain, but can't act as an AD Domain controller yet. This mains to set up an AD domain, you'd have to run a Windows 2000 Server or newer.

---

### Post by mistako on 2009-03-21
> **don bohrer said:**
> 
Is it possible to replace the windows DC hosting SAM db with an Ubuntu server doing the same thing? What's ubuntus equiv of Active Directory? 

thanks

Hi. I think it's possible. Look at here [http://sadms.sourceforge.net/]("http://sadms.sourceforge.net/") . If it wont help look at "man smb.conf". :D

---

### Post by capscrew on 2009-03-21
> **mistako said:**
> Hi. I think it's possible. Look at here [http://sadms.sourceforge.net/]("http://sadms.sourceforge.net/") . If it wont help look at "man smb.conf". :D

I believe that sadms is an abandoned project.  Nothing has been updated for quite awhile (Gutsy).

---

### Post by Vegan on 2009-03-22
> **capscrew said:**
> I believe that sadms is an abandoned project.  Nothing has been updated for quite awhile (Gutsy).

By the look of it, looks like years now. Another project rotting away.

---

### Post by don bohrer on 2009-03-22
It would be a huge step in gaining acceptance by the corporate IT world if Ubuntu could easily fill any of the roles that MS servers already do. While licensing fee's for MS are prohibitive at times another reason companies are not able to migrate are the industry specific applications they use. 


don

---

### Post by capscrew on 2009-03-23
> **don bohrer said:**
> It would be a huge step in gaining acceptance by the corporate IT world if Ubuntu could easily fill any of the roles that MS servers already do. While licensing fee's for MS are prohibitive at times another reason companies are not able to migrate are the industry specific applications they use. 


don
The design of a unified LDAP, KERBROS, dynDNS, ACL package is a huge undertaking.  There are alternatives to MS AD.  [[COLOR="Red"]**Novell eDirectory **[/COLOR]]("www.novell.com/products/edirectory/") is a great alternative and it runs on SUSE Linux.  I believe [[COLOR="Purple"]**Sun has an LDAP server**[/COLOR]]("www.sun.com/software/products/directory_srvr_ee/dir_srvr/index.xml") but no dynDNS integration. 

There are 2 projects working towards a solution right now.  They are [[COLOR="Green"]**eBox**[/COLOR]]("ebox-platform.com/")  and [[COLOR="RoyalBlue"]**Zivios**[/COLOR]]("www.zivios.org/").  Both are very bleeding edge ie: still problematic.

The parts are there, but only Microsoft and Novell have put it all together in a stable package at this time.

---

### Post by koenn on 2009-03-23
> **don bohrer said:**
> It would be a huge step in gaining acceptance by the corporate IT world if Ubuntu could easily fill any of the roles that MS servers already do. While licensing fee's for MS are prohibitive at times another reason companies are not able to migrate are the industry specific applications they use. 


don

It would be a huge step, but I'm not sure if it's the right direction.

As I mentioned, MS AD is basically Kerberos with some modifications by MS + LDAP implemented the Microsoft way + and some additional stuff, like for gpo's etc.

one issue with that is that Kerberos and LDAP are standard protocols, but MS implements them a litte different fro the standard, making integretion with non-MS products harder, and difficult to reproduce, since they usually don't make their code public.

An other thing is that a lot of the add-ons (group policy objects, software distribution, ...) are features that were added to solve a very specific Windows problem, i.e. the remote management of an operating system that was designed as a stand-alone system.

Trying to replace that will always put Ubuntu in the "cheap knockoff, costs less but isn't nearly as good" corner.

---

### Post by don bohrer on 2009-04-01
If Ubuntu isn't in the market to directly compete with MS in a corporate environment then what market are they going after? How will it gain acceptance in the business IT world? 

Koenn, you make some good points, and something to thing on. 

capscrew, thanks for the information. I'll have to do some reading.

---

### Post by koenn on 2009-04-01
I don't know if Ubuntu is in the market to directly compete with MS in a corporate environment. I can imagine Ubuntu as a server in an AD environment, as a member server with a specific role other than domain controller (file server, platform for web apps or other server-based applications, network infrastructure server, ... )

i can also see Ubuntu as a server in a linux environment or an other environment without a need for MS AD, GPO, etc, Ubuntu made its nameas a desktop OS first.  

To compete with Windows as a domain controller, a product with a 10 year head start in development time, in an area where the competition holds all the cards (closed source and no specs on both the server and the client side) would be ... a challenge ? a brave choice ? sure, but maybe not a sound business decision.

On the other hand, I tend to leave such decisions to those who actually have to power and influence to act on them. That would be Canonical, not me.

---

