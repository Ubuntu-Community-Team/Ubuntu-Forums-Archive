---
title: "Ubuntu in the Workplace"
date: 2008-03-30
forum: The Cafe
---

### Post by Everwanderer on 2008-03-30
I'm starting to tinker around with the idea of implementing Ubuntu in my workplace and I'd like to get some feedback on various aspects...

Has anyone ever seen/used Ubuntu in a gov't or business environment? If so, how did it fare? Were there any issues when dealing/interacting with outside clients/sources (ie using Windows, Mac, MS/Corel/Lotus products)?

Given the average user's computer knowledge, how did they make the transition forn a Win environment? Did they have problems woriking in Ubuntu? Also, did it have an big impact on tech support?

What about scalability? If you start with a few workstations, how easy would it be to move up to 10? 50? 100?

Also, were there problems "including" local home grown application in Ubuntu.

Big thing to ask, I know.. But given what my employer spends in new hardware and software, I figured giving them a less expensive solution might be a good thing.  Thank you!

---

### Post by freebeer on 2008-03-30
I'm rolling it out in a small office.  Not at the desktop, but in the back-end.  I'm running Ubuntu 7.10 as a Domain Controller and backup server.  I'm also trying to ease them into using Open Source apps where possible.  Unfortunately, they do depend on a few windows-based apps with no Linux equivalent.  I may go virtual machine with those.

---

### Post by HermanAB on 2008-03-30
You can do pretty much everything with a combination of Linux and Codeweaver's Cross-Over.  Your biggest head-ache in a government situation is authenticating to MS Active Directory.

---

### Post by Everwanderer on 2008-03-31
Interesting.. 

Crossover or VM would probably save me a lot of hassle. As for Active Directory, what exactly do you mean? (yes, I had to look it up). If I understand coorectly, AD would only come up as a problem is the Linux users shared resources with MS users, like a printer.. right?

---

### Post by PartisanEntity on 2008-03-31
It depends on the office, in our office the only tools we really need are word processing and web broswer. I am sure that Ubuntu would be fully useable in our office, you would simply have to give some of the colleagues training so that they could get used to OpenOffice and some menu structures in Ubuntu.

---

### Post by fatality_uk on 2008-03-31
I have now rolled out 15 desktop PC's all running Linux (Ubuntu) Stage 1.
For certain programs there has to be access under Windows as there is no Linux client to our ERP system and it would cost more to develop one than the system costs.

So instead, we use seamlessRDP. [http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/) This is a great combination as the user just needs an account of a Windows server and the software runs from there. There's no other OS to log into. The Windows only app runs directly from the Linux desktop. I highly recommend using the seamlessRDP method.

---

### Post by drascus on 2008-03-31
Scalability: Linux is famous for its scalability. That is why it became so poplular as internet servers and use in cheaper super computer alternatives. 

Gov't: I don't know about Ubuntu but I know that plenty of countries have their net infrastructures based on Gnu/Linux and Free software: For instance the Swiss Government has made the Switch to Gnu/Linux. Also all the Schools systems in Russia are about to switch over to using Gnu/Linux.
Check Wikipedia under the heading government: [http://en.wikipedia.org/wiki/Linux_adoption#Government](http://en.wikipedia.org/wiki/Linux_adoption#Government)

Local home grown applications: Gnu/Linux is a great platform for custom software. With all the source code available developers can be sure how the applications will interact with the rest of the system. Further more if any applications that already exist need modification it can be done easily. 

Tech support: Canonical has great Tech support. The Gnu/Linux environment makes it so that there is real competition for support so any company offering it must do their best so that their customers won't go somewhere else. 
Check out this: [https://shop.canonical.com/support.php?osCsid=c4e563410c951c3d7dfee41accc1175d](https://shop.canonical.com/support.php?osCsid=c4e563410c951c3d7dfee41accc1175d)

It is important that Governments use Free Software. Governments shouldn't trust their information tech to proprietary software they don't have control over. In that case the solution is Free Software that Governments can be sure is under their control and which saves tax payers dollars and provides a real secure solution. 

Hope all this helps.

---

### Post by Everwanderer on 2008-03-31
Thank you for the info! Whatever I can find for the higher-ups to chew on at work will be useful.. 'specially the integration of home grown apps. 

Regarding Crossover, I've looked it up and it seems that they've dropped working on Corel software (wiki says so, if memory serves), anyone knows of anything for Corel and Lotus out there?  And yes, my clients are notorious for using as many different types of word processors/spreadsheets/presentation softwares as possible.. all on the same machine.

VM are nice, and I admit could be useful to circumvent some issues, but since I'm trying to go as free as possible, buying licenses (or renewing them as the case may be) to run them on VM might look "counterproductive".

I'm picky, I know, but I'm also very greatful for any input that might further the use of free apps, etc. in the workplace.. and saving a few millions along the way.:p

---

### Post by macogw on 2008-03-31
Nah, no need for AD for printer sharing.  AD is like Windows' version of NFS, where the user's entire home directory is kept on a server and no matter where you login, it authenticates against that server and pulls the home directory over the network.  It's kinda like LTSP on steroids in that regard, I guess, except LTSP assumes all computers netboot from the same server.  AD lets you have lots of servers holding the home directories and passwords and wherever you login from it just finds the right server to authenticate against and pulls the info.  There are other directory services, of course.  AD is just Microsoft's proprietary one.  It really only would matter if you were doing a mixed environment.  If you're doing all *nix it wouldn't affect you.  [Wikipedia](http://en.wikipedia.org/wiki/Directory_service) has a list of directory services.  You may want to look at OpenLDAP if you need this sort of functionality.

I'd recommend loading up the Windows clients with lots of FOSS first so that they know how to use OOo, FF, etc before you switch.  Also, it almost *always* works best if you migrate the servers before the clients.  Windows clients will talk to a Linux server more easily than a Linux client messing with an Exchange Server and Active Directory and all Microsoft's proprietary backend junk.  That's because the Linux server would be running all stuff that's standard and that everything has to support just because...it's *the* standard.

If you need Exchange-like groupware, KDE has [Kolab & Kroupware](http://kolab.org/).  You'd just use the regular Kontact frontend and then Kroupware/Kolab goes on the server.  There's also Bynari Insight Server which has the advantage of being able to actually work with Outlook directly, but there's a license fee (it's not FOSS).  There's also [OpenGroupware.org](http://opengroupware.org), which handles lots of groupware stuff but not messaging.  [Open-Xchange](http://www.open-xchange.com/) does groupware and messaging.  Evolution is built to work with Novell's groupware easily.  From Mozilla, there's [Chandler](http://chandlerproject.org/).

---

