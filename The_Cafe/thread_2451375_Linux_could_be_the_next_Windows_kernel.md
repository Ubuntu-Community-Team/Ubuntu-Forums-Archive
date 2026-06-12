---
title: "Linux could be the next Windows kernel"
date: 2020-10-03
forum: The Cafe
---

### Post by germanix2 on 2020-10-03
[COLOR=#000000][FONT=Arial]**&#8203;**Windows running on Linux is the future[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This is my translation of an article written in the german language that first appeared on  ZDNet.de on Friday, Oktober 2, 2020 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] [https://www.zdnet.de/88383098/windows-auf-linux-ist-die-](https://www.zdnet.de/88383098/windows-auf-linux-ist-die-)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zukunft/[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]There is speculation that Microsoft is relying more on Linux. In the end, Linux could be the Windows kernel.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]A few days ago, Eric S. Raymond (ESR), developer and writer, announced that we were approaching the final phase of the desktop wars. The winner? Windows on Linux. Raymond argues that “WSL (Windows Subsystem for Linux) allows unmodified Linux binaries to[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]run on Windows 10. No emulation, no shim layer, they are simply loaded and executed ”. In fact, you can now run standard Linux programs on WSL2 without any problems.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]That's because Linux is well on its way to becoming a premium offering on the Windows desktop. Several Linux distributions, such as Ubuntu, Red Hat Fedora and SUSE Linux Enterprise Desktop (SLED), now run on WSL2 without any problems. That's because[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Microsoft replaced its WSL1 translation layer, which converted Linux kernel calls to[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Windows calls, with the WSL2. With WSL2, Microsoft's own Linux kernel runs on a thin version of the Hyper-V hypervisor.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]That is not all. With the current Windows 10 Insider Preview Build 20211, you can now via Windows File Manager and PowerShell access Linux file systems such as ext4. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In addition,make it easy for Microsoft developers to run Linux graphical applications on Windows.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Raymond points out that others are also working to make Windows applications easier to run on Linux. Specifically, he points to Valve Proton, a wine-based compatibility layer designed for running Windows Steam games on Linux. "Games are the most demanding stress test for a Windows emulation layer, much more so than business software". If you can run[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Windows games on Linux, why not run Windows business applications too?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]He also correctly noted that Microsoft no longer depends on Windows for its cash flow, but on its Azure cloud offering. Where by the way, more Linux instances are running as on Windows Server instances.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If that's the case, why should Microsoft continue to invest money in the notorious, troubled Windows kernel when it can freely use the Linux kernel? Good question. He thinks[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Microsoft can figure it out and switch to Linux.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Microsoft wants you to use replace your existing PC-based software, like Office 2019, with software-as-a-service (SaaS) programs like Office 365. Microsoft also encourages you to switch your voice, video, chat, and text communications to Microsoft's Azure Communication Services (ACS) even if you are not using Teams.[/FONT][/COLOR]

---

### Post by trpted on 2020-10-03
In English, you could see [http://esr.ibiblio.org/?p=8764](http://esr.ibiblio.org/?p=8764)

---

### Post by grahammechanical on 2020-10-03
And no license fees to pay on all that FOSS code. What might have been if Microsoft had funded development of a Linux smartphone OS instead of trying to replicate Windows on the smartphone.

This approach is a universe away from the previous Microsoft policy of buying and burying rival software.

Regards

---

### Post by TheFu on 2020-10-03
Not likely.

A few years ago someone tried to start a rumor that MSFT was buying Canonical too.

More FUD from msft.  Get used to that if you haven't already. They've been doing it since the 1980s.

---

### Post by webaake on 2020-10-03
Yes, a big yawn is all it's worth.

---

### Post by mastablasta on 2020-10-05
also usually when there are issues, it's not the NT kernel that is a problem. so changing a kernel won't help. and even if they did change the kernel, that doesn't mean applications would run on linux. Android uses a linux kernel and you can't run the apps native on linux desktop.

the only issue i see is that MS continues to make money form the OS, but at the same time their customer support level is dropping (poor testing, bad updates...). if it continues to drop and become critically low, then people might look at alternatives. ever since the dropped a bunch of testers, bug hunters & maintenance team from payroll things are going downhill (and OS looked quite promising when it started out).

nowadays they earn more money with other software & hardware (gaming...). they do much better job with their apps, but still not as good as they could be. office came a long way in it's development and adding various apps and features to it made it a lot better than it was back in 2003 (which is kind of where OO-->LO got stuck and not just with the user interface). 

they could decide to drop the OS maintenance all together and focus on the programs, but on the other hand OS provides them control over their "ecosystem". so even if it doesn't make as much money as it did before, it still bring in the money and some other benefits. 

i use business version (at work) so i am behind the latest features and upgrade and only read about them. i have to say as OS it is quite OK. the biggest issues are actually updates system (they take way too long) and data reporting to MS. this should be off completely. other than that the ride with this OS was uneventful. just like my Win XP experience (i got it after SP1). so mine is LTS (maybe even extended support) version and even so updates get tested and approved by internal IT team. but i can see that many users of home version have a different experience. updates pushed at wrong time, updates deleting files, updates causing boot loop. MS made home users beta tester after firing it's own team. might not be good in the long term.

---

### Post by Shibblet on 2020-10-07
> **mastablasta said:**
> the only issue i see is that MS continues to make money form the OS, but at the same time their customer support level is dropping (poor testing, bad updates...). if it continues to drop and become critically low, then people might look at alternatives. ever since the dropped a bunch of testers, bug hunters & maintenance team from payroll things are going downhill (and OS looked quite promising when it started out).

I like the way you worded that!  MS makes money "from" the OS.  It's been shown now that the licensing fees barely cover the cost of production.  Microsoft is now making money "from" the OS in the Microsoft Store, support, and other OS "related" things.  This might be why they wanted to push Windows 10 (S), and it ended up falling flat on it's face.

> **mastablasta said:**
> nowadays they earn more money with other software & hardware (gaming...). they do much better job with their apps, but still not as good as they could be. office came a long way in it's development and adding various apps and features to it made it a lot better than it was back in 2003 (which is kind of where OO-->LO got stuck and not just with the user interface). 

they could decide to drop the OS maintenance all together and focus on the programs, but on the other hand OS provides them control over their "ecosystem". so even if it doesn't make as much money as it did before, it still bring in the money and some other benefits.

You know... I am not sure why they don't.  They gave Windows 10 away to anyone who had a licensed version of 7 or 8... (I even heard of some people getting upgrades from XP)  If MS gave Windows 10 away for free, to the home user, they could essentially get back the market-share they had with Windows XP.

> **mastablasta said:**
> i use business version (at work) so i am behind the latest features and upgrade and only read about them. i have to say as OS it is quite OK. the biggest issues are actually updates system (they take way too long) and data reporting to MS. this should be off completely. other than that the ride with this OS was uneventful. just like my Win XP experience (i got it after SP1). so mine is LTS (maybe even extended support) version and even so updates get tested and approved by internal IT team. but i can see that many users of home version have a different experience. updates pushed at wrong time, updates deleting files, updates causing boot loop. MS made home users beta tester after firing it's own team. might not be good in the long term.

I agree with you.  Windows 10 is not a bad operating system.  It just suffers from a few under the surface problems.  It's kind of like dating a supermodel with insecurity issues.  She's beautiful, for sure, but every time you leave the house she thinks you're cheating on her...  I don't know... bad analogy maybe.

The problems I have with Windows 10 are the overwhelming privacy issues, CPU usage due to those issues, and the forced updates.  Windows is tracking everything you do.  And all that stuff is sent to Microsoft to target advertising to your advertising ID.  Microsoft has at least been transparent about this.

The CPU usage kind of irks me off, because they are using my CPU cycles to process this data before it's sent out...  So, not only do you want my data, but you want me package it up and send it to you as well?  Nope, sorry, forget that noise.

---

### Post by CelticWarrior on 2020-10-07
> [COLOR=#000000]Windows is tracking everything you do. And all that stuff is sent to Microsoft to target advertising to your advertising ID. Microsoft has at least been transparent about this.[/COLOR]
Yes, "at least" and "at last"... Previous Windows versions did the same. Windows 10 *at last* is more transparent about it, *at least *in its EULA.

But again nothing that is being discussed here would be solved with Windows running on top of the Linux kernel. And again it baffles me how so smart people get things so wrong and by smart people I mean the commentators here, not the dumb Youtuber/blogger at the core of this idiotic rumor.

Linux isn't going away, not anytime soon. Its market share on servers and mobile devices is stronger than ever. The issue is and always was "desktop Linux" and on desktop Microsoft reigns supreme and even [increasing its *de facto* monopoly]("https://www.omgubuntu.co.uk/2020/10/linux-marketshare-in-september-2020"). And Microsoft couldn't care less about the end-user, that was never their target and now even less so. Why would they spend millions recreating Windows as a better product - assuming it would be better if Linux based, something I'm not entirely sure would be - just for you? It works good enough for their bottom line and that's what matters, certainly NOT your "feelings".

Actually I'm afraid of the opposite situation: WSL2 running on a true Linux kernel will take away the one and only reason to dual-boot for those occasional developers that mainly run Windows for personal and professional use. WSL2 now enables them to do all their work in Windows.

And all of you giving credit to this rumor need to stop and understand the world is very different than it was 20 years ago. Namely the desktop market doesn't matter nearly as much as it did in the past. Linux with a healthy marketshare in the desktop could have happened but it didn't and now it never will because it no longer matters.

---

