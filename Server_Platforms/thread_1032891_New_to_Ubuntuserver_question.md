---
title: "New to Ubuntu/server question"
date: 2009-01-06
forum: Server Platforms
---

### Post by Aaron B on 2009-01-06
I'm researching what I need to start a credit card processing company and I've gained some good knowledge and ideas. I have been looking at several servers to start a reliable business but wanted to get some input from others. What type of server and hardware would you recommend for my needs? I don't need to start with anything huge but I would like a reasonable amount of room to grow at the beginning with out having to upgrade. Tips on firewalls and other such devices are very welcome as well.

Thank you.

---

### Post by windependence on 2009-01-07
There is nothing wrong with Linux but for this type of business I would highly suggest using OpenBSD, probably the most secure OS on the planet.

[www.openbsd.org](www.openbsd.org)

For server hardware, well, this is mission critical. I hope you're ready:

Enterprise class hardware router/firewall like Cisco PIX or Watchdog Firebox. (2)

UPS (2)

Redundant servers with redundant power supplies preferably clustered for failover

Redundant managed network enterprise class switches (2)

Redundant data connections, preferably from tow different vendors, suggest 2 T1 or T3 lines.

There's probably some stuff I forgot, but that would be basic.

Don't forget that the card companies also have requirements for stuff like this. I believe they require special encryption technology of you do any kind of volume.

Note that I have two of everything. You will want to configure everything to be in a failover of some kind in case your hardware dies. You absolutely can't be down in this kind of business.


-Tim

---

### Post by Aaron B on 2009-01-08
Excellent advice! I pretty much had the server and router/firewall picked out. I&#8217;m going with the Watchdog as far as firewall is concerned.

For a server I was planning one with multiple processors looking to be sure that one takes over the work load of the other if one should fail.

I certainly wasn't thinking of two of everything, it's something for me to look into. Especially the redundant data connections. I was planning on T1 or T3.

Thanks again for the good input!

:)

*edit*

I should add that at the start I will begin small scale and build from there. I'm not convinced I'd need a full blown redundant server let alone two of everything when I first start out. When you say redundant server are you talking a master server with at least one server as a backup? You suggest two of these configurations right at the start of the business? This will add quite a bit more to the start up costs than I was thinking :P

I do know I need it locked down tight against hacker and virus threats. Wouldn't a single server running multiple processors be enough until I get enough customers to expand?

---

### Post by windependence on 2009-01-08
The main thin is you want to eliminate any single point of failure you have on the system so if someting fails, you have a backup system to take over so you are not down and can fix the problem. 

You may want to take a look at virtualization so that if you need more servers, you don't have to buy more hardware. I am a VMware partner so if you need advice, just ask.

-Tim

---

### Post by Aaron B on 2009-01-10
I sent you a private message about this but I don't see it in my sent box. Not sure why that happened or if you got it, you might not accept private messages. I'll post what I was saying here.

When first starting I plan to do it with as little initial start up cost as possible but still provide a reliable service.

I had thought about a redundant server but was planning on implementing it later as we gained more clients. After reading your post I started to rethink the server issue and decided it would be best to go with a redundant server from the start. It will save time and money in the long run.  I am going to hold off on using multiple redundant servers until we grow larger.

I had also thought about getting a T1 connection but figure that could also wait to see how much the business grows. I will of course upgrade my DSL line to the fastest speed available and I am also thinking of going with a fiber optic connection instead. Depending on what I decide to go with, both DSL and fiber optic should remain active through a power outage as long as I have my system on a battery back up. I&#8217;m also considering having an engine/generator on stand by in case of extended outages. Instead of two data connections from separate providers I think I&#8217;ll split the one connection to two and run them through two routers and NIC cards. This again is to help save on initial costs.

As far as servers, HP Nonstop are overkill for startup. Even a simple blade server is a bit more than I would need. What I&#8217;m looking at is two Dell PowerEdge 2900 III tower servers with dual 2.5GHz processors, triple 80GB hard drives with RAID and at least 8GB of RAM each. I&#8217;d run those as a redundant system.

That alone should be enough to start up and run the business for a long time without the need to expand and upgrade the equipment.

I&#8217;ve been looking at the Watchdog firewall/router but I&#8217;ve also looked into using Astaro Firewall with a simple router. Do you have any experience with the Astaro software? Which way do you feel is more secure?

I&#8217;ll have to learn openBSD. I&#8217;ve also heard of netBSD, is there any reason you would recommend against that operating system?

---

