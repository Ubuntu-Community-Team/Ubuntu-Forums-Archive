---
title: "Are there something like Active Directory's Policy Manager for LInux?"
date: 2007-08-10
forum: Server Platforms
---

### Post by netlogic on 2007-08-10
Are there any tools out there let admins control Linux machines' policies remotely like the Active Directory's Policy Manager? Also, are there any apps out there let Linux servers control XP/2000/VISTA's policies through the directory of service without using the damn expensive MS servers?

Thanks

---

### Post by BoneKracker on 2007-08-10
I don't know and if you get other advice, take it.  But I may be able to point you in the right general direction to continue your search if no one else chimes in.

You may find what you're looking for as distribution-specific applications in one or more of the Enterprise-oriented GNU/Linux distributions, such as RedHat, CentOS, or possibly Suse.

For example, RedHat has RedHat Directory Services, which I understand to be similar to Active Directory (note the word "similar").

In general, there are many ways to achieve distributed administration of unix-like machines.  For example, using an NFS mount that contains the policies is a simple approach suited to a LAN.  NIS-based solutions are more suited to broader distribution.  Samba can act as an NT Domain Controller.  

Applications created by vendors like RedHat and Novell build upon basic tools available in GNU/Linux (such as LDAP, Samba, etc.) to provide AD-like capabilities.  I'm not sure exactly what these apps can do, but that's where I'd look.

I _think_ you'll find that distributed management of *nix machines is reasonably mature, while use of a *nix machine to administer Windows Group Policies per se is generally not done except in custom solutions created at the corporate level.  There may also be 3rd party administration suites from vendors like CA, IBM, HP*et al * that fit the bill, but I would expect them to be fairly pricey.

---

### Post by wirelessmonkey on 2007-08-10
Well, you could set up a SAMBA domain, and do policy control from the SAMBA Domain Controller.... Not easy though.

---

### Post by BoneKracker on 2007-08-10
From what I recall, Samba can act as an NT domain controller, but it cannot be a domain controller in an Active Directory -style domain.

---

### Post by netlogic on 2007-08-11
I gave up trying to figure out a way to replace MS servers with Linux. I think it isn't ready to be integrated with the MS world. 100% Linux environment is definitely ready for small companies. Linux is an impossible sell to mid to larger companies, because of the AD. The customers don't want to use Linux as DNS, DHCP, and File Sharing (why bother putting a SAMBA server if they already have licenses for each seats in the AD?) Even you are helping migrate NT4 domains companies into Samba Domains, they will be missing tons of features from NT4 domain as System Policy and Trust links. The standalone Samba is really good for companies under 100 in a single office environment.  AD has DNS and DHCP tightly integrated with the client machines. AD doesn't work well with Unix's DNS and DHCP. Also, how to sell something new if they already have something built-in to their OS? So far my success only have been Proxy and Firewall for companies who can't afford Checkpoint licenses. I freaking tried, but I am getting tired. I don't think people understand how important MATURE Directory of Service means to corporations. Oh, I rather use AD than Novell's NDS. I used to maintain Novell 3.x and 4.x in the 90s, what a piece of ****. I still LOVE Linux and I will always use it at home, but without a very good road map from the "real" world success, it is becoming impossible to map out a plan for clients.

---

### Post by jfinkels on 2007-08-11
Have you looked into OpenLDAP?

---

### Post by netlogic on 2007-08-11
Yes, I did. It is missing tons of features to manage client machines. Most IT departments don't go around fixing Windows PCs. They let the AD model control the clients using the structured OU. Yes, AD breaks a lot and have to restore the entire database every year. AD has tons of features, but just like any MS products, tons of features and breaks down like a little baby.

---

### Post by jfinkels on 2007-08-11
> **netlogic said:**
>  AD has tons of features, but just like any MS products, tons of features and breaks down like a little baby.

You hit the nail on the head, friend.

---

### Post by koenn on 2007-08-11
> **netlogic said:**
> I gave up trying to figure out a way to replace MS servers with Linux. I think it isn't ready to be integrated with the MS world. 
Let's say the MS world isn't ready for Linux. Windows, being a stand-alone single-user system by design, requires a tool such as AD to implement some sort of remote/centralised management - MS extended LDAP and DNS 'till it wasn't pretty anymore to accomplish that - and there you have the "Active Directory Services". 

But it does make running a mixed environment problematic.

