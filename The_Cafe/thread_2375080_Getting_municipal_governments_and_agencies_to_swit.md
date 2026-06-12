---
title: "Getting municipal governments and agencies to switch to ubuntu"
date: 2017-10-21
forum: The Cafe
---

### Post by metalbiker on 2017-10-21
This was a question asked on askubuntu and if my knowledge is correct, that service is for technical issues only. So I'm breaching the question here and I'm sure it's been on a number of people's minds over the years and I want to discuss it fully. Because it should be.

First of all, any level of government: be it municipal (local), state and federal, should have use of open source software, namely linux and maybe even ubuntu, already. we don't know that until we ask, correct? the first thing to do is to engage a local official. just email that person. or hell, CALL THEM. there's nothing wrong with just using a phone to leave a message for your local official. it's preferable to start with the mayor and then go from there. Try to get a meeting with this individual to discuss using Ubuntu and when you do go for the meeting, take every piece of convincing information you can get your hands on. DON'T BE UNINFORMED. what's the cost? what's the return on investment? what's the benefits? how about software? can we get specific titles to work on this? these are questions that you should be ready to answer because they'll come up for sure. the biggest issue is cost because any level of government is going to be concerned about cost. they run on a budget. that's a limited amount of money. make it count. 

Ubuntu, as well know it, is perfect for anything. It's free. built-in firewall and anti-virus software. free software. and you can still code programs that you need to work on it. 

but still, the question still remains. what would it take to switch over a municipal government to ubuntu? technically, it's not hard. one copy can switch over an infinite amount of computers. but my suggestion is this. get a computer that's not used and set it up for anyone to use and go from there. let the employees of the municipal government use it when they can and go from there. i'd switch over one computer at a time and especially work with the IT department of the local government to make sure it's fully implemented.

but if there's stiff resistance to change, just kindly keep up the pressure to use an operating system that's free, open source, has many software titles for free, a built-in firewall and anti-virus software, updates that get pushed out as soon as they're ready, etc.

that's my opinion. and it's my opinion only.

---

### Post by TheFu on 2017-10-22
Nothing is free.  Govts aren't IT shops.  They have to pay for support.  When they look into their Rotary Club contacts or Chamber of Commerce contacts - they find all sorts of IT shops.  They all push Windows because that is what they know and that is what normal people have heard about.  

Nobody gets fired for doing what everyone else does.  "Industry standard" is the term.  The fact that a city needs 20 Windows experts or 5 Linux experts isn't something these folks understand.  Saying software is "Free" really does a disservice to all the people and companies making the software we use on Linux systems every day.  It isn't free, it just doesn't require a commercial license, but installing it, maintaining it, training people how to use it and ensure compatibility issues are handled in the required way that a govt would need  definitely costs real money.

There are technical problems, but the real issues are political.  Politics are much more complex and difficult to handle.  The second something bad/unexpected happens, the govt will blame the IT shop and representatives who allowed/pushed Linux and they will be fired.  I've seen this exact thing.  We deployed Linux to a school system.  Everything was going great until someone who controlled the IT budget saw it.  I'm not certain what happened, but the company who did the purchasing and setup wasn't called - another IT company was called.  That 2nd company didn't have any Linux experience, so to solve the issue, they wiped the main Linux server, which rippled through the entire network, breaking things.  Clearly, Linux was the problem and the new company was better - right?  The fact that they were buddies with the head of the budget certainly didn't have anything to do with the failure or the complete wiping of everything Linux over the next few weeks.  

Plus there is the problem that corporation use Windows on the desktop by a huge margin, so teaching students Linux on the desktop "doesn't prepare them for corporate jobs."  I've heard that argument multiple times.  To most people, learning computers is hard, asking them to learn BOTH Windows and Linux would be crazy.

Ubuntu is **Not** perfect for everything, BTW.  There are still things that I use Windows to accomplish because the Linux method wouldn't be as efficient.  

I'm playing devils advocate here.