### Post by martien on 2009-01-10
> **windependence said:**
> There is nothing wrong with Linux but for this type of business I would highly suggest using OpenBSD, probably the most secure OS on the planet.

[www.openbsd.org](www.openbsd.org)
...
There is no conception like "most secure OS". Every OS/Distribution can be secure and all that is depending on the system administrator and his skills. If someone has the best hardware and software and he is an idiot, so he can make everything down.
Anyway, *BSDs are good for their stability - it can work for years, once you install and configure *BSD server, but linux is more flexible and dynamic and you have to decide what to use.
Personally i prefer *BSDs for something like caching dns server - install, configure and lock it in the rack, thats all for years. Good luck.

---

### Post by Aaron B on 2009-01-10
Yes, I agree that someone not doing the right things will not be able to secure a system to it's full potential. I think what windependence means is that openBSD in it's standard configuration comes very much locked down compared to others. For example, Windows isn't as secure out of the box as openBSD. I was asking about netBSD because I heard that it is completely locked down and you have to unlock everything.

---

### Post by Aaron B on 2009-01-14
Just an update.

I've found a lot of good information on the internet and I have to say that the info given to me in this thread was spot on. After finding out more about the industry I realized that being and ISO is what I'm actually looking to do. The advice given here was exactly what I had asked for in my initial post and now I know that it is way beyond what I am looking to do. Maybe in the future I'll be a large processor but for now I want to start small and starting as an ISO is the way to go. Thanks to everyone that helped me out!
:)

---

### Post by pdtpatrick on 2009-01-14
curious - isnt watchdog just a gui for iptables?

---

### Post by Aaron B on 2009-01-17
Probably, but we meant to be typing Watchguard
:P

