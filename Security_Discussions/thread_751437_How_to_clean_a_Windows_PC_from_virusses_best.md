---
title: "How to clean a Windows PC from virusses best?"
date: 2008-04-10
forum: Security Discussions
---

### Post by equity on 2008-04-10
My brother's got an infected IBM thinkpad with Windows XP Pro running on it. F-secure found a lot of virusses and now I am thinking about what Linux live distribution is best for cleaning his computer. Moreover I need to know how to preinstall some programs to the image so that they are available when I boot the live OS.
Please consider that I am new to Linux. I use Ubuntu since Gutsy and have only some basic knowledge on Ubuntu and Unix commands.

Thanks in advance for any suggestion.

---

### Post by HermanAB on 2008-04-10
Nope, the best way to clean a Windows PC is with BartPE, a Windows bootable CD.

---

### Post by netlogic on 2008-04-10
I don't want to jump in and say, "I agree," but best way to fix windows is to use windows. Only way to find that hard to detect rootkit for Windows is when the rookit isn't launched.

---

### Post by kerry_s on 2008-04-11
if it's that bad your best bet is to reinstall windows.

---

### Post by netlogic on 2008-04-11
Sometimes, Windows works better with a clean install.  If there is a possibility a Windows box has a rootkit, just start over or use a live cd.  The files become invisible once the system boots.

---

### Post by equity on 2008-04-11
Come on, man, you do not expect me to reinstall my brother's whole damn system each time when there is some malware on it. Actually I am glad to use Linux now and do not have to care about all that Windows like stuff permanently...

The point is I want a fast and easy way to clean his system without wasting too much time for it, anyway, nowadays virusses are superior to any AV application, so the system would not stay clean very long and I had to reinstall the system every few days.

What about booting a live CD like Ubuntu or Knoppix and preinstall ClamAV on it?

---

### Post by Saint Angeles on 2008-04-11
when i started using windows 98 SE, i had learned that the only way to keep it running smoothly was to reformat every 6 months.

i had no idea that an OS is supposed to be stable and secure.

a fresh install is always good... but if you are gonna go through all that, its easier to install ubuntu.

---

### Post by RJ Hythloday on 2008-04-11
I haven't used anti virus on a windoz box in years, I've also never gone more than about a year on a xp install. 6 months is better, more than that and stuff starts to get mucked up any way. Teach him how to back up important stuff to another hdd or dvds or thumb drives depending on how much he needs to get off the problem os hdd and then have him reinstall while you are there if he gets stuck, either that or get him to try a live cd and switch him over from the dark side.

---

### Post by netlogic on 2008-04-11
> **equity said:**
> Come on, man, you do not expect me to reinstall my brother's whole damn system each time when there is some malware on it. Actually I am glad to use Linux now and do not have to care about all that Windows like stuff permanently...

The point is I want a fast and easy way to clean his system without wasting too much time for it, anyway, nowadays virusses are superior to any AV application, so the system would not stay clean very long and I had to reinstall the system every few days.

What about booting a live CD like Ubuntu or Knoppix and preinstall ClamAV on it? clamav doesn't detect rootkit for windows

make a windows live cd (been around 4yrs)
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

