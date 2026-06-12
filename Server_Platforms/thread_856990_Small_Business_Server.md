---
title: "Small Business Server"
date: 2008-07-12
forum: Server Platforms
---

### Post by disabledveteran on 2008-07-12
I am working on an Ubuntu-based small to medium business server, and wanted to post my ideas here for review by the crowd.

Server Purpose:  Open Source small business server to be used as an Ubuntu-based drop-in replacement for commercial, closed-source products.  Similar to ClarkConnect, Collax, or SMEServer.

Hardware Constraints: Mini-ITX system scalable to rack-mounted, RAID-enabled, or SAN/NAS connected solution.  Wireless management strongly desired for a all-in-one SBS solution.

Design Constraints: software must be free, redistributable, and established.  I am not a Linux programmer, so the system will be comprised of established packages that can be customized via graphic or html/PHP template or design changes.

Solution:
[LIST]
[*]Ubuntu 8.04 Server Base
[*]Hard Drive Encrypted + LVM
[*]Webmin 1.420 Plus specific modules
[*]Kolab Server (Apache, OpenLDAP, PostFix, Cyrus IMAP, SASL) + OpenPKG to install Kolab components)
[*]SwiftMailer
[*]BIND
[*]DNS Server
[*]DHCP Server
[*]Turtle Firewall
[*]PHP 5 +extensions
[*]MySQL
[*]Horde Application Framework 3.2.1
[*]Horde Groupware Webmail Edition 1.1 (email, calendar, todo, file share, ec.)
[*]Jabber IM Server
[*]Privoxy
[*]SpamAssassin
[*]SQUID
[*]DansGuardian
[*]Surftrackr
[*]OpenVPN
[*]IPSEC
[*]CLAM AV
[*]Commercial AV (to be determined)
[*]PostGrey
[*]SA-BlackList
[*]DSPAM
[*]MajorDomo
[*]ProFTP
[*]SAMBA
[*]SMBD
[*]Print Server (CUPS)
[*]OpenSSL
[*]Bandwidth Management
[*]SNORT / SNORTSAM
[*]HylaFax
[*]Asterisk
[*]DMCrypt
[*]Open1X (Wireless Security)?
[*]Backup Solution (Restore-Backup or Zmanda (undecided))
[/LIST]

Also, I would appreciate any recommendations on a CRM/ERP/HR/Accounting solution appropriate for small to medium businesses.

I've got the box sitting next to my desk and am installing the apps now.

I realize that the best setup would be to separate the server from the security (firewall) but many small businesses either can't or won't do this.  For my clients, I recommend Untangle as a gateway and can disable some of the security and anti-SPAM features of the SBS.

Tell me what you think!

---

### Post by windependence on 2008-07-12
I think you'll never do this on an itx box.

I think it's a great idea, but IMHO some of this stuff is redundant and also should be separated out on to different servers. You may be able to accomplish this through virtualization, but you will need some power to do that.

I would get VERY familiar with the software you are going to use as most likely you are going to be supporting it.

Good luck!

-Tim

---

### Post by mwerlberger on 2008-07-13
Sounds nice. Is there the plan to provide an iso sometimes? Would be a nice project i am definitely interested in...

Regards,
 Manuel

---

### Post by Thirtysixway on 2008-07-13
You're going to run all of that on one box?  Let's hope you have enough resources for everything.

---

### Post by disabledveteran on 2008-07-13
The basic list of packages came from the ClarkConnect server (a Red Hat-based distro).  I really like the solution they have built but wanted to create an Ubuntu-based system.  I've toyed with other distro's but Ubuntu is the first one I've actually learned to use in any kind of depth.

Their *minimum* requirements for a 5-10 user system is a 1GHz machine with 1GB of memory - easily obtainable through a Mini-ITX system.

I've also noticed a ton of requests in these forums and a few groups created for a small-business solution, but they all seem to die out.  If I can get this to work, and I can learn how to package up my changes and create an ISO, I will definitely make it available to the community...at the very least, I am keeping documentation of what I am installing and changing, and I will make that available as well.

I've thought about virtualization - a perfect way to provide for security and scalability - and I'm going to be working on a small biz server based on VMs...but I need to get the hardware to run it on and practice with VM software - I'm new to virutalization.  

I would prefer a true bare-metal hypervisor (instead of running it on a host OS) but I was also thinking of setting up a firewall/filter/antispam/antivirus system and then running the VMs on top of that...this way, if the business application VM crashes or is taken off line for any reason, you still have the main machine and Internet access and security available.  

As the number of users scale, I agree that this should be separated out onto separate real or virtual machines (or, at the very least, set up on a multi-processor server).  However, I am looking at what I call *true* small business, with 5-10 connected employees.  A single box should be sufficient.  I will be trying different tests out to determine what load is placed on the machine with various programs running.

