---
title: "Ubuntu in Business - a short essay"
date: 2007-04-12
forum: The Cafe
---

### Post by Sternfan on 2007-04-12
Not sure where to post this, so I came here.  Maybe there needs to be an **Ubuntu In Business** forum?
[CENTER]
Ubuntu in Business [/CENTER]

*In the last few years,  I've been experimenting with using Linux (Fedora & Ubuntu) in a business scenario.  This  essay is an attempt at opening a discussion on what Linux needs to make it in the small/medium business networks.  For the purposes of this essay, I'll use a typical sized business of 300 – 500 desktops and a half dozen servers.  On those desktops, there are often large numbers of users who need an office suite and email.  And in all the Linux books I've read (probably close to a dozen or more) the issues I am going to be discussing have never really been addressed. *

**Why?**

Why focus on business networks compared to other types of users?  In short, money.  Do a quick survey of IT departments all over the world and come up with a rough idea of the money spent.  It's not uncommon to see costs in the hundreds of dollars per desktop (serious money for 300 to 500 desktops).  If Ubuntu were to make a business-capable desktop, it will need support.  Businesses are wary of “free software without support” - so to make the Board of Directors happy, you can get software for free, but buy support (think Canonical) at a substantial savings from what you were spending before.

So why isn't Linux making inroads on the business desktop?  It's costs nothing, is stable, secure etc. etc.  It should be a Network Admins dream, and should be installed all over the place, but it's not.  And most users just need an Office Suite and Email (which any Linux can do).  Sadly though,  I have yet to find ONE network with Linux on the business desktop.  And I've been doing network support since NT 3.51, Talking to other Admins I know, and their experience is the same – no Linux on the business desktop.  On servers?  Yes – but not desktops.

Ok – so why isn't Linux/Ubuntu on the business desktop?  Here are the reasons I've found while talking to other Admins & Network Support people (I'm the guy always asking about Linux and the following is based on the responses I get):

One of the things Linux is lacking is central control.  Running a network with 300 - 500 desktops from a server room that has two or three techs.  And while there may be “work arounds” - this needs addressed.  Every IT department I have ever visited is overworked and understaffed.  Central Administration is essential to their day-to-day work.  Example – you setup a new Squid Proxy box and want to point all 500 desktops to the new server.  How can you do this?  What if you only want 300 of the 500 pointing to the proxy?  There are countless issues like this – folder redirection (to file servers), browser settings, desktop settings etc.  etc. 

Software Installation -  Imagine a new version of OpenOffice comes out – big file – and needs to be installed on all 500 desktops.  You can't ask all the users to do it – they don't have install rights (or at least they shouldn't).  Visit each machine?  Remote into them all?  There might be some type of script to do this, but I've never found one.  In short, Admins need the ability to put software on their servers and roll it out to clients as needed.  Any of these solutions need to keep internet connection bandwidth in mind – big downloads tend to kill internet connections...

Domain Logons – Most businesses with between 300 – 500 desktops are running some type of Domain – NT or Active Directory (2000 or 2000 versions).  To take advantage of centralized user administration, Linux workstations must support domain logons.  Can it work?  Yes.  Is it efficient?  No.  Joining a workstation to a domain and pointing it to a Domain Controller for logons should be a task that should take no more than a few minutes.  This morning I set up my Fedora 6 test machine to do just this – and after reading all my notes and a few articles I downloaded off the internet – it took about 35 minutes to get it to work.  The procedure is also prone to errors – if you screw up a PAM config – the box is hosed (I've done it).  What's really needed here is a “Join a Domain Wizard” - that joins the Linux box to the domain, and sets up PAM, winbind, nsswitch etc all in one process.  Answer a few questions, reboot the box and the user should be able to logon with their domain account...  
  
Users – The average business user is not “technically capable” - they view computers simply as a tool to get a job done, and it should be setup and maintained by the IT people.  To this end, things like Roaming Profiles are a must.  In my experience, Roaming Profiles are now a given on virtually every network I've worked on.  And all a Roaming Profile is, is a centrally stored profile associated with a user.  Imagine you work in a hospital and you work on different units on different days on different PCs.  You have some network drives and shortcuts to all the files & programs you use plus Firefox bookmarks etc.  And a fancy desktop background (users love backgrounds).  It is a complete pain if your settings don't follow you – and a support nightmare.  Users barely understand the concept of network drives, let alone having to reset them on every workstation they visit.  Take the average user with 5 or 6 network drives, and think about that user having to reconnect them when logging onto a different machine...  This is a help desk nightmare.  And Linux already does profiles – on a single PC.  Log in as JOE and you get JOE's profile.  Login as NANCY and you get NANCY's profile.  It just doesn't follow you from PC to PC.  And while thin clients are interesting, they aren't often a good solution.  Servers need to be beefy, users are uncomfortable with them etc.  I've used LTSP, VNC and FreeNX, and while they all work in certain cases, they just don't fit every scenario.

I hope these ideas will spark some debate and support from fellow Admins (and non-admins) that would like to see Ubuntu make headway into business networks.  

Thanks,
Rob

---

### Post by aysiu on 2007-04-12
> **Sternfan said:**
> Not sure where to post this, so I came here.  Maybe there needs to be an **Ubuntu In Business** forum? Do you mean a subforum in the Ubuntu Forums? If so, this is the place (I moved you from General Help to Forum Feedback & Help).

---

### Post by Sternfan on 2007-04-12
Not really.  I just meant that whole post dealt with Ubuntu in Business - and their isn't a space dedicated for something this important.  

If you create a space/forum for business, I would like the idea of my post going there.  If not, I'm a bit concerned that most people browsing the forums would miss it so the best place for it would probably be where it was (General).

Thanks,
Rob

---

### Post by aysiu on 2007-04-12
In that case, I'll toss it into the Cafe. That gets a lot of traffic, and it's really the best place for a discussion. General Help is for support threads.

---

### Post by maniacmusician on 2007-04-12
I can't address all of your issues as I know squat about most of it, but a great solution for pushing out updates and having central administration is a thin-client setup. It's a great way to do things. Each user can still have their own account, but there will be a central way to control everything, and any updates applied to the server will get pushed out to all computers automatically. Bliss.

---

### Post by Sternfan on 2007-04-12
Thanks.  And I really think the forums need a business section - I hope you can take this idea to the powers that be and see if it is possible.

Thanks,
Rob

---

### Post by salsafyren on 2007-04-13
All of your wishes can be done with SUSE Enterprise Linux.

Why not pay for that?

You'll up and running in less time than it would take for Ubuntu to create those tools.

---

### Post by dmizer on 2007-04-13
ubuntu already has paid enterprise level support available through canonical: [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

but i think there are other major reasons than the ones you cited for linux not being on the office workstation.

> to cut down on costs, usually large offices have contracts with suppliers for most, if not all, their computer equipment and peripherals.  so it's a huge deal if the company makes a contracted purchase of 500 printers and none of them work on the work station (driver support).

> usually large offices are required to share documents with other offices and other companies who are using microsoft word.  while open office is a powerful document suite, it still has difficulty translating between word and odt.

> large offices rely heavily on proprietary task specific software for many things.  this software was expensive to develop, and was developed for a windows platform.  they would have to reinvest to have that company specific software ported to linux.

> many offices need to make use of some of the more powerful windows programs for which there are no linux equivalents (autocad), or for which the linux equivalent is inadequate (gimp)

> the cost of training an entire office of 500+ staff who have likely never even seen a screenshot of linux.  and while linux can be made to LOOK like windows, it can't be made to WORK like windows.  it took me a good 6 months to become passable as a full time linux user, that kind of loss in productivity for 500 staff members would be enormous.

a better move in an office environment is to try to encourage use (in windows) of open source software instead of proprietary software that costs money.  things like gaim for intra office messages, openoffice if at all possible, thunderbird for email, firefox as a browser, and so on.  for the time being at least, it's too risky and too costly for most large offices to make a switch.

---

### Post by PetePete on 2007-04-13
i agree compleatly with the above essay. 

windows has a few BIG advantages
1) active directory, its just so easy and powerful. different admins have different rights, can control any user profile, find any server, workstation, edit user rights, create dist lists etc 
2) SMS, brilliant for pushing software out to a large number of PCs
3) easy to setup wtih nice GUI interfaces = less skilled admins = more of them = cheaper to employe
4) MCSE/MCSA industry standard qualifications..