In my mind, we should forget about the OS wars and push for open data formats. THIS is where F/LOSS solutions, including Linux shine.  We should convince govts that all documents must be published using ODF and PDF should be outlawed since it is a commercial standard.  Just last week I was asked to complete a PDF form for a v1.8 PDF document.  Linux PDF tools only support v1.5 or earlier, so effectively, I couldn't do what was required on Linux.  What is the solution?   Similar issues happen all the time with companies trying to share documents using different software and also using different fonts.  Fonts are a terrible issue for most companies.

---

### Post by mastablasta on 2017-10-23
> **TheFu said:**
>  When they look into their Rotary Club contacts or Chamber of Commerce contacts - they find all sorts of IT shops.  They all push Windows because that is what they know and that is what normal people have heard about.  


yup. they have to keep their "sponsors" happy. maybe even earn a little something for their (hidden) Panama bank account.

---

### Post by QIII on 2017-10-23
Will you volunteer to port all mission critical software to Linux?  Retrain employees?  Retrain SysAdmins, system engineers and help-desk personnel?

I submit that you are very naïve if you believe that the costs of such changes are not prohibitively large.

Why should they change?  Is there some moral issue here?

---

### Post by ian-weisser on 2017-10-23
> **metalbiker said:**
> but still, the question still remains. what would it take to switch over a municipal government to ubuntu? technically, it's not hard. one copy can switch over an infinite amount of computers. but my suggestion is this. get a computer that's not used and set it up for anyone to use and go from there.

There are at least three big hurdles:
- Many use Word-specific templates in their workflow, or rely upon Word rendering that LibreOffice cannot open or render properly. Others use Excel-specific functions incompatible with LibreOffice.
- Some use specific applications, like accounting/payroll, that simply have no Linux alternative.
- IT Departments may view the new applications and OS --and the whole migration-- as a burden. Who want to maintain two sets of platforms? It's just two sets of headaches instead of one.

Try this: IT needs to buy in first. Then migrate to cross-platform applications, one by one. Gradually identify who cannot migrate further for legitimate reasons. Then you're ready to migrate OS.
It's a lot easier in shops that are already running Linux on the back end for servers and backups and phones and the like.

---

### Post by cariboo on 2017-10-25
The company I work for just moved from AIX on the back end to Linux, and we are running into all sorts of permission problems ( I attribute this to lack of training). Personally it took them 4 weeks to get me the correct permissions to be able to access the company intranet and my email account. This is a global multi-billion dollar enterprise, if they have such problems, just imagine what cash strapped local governments will go through if they converted to using a Linux distribution.

---

### Post by kurt18947 on 2017-10-25
I am not involved with schools or education in the usual sense. It seems like schools are not teaching "computers", they're teaching "Microsoft". If students have been exposed to other desktops & O.S.s in addition to Windows, they should have a better understanding of computers including Windows. And as far as vocational education goes, what jobs tend to pay better, Windows or Linux related? There may be more Windows jobs out there (or not) but I'll bet the Linux jobs pay better.

---

### Post by TheFu on 2017-10-25
A RHEL cert engineer earns (on average) $15K/yr more than the other certs ... in the USA.
A RHEL guy with devops and cloud experience can earn $150K/yr in cheap parts of the country. Those skills are in high demand.

There are still some things that require UNIX - mainly huge DBs where Linux systems just haven't been proven.  Used to run a set of (5) 64-CPU HP-UX servers handling a transactional DB, for example.

---

### Post by 7dEfOk4AgU on 2017-10-26
Over the years various municipals have tried opensource both Linux based desktop and or Libre Office. Off the top of my head the ones that have tried have gone back to Windows and MS Office. The cost of conversion is very high and the cost benefit equation makes the the transition non viable.

---

### Post by TheFu on 2017-10-26
> **mikeb42 said:**
> Over the years various municipals have tried opensource both Linux based desktop and or Libre Office. Off the top of my head the ones that have tried have gone back to Windows and MS Office. The cost of conversion is very high and the cost benefit equation makes the the transition non viable.

There is a point where the pay-off begins, but it isn't 3 yrs.  I ran the numbers for a 22K group using just normal MS-Office like stuff and it was over 10 yrs to get the pay back.  All that time, there would be some small group whining, complaining, being disruptive that things weren't like MS-Office. Group productivity would be impacted.

OTOH, new organizations are choosing NOT to deploy MS-office and use alternatives all the time. Anything that moves to ODF files is good in my mind.  Google-docs, libreoffice, MS-office with ODF as the defaults ... fine.