---

### Post by netlogic on 2007-08-11
Like I said before, I love Linux. In case you have a wrong impression. Windows has been a multi-user environment since win2000 in 1999. Software turns it off on the workstation and only utilized it during the RDP. Workstation and Server have very similar kernels. Software just turns thing on and off. Microkernel does support multi-user environment. I think most companies stop using DOS, 3,1,95,98 many years ago. I really hope so.  Windows' LDAP does more than the directory of service. AD has more than User management in MMC snap-ins. Since, it is missing all these tools to manage Windows workstation, how would you sell Linux servers? Just say, Linux is soooo cool to the customers? What should I  say to them? "Hey, I know you used to push applications and security patches remotely with few clicks, but now you have to visit all your clients. It will make you feel so cool. It will also save some money that doesn't belong to you. I know your company appreciates the IT department and never understands your software budget, why not appreciate them more for hating you?"  Windows don't have something like apt or apt-cacher. However, Linux doesn't have anything to centralized network , policies, applications, security, desktop interface of Windows through one server interface. Long as there are Windows Desktop, how would you migrate them over? 100% Linux environment is a joke to integrate, but you know most companies, it will not happen. It will always be a mixed environment and long as MS controls the desktop, it is becoming impossible.

---

### Post by netlogic on 2007-08-11
What Linux needs as a ***KILLER ***app is Windows Desktop management tools. If we have that, selling Linux will be easy as selling crack to crack whoes.

---

### Post by koenn on 2007-08-11
I didn't get a wrong impression, I don't doubt your love for Linux. 
I do get the impression now that you're so used to windows that it affects the way you design your sollutions. But that's not my problem. 
I'm also not in the business of selling Linux servers. If you want to be, make your own business case. 

Frankly, I don't think it's possible to manage Windows desktops from a central Linux server. Windows wasn't designed to be managed by Linux servers, and Linux servers weren't designed to manage windows desktops. There are some noteworthy attempts to integrate both worlds, with the efforts almost exclusively coming from the Linux side, but these attempts strive towerds compatibility and interoperability. Integration and drop-in replacements won't happen for a long while. 

I know Win 2k is a multitasking multiuser system. That's not the point. The point is that MS lacks the 40 years of expertise with centralised computing that Unix has . They're doing their best to catch up, but they're still struggling. 
Unix never needed to develop an Active directory with GPO's and what not because user configurations could be handled by writing directly in user home folders pon a central server and mounted to the workkstations over NFS. Unix didn't  integrate software deployment into a directory service because their focus was on server-based environments - you install software on a server and let multiple users use it. As opposed to Windows, where you *need* to install software on workstations, to be used by 1 person at the time (even if the OS is said to be multi-user).  So you also need a deployment system - yeah yeah, I know MS has its Terminal Services too. Like I said, they're trying to catch up.)

That 's the reason mixed environments are problematic : it's 2 different worlds, each of which having  developed its own sollutions to its own problems. Expecting to find Unix/Linux sollutions for Windows problems, or vice versa, is going to be hard. I'm glad I'm not in the business of promoting mixed environments. 

On the other hand, interoperability is becoming hot, so things may improve in the future.

---

### Post by netlogic on 2007-08-11
You are right, but you are also forgetting networks are changing. Many people are working from home through slow VPN DSL connections. Need for distributed applications will always be there. Is it really necessary to create huge server farms, so users can run a word processor through a remote X session over ssh while these client machines are becoming dual core processors? What would be the solution for the laptop users? Tell them they should use the Google Java apps? Decentralized application installations will not go away.  That is impossible. Admins will need to push and deploy apps to the client. We still don't live in the world where every devices are wired or wireless to the net. I think you are completely misunderstanding how IT departments operate. We live in a graphical world where client machine processors are getting too high while programmers are writing bloated programs. That means if you dump all these bloated client programs to the servers, you will end up with a huge server farm. That might end up being more work to manage.

Yes, UNIX is wonderful, because it uses flat file configurations which can be easily deploy to various clients. Unlike Windows, it is based around binary compact database files, which is the NIGHTMARE registry. The everything is file and folder concept is more logical than Windows' everything is an object philosophy. However, the downside of manging Linux workstation is managing all your pgp and ssh keys that are all decentralized. Imagine manging 5000 ssh keys can be a nightmare to deploy to securely mange configurations of all the client machines. You have to understand many IT departments no longer fix one to one PC configuration issues anymore. These days, each admins are responsible up to 500 to 1000 nodes.  Stupid user related issues are handled by oversea and outsourced Help Desk for answering stupid questions like &#8220;what happened to my wallpaper.&#8221; If IT doesn't have a centralized management for all client PCs, it is no sell to mid to large corporate America. Also, most admins don't have time to write perl scripts for every windows applications to deploy through login scripts.

