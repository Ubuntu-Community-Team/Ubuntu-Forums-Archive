---
title: "Windows Server vs Ubuntu Server"
date: 2009-07-24
forum: Server Platforms
---

### Post by AnimeOmega on 2009-07-24
Yes, I know this is a forum for ubuntu-stuff so the answer should be obvious... :D

I mainly want to know if what I want is possible with Ubuntu server and get 'pointed in the right direction'.

What I want:
* Create a 'Windows Domain' for Windows XP clients:
> All account information and privileges editable in the server.
> Users can login into any computer in the domain and have their desktop, wallpaper, documents, settings. 

Would be really nice:
* Install software from the sever to all the clients (.msi(?))
* Integrate Mac OS X clients
* Integrate Linux clients

Random Questions:
* How powerful (Processor & Ram) should the sever be for 10 clients? or 20? 
* What things should I read up on that will help me achieve my goals? (SAMBA, LDAP, etc)?

(Off-topic)For the curious:
I want to help a non-tech-savy high-school-teacher friend setup a better environment in a computer lab at a local high school. And no, I wont be experimenting with this there. 

Thanks ! :D

---

### Post by giggins on 2009-07-24
I can say that, for sure, this is possible with Ubuntu server, especially if you don't need multiple servers or LDAP. Samba is pretty easy to get up and running.

This guide pretty much walks you though it:
[https://help.ubuntu.com/9.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/9.04/serverguide/C/samba-dc.html)

The guide includes support for:

[LIST]
[*]An NT4 compatible Domain for XP Clients
[*]All accounts are stored on the server
[*]Any machine joined to the Domain will allow logins
[*]You can probably do remote installs of .msi files through login scripts
[*]Linux and OS X can use the file sharing services provided by the server
[/LIST]
If you really want to get fancy and support more complete cross-platform integration, you can try this guide on for size:
[https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix)

That one uses LDAP, and will support scaling to additional servers pretty easily, plus it holds all the posix info in LDAP, so Linux (and probably OS X) clients can use the server for authentication also.

Excellent question, and the good news is you probably won't have to spend money on a Windows license. :D

---

### Post by giggins on 2009-07-24
> **AnimeOmega said:**
> * How powerful (Processor & Ram) should the sever be for 10 clients? or 20? 

CPU and RAM really won't be too big of an issue... I think you'll get more benefit out of fast disks, probably in a RAID configuration. I'd say any modern, multi-core processor and 1GB of RAM (the more the merrier) will suffice for light usage. If all 20 clients are simultaneously copying files, then you will (obviously) see a performance hit. Moving stores to separate disks should help with that.

Just my thoughts. Your mileage will likely vary.

---

### Post by toupeiro on 2009-07-24
I think you need to take a few steps back and think about the big picture of what you are trying to accomplish.

1)  NT4 compatible domains are old, limited, have various security flaws which were never really fixed.  Any Enterprise or windows administrative tool you may want in the future will require Active Directory these days.

2) OpenLDAP != Active Directory.  You can make Linux do full active directory authentication and group policy enforcement since I believe 8.04.  There are other packages like Quest softwares Vintela offering which can do this on Linux, UNIX, IRIX etc etc.

Roaming Profiles are simple to setup.  This will get your wallpapers, desktop icons etc etc, available on all systems.  Active Directory does redirection, which is far more efficient.

I've never thought it was a great idea to run linux servers as windows domain controllers.  Samba 4 boasts Active Directory compatibility, but I would certainly wait until that support has matured a bit before you consider it in anything other than a test lab.

As much as I like Linux for stand alone servers, network IO, and outright stability and security, Microsoft has the best, and most scalable directory model available.  For everything Microsoft does that many in the linux community see as wrong, to deny them that would simply be a lie.

---

### Post by giggins on 2009-07-24
> **toupeiro said:**
> OpenLDAP != Active Directory.

I don't see where anyone stated "OpenLDAP == Active Directory". But I suppose its good to atleast point that out, incase anyone was confused.

> **toupeiro said:**
> You can make Linux do full active directory authentication and group policy enforcement since I believe 8.04.

This might be a good topic to discuss further. Are you saying there's a way to make Linux (hopefully Ubuntu) *provide* active directory authentication and group policy enforcement, or are you just stating that Linux can authenticate to AD?