A few years ago, CNet ran an article (since removed) about a small business that completely switched to Linux after the BSA performed an audit, found 8 unlicensed, unused, software on their network.  

About $100K in legal fees and fines later, the CEO was pissed. He demanded that Microsoft be completely gone from their company. Change demanded from the top also works, at least inside a business.  City govts are different, a different dynamic with the employees.

---

### Post by 7dEfOk4AgU on 2017-10-26
> **TheFu said:**
> There is a point where the pay-off begins, but it isn't 3 yrs.  I ran the numbers for a 22K group using just normal MS-Office like stuff and it was over 10 yrs to get the pay back.  All that time, there would be some small group whining, complaining, being disruptive that things weren't like MS-Office. Group productivity would be impacted.

OTOH, new organizations are choosing NOT to deploy MS-office and use alternatives all the time. Anything that moves to ODF files is good in my mind.  Google-docs, libreoffice, MS-office with ODF as the defaults ... fine.

A few years ago, CNet ran an article (since removed) about a small business that completely switched to Linux after the BSA performed an audit, found 8 unlicensed, unused, software on their network.  

About $100K in legal fees and fines later, the CEO was pissed. He demanded that Microsoft be completely gone from their company. Change demanded from the top also works, at least inside a business.  City govts are different, a different dynamic with the employees.

As much as I would love to see Linux Desktop make inroads into the SMB, Enterprise and Government sectors as I believe that it offers a better package than Windows 10 currently does the reality is Microsoft products and products that require Windows are too deeply inserted into these markets. To move to Open Source is a minefield that is very expensive and very complex. At the end of the day the cost benefit analysis is simply on the wrong side of the balance sheet. I have recently been through this exercise with a client and the POC proved that they were better off staying with what they had and putting the effort into negotiating better licensing regimes.

---

### Post by TheFu on 2017-10-26
> **mikeb42 said:**
> As much as I would love to see Linux Desktop make inroads into the SMB, Enterprise and Government sectors as I believe that it offers a better package than Windows 10 currently does the reality is Microsoft products and products that require Windows are too deeply inserted into these markets. To move to Open Source is a minefield that is very expensive and very complex. At the end of the day the cost benefit analysis is simply on the wrong side of the balance sheet. I have recently been through this exercise with a client and the POC proved that they were better off staying with what they had and putting the effort into negotiating better licensing regimes.

I worked in a small company where we only used F/LOSS on our servers.  Each person got to choose their own desktop/laptop (we just paid them a little more), so I know that for almost every need, the Linux-based solutions not only work, but work very well in many situations.  We did leave 1 thing on Windows - the accounting software, for the book keeper. Some things just aren't worth the effort and our files were compatible with the external accounting firm who really handled everything.

* Zimbra - MS-Exchange replacement + much more
* Alfresco - Document Management, full text search, clear permissions to allow different teams limited access
* x2go - remote desktops for when teams needed to edit the same files concurrently.
* openvpn - provide access to systems that were not safe on the internet
* wikimedia - knowledge-based for internal use
* LDAP - password credentials (almost SSO)
* vTiger - CRM (SugarCRM / Salesforce) replacement
* git - code versioning
* Redmine - project management (we actually tried 3 other solutions first)

I'm certain there are others, but those are off the top of my head.
Zimbra, Alfresco, vTiger and Redmine all integrated.  Best of all, there weren't any licenses to track or any CALs to get.

Client-side software really wasn't my role.  We did provide normal Linux desktops via x2go that many employees used rather than dealing with local _productivity_ software installations.  We didn't buy MS-Office for anyone, but a few employees bought it with their annual "IT" budget for personal items.  I got a chromebook and smartphone with my IT allowance.

So it isn't as hard as people think to avoid MSFT software inside a company. Just depends on how embedded it is already and if "the top" will press for F/LOSS solutions or not.

IMHO.

---

### Post by mastablasta on 2017-10-27
> **TheFu said:**
> 

So it isn't as hard as people think to avoid MSFT software inside a company. Just depends on how embedded it is already and if "the top" will press for F/LOSS solutions or not.