---

### Post by netlogic on 2007-08-11
I would like to add following idea for developers. Please, listen up developers! In the early 90s, Novell developed a client app that will work with DOS machines to logon to their standalone servers. Eventually, they have written client apps for Windows 3.1,3.11,NT3.51, and NT4 clients to logon to Novell 4.x servers. After that it was very easy to manage Windows boxes. How come there are no projects for Linux server to Windows client applications? Why is everyone so hard to reverse engineer Windows Networking app to logon to Linux? Why constantly reverse engineer something Microsoft controls and can change on every service packs? Why isn't someone developing a client app that runs on Windows that integrates with Linux servers?
FOOD FOR YOUR THOUGHTs!

---

### Post by BoneKracker on 2007-08-12
You're wrong.

Here's where I think it's going to happen.  Public organizations, like national governments, are finding it increasingly difficult to justify the never-ending expense of software licenses.

FOSS is so closely aligned with the purposes of most governments that it's a no-brainer that they adopt it.  In fact, UNIX was a U.S. federal government project to begin with.  Reuse, standardization, interoperability, government-academia-corporate partnerships, good fiscal stewardship... it just makes too much sense.

It's organizations that are massive enough to create and maintain a distribution of their own for whom gnu/linux makes the most sense of all.

And they have a much bigger influence on what corporations do than people realize.

---

### Post by jrusso2 on 2007-08-12
> **netlogic said:**
> I gave up trying to figure out a way to replace MS servers with Linux. I think it isn't ready to be integrated with the MS world. 100% Linux environment is definitely ready for small companies. Linux is an impossible sell to mid to larger companies, because of the AD. The customers don't want to use Linux as DNS, DHCP, and File Sharing (why bother putting a SAMBA server if they already have licenses for each seats in the AD?) Even you are helping migrate NT4 domains companies into Samba Domains, they will be missing tons of features from NT4 domain as System Policy and Trust links. The standalone Samba is really good for companies under 100 in a single office environment.  AD has DNS and DHCP tightly integrated with the client machines. AD doesn't work well with Unix's DNS and DHCP. Also, how to sell something new if they already have something built-in to their OS? So far my success only have been Proxy and Firewall for companies who can't afford Checkpoint licenses. I freaking tried, but I am getting tired. I don't think people understand how important MATURE Directory of Service means to corporations. Oh, I rather use AD than Novell's NDS. I used to maintain Novell 3.x and 4.x in the 90s, what a piece of ****. I still LOVE Linux and I will always use it at home, but without a very good road map from the "real" world success, it is becoming impossible to map out a plan for clients.

I thought Novells NDS now edirectory was superior to Microsoft's AD which is pretty much a copy.  I think the best bet would be to use SLES and SLED for that type of setup.

---

### Post by netlogic on 2007-08-12
> **BoneKracker said:**
> You're wrong.

Here's where I think it's going to happen.  Public organizations, like national governments, are finding it increasingly difficult to justify the never-ending expense of software licenses.

FOSS is so closely aligned with the purposes of most governments that it's a no-brainer that they adopt it.  In fact, UNIX was a U.S. federal government project to begin with.  Reuse, standardization, interoperability, government-academia-corporate partnerships, good fiscal stewardship... it just makes too much sense.

It's organizations that are massive enough to create and maintain a distribution of their own for whom gnu/linux makes the most sense of all.

And they have a much bigger influence on what corporations do than people realize.