I also am having problems with deciding on a groupware solution.  I am looking at eGroupware, Tine2.0, and Horde, and I can't decide which would really be best.  I've also looked at Citadel (since it's been promoted so many times in this forum) but the navigation is a bit odd to me, and I haven't found a file manager module for the solution.

I looked at CK-ERP as a possible solution for the CRM/HR/ERP applications.  Where some of the other ERP solutions (OpenERP, OpenTAPS, etc.) are a bit too much for a small business, CK-ERP is comprehensive but simple enough to actually use.  However, the developer and I have a difference of opinion on the layout of the disclaimers, and - though the software is GPL licensed and I could make the changes I wanted - I don't think that's a good way to do business.  I am also looking at Hipergate, but my queries to them have - so far - gone unanswered.

Oh, and the test box I am using to install/test on is a Penitum III 833MHz with 512MB of RAM and a 5400RPM 40GB drive...

---

### Post by WSiaB on 2008-10-20
Hey DisabledVeteran - you are absolutely right - all us Windows admins are desperate for a Linux distro to replace SBS so we can give MS the finger (you know which one).  If there is anything I can do to help, let me know.  I have been toying with the instructions at [http://www.rrcomputerconsulting.com/view.php?article_id=3]("http://www.rrcomputerconsulting.com/view.php?article_id=3").

---

### Post by rushowr on 2008-10-22
Thought I'd share this quick offering, you had requested a CRM/Groupware app? Try [eGroupware]("http://www.egroupware.org"), which is in pre-release for 1.6. It's a web based interface, and includes project management, CRM, issue tracking, and more. I use it to run my consulting practice :)

---

### Post by lykwydchykyn on 2008-10-22
First off, kudos to you DV for taking a crack at this.  The world has been waiting for a "linux server for the rest of us" (even though I'm not really part of that us, being a total command-line geek.. but that's not the point), and I'm surprised Ubuntu isn't the one delivering it.  No matter, it can be done with Ubuntu's repos.

Second, I think some here underestimate the power in a P4 box.  I have  P2 450 with 392 MB server here at home that hosts a surprising amount of services without problems (DNS, Samba, Squid+Dansguardian, Apache, and MySQL to name just a few things it does simultaneously).  

That said, I think your list needs to be pared down a bit -- sometimes less is more.  Probably either Horde or Kolab need to go.  And I would stick to services that have either a webmin interface or their own web-based interface.  Having somethings managed from the web and others from the CLI is confusing and would be a turn-off to newbies.

You also may want to look at ebox instead of webmin.  I personally prefer webmin, but I've had a look at ebox and it seems very intriguing and a bit less daunting.  Doesn't have as many modules, but it brings together a lot of things like ldap and samba that are hard to integrate on webmin if you don't know what you're doing.  Of course, I could be mistaken in my impression.  I need to research ebox more.

I don't see any reason to mess with virtualization.  That would only add an overhead that would make it less possible to run this on an ITX machine.  Seriously, what would you gain from virtualization in this instance?

---

### Post by nicolasdiogo on 2008-10-30
hi,

isn't this project already done by ebox-platform?

---

### Post by alienprdkt on 2008-10-30
> **Thirtysixway said:**
> You're going to run all of that on one box?  Let's hope you have enough resources for everything.
Thats what i was thinking!

Heres what I would do in your case:
         
      one machine:

[LIST]
[*]BIND (DNS Server)
[*]DHCP Server
[*]Turtle Firewall
[*]Bandwidth Management
[*]Open1X (Wireless Security)?
[/LIST]
  second machine:

[LIST]
[*]SAMBA
[*]Print Server (CUPS)
[*]OpenSSL
[*]Squid
[*]SNORT / SNORTSAM
[*]ProFTP
[*]Asterisk
[/LIST]
  third machine:

[LIST]
[*]Webmin 1.420 Plus specific modules
[*]Kolab Server (Apache, OpenLDAP, PostFix, Cyrus IMAP, SASL) + OpenPKG to install Kolab components)
[*]MySQL
[*]Php Extentions
[*]SNORT / SNORTSAM
[/LIST]

yes your going to need to break it down into multiple machines (virtual or physical, sorry)

---

### Post by alienprdkt on 2008-10-30
> **lykwydchykyn said:**
> First off, kudos to you DV for taking a crack at this.  The world has been waiting for a "linux server for the rest of us" (even though I'm not really part of that us, being a total command-line geek.. but that's not the point), and I'm surprised Ubuntu isn't the one delivering it.  No matter, it can be done with Ubuntu's repos.

Second, I think some here underestimate the power in a P4 box.  I have  P2 450 with 392 MB server here at home that hosts a surprising amount of services without problems (DNS, Samba, Squid+Dansguardian, Apache, and MySQL to name just a few things it does simultaneously).  



