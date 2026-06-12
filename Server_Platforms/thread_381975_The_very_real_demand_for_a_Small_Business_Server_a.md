---
title: "The very real demand for a Small Business Server alternative"
date: 2007-03-11
forum: Server Platforms
---

### Post by rc55 on 2007-03-11
Hi,

I work as a self employed IT Consultant and I've been a fan of Ubuntu for a while, I even met Mark Shuttleworth when he came along to my demoscene party (Sundown 2006) which was a huge surprise. Anyhow, part of my work involves looking after the IT demands of Small Businesses, and a few of them have opted for using Windows Small Business Server.

For those uninitiated, Small Business Server is a customised version of Windows Server that provides a basic toolset:

- Windows Server (For authenticating logins, storing user files)
- Windows Backup (For data backup onto tapes)
- Microsoft Exchange (For E-mail handling)
- Sharepoint (Web based collaboration / documentation facilities)
- Remote Access 
- SQL Server

In real terms, with the nature of clients I deal with all they generally require is Windows Authentication, backup facilities and Exchange. I know for certain this is acheivable in ways with Linux but what makes SBS more attractive is it's ease of use, and turnkey approach to handling small business demands.

The cost of course, is quite hideous. Especially when it comes to adding more workstations and having to slap down serious money just for computers to access the servers! I suppose to an extent, you get what you pay for.

My question is - is there anyone in the community making provision for this kind of environment, where skills on-site may not be exceptionally great? If you actually use Small Business Server, a lot of the setup is wizard driven, and asks only the really relevant information you need to know. For most companies, you can get the whole thing setup within a day.

I understand there will be many opinions on this, a lot of people suggesting converting client workstations to Ubuntu, but for some companies I think it's a case of introducing functionality slowly. I've looked at IBM's Linux Migration Cookbook as inspiration - it's a great document but due to the fragmented nature of Linux fails to address individual direct concerns with migrating and staff training.

I'd like to know your thoughts on this, and please, don't slap me with heavy open source ideology, while I respect these opinions, I'd rather keep the discussion on making provision for simple business servers.

Ruairi

---

### Post by Mr. C. on 2007-03-11
Many attempts are made towards that goal; these problems, however, are very difficult to solve.

Enormous numbers of man hours and sums of money have gone into creating, testing, and supporting the SMB product.  Some companies are working towards alternatives, but they are not doing it for free.

One of costs of free software, is that there is typically a substantial lag before offerings are available that can compete head-to-head with those produced by the giants.

Its going to take a lot of time and effort, but eventually it is likely to happen.

Start the effort!
MrC

---

### Post by rennen01 on 2007-03-11
I am currently setting up an all Linux environment for a client.  They were willing to do it because I am paralleling their existing infrastructure, so as to minimize downtime.  I've yet to find a Sharepoint equivalent, but that is because I am very busy setting up their authentication services, printing, and other "necessities".  It is taking me awhile since this is my first crack at this.  I can see the next rollouts not taking very long at all for companies that have less than 50 PCs.

Wish me luck!  :)

---

### Post by VorDesigns on 2007-03-18
RC55,

I am also a consultant in the IT field; while not unique in the industry I am unique in my company in that I'm the tinkerer in the group.  This means that I do all the in-house support for technical folks.  For those old enough to remember him, I'm like Mikey in the Life cerial commercial, I'll try anything, well, almost.
This means that I have supported Exchange, SendMail, Postfix, Domino, you name, I've dabbled in it.
I was very interested when Open-Exchange came out, unfortunately, I haven't had the time or available resources to roll it out for testing.
[Open-Exchange 5]("http://typo3.open-xchange.com/header/products/openxchange_server_5.html")
I am researching alternatives to MS products in self defense as I watch my clients investigate alternatives in an ever increasingly more agressive manner.  At the same time, I'm continuing to maintain my Microsoft literacy.
Windows Vista seems to be the biggest boost towards seeking an alternative to Microsoft that I have ever seen.
Like it or not, business embraced the Microsoft proprietery model and we, professionally, are stuck with it for the forseeable future, until such time as open source alternatives are developed.  Despite the hate, we still seek to emulate; [Fedora Directory Server]("http://directory.fedora.redhat.com/").
Open source doesn't yet have the financial backing for research and development available to the likes of Microsoft.  Sure, new backing has come into the community through the efforts of Novell, IBM, Oracle and the like but, all of these business must make their shareholders happy and Open Source doesn't meet the needs of the investor.
Manufacturers have little incentive to build drivers for their hardware that will speak natively to non-Microsoft products and this is a shame because it makes building alternatives that much harder
Me, I'm a geek, I'll go with the flow and actually look forward to expanding the depth of my computing knowledge.