I doubt you are an IT person. I don't think you understand the perspective of IT departments. Let's go back to the concept of pushing the open source world history. In the past five years, we have ported so many apps over to Windows, because of the assumption of many programmers that users only care about apps, not OS. We got OpenOffice, Evolution, Firefox, Gaim, and tons of cross platform open source applications to Windows. Did that worked? I think that only made Linux home users more happy at work in the Windows environment.  Still, PC manufactures aren't packaging these free applications with brand new Windows machines. It is still bundled with tons of free trial CRACK commercial application for Windows users. It has been over 12 years to push the Linux Desktop to commercial vendors. Seriously, are we going anywhere now? The users will still want Windows, because that's where skills reside. The training programs to switch users to different applications aren't cheap. I have experiences in various migration planning. I was in various projects. These training firms will charge up to 150,000 dollars for three to four sites to train every users in your company. What do we have left? Beg and wait for PC vendors start shipping more Linux OS than Windows, so users can learn Linux Desktop on their own time? The best hope is force all the admins in your department to get used to Linux. Tell them they might get replaced if they don't learn Linux servers. That option is very doable. However, we still have Windows Desktop integrations to deal with. When average Joe sales person write down their computer skills on the resume, it isn't OpenOffice. It is virus prone Ms Word. You aren't seeing the big picture. If the college really cares about Linux, how come they are still pushing Windows and OSX boxes at their college computer stores? Our USA govt? I don't know where you get your information, but they are still 90% Windows.

---

### Post by koenn on 2007-08-12
> **netlogic said:**
> You are right, but you are also forgetting networks are changing.
Again,  was giving some historical background that explains more or less the situation as it is now, and why you're having these problems. 

As for slow VPN connections over DSL a.o., isn't this where MS Terminal Services or Linux remote sessions play their role ? 

You should build your sollutions around the business needs of your customers, and then implement them the best way possible. I think that's what IT departments do : design and implement sollutions for the business needs of the customer.
If, in a given situation, server-based computing (be it on a Windows platform, a Linux platform, or something else) is the way to go, then yes, obviously building server (-farms) is the logical consequence, but you may then have to reconsider the specs of the client machines - maybe the don't really need to get the latest, fasted, dual core CPU with bells and wissles, to be replaced by even a more powerfull machine every 3 years. 
If  your sollution requires network connectivity, you create network connectivity. If that's not an option, you need to develop a different sollution. 
On the other hand, if you decentralise and have Windows PC's all over the place, you'll want to manage them centrally and then creating Acrive Directory domains might very well be the way to go. In that case I'd probably just go for a MS Windows Domain controllers and their native management tools rather than trying to find cheap replacements that do only half of what you need them to do,  or add unnecessary complexity. 

Now for some nitpickin,g :
> **netlogic said:**
> 
. However, the downside of manging Linux workstation is managing all your pgp and ssh keys that are all decentralized. Imagine manging 5000 ssh keys can be a nightmare to deploy to securely mange configurations of all the client machines. 

Isn't this where you start looking  at PKI infrastructure, certificates, etc., to automate your administration ? 

> **netlogic said:**
> 
Also, most admins don't have time to write perl scripts for every windows applications to deploy through login scripts.
Whatever sollution you chose whether it's perl scripts, login scripts, custom made msi's, mst's, answer files,  and deplyoment  through SMS, Active Directory, specialised 3th party tools or simple scheduled jobs, that admin better takes the time to design it, set it up, do all necessary preparations and configuration, takes into account limiting factors and relevant constraints such as processing power and network bandwith, test it, design, setup and test a rollback-scenario if things go wrong and then plans his roll-out. 
The choise of the actual technology (perl ? SMS ? ) is of lesser importance - but that's almost always the case.

---

