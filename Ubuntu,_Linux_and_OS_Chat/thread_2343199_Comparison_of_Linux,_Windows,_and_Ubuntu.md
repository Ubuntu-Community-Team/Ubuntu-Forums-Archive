---
title: "Comparison of Linux, Windows, and Ubuntu"
date: 2016-11-14
forum: Ubuntu, Linux and OS Chat
---

### Post by kennster2 on 2016-11-14
Hello Guys

I am trying to understand the advantages of Linux over Windows, is it that Linux is more flexible? And also, how does Ubuntu compare?

Thanks

---

### Post by coffeecat on 2016-11-14
Not a (Windows) support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldfred on 2016-11-14
Windows is not Linux
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) 
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
Thread with discussion Sept 2012
[http://ubuntuforums.org/showthread.php?t=2051228](http://ubuntuforums.org/showthread.php?t=2051228)

When you say compare with Windows, compare with what.
Most games run better in Windows, those users usually dual boot, so they can run games in Windows but still use Ubuntu.

---

### Post by Quarkrad on 2016-11-15
In addition to the above, for me, there are two advantages over windows on a day-to-day perspective.  Having just helped a friend recover from a Ransom Virus on their Win10 machine the inherent protection Linux/Ubuntu has over Windows in terms of virus attacks is huge (if not fundamental). Also - I dual boot with win10 (itunes for my ipod) and the time it takes to do the constant updates is crazy compared to Ubuntu.  When shutting down and restarting it seems to take 'for ages' for Windows to install the updates - ubuntu takes a fraction of the time - you hardly notice any difference in shut down or boot times and only occasionally do you have to do a re-start.

---

### Post by poorguy on 2016-11-15
Linux offers speed advantage over Windows for the old computers that I'm still using. :D
I decided to give Linux Ubuntu a test drive and found that it really works well for my computer needs.
I also like the many different choices of GUI / Desktops that I can choose from.
Linux gives a user the option to roll their own Distro and to only install software that is needed a future project for this Linux user.
I can install Linux on every computer I own without the issues of a COA license for each computer.

---

### Post by TheFu on 2016-11-15
> **kennster2 said:**
> I am trying to understand the advantages of Linux over Windows, is it that Linux is more flexible? And also, how does Ubuntu compare?

Ubuntu **is** Linux, so there isn't any comparison. It is identical.
Is Linux more flexible than Windows?  Cannot say. Depends on the user and the skill level.  A low-skilled Linux user wouldn't be able to make it any more flexible than a low-skilled Windows user.  The knowledge of the user matters.  I would suggest that a highly skilled Linux user would be able to accomplish 20x more things than a highly skilled Windows user.  But there are always exceptions, right?

I've been a programmer, systems admin, network admin, and user of many different computing systems over the decades.  Started with Unix in 1991, Linux in 1993, Windows in 1989 ... today I think I know about 10% of Linux.  I don't expect to know everything. Not possible and things are always changing a little.

Also, just for pedantic clarity - **Linux** is just the kernel. No users really interact with the kernel directly. In a shell, we probably use mostly GNU utilities like ls, mv, df, more, cat, grep, ... This is all without any GUI.  Add in a GUI and we've abstracted to be about 5 layers higher than the Linux kernel. A GUI hides most of the core GNU/Linux stuff from most people.

[Why I use a Linux Desktop]("http://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop")? 
[Why I run LTS Ubuntu]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release")?   

There are good reasons to run Windows too.  Fortunately, this isn't an either/or question. We can have both.  I use Windows almost every day, for about 15-30 minutes.  The rest of the time, I'm on Unix-based systems, mostly Linux, but some Solaris, BSD, and other Unix-like systems.

Trying out Ubuntu or Fedora or Arch or Mint or SuSE doesn't have a price, just the time spent. Ubuntu has a few different "flavors" which use the same base OS, just different GUIs.  Try them - each, for about a week. See which you prefer. For someone coming from Windows, I'd suggest Ubuntu-Mate (Ma-tah). It will feel comfortable, like XP.  Things will be where you expect. 

I ran different Linux distros inside virtual machines for years before switching to it as my main system. There isn't any hurry. Take your time.  Decide for yourself.  Took me about a year to get comfortable with Linux (it was a long time ago and getting a GUI running was hard back then).  It is like learning to speak a new language, so to become an expert does require effort and commitment.  OTOH, my elderly Mom picked up Lubuntu and used it for years without much help at all. She switched after being hacked.  Of course, I did the install and initial setup for her, plus weekly patching and backups (from 4 states away).

---

### Post by kennster2 on 2016-11-21
Thanks for all the helpful responses guys. A bit of context, I am a relatively low skilled user. I like the points raised about system security especially, as that is especially important to me. I was actually doing some more research and found some more interesting information on this article: [https://www.1and1.com/digitalguide/server/know-how/linux-the-cost-effective-alternative-to-windows/](https://www.1and1.com/digitalguide/server/know-how/linux-the-cost-effective-alternative-to-windows/). 
 
A really crucial point for me that's raised by the article is the excellent cloud support for Linux. If anybody here can compare this aspect, it would be great:)

---

### Post by TheFu on 2016-11-21
1and1 is a server hosting provider - i.e. "cloud."  From that perspective, Linux has about 98% of the market for [non-hobby]("https://en.wikipedia.org/wiki/Usage_share_of_operating_systems#Public_servers_on_the_Internet") websites.  This has very little to do with normal desktop Linux users and doesn't matter to anyone not actually running servers/VPS/containers on someone else's hardware and premise.

Why don't many people choose Windows for their cloud deployment?  For me, it was cost. Running a Windows server was $10/month more than Linux. If you have 1,000 servers, that adds up.  

Plus, it is possible to manage 1,000 Linux/Unix server remotely with F/LOSS tools.  Windows needs a license to do that.  Originally this line said "pretty easy", but managing 1,000 servers isn't easy, but it doesn't have to be hard either. For clarity, I've never done that. Largest count of servers on a single project for me was about 200 servers and they were all a little different, 2-by-2 with active-failover clustering for the application and DB servers. Web front-end servers were load balanced.

If you'd like to run most "cloud services", but on your own equipment, perhaps in a virtual machine, or a VPS you control, then there are lots and lots of F/LOSS projects which provide those things - or use [Sovereign]("https://github.com/sovereign/sovereign").  I've been following sovereign for about a year, but never used it to setup things.  Currently run these "cloudy" services:
* nextcloud - sync file and photo server; centralized RSS reader
* wallabag - Save-it-later clone.
* zimbra - MS-Exchange + much more (IMAPS, SMTP, CalDAV, CardDAV); Zimbra is NOT directly on the internet, however.
* email front-end - need to protect zimbra from outside attacks.
* MyPhotoGallery - nice, perl, online photo gallery (my system of record for photos)
* numerous tiny servers like openvpn, ssh, proxies, blog server and assorted specialized websites for specific non-profit, groups.
* Plex MS - Not using a plex account, but thanks to ssh and proxies, complete access is available worldwide. Great for audio. Transcode to DVD quality for videos.

All of these could be run at a VPS, but if we add up the monthly costs, it doesn't always make sense for a family.  Zimbra doesn't run on a minimal server, for example. It demands 3G of RAM and 2 vCPUs, so that is at least $20/month at Digital Ocean (a reputable VPS provider). All the other services can be run on a single, 512MB RAM VPS for $5/month.  A $50 raspberry Pi v2 can easily handle everything but zimbra, as another option.  For a household, that might be a more cost effective and fast-enough solution, if a home server isn't running 24/7 already.  BTW, power use (Watts) on modern desktop system like a $120 Pentium G3258 (53W), is pretty small. The performance of that pentium compared to any r-pi isn't really comparable. The pentium blows away the r-pi in performance and probably costs $1.50/month in electricity here. Maybe less.

Clouds do have a place, I've just not felt comfortable using them for anything that wasn't going to be shared with the world anyway.

---

### Post by mintmag on 2016-11-22
At the moment I still prefer Windows, but my favorite distro is Mint I'd suggest giving it a try.

---

### Post by mastablasta on 2016-11-22
for desktop user the advantage is speed, flexibility and security (e.g. the option of hardened kernels, anti-sec distros that leave nearly no trace of what was done by who online, often and regular patches, good security tools...)

---

### Post by 7dEfOk4AgU on 2016-11-23
Best way to decide is to look at your computing needs, what and who you need to interact with, what your skill set is  and your budget. If you start looking at it by starting with the OS's you can end up in a mess. Once you have sorted your or needs, make a list and then start ticking the boxes, at the end you will have your decision.

---

### Post by Wadim_Korneev on 2016-11-24
I love Linux, hands down. Windows 7 slows down in a matter of months, which kind of sucks - the reason why I UPGRADED to Ubuntu. So far, I am and I will be loving Ubuntu. Hooray for OpenSource!

---

### Post by richardsdma on 2016-11-24
windows has a lot of advantages. one of the advantage is that you can even install video drivers, made back for windows vista, in windows 10. for my laptop with amd E2-7110, radeon r2, using <16.04, I have no video driver, I mean, good video driver.  I have video driver for Ubuntu 14.04 but wireless does not work. I tried windows 10 on two old laptops, a dell inspiron 1521 and installed video driver from 2010 and on FS amilo li 1705 and installed video driver from 2007. and if someone is telling me that someone from amd or via chrome is working on this drivers to make them compatible with windows 10, I can tell him that is joking.

---

### Post by g33zr on 2016-11-25
I've used Apple/Mac, Windows, and Linux over the years, but I would unlikely return to either Mac or Windows. I love Linux for the same reasons that mastablasta cites above. After much distro-hopping, I'm hesitant to commit to a distro that isn't well supported by a group of dedicated devs, as well as also financially well supported. For this reason, I prefer distros like Ubuntu, Mint, Fedora, and OpenSUSE, but there are others if you're more inclined to experiment and tinker.

---