---

### Post by Mathiasdm on 2007-04-13
> Software Installation -  Imagine a new version of OpenOffice comes out – big file – and needs to be installed on all 500 desktops.  You can't ask all the users to do it – they don't have install rights (or at least they shouldn't).  Visit each machine?  Remote into them all?  There might be some type of script to do this, but I've never found one.  In short, Admins need the ability to put software on their servers and roll it out to clients as needed.  Any of these solutions need to keep internet connection bandwidth in mind – big downloads tend to kill internet connections...
Just create a server and host a repository on it. You can let all the desktops point to that repository.
If a new update for OpenOffice comes out, just let your server download it 1 time. The 300-500 computers will check the server and download OpenOffice from there.

I'm pretty sure all of the others can be done too, but you'll have to do some research. Send out some mails to other Linux 'tech guys' and listen to what they have to say.

Hmm... Perhaps a Business distribution wouldn't be required, but a place on the wiki or something with information like this would be VERY useful.

---

### Post by eentonig on 2007-04-13
> **aysiu said:**
> In that case, I'll toss it into the Cafe. That gets a lot of traffic, and it's really the best place for a discussion. General Help is for support threads.


In my humble opinion, a seperate sub-board regarding the support and promotion of business use would be beneficial for the community.

Desktopwise, a business desktop will most likely be much alike the regular desktop. But the whole infrastructure management is very important when you plan on using Linux in a company. Even in a very small company with only four or five pc's, you'll want some easy to use tools or intefraces to create users, central management, version and software control, yadayadayada....

If I were to plan a Linux employement in my company. I would need answers to several questions. So it would be nice if there was a place where I could find answers or ask questions regarding those specific needs.

---

### Post by dmizer on 2007-04-13
> **PetePete said:**
> i agree compleatly with the above essay. 

windows has a few BIG advantages
1) active directory, its just so easy and powerful. different admins have different rights, can control any user profile, find any server, workstation, edit user rights, create dist lists etc 
2) SMS, brilliant for pushing software out to a large number of PCs
3) easy to setup wtih nice GUI interfaces = less skilled admins = cheaper to employe
4) MCSE/MCSA industry standard qualifications..