it depends on the company. what happens when mostly older people with no IT knowledge work in company? what if company has production (manufacturing), design, development. many apps for tasks are not as evolved or not available on Linux. if i look at my company i think we could use maybe 70 % of PC on Linux. maybe. it all depends on the ERP.

then there are the partners. we communicate with them via Skype for business (previously Lync). though there is a web version of it has missing features.

let's not even start with documents exchanges.

maybe if we had massive IT support, we could pull it off. it would mean a lot of investment.

---

### Post by TheFu on 2017-10-27
Unless the programs **must** be run locally on the machine the person sits behind, the desktop CAN be linux with access to an RDP server running Windows to provide access to MSFT programs/tools.

As I mentioned above, I was asked to find a way to replace Windows for 22K people in a prior job.  That was impossible because those systems had to run about 10 highly specialized, driver-dependent, tools for telecom hardware diagnostics.  There weren't any drivers except those for MS-WindowsXP available, period.  Asking and getting the vendors of the software to port to Linux would have cost well over $100M for the tools and $100M for the drivers - assuming those vendors would even consider doing it at any price.  Vendors say NO all the time.  Plus, much of that HW is obsolete today, so by the time they get the updated SW and drivers, only a few more years of use would have been possible for most installations.  Ok, that isn't really true, because some customers will be running the old, old, old stuff for 3 more decades (probably) even after most others have moved to faster, cheaper, easier to maintain solutions.  There are people who have been renting a telephone from the phone company for $3/month since the 1950s - they are still paying for it today.

My point is still that while not always possible, it is possible much more often than "IT people" think it is to switch to Linux on the desktop.  And it is becoming even more possible as more and more solutions move to web-based environments.

---

### Post by kurt18947 on 2017-10-27
> **TheFu said:**
> There is a point where the pay-off begins, but it isn't 3 yrs.  I ran the numbers for a 22K group using just normal MS-Office like stuff and it was over 10 yrs to get the pay back.  All that time, there would be some small group whining, complaining, being disruptive that things weren't like MS-Office. Group productivity would be impacted.

OTOH, new organizations are choosing NOT to deploy MS-office and use alternatives all the time. Anything that moves to ODF files is good in my mind.  Google-docs, libreoffice, MS-office with ODF as the defaults ... fine.

A few years ago, CNet ran an article (since removed) about a small business that completely switched to Linux after the BSA performed an audit, found 8 unlicensed, unused, software on their network.  

About $100K in legal fees and fines later, the CEO was pissed. He demanded that Microsoft be completely gone from their company. Change demanded from the top also works, at least inside a business.  City govts are different, a different dynamic with the employees.

In my non-IT pro mind, there would be two major obstacles to moving away from MS. The first would be familiarity and training. Lots of FUD out there, more than a little of it provided by MS associated trolls. " What do you mean I don't have to use the command line? That's what {whoever} said" Then there's the "I've been using Windows since 1992 and know all about it. Why would I want to change?" "What do you mean, my computer doesn't have a C drive?"  Then there are the legitimate obstacles mentioned - "Our business relies on Quickbooks/Sage/Autocad/Adobe CS/CorelDraw/some esoteric design package", none of which run locally on Linux. On another forum I frequent there's a lot of discussion about mechanical and laser engravers. None of them have Linux drivers and more than a few don't even have current version Windows support. There are people running Windows 98 because that's the last version of Windows supported even though the machine is working great, making money and ain't cheap to replace.

---

### Post by SeijiSensei on 2017-10-27
I think the real competition is from the "cloud."  One of my clients is moving everything to Microsoft's cloud services to reduce their costs.  Why pay for servers and the staff to manage them when you can let Microsoft handle that responsibility for you?  All the office staff then needs is a browser.

This client is a community health center which has prior experience outsourcing their computing requirements.  They use online systems to manage patients, schedule exams, and track medical records.  It didn't make any sense that people needed to use Microsoft Word on individual machines when they could use Office 365 instead.

I have never been unhappy with my decision to decommission hardware servers in favor of virtual servers at Linode.  Why should I need to worry about reliable power, air conditioning, big pipes to the Internet, or server maintenance?  I'm much happier having Linode handle all those tasks for me.

---