you can automate a fresh install (been around 3 yrs)
[http://www.nliteos.com/](http://www.nliteos.com/)

this live cd has an application called, partimage (works like ghost).
make an image after the clean install and all the apps you use.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by hyper_ch on 2008-04-11
> **equity said:**
> Come on, man, you do not expect me to reinstall my brother's whole damn system each time when there is some malware on it.

you asked for help and help was given... whether you like this or not doesn't matter...

In the end it's your decision what you do... you could also say to your brother: "Either let me install linux and configure it and I will help when problems arise there OR take care of your windows box yourself"

---

### Post by equity on 2008-04-11
> you asked for help and help was given... whether you like this or not doesn't matter...

In the end it's your decision what you do... you could also say to your brother: "Either let me install linux and configure it and I will help when problems arise there OR take care of your windows box yourself"

^^ The point is my brother does not have the faintest idea of computers and he needs lots of native Windows applications. Maybe next year  when I got more anticipation about Unix-like systems and when Ubuntu is more user friendly I will get him closer to it, but at the moment it is senseless.

---

### Post by hyper_ch on 2008-04-11
> **equity said:**
> ^^ The point is my brother does not have the faintest idea of computers and he needs lots of native Windows applications. Maybe next year  when I got more anticipation about Unix-like systems and when Ubuntu is more user friendly I will get him closer to it, but at the moment it is senseless.

So? He can learn about computers...

---

### Post by equity on 2008-04-11
Lol, my brother is jurist and he does not like computers but for work, that's the point...

---

### Post by Rhubarb on 2008-04-11
You can't guarantee that any viruses / malware are removed unless you re-install windows.  This goes no matter what antivirus / firewall / anti-malware prevention programs you use.  Once a virus or malware has infected windows, it can do whatever it likes where ever it likes.

Your best bet is to re-install windows (unless you can convince him to use Ubuntu), set up a separate non-administrator account for day-to-day use, and only use the administrator account when installing software / updating windows.

Or maybe you could install Ubuntu, put windows in a virtual machine in virtualbox, get it all set up, then take a snapshot of the windows vm.
So if / when windows does die / get infected, you can easily revert back to a known good working windows install.

---

### Post by hyper_ch on 2008-04-11
> **equity said:**
> Lol, my brother is jurist

So am I... and as he has studied, he knows that learning is essential and he has proven that he can learn..

---

### Post by astabi on 2008-04-11
Ok, I have supported many pc's for years, at work and at home. I agree that you get better results using a live cd, but an average windows pc user won't want to go through the hassle. 

In your case you may want to for the first time just to make sure it's a clean pc. Once it's cleaned up you have a couple of options, put good protection software on it, I have had good results with Antivir, but recently have used PC Tools Antivirus, along with their Threatfire tool.

I always have spywareblaster installed but you might want to use another spyware scanner such as AVG's antispyware.

These are all free for personal use tools. 

Once this is done then image his drive, now a restore to a clean system, with all the apps and setings he may use will be saved. I use Ultimate boot cd for windows and Driveimage xml to image hard drives.

Anything else I can help you with just ask.

---

### Post by aysiu on 2008-04-11
> **equity said:**
> Come on, man, you do not expect me to reinstall my brother's whole damn system each time when there is some malware on it. Of course we do, because there won't be another time there's malware on it. When you reinstall, make your brother's account a *limited* user account instead of an *administrator* account. That's better than any anti-malware program you could install in terms of preventing infections.

---

### Post by equity on 2008-04-11
> So am I... and as he has studied, he knows that learning is essential and he has proven that he can learn..

^^ Yes, of course, he can learn. And I guess if he wanted, he could learn all that computer stuff right away, but he does not want to. He is just a user.


> Ok, I have supported many pc's for years, at work and at home. I agree that you get better results using a live cd, but an average windows pc user won't want to go through the hassle. 

^^ I think that I will just protect his computer as good as I can and every now and then I will boot some live system in order to watch out for some kind of malware.


> In your case you may want to for the first time just to make sure it's a clean pc. Once it's cleaned up you have a couple of options, put good protection software on it, I have had good results with Antivir, but recently have used PC Tools Antivirus, along with their Threatfire tool.

^^ The point is, current virusses are superior to ANY anti virus program out there, so thinking about what AV program to use is like deciding between being hanged or being shot.
I think I will install antivir or avast.


> I always have spywareblaster installed but you might want to use another spyware scanner such as AVG's antispyware.

I prefer the Spybot S&D at most, especially since it supports watching out for rootkits.


> Once this is done then image his drive, now a restore to a clean system, with all the apps and setings he may use will be saved. I use Ultimate boot cd for windows and Driveimage xml to image hard drives.

^^ Yes, I think creating some backup is a good idea, I will do this. But what do you mean with "Ultimate boot cd for windows"? And why xml? I hate all these MS Office formats.

---

### Post by Wolfmight on 2008-04-11
Use BartPE and then set up the internet on it or have this file avalable:

[http://devbuilds.kaspersky-labs.com/devbuilds/AVPTool/setup_7.0.0.180_11.04.2008_17-38.exe](http://devbuilds.kaspersky-labs.com/devbuilds/AVPTool/setup_7.0.0.180_11.04.2008_17-38.exe)

That's Kaspersky's Stand Alone antivirus scanner.  It's free, and they always update the virus definitions in each build and that's the April 11th build.  It installs and runs perfectly fine in BartPE...I've used it twice.  Cleaned all the viruses off my windows system.

go here for the very latest version:
[http://devbuilds.kaspersky-labs.com/devbuilds/AVPTool/](http://devbuilds.kaspersky-labs.com/devbuilds/AVPTool/)

Good tool, works wonderfully in BartPE.

---

### Post by sub2007 on 2008-04-11
Yeah sounds like he needs some very serious security advice if he gets that many infections.

Even though they're not perfect I'd still install an antivirus, I think of it as a safety net - you shouldn't need one but if you do and it works then you'd be glad you had it. If it's catching a lot though then you need to seriously address your surfing habits and you should always be aware that there could be stuff there that it couldn't catch. I'd go with Antivir, it's a great program (even though it does nag you to buy the full program when you update it) and it always performs well on AV-Comparatives tests.

The best security advice is to use common sense. Keep up to date on Windows Updates. Install Firefox or Opera and tell him to use that for all his surfing if he can. Install a browser add on like WOT or SiteAdvisor which warn about dangerous sites and make sure he has a good firewall installed (like Comodo). And be aware of social engineering installations (warnings about needing to install a codec to play a video which installs a trojan, warnings about needing to buy an antivirus etc).

And remember that XML is an open standard and is (as far as I know) nothing to do with Microsoft. Don't confuse it with OOXML whch is the Microsoft Open Document standard ;)

---

### Post by hyper_ch on 2008-04-11
> **equity said:**
> ^^ Yes, of course, he can learn. And I guess if he wanted, he could learn all that computer stuff right away, but he does not want to. He is just a user.

If he does not want to learn, why should you waste your time?

---

### Post by FakeOutdoorsman on 2008-04-11
Recent similar thread with some good info:
[How do I use Linux to clean up malware on a Windows partition?]("http://ubuntuforums.org/showthread.php?t=720183")

---

### Post by Cope57 on 2008-04-11
[Trend Micro's FREE online virus scanner]("http://housecall.trendmicro.com/")

Clean it online, and you will not need to download anything.
Besides, if the anti-virus installed is corrupt or something, it could bypass some viruses.

---

### Post by netlogic on 2008-04-11
Maybe, someone who still use Windows can explain this to me. Do antivirus and spyware detection software do a key authentication? Two years ago, they weren't. If they don't do it. It wouldn't be hard to change their database updates.

---

### Post by equity on 2008-04-13
> Don't confuse it with OOXML whch is the Microsoft Open Document standard ;)

^^ Ah of yourse... he meant the extensible markup language, I did confuse it with OOXML, although I used XML years ago with HTML...

Okay, I think I will reinstall his system. Yesterday I had some idea: What about installing VirtualBox with some light Linux distribution? He could use this VM only for surfing and his Windows environment would not be infected. He would not have to care what site he visits.

---

### Post by isparkes on 2008-04-13
I know it's probably not the answer to the question, but I'll tell you what I do:

I run a virtual XP inside VirtualBox (admittedly for the few things that I have to use Widows for - mostly working on team Word/Excel/PowerPoint projects for proposal work). When I have finished the work, I go back to a snapshot of a clean install.

If you have lots of RAM and work mostly outside of the virtual machine it's a nice solution.

For someone that works mostly on Windows, I'd recommend the following:

1) Get the user to strictly divide data from programs. Keep backups.
2) After a clean install, maintain an "install image" using Acronis or Ghost or whatever
3) Re-install the programs (but not the data) every n months, maintaining the install image with all the bits that are missing
4) After a clean install, perform a full scan on the data portion, before a rootkit has the possibility to get going again