this is a bit misinformed i think.

first of all, linux can host, and connect to active directory, and many large office servers have already been moved to linux, and are hosting active domains.  networking is NOT a weakness in linux.

linux can indeed push remote updates and installs, and was likely doing it before windows.

gui interface /= easy setup.  many (if not all) skilled windows admins make judicious use of the command line.

there are standards for linux that have just as high a reputation in the computer world as mcse/mcsa.

that said, windows admins are less costly than linux admins.  further ... windows admins are cheaper to train because of pre existing windows knowledge and experience.

---

### Post by eentonig on 2007-04-13
> **maniacmusician said:**
> I can't address all of your issues as I know squat about most of it, but a great solution for pushing out updates and having central administration is a thin-client setup. It's a great way to do things. Each user can still have their own account, but there will be a central way to control everything, and any updates applied to the server will get pushed out to all computers automatically. Bliss.

Are these thin clients also useable disconnected from the network.

I mean, when I connect my laptop the office, I get my profile from the server. but later that day, I work at a client. Will my desktop be the same? And will it be updated when I later connect tot the network again?



PS. How can I quote more than one post in one reply?

---

### Post by koenn on 2007-04-13
to the OP:
I fully agree it would be interesting to discuss Linux as a desktop OS in a business environment and the system- and network administration isssues that come with it. However, I do not agree with most of what you say. 