[http://www.watchguard.com/](http://www.watchguard.com/)

---

### Post by windependence on 2009-01-17
> **martien said:**
>  but linux is more flexible and dynamic 

Can you explain this statement? There is nothing I can't do in *BSD that can be done in Linux. It may be a bit more time consuming, but in the end, as stated the box will run for years.

-Tim

---

### Post by albinootje on 2009-01-17
> **windependence said:**
> There is nothing wrong with Linux but for this type of business I would highly suggest using OpenBSD, probably the most secure OS on the planet.

[www.openbsd.org](www.openbsd.org)


I agree with OpenBSD being probably the most secure open-source Operating Systems around for having on a server.

However, this goes for the default installation.
Adding more software (FreeBSD has ports, NetBSD has pkgsrc, forgot the name in OpenBSD) is something else.
Configuring that software is again something else.
Administrating that OpenBSD box properly is something else.
And again, dealing with php or cgi scripts or SSL certificates for your webserver is a different thing.
The knowledge and capabilities of the sysadmin are the next step in making this all secure and keeping it secure.

---

### Post by Aaron B on 2009-01-18
Sounds like a steep learning curve? I'm up for it.

Thanks for all the info and input from everyone.

---

### Post by adlabens on 2009-01-18
> **Aaron B said:**
> I had also thought about getting a T1 connection but figure that could also wait to see how much the business grows. I will of course upgrade my DSL line to the fastest speed available and I am also thinking of going with a fiber optic connection instead. Depending on what I decide to go with, both DSL and fiber optic should remain active through a power outage as long as I have my system on a battery back up.

I'm a very experienced DSL tech for one of your friendly, neighborhood, global telecommunication giants (name is 3 letters beginning with an "A" & ending with a "T"), so I'll give you the very best advice I can with regard to your thinking about DSL.  

First, DSL is intended to be nothing more than a consumer product.  It was not, never has been, and never will be, a business class product.  What I mean is that it is a very low priority line of business for the telephone communications companies.  As such, it should be considered the same by anyone who is using it.  In other words, when your DSL goes down, your trouble ticket will go into the pool of tickets where it will have to wait until it's turn.  And then, you will be given, at best/least, a 4 hour window of time during which the technician can arrive.  If he is not able to get it fixed, it may require more time.  There is no guarantee that the service will continue to work at the level that you expect, and there definitely is no method or right for you to recover the income from business lost during a DSL outtage.  As a business, you pay a bit more for DSL than as a residential consumer, but it is still considered a "consumer" grade product.  And, just so you'll know, just because you are told by the sales department that xyz speed is available, there is no way to know whether anything is available until it's up & running - subject to line conditions as they develop over time.  The phone companies do not consider DSL to be a mission critical service, and they treat it with that level of low priority.

T1 (& T3) are definitely considered mission critical services.  The only service provided by the telecommunications companies that hold a higher priority than standard T1 (or T3) services are the 911 emergency services that exist at the local police, fire, & ems service departments across the USA.  While you definitely pay a bigger nickel for T1, they pretty much guarantee that someone will be at your site within an hour of a reported outtage.  Plus, they usually install a second fiber for the T1 so that redundancy is built-in.  It may take the recovery team a period of time to fix your problem, but generally that would only be if they are waiting for equipment to be priority shipped to replace equipment that has gone bad.  And, even then, there will probably be a technician on-site the entire time trying to figure out a way around the issue so that you can be up and running.  You're not necessarily paying for the speed, as T1 is comparable to 1.5 (high end of the low speed tier) mbps.  But, T1 can be fractionalized to provide 24 phone #'s that are local to one area but may be located anywhere within the lower 48.  And, T1 customers get the level of service from the company and technicians indicative of a mission-critical service.

DSL may work.  Upstream is MUCH slower than downstream, unless you get SDSL, and even then it slows down the downstream to match the upstream.  DSL is a good product, and it definitely meets it's design criteria.  But, it is not T1, and it will never be considered a mission critical service.  I'd hate to see you lose a customer over an issue with the DSL that would otherwise never materialize with a T1 line.

Hope this helps.

-> David

---

### Post by StevoIBM on 2009-01-28
> **Aaron B said:**
> I'm researching what I need to start a credit card processing company and I've gained some good knowledge and ideas. I have been looking at several servers to start a reliable business but wanted to get some input from others. What type of server and hardware would you recommend for my needs? I don't need to start with anything huge but I would like a reasonable amount of room to grow at the beginning with out having to upgrade. Tips on firewalls and other such devices are very welcome as well.

Thank you.


Hey Aaron, 

I was just reading your post and some of the comments people have posted and when it comes to credit card processing there are two things that are most important and that is security and high availability.

In regards to security you have to be able to maintain compliance that the credit card companies will make you verify and maintain because credit card info is considered to be sensitive information. 

Here is a link in regards to credit card policies and compliance requirements:

[http://www-304.ibm.com/jct03004c/businesscenter/smb/us/en/newsletterarticle/gcl_xmlid/154874/?&ca=smbPCI111108&tactic=&me=W&met=inli&re=homeherous1](http://www-304.ibm.com/jct03004c/businesscenter/smb/us/en/newsletterarticle/gcl_xmlid/154874/?&ca=smbPCI111108&tactic=&me=W&met=inli&re=homeherous1)

[http://www-01.ibm.com/software/tivoli/governance/security/pci.html?&ca=smbCompliant101508&tactic=html&me=W&met=inli&re=nonsmbNewsArticle2LM1](http://www-01.ibm.com/software/tivoli/governance/security/pci.html?&ca=smbCompliant101508&tactic=html&me=W&met=inli&re=nonsmbNewsArticle2LM1)

[http://www-935.ibm.com/services/us/iss/pdf/pci_brochure_092507.pdf?&ca=smbPCI101508&tactic=html&me=W&met=inli&re=nonsmbNewsArticle2LM2](http://www-935.ibm.com/services/us/iss/pdf/pci_brochure_092507.pdf?&ca=smbPCI101508&tactic=html&me=W&met=inli&re=nonsmbNewsArticle2LM2)

as you can see this is one of the most important aspects of the business you will be going into. IBM does have products and services that can be implemented as the business grows. We have consultative services that can help plan a growth road map, so as to maintain security compliance and still be profitable.

In regards to high availability a few posters have already outline how important the lack of down time is. IBM servers are designed to remain up as much as possible and a lot of the architecture is sourced from our high end mainframe servers that are designed with high availability in mind. For a start IBM X-Series is an excellent platform to accomplish this. Here is some resources on these servers that will outline how our servers can help maintain this need for the service you wish to provide your client. 

[http://www-03.ibm.com/systems/migratetoibm/systems/x/getthefacts.html](http://www-03.ibm.com/systems/migratetoibm/systems/x/getthefacts.html)

[http://www-03.ibm.com/systems/migratetoibm/systems/bladecenter/compare.html](http://www-03.ibm.com/systems/migratetoibm/systems/bladecenter/compare.html)

[http://www-03.ibm.com/systems/services/highavailabilitycenter/index.html](http://www-03.ibm.com/systems/services/highavailabilitycenter/index.html)


I hope this information is useful, and that it should help guide you in the right direction for this start up business.

If you do in the future have any questions or would like to talk about this in more detail. You can message me anytime or shoot me an email @ [email]sversa@ca.ibm.com[/email].

Cheers!!

---