### Post by koenn on 2007-08-12
BoneKracker ( [http://ubuntuforums.org/showthread.php?p=3175609#post3175609](http://ubuntuforums.org/showthread.php?p=3175609#post3175609) ) is right - FOSS is a natural choice for the public sector. There's the price issue (public organbisations usually have limited funds, and governement agancies are often required by law - at least in Belgium - to choose the cheaper of 2 technically equal sollutions). 
More important :  Open standards and open formats ensure access to informtion and exchange of information independent of vendor-specific, closed applications. Open source software ensures that it will always be possible to (re-)create an appllication needed to have acces to data, which matters a great deal in regard to archiving and the availability and accessibility of public records. It just makes sense. 

The only limiting factor is a technical one. Take the Office suite example : If you happen to have a custom made application that expects to be talking to MS Word 2000 (and nothing else) and / or depends on the presence of certain MS Word macro's to produce its output (it's terrible but it happens) you have little to no choise than to go with MS Office, and you most likely don't want to confuse your users by giving them 2 Office suites. So you end up using MS Office until you've ironned out those other problems.

---

### Post by BoneKracker on 2007-08-12
> I doubt you are an IT person. I don't think you understand the perspective of IT departments. 
Perhaps not.  But that would be unfortunate considering that I happen to be a senior-level information technology leader with 20 years of experience working in and with the IT departments of small, medium and large organizations (ranging from eight users to more than 450,000 users) in the corporate and public sectors, including at least eight different industry sectors, the federal governments of three countries, and half a dozen state/local governments in two countries.
```

Our USA govt? I don't know where you get your information, but they are still 90% Windows.
```Among the above, I spent about 18 months as a strategy and policy advisor to the CIO of one of the branches of the U.S. military.  You are talking about desktop systems and about a current snapshot in time -- neither are the 'the big picture'.

You talk about the 'big picture', but I think you should examine whether you really understand what 'the big picture' is.  The most highly mission-critical information systems present in any organization are those used for 'direct labor' (in accounting-speak), those that support 'core business processes' (in management-speak), those that are 'national security systems' or 'warfighting systems' in (military speak).  Process control systems for manufacturing (so-called 'embedded' systems) are a good example.  These mission-critical systems are rapidly being migrated to Linux.  The U.S. Army is standardizing its future 'warfighting' systems on Linux.

While all organizations tend to have "shop floor" versus "back office" architectures, these are becoming increasingly integrated.  Why do you think your beloved Microsoft is so eager to be seen as a useful extension to SAP? They know that the shop floor (loosely put -- I mean anything direct like materials management, inventory, manufacturing, distribution, sales, etc.) is the center of mass -- where measurable business value is created.  In the military, the analogous systems are command & control, intelligence, tageting, and so on (and yes, they have back offices too -- in fact, they are the largest 'knowledge-worker' organizations I am aware of, with a whole lot more folks sitting behind a desk than manning a weapon).  But they are an interesting case, because nowhere else will you hear with such a unified voice that it is the "shop floor" that takes priority.

While "shop floor" changes will not cause people to change desktop computers in the back office overnight, they do produce the necessary in-house apparatus to later do so.  In the case of the U.S. Army's use of GNU/Linux, it will produce a cadre of skilled linux developers, architects, systems administrators (and contractors who provide these services); it will produce the necessary governance structures such as architectures, standards, and processes; and it will produce the knowledge capital and organizational learning that will overcome the very objections you raise.

A major part of the 'warfighting' systems is logistics (which I'll simplify here to include resupply, maintenance, medical, personnel replacements, etc.).  Logistics is a 'long tail" reaching all the way back into the home country and its industrial base.  All those systems have to be highly integrated.  Yeah, we've got xml, but integrated systems have a way of influencing each other's architectures.  You can see that the entire logistics community will also be more predisposed than before to use the Linux platform.  The databases already run on it, why not the rest.  Why put my SAP on a Windows server when I can put in Linux -- that's what the systems I have to talk to in the field are running on anyway.  (The reason this comes to pass is that these adjacent systems are often conceived, architected, developed, integrated, and/or supported by the same groups of people -- like the Mitres, the Lockheeds, the General Dynamics, and the EDSs.)

These changes in the systems supporting 'core business processes', in turn influence the desktop systems.  Taking the U.S. Army as an example.  Once they have fielded say 200,000 linux-based 'warfighting'  systems and maybe a couple hundred or so major logistics systems that are linux-centric, do you think they will lack the resources (and more importantly, the confidence) to use it as a desktop system?  The costs to make the switch will have dropped dramatically because of what's been created to support the 'NSS' and logistics systems.  The contractors who are building them the warfighting systems will be banging at their door telling them how they save $500 Million a year in desktop OS licenses alone.  And the Washington Post will be asking why they're not doing it.  Across the D.o.D. -- couldn't those $Billions be put to better uses, like improving education or health care (or be given back to taxpayers)?  Across the Federal Government and all state/local governments combined, the figure would be staggering (hundreds of billions I would guess).

In fact, the D.o.D.'s C4ISR architecture used to be very UNIX-centric and that center of gravity still exists in its policies, standards, and processes.  I has been stubbornly resisting salesmen like yourself trying to change it to the "next big thing" (being Windows) for the last decade.  Adapting it to Linux is a noop and will be met with little resistance from the architectural powers-that-be.

Desktop systems are just a small piece of the big picture, and as I say, they are influenced by the other systems.  You are not going to change the world by trying to sell the Linux desktop (or servers) to the U.S. government or a corporation.  But, I'm saying, it is in fact happening.

> I thought Novells NDS now edirectory was superior to Microsoft's AD which is pretty much a copy. I think the best bet would be to use SLES and SLED for that type of setup.Yes, this is what I was trying to point out in my original response.  I believe there ARE some good tools for this, but you're not going to find them diddling around with a home-user distro (like ubuntu currently still is) or a hobbyist distro (like gentoo).  The "enterprise" distros like Red Hat and Suse (Novell) have been working on this problem for years, trying to make their product relevant to "the Enterprise".  Some of what they've done might be accessible via Centos, Fedora, or OpenSuse, but the "killer app" you're looking for is probably a commercial product from one of these vendors.

While directory services, centralized administration, single-sign-on, authentication and so-on are all critical aspects of enterprise architecture, they are small picture.  The big picture is identifying the levers that influence an enterprise's architecture away from one center of gravity (the standards and architecture promulgated by the Windows eco-net) and toward another center of gravity (the standards and architecture promulgated by the FOSS eco-net).

For example, based on what I've theorized above, a salesman like yourself might decide to focus on logistics subcontractors that work in the Aerospace & Defense industry sector.  "Big picture" is a relative term.  You should be careful how you use it.  The more I learn, the more I realize it is true that, "One does not know what one does not know".

[Edit]: Let me add an example that's more down-to-earth, possibly more applicable to you if you are working with smaller organizations.

I frequently talk with the IT Director at a hospital (which is part of an very large publicly-held healthcare enterprise).  Listening to his problems, I have taken the opportunity to point out GNU/Linux when it happened to be a good solution.  For example, as a subordinate IT department in an enterprise, particularly in an enterprise that does not recognize IT as of strategic value, they don't have much freedom to spend money on experimentation and innovation.  So, often, needs go unmet.  At the "enterprise" level, simmering user dissatisfaction and lack of distributed freedom to innovate are considered necessary evils of IT cost control.  At the IT department level, however, user dissatisfaction is in your face.  That and lack of freedom/resources to innovate mean low team morale, stress, and poor job satisfaction, which are a recipe for failure across the board.  Here are some examples of how Linux "saved the day":

1)  He was having trouble getting the capital for a good enough back up system, so I talked to him about the various rsync-based solutions and the superior economics of hard-link-based solutions.  They now have a Linux-based backup solution, cobbled together from a retired server and a couple hundred dollars worth of parts.  He was commended by the CFO for saving the $25K he had earlier requested for a backup system.

2) He is understaffed and his small team scrambles around trying to manage (along with everything else) dozens of application-specific servers scattered throughout their facility.  He doesn't have room for them all in his tiny "data center" (which is more or less dedicated to basic infrastructure).   I spoke with him about virtualization and the role it can play in server consolidation.  After dabbling with it a bit, they decided to consolidate a couple of Windows Servers.  It worked, everybody was amazed, and now they have a funded project to consolidate most of their application servers on virtual hosts.  (Some they can't because the 3rd party vendors have not yet certified them for virtualization environments).