First, to get a few facts right : 
> and should be installed all over the place, but it's not.  ... Sadly though, I have yet to find ONE network with Linux on the business desktop.
how about these : 
France goverenement : [http://news.zdnet.com/2100-3513-6138372.html](http://news.zdnet.com/2100-3513-6138372.html)
City Of Munchen, Germany : [http://news.zdnet.co.uk/software/0,1000000121,39195204,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39195204,00.htm)
Venezuela : [http://blog.blanco.net.ve/2007/03/ubuntu-takes-advantage.html](http://blog.blanco.net.ve/2007/03/ubuntu-takes-advantage.html)
and many others : [http://ubuntuforums.org/showpost.php?p=2291105&postcount=54](http://ubuntuforums.org/showpost.php?p=2291105&postcount=54)
granted, these are 'not-for-profit' organizations so no 'real' businesses in the strict sense, but the network and sysadmin issues remain the same or very similar. 
> And most users just need an Office Suite and Email (which any Linux can do).
Not always. Every business sector probably has it's own specific applications (eg a logistics application, bookkeeping applications, a bookstore inventory application, a  production process monitoring app,  ...) and they'd have to migrate these to linux compatible client software (assuming its a client-server app) -* if it exists*. 

But these are minor points. The main problem with your post is that you seem to be looking for 1:1 Linux replacements for Windows applications (and PetePete reinforces that with his list of "things Linux needs"). It doesn't work that way. 

For starters, you really should consider server-based computing a viable option. Heck, even Microsoft is trying to catch up in that field with its Terminal Server. Linux/Unix has 30 years head start and they know the ropes. But it can not be applied as a 1:1 replacement for an Active Directory Domain - you'd have to rethink your IT environment. 

Secondly, your post seems to assume some sort of mixed environment -eg you want to integrate Linux desktops into a Microsoft Active Directory Domain. Now, a lot of things have been accomplished in this field, mainly through the use of Samba and LDAP modules for a great deal of applications, but imo you should consider that
- mixed environments are always difficult and will always require trade-offs, compromises and workarounds
- making Linux work in a Windows environment is forcing it to work outside its natural habitat and foregoing some of its inherent advantages
- interfacing with Microsoft apps is just plain hard because Microsoft doesn't want it to be easy. Think closed, non-standard interfaces. Think closed, non-standard protocols (or proprietary extensions to standard protocols). Microdoft doesn't want Linux desktops to integrate in a AD domain, they want Windows desktops to do that. The fact that Linux is at all able of functioning in a Windows environment is in itself remarkable. 


Then, for most of the points you mention, there are Linux compatible alternatives.

- "roaming profiles" can be accomplished by having /home on a server and mount it locally to the desktop filesystem, through one ofe the many standard / unix protocols (usually nfs), or through smb ('microsoft networking'). 

-"One of the things Linux is lacking is central control. ". With server-based computing you get all the central control you want, but that's not what you want to hear, you want a Linux replacement for the AD features that were invented to solve the problem of remotely managing PC's with what was originally designed to be a stand-alone operating system. Now, for the proxy example you give : to point to the new proxy, you could use proxy auto configuration or auto detection, or play with DNS address and alias records. And if I'm not mistaking, AD can be used to set the proxy for Internet Explorer clients, but I'm not too sure about other browsers / other software with internet access.

- software installation. 
you mention "bandwith" and "internet connections". Surely you weren't thinking of updating 500 workstations from internet repositories ? You'd cache them, or set up a repository on your LAN. And yes, you can create a scipt that ssh's into each PC and installs updates.  And of course, a server-based environment would make all this unnecessary. 
Or you can have a scheduled jub running with the required permissions to check for available updates and install them on a regular basis - you'd roll out your new OpenOffice version by simply moving it into your own repository and it will get installed the next time that scheduled job runs. I imagine you could even create repo subdirectories for specific predifined groups to diversify the software they get (the finance department installs from //server/repo/finance and the sales department installs from //server/repo/sales) while file links make sure that files common to both subdirs don't need to be duplicated. 
Like I said, you need to think outside the Windows context.

---

### Post by koenn on 2007-04-13
> **Sternfan said:**
> 
Software Installation -  
...  Remote into them all?  There might be some type of script to do this, but I've never found one.  

How about something like
```


for COMPUTER in $( cat /path/to/list_of_target_computers); do

        ssh root@$COMPUTER apt-get update && apt-get -y upgrade
done

```

I'm not a unix/linux sysadmin so I have no idea how they'd go about software management, but something like the above works and looks quite doable to me.

It's just concept code : it would require you've set up host-based authentication for ssh if you want to avoid password prompts, ssh as root is not the most secure way oif doing things, etc, but as proof-of-concept this looks OK to me.

---

### Post by Sternfan on 2007-04-13
Thanks for all the replies.  A few thoughts.

Time - I wasn't real clear on this, but in no way did I mean to imply these issues need addressed now or in the short-term.  I am thinking long-term here, where Ubuntu will be in a few years or so.  Lots of time to figure this out, business networks aren't going anywhere.  And the vast majority of networks are running 2000 or XP and won't consider upgrading for some time.  

Centralized Repositories - sorry I missed that.  I actually knew about setting these up and it slipped my mind when I was writing this.  Once again though, I think this is something that needs treatment (like MySql has MySqladmin, Samba has SWAT etc).  

Printers - good point.  A lot of the companies I visit have printers that they keep until they die.  You would be amazed at the number of HP LJ8000s (and printers of that ilk) still on networks. 

OpenOffice compatibility - I agree it's not perfect, but you run into that with different versions of Word.  Word 2000 has issues with 2003, and so on.  In my experience,  OOo is good enough (just set the file setting to MS).

Clients & software - in no way did I mean every workstation be moved to Ubuntu - I meant just the users that only need an office suite and email.   Things like autocad, etc - those are outside the realm of what I am talking about.

Training - Training is an issue - but if the only thing a user needs is an Office Suite & email, these are so close that I think most users can figure it out.  The users I am referring to don't use an OS per se, they use APPS that happen to be sitting on an OS.  They just need to make docs, spreadsheets and get email mostly.  Talking to those using Office2007 - it is so different that it would probably take less effort (and by extension money) to move them to OOo.  

eentonig - I agree.  Ubuntu needs a business forum/space to hash out these issues.  

koenn - Just a few points - while there are some businesses using Linux as a desktop, I have yet to see it, let alone ever hear of one.  Hybrid networks - I agree, they have considerable overhead.  But once again, I am emphasizing this on clients that only need an Office Suite & email.  Think Cube farms.   I am not thinking of "1 to 1" replacement - with a few things added, I think Linux can be a viable desktop for the workers I mentioned.  If you think of spending say $500 (for example) per desktop in licensing just for producing documents & emails, I think LInux/Ubuntu can be a strong alternative.  Particularly when that PC gets bogged down with viruses, spyware and all the other junk users find to clog up PCs. 

Thin client issues : - need a big server, particularly if you have a lot of desktops.  I agree that this is a solution for smaller situations (say under 25 PCs).  But not really viable for hundreds - unless you get multiple servers, which is a whole other issue.

What I'm really hoping for is to start a discussion about using Linux/Ubuntu in the business world.  What needs to be done to make it work?  Is it truly feasible?  I believe it is.  And I believe it's worth the effort - there is serious money out there to be had.  And make no mistake, Admins are willing to give it a shot, the Linux/Ubuntu world just needs to help it along a little bit.

Thanks,
Rob

---

### Post by Timokl on 2007-04-14
> **dmizer said:**
> > usually large offices are required to share documents with other offices and other companies who are using microsoft word.  while open office is a powerful document suite, it still has difficulty translating between word and odt.

At my office, we still use Office 2000. A few weeks ago, a colleague of mine received a Word 2007 document. That's really fun, because you need at least Office 2003 to be able to install the plugin for the new MS Office formats. :shock:

---

### Post by Spr0k3t on 2007-04-14
I'm all for a business model forum grouping used to discuss multiple distros and thin client setups.  This is an area I'm learning more about for linux in the workplace and would love to be under that drive as it happens.

---

### Post by bodyguard on 2007-04-14
I work for the company that uses Microsoft for everything because of a deal made in the past. My cut of the administration cake is 300 PC's big and 120km wide. And things here look like this:

1. All of the business software that was "DOS/Windows only" in the 90-s is now Client/Server applications. (servers are HP-UX = totally Microsoft free)
2. All workstations use XP but 90% of the users are not aware of that - they use applications. 
3. Users that do know their OS name don&#8217;t care about it until that OS works - as the background for applications
4. All of the intranet connections are carefully optimized for business applications without any bandwidth for once in the year remote XP SP2 or Office2007 installation (so there is no space for SMS, repositories or anything else) 
5. Every huge change in client software is a problem so client software is replaced with a browser
6. Voip is more important for the company then client software upgrades and I fully agree
7. In my company all printers will be replaced with network attached ones
8. The half of users would prefer a simple http based wysiwyg editor then MS or Open Office suite they are forced to use (they use 5% of its capabilities)
9. They don&#8217;t like email clients (too complicated) and some are using http based alternatives

So there is no point of using Linux or Windows OS as a desktop in 300-500 nodes company. Sooner or later it will be there in a form of embedded OS in 19" all in one thinclient device. So the battle is won and Microsoft cant compete in that area.

I think that a real market for desktop Linux PC are little companies with 5-20 PC-s just starting to grow.
They are low on money and they need to build their specific software by themselves using the office suite because there is no ready maid software for them. 
They want free, all in one, software rich OS ready for anything future may bring = LINUX. 

ITS A PITY THEY DONT KNOW THAT LINUX EXISTS.

---

### Post by jman623 on 2007-04-14
> I think that a real market for desktop Linux PC are little companies with 5-20 PC-s just starting to grow

I work for one of those types of companies, It's a non profit after school and summer progrram for for at risk youth.


This is a all MS enviroment however this organization cannot afford the licensing that plague Windows Server OSes. So I decided to go the linux route with ubuntu of course:D  So here's what I got cooking:

First of all I actually have ubuntu running in VMware because the people I work for are very technical inept and I don;t want to scare them. ;-)

So I am using Samba 3.0 so the students can have my version of "roaming profiles" I'll get to this in a second ;-)

FTP so i can upload files when I am not at the office, and so I can do image deployment with Ghost4Unix.

Web Server so I can host the company website locally for testing purposes before launching it to our hosting provider.

SSH so i can putty in from any workstation or from home if needed.

UltraVNC running on the Host Windows 2000 pro OS with encryption of course.:mrgreen: 

DynDNS updater since we have basic Verizon Business DSL and they like to change the IP on us everyday.:mad: 

Print Server running on the Host Windows 2k pro OS cause of driver issues.:( 

Still trying to think of a backup scheme.

Ok so here is how I setup the student's roaming profiles; BTW I didn;t do things the "traditional" way because I had a heck of a time getting Samba to work as a PDC.

First off I am using [G4U/]("http://www.feyrer.de/g4u/") for image deployment. So on the PC image I did the following the regedit:

```
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\
User Shell Folders]
```

The students use one account called student ( thats how it was before I stepped in and decided for obvious reasons to keep that way:roll: 

first off on the server I have share called 'Students'. In that folder their are subfolders one for the Desktop, Favorities, Application Data (firefox bookmarks), and Documents which will obviousily be there 'My Documents' folder. In the Documents I have a subfolder  for each student.

I also have Security set to share in smb.conf since I had a hell of time getting samba to work as a PDC, so I decided it really doesn't matter if student's can see each other files.

So in the Regedit I mentioned above ("User Shell Folders") I changed each key that corresponds to the respective folder set up on the server 


For example for the Desktop, I set the Desktop key to:
```

\\<IP of server>\students\Desktop
```

that way no matter what computer they decide to go to they have the same Desktop with the same files and shortcuts. I also disabled the changing of desktop background so we dont have kids argueing over desktop backgrounds plus that can complicate things for me.


I know this isn't the straight forward scenario but it's working for me. I think more effort should be put into Ubuntu Server. It already comes with LAMP and DNS preconfigured why not have Samba and LDAP preconfigured so we can just bascially ditch Microsoft?:confused:

---

### Post by WindForce on 2007-04-14
> **bodyguard said:**
> I work for the company that uses Microsoft for everything because of a deal made in the past. My cut of the administration cake is 300 PC's big and 120km wide. And things here look like this:

1. All of the business software that was "DOS/Windows only" in the 90-s is now Client/Server applications. (servers are HP-UX = totally Microsoft free)
2. All workstations use XP but 90% of the users are not aware of that - they use applications. 
3. Users that do know their OS name don&#8217;t care about it until that OS works - as the background for applications
4. All of the intranet connections are carefully optimized for business applications without any bandwidth for once in the year remote XP SP2 or Office2007 installation (so there is no space for SMS, repositories or anything else) 
5. Every huge change in client software is a problem so client software is replaced with a browser
6. Voip is more important for the company then client software upgrades and I fully agree
7. In my company all printers will be replaced with network attached ones
8. The half of users would prefer a simple http based wysiwyg editor then MS or Open Office suite they are forced to use (they use 5% of its capabilities)
9. They don&#8217;t like email clients (too complicated) and some are using http based alternatives

So there is no point of using Linux or Windows OS as a desktop in 300-500 nodes company. Sooner or later it will be there in a form of embedded OS in 19" all in one thinclient device. So the battle is won and Microsoft cant compete in that area.

I think that a real market for desktop Linux PC are little companies with 5-20 PC-s just starting to grow.
They are low on money and they need to build their specific software by themselves using the office suite because there is no ready maid software for them. 
They want free, all in one, software rich OS ready for anything future may bring = LINUX. 

ITS A PITY THEY DONT KNOW THAT LINUX EXISTS.

You hit the nail right on it's head :-)
I am an independent Microsoft Visual Foxpro developer, for the last 16 years. I write customized applications for 10 to 100 pcs companies. I now support over 20 of those applications, installed in over 30 servers and 500 workstations. In 100% of the cases, the main application running in all workstations is the one i developed. Since it works on Windows, all desktops are Windows, and since they need email and office apps they also buy MS Office.
For servers i used Novell Netware ( excellent file server ) and lately Ubuntu ( although i'm still a complete noob at that ).
The point is that most customers need their specific application, no matter on what OS that runs. In my oppinion, if there were any tool similar to VFP for Linux, with it's RAD database dev., fast local data engine etc..., then that's the golden road to millions of linux based pcs.

---

### Post by koenn on 2007-04-14
Just a couple of side notes : 

When those 5-20 PC outfits realise that some sort of server to share files or have a common database, might be a good idea, they'll buy MS Small Business Server, unless they have an inhouse geek who can set up, maintain and troubleshoot a samba server, aside of his actual job in the company.  

The larger (couple of 100 pc's) outfits probably already have some IT personel, so for them it might be easier to maintain a Linux environment - but if most of them are trained/self-taught windows administrators, they'll tend to stick with windows.


Of course, in the end its applications that matter - especially if it's about custom made specialist applications. 
Now, WindForce, if a small business can use a Linux platform for all its file sharing, mail, web and office productivity needs, except for that one application developped in FoxPro, what is the real problem then ? imo, it's the fact that they're tied to the Windows platform by that 1 application, and thus by the developers choice for a platform-dependent development environment. 

I know what I'm talking about. I've seen applications build in MS Access, apps that depend on MS Word Macro's for basic functionality, the lot. Even web apps that require client side AxtiveX components etc, you name it.  So what's the deal then : Linux will have to come up with something to replace all that - preferably with 100% compatibility to ease migration ? Or application developers such as yourself should realise that their choises force an OS upon their customers, and maybe that needs to change ?

---

### Post by WindForce on 2007-04-15
> **koenn said:**
> Just a couple of side notes : 
When those 5-20 PC outfits realise that some sort of server to share files or have a common database, might be a good idea, they'll buy MS Small Business Server, unless they have an inhouse geek who can set up, maintain and troubleshoot a samba server, aside of his actual job in the company.  
That size of companies generally have some guy for hardware/network maintenance contract. All *heavy* installations and decisions are done by myself.

> **koenn said:**
> 
The larger (couple of 100 pc's) outfits probably already have some IT personel, so for them it might be easier to maintain a Linux environment - but if most of them are trained/self-taught windows administrators, they'll tend to stick with windows.
Of course, in the end its applications that matter - especially if it's about custom made specialist applications. 
You're right about that. Still, i do have the ultimate power in those cases to change the IT personnel/outsource support company as i see fit. I generally try to subcontract a company where i know there are gurus in other OS than Windows.
> **koenn said:**
> 
Now, WindForce, if a small business can use a Linux platform for all its file sharing, mail, web and office productivity needs, except for that one application developped in FoxPro, what is the real problem then ? imo, it's the fact that they're tied to the Windows platform by that 1 application, and thus by the developers choice for a platform-dependent development environment. 
I know what I'm talking about. I've seen applications build in MS Access, apps that depend on MS Word Macro's for basic functionality, the lot. Even web apps that require client side AxtiveX components etc, you name it.  So what's the deal then : Linux will have to come up with something to replace all that - preferably with 100% compatibility to ease migration ? Or application developers such as yourself should realise that their choises force an OS upon their customers, and maybe that needs to change ?

Well, i have tried many development environments years back, but none had the power to get the job done well and fast like foxpro, hence i choose it as my main environement. 

Following my logic, if Linux came up with a similar tool, that would count for hundreds of thousands if not millions of new Linux desktops.

You're right about having to choose a development environment that doesn't force an OS and that's why i am looking into options, but still haven't found anything that comes close to what i have with Foxpro .  Take a look at morfik ( [www.morfik.com](www.morfik.com) ). This one is a serious contendent, and they are thinking of implementing Foxpro language as well into their scripts panoplie, which is plain smart in my opinion.

---

### Post by Al Foytek on 2007-04-18
[QUOTE=Mathiasdm;2445824]Just create a server and host a repository on it. You can let all the desktops point to that repository.
If a new update for OpenOffice comes out, just let your server download it 1 time. The 300-500 computers will check the server and download OpenOffice from there./QUOTE]

Downloading is not installing.  Installing from a central server is not the same as being able to install locally.  The user would not know how to download or install, and does not want to be bothered with either.  It is IT's job to do such things.

alf.

---

### Post by Al Foytek on 2007-04-18
Thank you Rob for starting this thread.

I agree a forum on this subject could be very useful.  I would love to see a distribution which makes deployment to our business uses simple.

We have about 2,000 administrative workstations - all Windows.  It would be great to get them on Linux.  Most only need office automation tools.  We do have some proprietary applications which they need.  Most are Windows, one is HP 3000 base  at present, but moving to Linux in the near future.  I am hoping an emulator for the MS Win 2K/XP clients will work for the Windows applications.

The entry of MS Vista with its new hardware requirements and need for upgrading systems brings a juncture which provides a significant opportunity.  I am looking for an alternative to Windows.  I think others may be too.  Vista is expensive and provides a lot of stuff we do not need or want on our desktops.

Printers - We have several HP LJ4's still!!!  If it works, why change it out?  Business needs are mostly black and white, simple, and have not changed that much in ten years.  We don't want our employees watching videos, listening to audio downloads, and creating their own movie productions.  We want them do the administrative or other work they were hired to do.  

Training - KDE or another windowed interface is a work-alike to Windows.  Folks will not have that much trouble switching.  Moving them from DOS or terminals to Windows, now that was a big task.

---

### Post by corbouk on 2007-06-07
I agree we need a forum for this.  I'm looking for a client server setup to compete with Small Business Server.  So I need a server hosting email, file sharing, authentication, backups etc and a client machine with office productivity and an email client that can rival Outlook.

Finding something to touch Outlook 2003/2007 isn't as easy as it sounds.

---

### Post by Rede on 2007-06-07
> **corbouk said:**
> I agree we need a forum for this.  I'm looking for a client server setup to compete with Small Business Server.  So I need a server hosting email, file sharing, authentication, backups etc and a client machine with office productivity and an email client that can rival Outlook.

Finding something to touch Outlook 2003/2007 isn't as easy as it sounds.

Evolution can interface with Exchange, and with projects like OpenXchange and OpenGroupware its only a matter of time. What we really need is an open-source Directory Service so that we don't have to rely on Active Directory. 

APT/YUM takes care of updates, and with ssh available on the internal network you can send remote commands very easily. A little scripting knowledge is all you need to get most of the same functionality and once its written it doesn't need to be rewritten every time. I think someone posted some sample code previously, and it wouldn't be hard to put a script on each workstation to update a computer list or even just retrieve it via LDAP.

I think the centralized administration is where the problem lies more than anywhere else. I know about OpenLDAP, but compared to implementing AD you need to install and configure OpenLDAP, Kerberos, encryption, slapd, slurpd, etc all seperately and it seems like quite the job. I've been looking at going through the process but haven't yet, so I can't speak to the overall difficulty but I've set up and had an AD DC running on Server 2003 in about two hours, most of which was spent installing and patching the OS.

(I've also heard Fedora has a directory server but I haven't worked with it. I've seen there is a Ubuntu project in the works but I haven't seen any progress.)

The BIGGEST problem that needs to be overcome is the lack of something akin to Group Policy. Being able to change settings on each workstation based on its LDAP location (OU) and control various parts of the OS is so convenient its the biggest feature I think the open-source community needs to play catchup on. If the desktop environments (KDE, GNOME) implemented some way of doing this (if there isnt already a way that I'm unaware of) and access to the console is restricted to administrators you can effectively control user access.

---

### Post by cacycleworks on 2008-04-05
> **Al Foytek said:**
> Thank you Rob for starting this thread.

Yes! Thanks from me as well.

> **Al Foytek said:**
> I agree a forum on this subject could be very useful.

Agreed. I should actually look around to see if it's happened in the year since this thread.

> **Al Foytek said:**
> The entry of MS Vista with its new hardware requirements and need for upgrading systems brings a juncture which provides a significant opportunity.

Vista is why my company is going linux. I'm the guy in charge and now that I have spent about a year with Kubuntu on my desktop and fuddling around with 3 linux servers in our shop, I have decided we'll try and shift to all web apps served on our servers and have all workstations be thin clients. With as little as 5 workstations, the hardware cost is approaching half. 

No comparison between M$ and OS... each workstation is minimum $1000 in licensing from M$, etc.

> **Al Foytek said:**
> Training - KDE or another windowed interface is a work-alike to Windows.  Folks will not have that much trouble switching.  Moving them from DOS or terminals to Windows, now that was a big task.

I got my secretary switched to KDE on her notebook after its M$ was overrun with virii ... she didn't even blink. I fed her a simple page of cheat sheet items on how to solve problems. I was so proud when she mentioned googling for a solution ... and solving her problem via the command prompt. She gained computer confidence AND is M$ free.

:) Chris
President of a small e-commerce concern.

---

### Post by cmdln on 2008-09-05
I realize this seems to be quite an old thread but I stumbled on it and figured I would drop in my 2 bits.
Disclaimer: I am a sysadmin for a small/medium sized business (about 50 employees)
I am in the middle of a desktop migration to linux for about 70% of our office. And I can tell you there are answers to most of your issues. They may not be click and drool but it works, and from a management standpoint my pilot workstations have required less tender care than any windows machine. Any new magic requests that I get are typically centered around something looking or acting slightly different. I did go to some trouble and have a non-paid "meeting" to anyone interested to do a demo after work. Doing that seems to have calmed some fears and even excited a few people.

> **Sternfan said:**
> 
One of the things Linux is lacking is central control.  Running a network with 300 - 500 desktops from a server room that has two or three techs.  And while there may be “work arounds” - this needs addressed.  Every IT department I have ever visited is overworked and understaffed.  Central Administration is essential to their day-to-day work.  Example – you setup a new Squid Proxy box and want to point all 500 desktops to the new server.  How can you do this?  What if you only want 300 of the 500 pointing to the proxy?  There are countless issues like this – folder redirection (to file servers), browser settings, desktop settings etc.  etc. 


Configuration management, thats the key term to look for when talking about the Squid Proxy scenario. Puppet is well suited for that type of suitation, cfengine could do the same. Folder redirection ... not exactly sure what you mean here but Im thinking bind mounting will do what you want ... checkout mount -o bind. Browser Settings .... well you can push out a firefox extension, you can customize and lock the global prefs, or you could use some fancy external service like mozilla weave. None of those are ideal by any means. Novel has a patch to firefox that allows it to get configuration from gconf, to me that seems like something that needs to go back upstream so the rest of us can benefit from api configuration. Desktop settings ... well if you use gnome (you should, I tried kde and purely from a management perspective gconf is far superior). I have a login script that sets gconf settings on user logon. Im only on revision .2 and its really ugly but it will get better as I get clear grasp on gnome and gconf. As it stands I set background, screensaver, remove the top panel, move the menu-bar to the bottom panel, ensure that firefox and thunderbird have launcher icons, move notification to bottom panel, set workspacees to 1 and remove the workspace switcher, and change the menu-bar to a menu-object to get a more  windows like start button.

> **Sternfan said:**
> 
Software Installation -  Imagine a new version of OpenOffice comes out – big file – and needs to be installed on all 500 desktops.  You can't ask all the users to do it – they don't have install rights (or at least they shouldn't).  Visit each machine?  Remote into them all?  There might be some type of script to do this, but I've never found one.  In short, Admins need the ability to put software on their servers and roll it out to clients as needed.  Any of these solutions need to keep internet connection bandwidth in mind – big downloads tend to kill internet connections...

Puppet or cfengine, write a rule to ensure latest version. Also have a local repository or cache so its only downloaded once. Im using apt-proxy and it seems to be working well.

> **Sternfan said:**
> 
Domain Logons – Most businesses with between 300 – 500 desktops are running some type of Domain – NT or Active Directory (2000 or 2000 versions).  To take advantage of centralized user administration, Linux workstations must support domain logons.  Can it work?  Yes.  Is it efficient?  No.  Joining a workstation to a domain and pointing it to a Domain Controller for logons should be a task that should take no more than a few minutes.  This morning I set up my Fedora 6 test machine to do just this – and after reading all my notes and a few articles I downloaded off the internet – it took about 35 minutes to get it to work.  The procedure is also prone to errors – if you screw up a PAM config – the box is hosed (I've done it).  What's really needed here is a “Join a Domain Wizard” - that joins the Linux box to the domain, and sets up PAM, winbind, nsswitch etc all in one process.  Answer a few questions, reboot the box and the user should be able to logon with their domain account...  

I wont argue that pam can be a pain to setup. But once you have it setup it should be easily replicatable. Again configuration management. Ensure each desktop has the correct version of the config it needs. Puppet will say nirvana is minimal install then let puppet do the rest. I like to be able to use the system as soon as its done so I have a custom installer that does some postinstall tricks, and adds and removes. Then I will have puppet take over after that. Also Ive found that using windbind sucks, just use pam_ldap.

> **Sternfan said:**
> 
Users – The average business user is not “technically capable” - they view computers simply as a tool to get a job done, and it should be setup and maintained by the IT people.  To this end, things like Roaming Profiles are a must.  In my experience, Roaming Profiles are now a given on virtually every network I've worked on.  And all a Roaming Profile is, is a centrally stored profile associated with a user.  Imagine you work in a hospital and you work on different units on different days on different PCs.  You have some network drives and shortcuts to all the files & programs you use plus Firefox bookmarks etc.  And a fancy desktop background (users love backgrounds).  It is a complete pain if your settings don't follow you – and a support nightmare.  Users barely understand the concept of network drives, let alone having to reset them on every workstation they visit.  Take the average user with 5 or 6 network drives, and think about that user having to reconnect them when logging onto a different machine...  This is a help desk nightmare.  And Linux already does profiles – on a single PC.  Log in as JOE and you get JOE's profile.  Login as NANCY and you get NANCY's profile.  It just doesn't follow you from PC to PC.  And while thin clients are interesting, they aren't often a good solution.  Servers need to be beefy, users are uncomfortable with them etc.  I've used LTSP, VNC and FreeNX, and while they all work in certain cases, they just don't fit every scenario.

Here your going to have to do some legwork. I know I searched for a long time to come up with what I think will work ... not implimented yet. Part of the issue when looking for information is most people just mount the home directory. Well if you want windows style offline profiles and syncing your going to have to hook into gdm and write yourself some short sync scripts. Take a look at /etc/gdm/{PostLogin,PreSession,PostSession}/Default. I will take my scripts to the point of enforcing size constraints on the home dir at sync time and error out if not smaller than what I deem acceptable. I may even exclude some pieces of the home directory that cache data like specific parts of thunderbird profile.


Then take it a bit further ... get asterisk, modify your login scripts, add vnc2swf, and get enterprise monitoring on a dime to boot!

---

