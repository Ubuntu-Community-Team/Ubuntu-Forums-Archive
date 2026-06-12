---
title: "Groupware server"
date: 2006-06-22
forum: Server Platforms
---

### Post by hotpurple on 2006-06-22
Hi there all,

I have a dapper based server at home that I would like to use as a groupware server, in a similar way to microsoft exchange (ie shared calenders, email contacts directory etc). Is there any way to achieve this currently? I would also like to be able to use Kontact and evolution as clients if possible.

Many thanks

Chris

---

### Post by linuxone on 2006-06-25
Hi,

[QUOTE=hotpurple]I have a dapper based server at home that I would like to use as a groupware server, in a similar way to microsoft exchange (ie shared calenders, email contacts directory etc). Is there any way to achieve this currently? I would also like to be able to use Kontact and evolution as clients if possible.[/QUOTE]

select your prefered application:

**OpenSource**
[Kolab 2](http://www.kolab.org/)
[OpenGroupware](http://www.opengroupware.org/)
[Exchange4linux](http://www.exchange4linux.org/)
[OpenXchange Community](http://mirror.open-xchange.org/ox/EN/community/)

**Commercial**
[Scalix](http://www.scalix.com/) (also free Community version available)
[Instant Ogo](http://www.instantogo.com/) (commercial version of Skyrix' OpenGroupware)
[Skyrix](http://www.skyrix.de/en/) (OpenGroupware founders)
[Exchange4linux (commercial website)](http://www.exchange4linux.com/)
[Open-Xchange commercial](http://www.open-xchange.com/EN/)


Which one to select? Difficult to answer ... **Scalix Community** seems to be very interesting because this free version of the commercial Groupware server does include **25** licenses for the specific native Outlook connector. On the other side: Scalix System requirements mention only a few Linux Distributions ... don't know if you can install this software in a Debian based environment.

About exchange4linux: I don't know if this product is commercial or not? Source code can be downloaded from the .org site but the .com mention a price list.

The above list should be mostly complete. A few other groupware solutions were based on one of the above products, like a complete distribution with including groupware server.

Thomas

---

### Post by LordMerlin on 2006-06-29
Can anyone give feedback on any of these? I have some clients running Exchange at the moment, utelising the shared address book, shares calendar, shared everyhing. 

Costs are climbing, dramatically, and I want to propose something alternative. It must be able to wortk with Outlook, utilise spam & virus filtering (spamcop?) have extras like webmail access, PDA connectors, etc

Any defenate recommendations?

---

### Post by mushr00m on 2006-06-29
I've just spent some afternoons tweaking egroupware for our small co-op community....

It supports the basic functions you are asking for.  They have sketchy iCal support at the moment so I don't know about Calendar integration into Evolution, their support forum is well stocked with info about this.

External LDAP and IMAP servers to increase the usability and I think that by using Ldap you can connect port your contacts into Evolution(not sure since I haven't implemented Ldap in my project, sorry)

As php based groupware project it is very usable from the web interface.  I had some trouble with repo install, via phpwapi module, but after a crash course in PHP<->mysql I was able to rebuild the data tables by hand and everything has worked great since then.

Hope that helps.
mushr00m

---

### Post by LordMerlin on 2006-06-29
Have you tested egroupware with Outlook?
 
I just installed it, and it seems nice. But nice isn't always practical... Accessing it via the Web will more be like a bonus feature @ this stage, could become usefull when an agent is on the road. 
 
We need something that will work with MS Outlook, and I need to be able to import all the user's existing email, todo's, appointments, calendars, address books, etc etc. 
 
Any comments?
 
P.S. How do you get it to download POP3 from an upstream mailserver?

---

### Post by mushr00m on 2006-06-29
[QUOTE=LordMerlin]Have you tested egroupware with Outlook?
 
We need something that will work with MS Outlook, and I need to be able to import all the user's existing email, todo's, appointments, calendars, address books, etc etc. 
 
Any comments?
 
P.S. How do you get it to download POP3 from an upstream mailserver?[/QUOTE]

I read today that openDAV is working on phpgroupware support... egroupware support wouldn't be to far beyond that.  I don't know what kind of support they have for Outlook... I like the idea of web-based groupware myself.  I'm thinking about setting up a css/theme for output to the blackberry/cellphone because I have an unlimited net package but am still getting dinged for all those text messages/reminders.

I figured Pop3 out after the second time installing, use the regular egroupware-email package instead of the feliamail, which is only IMAP. after that set up the POP3 preferences in the regular user pref's.... not the admin preferences, something that was not very clear at first.

Doesn't keep local copies of mail though.... for that I was thinking of a IMAP server with a POP3 module... I hear Courior is nice.

---

### Post by tribaal on 2006-06-30
Is there a failsafe way to install egroupware from the repos on an LAMP server install? I tried several times but always got stuck with the php4<->mySQL problem...

What a shame the packages depend on php4 and not php5 :(

Any idiotproof way to get easily egroupware up and running on php5 mySQL5 on a LAMP install?

Cheers!

- trib'

---

### Post by hotpurple on 2006-07-07
Open exchange looks good. Has anyone had any luck installing it on dapper? I can't get it to compile.

Chris

---

### Post by Macchi on 2006-07-15
> **hotpurple said:**
> Open exchange looks good. Has anyone had any luck installing it on dapper? I can't get it to compile.
Chris

There is a detailed tutorial on on the july 2006 print edition of LinuxFormat with six pages describing the installation of the open source version of Open-Xchange on an Ubuntu Breezy server. 
(By the way LinuxFormat is an excellent publication, presently my favorite! )






PS: Can we start an initiative to improve the installation procedure for the open source version for Open-Xchange on an Ubuntu server? One solution is to create installation scrips trimmed for a standard template such as a newly installed Ubuntu Dapper server.

The first challenge will be to obtain acceptance from Open-Xchange Inc in a true open software atmosphere of cooperation. The common goal is definitely to offer a free software alternative to the present market leader on that segment of groupware.

I believe that Open-Xchange Inc would benefit from a lower threshold for test and adoption of their products in the segment for small offices and home offices. 

I did have not have time yet to try the installation. The ideas around Open-Xchange are very good and I really would like to see it running on my Ubuntu server. But the time-demanding and somewhat risky installation procedure disencouraged me from further experiments on my primary server. If I install that sowftware then I will also have to maintain it. This includes being capable to efficiently recover the system and all data from the worse possible crashes. Definitely I am still interested in a smotth procedure to install the open source version and would not have the resources for acquiring a commercial version just for experiments in a realistic environment. I apologize for the long reply if that happens to offend someone.

---

### Post by gluemonkey on 2006-07-19
Scalix does provide is CE Raw Edition in .deb format, I'm installing it now.  On a Dapper based server.  I tested it out at my work when we searching for a good groupware server.  It's pretty robust and provides both good Outlook and Evolution support, as well as a pretty slick Web interface.  It also not too difficult to setup.  Unfortunately for Scalix I made the decision to go with Groupwise from Novell instead, we have too many mobile users with Blackberry's and Treo's and needed better support for the than Scalix offered and with BES for Groupwise being release and the fact that I'm in lust with eDirectory (not SuSe though, they could take a lesson from Ubuntu on what the Linux under pinning should be like) it was really a good decision.  But I would run Scalix in a heartbeat, well I'm well on my way for my personal domains and also for a smaller non profit... The free version just can't be beat. :-D

---

### Post by thematrix on 2006-07-19
I think Macchi is right... 
Open-Xchange is doing it the right way, and I think they have the  greatest chance of taking the market. They have a complete and well designed solution with a good marketing strategy (this is what kolab lacks if you ask me).

The problem I see is that it's hard to maintain the system in the current situation and that's way many people stay away (me too).
I think the ubuntu server project has a clear opportunity here in integrating open-xchange.org into the distribution. I think this is a market for linux with the largest growing possibilities.

Kind regards,

Frederic




> PS: Can we start an initiative to improve the installation procedure for the open source version for Open-Xchange on an Ubuntu server? One solution is to create installation scrips trimmed for a standard template such as a newly installed Ubuntu Dapper server.

The first challenge will be to obtain acceptance from Open-Xchange Inc in a true open software atmosphere of cooperation. The common goal is definitely to offer a free software alternative to the present market leader on that segment of groupware.

I believe that Open-Xchange Inc would benefit from a lower threshold for test and adoption of their products in the segment for small offices and home offices. 

I did have not have time yet to try the installation. The ideas around Open-Xchange are very good and I really would like to see it running on my Ubuntu server. But the time-demanding and somewhat risky installation procedure disencouraged me from further experiments on my primary server. If I install that sowftware then I will also have to maintain it. This includes being capable to efficiently recover the system and all data from the worse possible crashes. Definitely I am still interested in a smotth procedure to install the open source version and would not have the resources for acquiring a commercial version just for experiments in a realistic environment. I apologize for the long reply if that happens to offend someone.

---

### Post by Neural oD on 2006-07-26
Pity that open-xchange charges for the oulook connector! We'd like to setup groupware where people can connect from M$ Outlook as well as evolution and other OSS ones!:-k

---

### Post by rdjurovich on 2006-09-03
Hi there,

I think it would be really cool if Kolab could be installed via apt with a simple command:
```
# sudo apt-get install kolab
```

Ryan.

---