3) Their doctors are asking for some advanced telephony functionality not available in their current pbx system.  Enter Asterisk. Etc.

4) Dedicated development environments - can't afford.  Re-enter virtualization.

After seeing these successes over an 18 month period, this IT department, the financial decision-makers who set it budget, its customers, and to some extent its parent enterprise, are becoming increasingly comfortable with GNU/Linux.  They are far from ready to make it their standard desktop -- BUT -- without any prompting from me, the have decided to have a pilot project to outfit an entire department of users with Linux desktops.

5) Future -- I suggested they look into LTSP, in which case they could recoup 80% of their budget for desktop technology refresh next year, but simply converting these desktops into X terminals served by an additional virtualization server.

Don't bang your head against the wall -- look for pain points -- look for unsatisfied needs where GNU/Linux fits and sell it there.  Critical mass will build slowly and then you will have overcome the seemingly insurmountable barriers.

---

### Post by jrusso2 on 2007-08-13
Some very well thought out solutions, bravo.

---

### Post by netlogic on 2007-08-13
These types of talk have been discussed for over a decade now. First of all, I am not defending Microsoft. Since, these are typical internet discussion, the psychology of perspective of people's assumption are typical on the net. Many pointless arguments based on assumption and their personal histories of lives. On your 20 years of experience as the IT leader, have you not dealt with any meetings with head of Operation Management folks about the increase in the cost of their operations due to the migration? It doesn't matter if Linux is free. In your 20 years of experience as a head of IT, have you had any discussions with your past CTO and CIO about the hidden future productivity loss income? You have to consider the support costs, restructuring of Help Desk costs, training costs for users and staff, migration costs from consultants, documentation costs, and increase in the hardware costs during the migration. The most important factor is the slowing down of user productivity costs during the migration path. The license costs are cheap if you compare millions of dollars will be spent during the migration. You also have to factor in the regression formula of the average of slow down in the business costs. Yes, Linux isn't Windows. It probably will never be. However, if certain tools aren't there to lower the adjustment, it will get stamped every five to ten years that indicate, &#8220;Linux isn't ready for the corporate America.&#8221; The issue is many Linux folks don't work in the enterprise IT departments. In the spirits of Linux, developers aren't caring what the Enterprise wants, because it doesn't matter to them. Why should they care? They are coding for the love of Linux. Linux is a religion. I am sorry to say I am still disappointed with the Enterprise Linux. It isn't still listening to the IT people what they want. I believe IT departments have the biggest path to the adoption of Linux. If we are still waiting for PC vendors change the world, it will be forever.  Why did Windows adoption won over Mac? We all know, it wasn&#8217;t, because Windows offered a better product. Most people bought Windows, because that&#8217;s what they used at work. Most people have waited 10 years for this. PC vendors will push whatever product customers want. In their perspective, what benefits will they gain by cheering on Linux?  They are in the business of making money. They don&#8217;t start a PC hardware business for the political reason. Right now, it probably costs them more to sell Linux than Windows, because of the support costs.  Like I said before, the real costs aren't license costs. 