> **AnimeOmega said:**
> I mainly want to know if what I want is possible with Ubuntu server and get 'pointed in the right direction'.

I'm worried that you may be spreading more [FUD]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt") and free Microsoft advertisements than helping answer the main question. I think you have valid points, but if you look at what AnimeOmega is asking for (10 - 20 clients), is it really necessary to go off on a tangent about how Samba and / or OpenLDAP is not as good at emulating Microsoft as Microsoft is?

I've had great experiences using Samba (and OpenLDAP), and I've got to say that I think the pros far outweigh the cons.

---

### Post by grantemsley on 2009-07-24
To be completely honest, if you want things like group policies and such for your domain, you are better off with a windows server.  I use linux for almost everything else...but for complete control over windows machines, a windows server domain does it with the least effort.

---

### Post by TwiceOver on 2009-07-24
The easiest would be to do a Windows Server environment.  I am fairly certain that Linux/Samba cannot control group policy settings.  The rest would be fairly easy.

Just remember to bring your wallet.

Server 200x Small Business ~$1000 w/ 5 Client Licenses
$100 for every license after that purchased in groups of 5 (so ~$500 for 5).

---

### Post by toupeiro on 2009-07-24
> **giggins said:**
> I don't see where anyone stated "OpenLDAP == Active Directory". But I suppose its good to atleast point that out, incase anyone was confused.



This might be a good topic to discuss further. Are you saying there's a way to make Linux (hopefully Ubuntu) *provide* active directory authentication and group policy enforcement, or are you just stating that Linux can authenticate to AD?



I'm worried that you may be spreading more [FUD]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt") and free Microsoft advertisements than helping answer the main question. I think you have valid points, but if you look at what AnimeOmega is asking for (10 - 20 clients), is it really necessary to go off on a tangent about how Samba and / or OpenLDAP is not as good at emulating Microsoft as Microsoft is?

I've had great experiences using Samba (and OpenLDAP), and I've got to say that I think the pros far outweigh the cons.

I always think its so funny how quick people are to throw the term FUD out there..  I support many linux and UNIX servers just at my specific job location that authenticate to AD every day, so the FUD factor is nil.  Throughout the company I work for, there are thousands of UNIX and Linux workstations and servers that are AD objects with full participation.  To better clarify what I said, ubuntu can be an active client in an AD200x domain, and interpret GPO (group policy objects).  

I'm well aware of what the OP asked for.  I brought up active directory in support of NTDOM's being very, very old and unsupported.  OpenLDAP is also not a sufficient alternative to AD, so by saying Active Directory != OpenLDAP, i'm reinforcing my oringinal point, AD for microsoft domains is the *right* thing to do, and since samba-AD is addmittedly (by their own project developers) not fully there yet, the OP really needs to step back and think about the direction he/she is planning to take, because it may not be the best for him/her, or whoever he/she is trying to set it up for.

Finally, I didn't go off on a tangent, I stated very accurate facts that aren't tinged by FOSS bias because I figure anyone wanting to setup domains and a handful of clients might be a bit more than a hobbiest and perhaps their reputation is on the line here..  I don't think you want a **current** windows domain model that half works because you didn't want to buy windows to build your domain controllers.  Sure Samba might do old NTDOM's, but you're unsupportable out the gate from a domain model perspective. Samba-AD is hot off the press, claiming to support AD2003, but in what mode?  Mixed? Native?  And now that the current directory model for AD is 2008, how will this samba AD controller participate in that environment?  Now If I went off and said that Samba could not participate in AD at all, or that it would crash constantly on you, that would be FUD.  Instead, I talked about what I knew about, and warned about what to be cautious about.  That is not FUD.  Thats what any reasonable IT consultant would do that would normally charge hundreds, maybe thousands of dollars for, except on UF I charge nothing because I just enjoy helping out.

If you're just playing around with domain models for fun, its a perfect opportunity to find out, but not if you are actually expecting to rely on it to be there and fully functional regardless of how many clients you have.

If you google around, you can find windows server [2003 standard SBE for around $399.]("http://www.buycheapsoftware.com/details.asp?productID=3112&cid=76")  even cheaper if you [buy it off ebay]("http://cgi.ebay.com/Microsoft-Windows-Server-2003-R2-Standard-Edition_W0QQitemZ180387023266QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item29ffe789a2&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|293%3A1|294%3A50"), and for the domain functionality you will get, its well worth it.

---