---

### Post by Zero Override on 2007-04-08
As I am currently developing our new infrastructure, I'm at the point where I have to choose either for a Windows (Small Business or 2k3) Server, or one of the Linux alternatives. Since I have never worked with any of these alternatives, it's hard for me to say which product is worth trying. There are lots of people in our company that are willing to run Ubuntu/other distro, as their main-OS, but lack of support for a MS Exchange server in (as example) Evolution, keeps my employees at Windows as primary OS.

Can someone give me a brief overview about what the possibilities are for alternatives to Exchange?

Sorry for kicking this topic, but I think it is related to this topic! :)

Thanks in advance for all peeps that are willing to answer! ;)

---

### Post by matcram on 2007-04-09
Hi all, (i'm french, i'll do my best to be understandeable)

i'm glad to see this subject beeing raised as i am currently trying to emulate windows services with Linux tools (exchange, Active directory, File sharing).

I don't have many computer at home so i started with my new Intel macmini wich i upgraded to 2Gb of ram.
I installed Ubuntu dapper on it with vmware-server and i am currently running virtual machines on it.

The first one is deepofix server [http://deeproot.in/deepofix](http://deeproot.in/deepofix). It takes care of the mail server and can run the LDAP server. (i personnaly prefer to have it on a separate server)
Screenshots : [http://deeproot.in/deepofix/demo](http://deeproot.in/deepofix/demo)
This is a ready to install and use distro. From the website :
[LIST]
[*]Simplified installation system
[*]Integrated server management system
[*]Built-in LDAP support
[*]Intelligent & flexible account management
[*]SMTP / POP3 / IMAP Services
[*]Web-based email
[*]Pre-integrated anti-virus and anti-spam tools
[*]Centralised LDAP-based addressbooks
[*]Groups and Distribution Lists
[*]and some other...
[/LIST]

The second one is Alfresco. [http://www.alfresco.com/](http://www.alfresco.com/) that takes care of file sharing (smb, webdav and from a webinterface)
I'm going to install it on a separate VM soon but from what i've read it works like a charm and you can use an LDAP server to authenticate.

For remote access i would use a standard Ubuntu Desktop distro with a login against the same LDAP server throught Freenx.


That's all for now. What do you think ?
Matthieu.

---

### Post by rsermilik on 2007-04-09
There is also SME Server at [www.smeserver.org](www.smeserver.org).
It's based on CentOS which is actually Redhat Enterprise Linux

---

### Post by tribaal on 2007-04-09
I too have been poking at this problem for a while now.

Having Ubuntu propose a SMB server would be awesome (and would be a quite logical step to take towards fixing bug n°1). How could we speed up the process? Is there any kind of "central coordination" place where efforts are concentrated? 
Would a dunc-tank like method work in your opinion? 
With enough independant IT professionals sharing a few hundred dollars, the total bounty would be pretty interesting I guess...

Hope we'll see a SMB server option in the server install CD soon :)

- trib'

---

### Post by Zero Override on 2007-04-10
deepofix sounds promising so far! :)

I think that deepofix will be a serious alternative for MS Exchange, since it covers all basic operations. For "normal" companies that should be enough, I guess.

Further on, I really hope that Ubuntu will release a SMB edition, since the OS is the best for now, for me. Hopefully they will make one soon enough! :)

Are there more projects up and running by forum-members here? Or are we alone in the field? :P

// EDIT: Does deepofix also have the possibility to share Calenders? Since that is one of the most important things that I'm planning to use the SMB for, after email! :)

---

### Post by curuxz on 2007-04-10
DO NOT USE DEEPOFIX, its a pile of crap and will turn your server into a brick.

Broken, very poorly coded distro. BIG WARNING

---

### Post by Sternfan on 2007-04-10
Hi all,

I love this subject.  I've been working on a "move businesses to Linux" kind of essay that I hope to be posting sometime in the future - and the part on the Back Office/Exchange has some interesting items.  

For Email google the following:

[LIST]
[*]Zimbra
[*]PostPath
[*]Scalix
[*]OpenExchange
[/LIST]

In my opinion, I find PostPath & Zimbra to be the most impressive of the bunch.  

They all have their "pluses & minuses" - some of them even have completely free versions too.  If you need something 100% Exchange compatible, look into PostPath.

For a Linux version of Sharepoint - look into Alfresco - looks pretty cool. 

Rob

---

### Post by curuxz on 2007-04-11
how much drive does the ubuntu server project have? is it an active project? I would be willing to get involved.

---

### Post by sorryd on 2007-04-11
I am also about to set up a server for my home office. I have been playing with an SBS evaluation pack for the past few months but the eval period is about to come to an end and my experience with SBS, while reasonably good, didn't quite seal the deal. 

_One thing I really want is the functionailty of sharepoint lists. Is there any way to do this in linux?_ Alfresco doesn't seem to offer that functionality at first glance.

Other than that, I am currently looking at the following setup

Samba (perhaps with snapshots shared for pseudo-shadowcopy functionality)
Zimbra (not sure about this one as I remember it being a resource hog)
rsync for local backup and jungledisk for remote backup

Well, my data is all backed up and I am ready to pull the plug on windows SBS. See you on the other side!

---

### Post by dughutch on 2007-04-12
I'd like to bump smeserver.org.  That organization has a great product based on CentOS... it has been around for years, is stable, proven, and very reliable.  I have personally been using and deploying it since ~2001 (6.0 version) days and have been extremely happy with it.  All of it should be up on Sourceforge and utilizing it as a starting point would make great sense.

---

### Post by rvjcallanan on 2007-04-12
Like you, I am also a freelance IT consultant and have taken the plunge to create an open-source SBS alternative using Linux(Ubuntu), Samba, HA and related offerings. My ultimate objective is to create a fault-tolerant installation template using cheap commodity servers such as Dell PowerEdge. I have partly reached my goal in a live customer installation. I will not dive into the fault-tolerant part until I have the rest working smoothly.

The basic premise to any installation is that, if I take a few days off or go on vacation, I don't want any worries.

With Microsoft, the so-called "smarts" in system and application software have made it very difficult to achieve the basic quality objective of "locking down" tried-and-tested configurations. There is too much going on behind the scenes that you cannot control. You basically need an "always-on" standby admin capability which can be a problem with one-man operations. The only consolation is that it is easy to source a standby person with a good knowledge of SBS.

With open-source, there is more control and less smarts, fewer things to go wrong. But it involves an enormous amount of effort!!! There are a number of very serious faultlines with open-source and you need to be extremely stubborn to overcome them. My motivation to escape from Microsoft's clutches has helped me in this regard. When you have reached dry land, there is consolation in the fact that you can easily replicate your "solution" with a number of clients. However, the relentless patch/update cycle means templates are quickly out-dated and you are always playing catch-up and trying to grasp some new side-effect of a bug-fix or enhancement.

I was very impressed with SAMBA documentation and this gave me the confidence to try out the product. On a test installation, I got an XP client logging on to a Linux server and noticed a dramatic performance improvement in file speeds (2x) compared to SBS on the same hardware. A very cursory visual examination of security permissions in files/folders within Samba shares (via the file/folder properties window on the XP client) led me to believe that Samba somehow emulated NT ACLs and this prompted me to dive right in. Of course, I was shocked when the realisation dawned that this was not the case and I had to make do with basic UNIX file access attributes (I am reluctant to use LINUX ACLs due to implementation inconsistencies and lack of maturity). THIS, IN MY OPINION, IS THE SINGLE BIGGEST DRAWBACK TO USING SAMBA. While I can accept the philosophical reasons put forward by the Samba team, it is patently obvious that they need to create an independent NT/2K security emulation layer for low level file access. They have done the really hard work, reverse-engineering SMB/CIFS and doing a better job that Microsoft...this would be relatively easy to implement and would remove all the confusion about synchronising LINUX and Samba user accounts etc.

---

### Post by Sternfan on 2007-04-12
A few comments...

curuxz - there is HUGE demand for Linux servers.  This is where Linux shines, but it needs a few "tweaks" to make it work.  I am running several servers - apache, squid, Wildfire (Instant Messaging - very cool) MySql, FreeNX etc.  Once again, I have an essay coming that will address all of this (in my opinion).

rvjcallanan - ACLs & Linux.  You are stating something that I've been hoping for since 2004 - Linux support for security ACLs.  It exists, and you can make it work, but it is a pain to set up.  I have a PDF on how to do this with Fedora 4, 5 or 6 and I can verify that it does work.  Let me know if you want a copy.  Pretty neat to setup a network share on a Linux box and see ACLs based on Active Directory accounts.  If someone could write a GUI for this, it would be gold.

sorryd - I'm not real familiar with sharepoint, so I really can't help other than to suggest you drop Alfreso an email and ask them point-blank.  As for Zimbra being a hog, the system specs don't seem to be that big of a deal and the speed issue seems to be mostly on web-based email in older versions of IE and Firefox.  From what I hear, if you use IE7 or FF 2.x - all should be good.  If performance is really an issue, take some time to look at PostPath.  I just finished reading all their PDFs, and they are doing something pretty unique - their information store (mailboxes) isn't contained in a database (like MySql for most linux servers and JET for MS Exchange) - resulting is serious speed increases. 

Thanks,
Rob

---

### Post by rvjcallanan on 2007-04-13
Sternfan,

Please do post your ACL PDF. I'm all ears and I'm sure it will be welcomed by many. I don't know how transparent this solution will be to Windows clients. Ideally, it should be possible to control ownership, access permisions, inherited permissions etc. via Windows Explorer on client side. There is also the annoying issue of synchronising SAMBA(NT) and LINUX user accounts. I would prefer to have all SAMBA user account management independent of the underlying LINUX platform.

On the subject of exchange server alternatives...
With laptops and other mobile devices in widespread use, I have come to the conclusion that doing e-mail management in-house is more trouble than it is worth for the majority of small businesses. Outsourcing mail management to an ISP is more practical and very cost-effective nowadays (you can even get MS Exchange and LDAP functionality with companies such as 1&1). While security may be an issue here, you will always be dealing with an ISP at some level, so some element of trust is required.

The holy grail for me is achieving HA (High Availability) with SAMBA using a hot standby server arrangement. If the primary server goes down, the secondary server should take over gracefully. I am dipping my toes at the moment so any pointers would be welcome. I am interested in test results and feedback from live installations. I have been unable to obtain anything other than anecdotal information about failover behaviour. This makes me a little nervous. Some hard-nosed failover results with systems under stress would be welcome.

On a more general note, while freedom and choice are important buzzwords in the open-source community, there are many dangers here when it comes to hard-nosed business needs. There is a glut of distros, versions and information out there and it can be very difficult to get to the nub of a problem. There is a need to differentiate between the needs of business and the endless tinkering that harks back to early microcomputer hobbyists. I often feel that we are in the middle of one big hack fest and that people really believe that there is something inevitable about this. The differentiation between enterprise editions/LTS and community releases/release candidates does little to ease my concerns. Most of the technology we need for business is out there in one or more open-source implementations. I think it is high time we consolidated and stabilised open source software and let documentation and our shared knowledge catch up.

---

### Post by Frosty Cold Drink on 2007-04-13
This kind of stuff shouldn't be too bad as it is. A quick package to overwrite some config files to get verything using PAM (including Apache), and a mail server that will auto-create mailboxes (you can do this with Cyrus) and you can get a lot of functionality pretty quickly and easily.

---

### Post by dughutch on 2007-04-14
Perhaps we might also be guilty of answering the wrong question in relation to files and Windows clients... perhaps iFolder (with 3.6 supposed to be released this summer) may make sense in many situations... it natively handles offline ability, has permissions, and works securely across the internet...

thoughts?

---

### Post by matcram on 2007-04-24
> **curuxz said:**
> DO NOT USE DEEPOFIX, its a pile of crap and will turn your server into a brick.

Broken, very poorly coded distro. BIG WARNING
... do you have a particular experience to share with the rest of us ?

I have been running it as a VM under VMwareServer for a month now and it's pretty reliable. It is based on debian by the way. Why so much anger  ;-) ? From their wiki, you can also install the system by yourself.

So what is so horrible with deepofix ?

---

### Post by az on 2007-04-24
> **curuxz said:**
> how much drive does the ubuntu server project have? is it an active project? I would be willing to get involved.

[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)

The Ubuntu enterprise server is a google summer of code project for 2007.

---

### Post by garba on 2007-04-25
i think that a nice, clean way to integrate ldap and kerberos would be a good start to provide centralized authentication, the amount of howto's and docs spread on the web covering this issue is abysmal, yet a lot of people are having trouble with getting it to work properly... just imagine the waste of effort and time this leads to, why not provide an out-of-the-box solution that just works? this is just an example, but a "do it once do it well" approach to many issues and common scenarios should be the way to go...

---

### Post by curuxz on 2007-05-10
Anyone interested in working on a linux for business project please PM me, all and any help needed to pool resources for getting linux and all FOSS into the work place (mainly small to med businesses please or developers)

---

### Post by dfsixstring on 2007-07-23
I went through this same thing several years ago after my Exchange 5.5 (Server 2K) melted down for the second time.  The database on that particular version would corrupt after a few years in service.  I spent the entire day on the phone with Microsoft and the end result was that I was going to have reinstall the server and reload the Exchange server from the ground up.  I had about 100 users so it wasn't that big of a deal to do the reload but this was a corporate server handling business email - not just POP mail for casual users.  We also had shared calendars, shared contacts, desktop faxing, etc - the normal MS Exchange scenario.  I scoured the Internet looking for a Linux alternative because I was sold on Linux' stability and security.  After about three months of searching I found the name of a company on a Fedora users' group called Bynari ([www.bynari.net](www.bynari.net)).  They had a bundled software package that claimed to do exactly what I was looking for - corporate email with all of the collaboration functions running on Linux.  I purchased this software (I am the CIO for a municipality) for a fraction of the Exchange price and then installed it on a new Dell server.  The install was a single RPM that I downloaded and after running the RPM command and shell installer it was done.  In fact, I installed it three times and then called their tech support because I knew something must be wrong - it literally took me less than 15 minutes to install this on a Fedora box.  I have since installed another instance on a Centos box (Fedora is gone now) and it worked great.  I have had both systems running for over 3 years now with almost no issues at all.  There is a client-side piece that you have to get called a connector that makes Outlook talk to the server in IMAP and I also go (for one of the servers) their LDAP address book.  This whole thing gave me all of the pieces that I used with Exchange - shared contacts, shared calendar, fax from desktop and it also integrated web mail (with all the bells and whistles of exchange online) anti virus and anti-spam software with it.  I am sold on these folks and I tell people about them whenever I am at conferences or speaking with other IT professionals.  I am more than happy to speak in detail about my set up with anyone that is interested - I bought this software and use it in a real-world environment to this day.  I think you can even download a demo of it - at least you could back when I was looking into it.  If I were in your shoes and wanted to at least have an understanding of what was out there - I would check this one out.  You mentioned at the beginning that your skills might not be that great - they have PDF manuals that you can download that will tell you what to type - you really don't need anything to use this stuff.  After it is installed it is all GUI anyway.  Hope that helps...

---

### Post by crobruncato on 2007-09-25
Also take a look at clark connect - also a good product. Community version for (if I remember correctly) 10 users and then $$ for more users

---