Maybe but I wouldn't be the one to be mixing routing software on a webserver, guess it all depends on what your using it for, I have these services running across 4 pcs. 2 Dual-core 3.0GHz, 1 small pII (router), and a p4 (file server & print server)

but if he wants to manage all this on one server.. I guess so.

---

### Post by lykwydchykyn on 2008-10-30
Well I would agree, I wouldn't want my *public* webserver on my router, but the criticism I was responding to was focused on resources, not mixing functions.  

If the goal is to create a distro that is focussed on small business server needs, it's probably not necessary to include routing, but if you don't someone is going to point out the lack of it.  I guess even if they split it up on two or more boxes, they'd rather use the same distro for everything (think about the target demographic).

---

### Post by perspectoff on 2008-11-18
Kolab will do most of that for you.

It is the only fully functional truly open source groupware powerful enough for a small to medium business.

---

### Post by HermanAB on 2008-11-18
The problem with doing all of that on a single server is that it will turn into a huge maintenance problem, where you update one thing, causing other things to break.

You will have better luck by installing a virtualization system and running at least 3 separate Ubuntu VMs for:
a. Email with calendars, spam and virus filter
b. Web server
c. Samba file server

and then using the host as the firewall and Squid proxy.

Another advantage of separate VMs is that it provides an easy growth path, where you can move a VM that became very busy, off to another server with very little effort.

Cheers,

Herman

---

### Post by jcimagem on 2008-12-01
I ve deployed a solution using virtualbox.

Host:
3 wired network + 1 Wireless PCI Atheros
Ubuntu 8.04 with services (Virtualbox-2.0, Samba, FTP, Hostap)
Load Balancing using iproute2 (My 2 wans running inside the VMs)

Two instances of Virtualbox Headless

Firts VM - IPCOP 1.4.21 (WAN1) - (BOT, Snort & guardian)
- Forwarding services like ftp, http and mails to host

Sencond VM - IPCOP 1.4.21 (WAN2) - (BOT, Snort & guardian)
- Forwarding services like ftp, http and mails to host

With this approach  i ve got a solution that uses the IPCop as my firewall. All other services that cant be installed on it i ve installed on ubuntu host.

Jose Carlos R Lima

---

### Post by zaddik01 on 2008-12-31
> **disabledveteran said:**
> 
Their *minimum* requirements for a 5-10 user system is a 1GHz machine with 1GB of memory - easily obtainable through a Mini-ITX system.


I think they are taking advantage of their client's lack of knowledge. The Minimum most likely applies to booting the package. Their "groupware" functionality is them supplying a link and instructions on how to install Toltec Connector on Windows. They have a link to Kolab Groupware suite, which I think you install on your own. They provide some sort of FTP thing for "file sharing and collaboration". 

You also mentioned you want to have it scalable to a rack mount system. Micro-ITX does not have an upgrade path, it is an end solution, mostly used for running kiosks or embedded manufacturing solutions.

> **disabledveteran said:**
> 
a multi-processor server).  However, I am looking at what I call *true* small business, with 5-10 connected employees.  A single box should be sufficient.  I will be trying different tests out to determine what load is placed on the machine with various programs running.


The ClarkConnect offers many features, but too many times people promise solutions that they just can't deliver. A realistic test would be to have 10 machines connected to your server, with several people chatting, all of them checking email accounts, moving files around the network, and collaborating on a few documents, plus throw in a few people downloading a copy of Ubuntu. 

5 real estate agents will have a different usage profile from 5 software developers, or 5 graphic designers. 

This is where open-source can get burned by snake-oil salesmen promising the stars and delivering a buggy steaming pile that could actually destroy a company's data and reputation. Before you try to get any clients, make sure you have signed agreements of what their expectations are, what your duties are, and what recourse each of you has. 

> **disabledveteran said:**
> 
Oh, and the test box I am using to install/test on is a Penitum III 833MHz with 512MB of RAM and a 5400RPM 40GB drive...

Ouch. That is fine for doing the firewall/filter/email/dns stuff, but I don't think that will be able to host much in the way of a production web site AND groupware.

---

### Post by windependence on 2009-01-01
I agree with zaddik01, this should not be done on one box, or you will surely be giving Open Source a black eye. One of the reasons I run most of my stuff on *BSD is that the footprint is very very small and BSD has been around much longer than Linux. 

The way to this IMHO is like Hermann said, with virtual machines, however, I'm not sure virtual box is the best choice here. I would probably use VMware or Xen. I actually have some boxes similar to this running VMs and they are rock solid, however, not on an ITX board, these are all rackmount multi-processor boxes with tons of RAM. ITX is great for firewalls, maybe a DNS server, or a thin client, or even a small FreeNAS box, but not for all the enterprise stuff you are trying to incorporate here.

-Tim

---