Long winded, but this is what I ended up doing before I moved over to Linux.

---

### Post by astabi on 2008-04-14
> **equity said:**
> ^^ The point is, current virusses are superior to ANY anti virus program out there, so thinking about what AV program to use is like deciding between being hanged or being shot.
I think I will install antivir or avast.


Threatfire is a proactive antivirus solution, it isn't signature based.


> I prefer the Spybot S&D at most, especially since it supports watching out for rootkits.

Spybot isn't updated often enough, was good in it's day but just doesn't cut it anymore, misses way too much. I wish this wasn't the case, I used to use it myself.


> ^^ Yes, I think creating some backup is a good idea, I will do this. But what do you mean with "Ultimate boot cd for windows"? And why xml? I hate all these MS Office formats.

Ultimate boot cd for windows is a CD you can boot off of to clean your computer, it has a very good disk imaging program that is based on the open forrmat, XML (nothing to do with Microsoft).

---

### Post by Chayak on 2008-04-15
Simple advise... reinstall.  If you let the computer boot using the infected OS then if a kernel level rootkit kicks in no virus scanner will find a thing.  That and you can never really trust it again as I've seen quite a bit of malware patch system drivers.

Antivirus?  It's simple that some will detect what others won't or I've seen a lot that don't show up at all.  ClamAV/Win is probably one of the worst for picking up newer malware

[http://www.virustotal.com/]("http://www.virustotal.com/") is a good site to use as it has a lot of different AV engines to scan with.  I have seen some false positives though.  The only real way to tell if a file is malware is to run it in an isolated VM with analysis tools running or opening the file up with a debugger and picking it apart to see what it's coded to do.

---

### Post by netlogic on 2008-04-16
I don't think we are too far in the future for making open source OSes **BULLET** proof. Of course, virus is very rare in Linux. It is like getting hit by lightning. Once in a while we hear stories, but it is so rare it really happens.  Also, I think rootkit and malware will be a thing of the past for Linux. It won't be long when every linux apps and configuration will be ran by the container mode (jailing) and only apply changes by the request of administrators. This can be done by using a virtual drives and apply changes when changes are reviewed. 100% bullet proof OS will become reality for Linux and companies will be wanting that in the future. I think Linux is coming closer everyday becoming a bullet proof.  I doubt this will happen with Windows due to the close source nature. There is so much hope for Linux. That is why I still use it. I know people waited long time for Linux Desktops to take over. I have a feeling we aren't too distant away from that nature.

---