Still, the Enterprise Linux doesn't focus on writing their own codes around Linux that might satisfy corporations. They are still focus around bundling the codes that are available in the world.  Currently, the Enterprise Linux doesn't offer any migration path from Microsoft. If you look at the history of how MS crushed Novell's Netware product lines, it was the tools and apps to migrate. I think we need to take it to the next step than just focus on the web server market. Also, this discussion is starting to get pointless, because it has been debated over many years now. I think Linux world should focus on less on the marginal increase and start taking bigger jumps. In order to this, the easy adoption has to take place instead of keep on dictating Linux isn&#8217;t Windows attitude and tell non-technical people to change how they work.  IT business exists to save the business folks money. We don&#8217;t exist to make them feel cool about themselves.

---

### Post by koenn on 2007-08-13
long rant. rather pointless, unfortunately.

- yes, migrations are expensive. 

- This was funny :
> Yes, Linux isn't Windows. It probably will never be Sounds like you expect Linux to be just a cheap replacement for Windows. It isn't. It's a different OS, with different design principles behind it and a different historical background. It's never going to be "Windows".  Not does it have to be. And no, this is not "dictating that non-technical people should change the way they work". People use applications - not operating systems. 

- for someone who wants to sell Linux servers to Windows users, you do a good job at pointing out the downside of such a strategy. Sounds like you choose Linux for reasons of your own, then you complain that it isn't suitable for you customers' needs. Strange. 

- in Linux Land, things get done when people go and do them. Not because someone on a blog or a forum rants about "Linux shoud do this" and "Linux should be that"

- A migration path from Windows to Linux, now that's an interesting idea. In light of my previous point : care to do develop one ? 

- > Also, this discussion is starting to get pointless
Agreed.

---

### Post by netlogic on 2007-08-13
People can whine and say who cares about the migration path. MS blows, and maintain who cares attitude. If the tools aren't there to create more market shares, the money for support costs can't be transfered to the commercial Linux support company as Canonical. Also, companies like Dell will stop selling pre-installed Linux PCs. I think you already know this is the 3rd wave of the trend from Pc vendors to push Linux again. 

Money doesn't grow on trees. We all can't live off from the labor of love. More potential paying customers, more money companies like Canonical can make. It return more donations money will be raised to fund more projects. We can't go Linux installations from the numbers of ISO downloads from distrowatch.com. Linux is a tiny market share. I think I personally download three a week to just to get those numbers up.  For myself, if I was selling Honda and I tried my best to sell VW and most people didn't want them, I will got back to selling Honda. However, I probably will be driving VW. We aren't all some hippie college kids who are living off ramen. Techs have families to feed too.

---

