---
title: "Pulling the plug on Ubuntu"
date: 2009-03-27
forum: Testimonials &amp; Experiences
---

### Post by alisonnic on 2009-03-27
It is with regret that I have decided to pull the plug on my Ubuntu experiment.

A year ago I put together a machine out of older parts (mostly donated to me by a friend) to use as a platform for experimenting with and learning about Ubuntu.

I was a Unix user and software developer for many years, although in recent years I've used XP almost exclusively. I liked the idea of going back to a robust, stable operating system, and I loved the idea of getting away from paying for an expensive and frequently broken Microsoft OS - and I'd love to stop lining Bill Gates's pockets. 

I love the idea of open source, too. I've used a number of open source applications (Firefox, Thunderbird, Foxit Reader, VLC Player, and more) with great success. Why not try an open source operating system? Ubuntu was growing in market penetration and was clearly the dominant flavor of Linux on the desktop. It seemed the perfect choice.

I initially installed Ubuntu 7.10 in late 2007. This install worked but was fraught with problems, mostly revolving around video card and monitor resolution issues. I eventually resolved these, and was delighted to find that many core applications such as Firefox, Thunderbird, Foxit Reader and VLC Player ported effortlessly from XP to Ubuntu. The Mozilla apps even allowed me to transfer my profiles with data and extensions intact. Terrific!

Also, I loved the elegance of the software repository concept, and the Compiz desktop extensions were not only cute and fun to play with, some were actually useful. I loved various system tools like System Monitor and Disk Usage Analyzer.

However, I found that some of my key applications (two of which involve synchronization with pocket devices, a Treo and an iPod) had no satisfactory equivalents on Ubuntu. Other applications, such as Open Office, had deficiencies in key areas which rendered them less effective than their Windows-based equivalents. The Gimp proved to be far more cumbersome to use than Paint.NET. File synchronization required considerable user intervention (writing a shell script, setting up a cron job, etc.), while on XP, FolderShare/Windows Live Sync just works. Ditto things like backups across a LAN to a Windows server, file sharing in general, and remote desktop connection.

I found that, while some basic functionality in Ubuntu is covered by GUI's, there are many other things that require poking around through an endless thicket of man pages, config files, and endlessly intricate and arcane terminal commands. As a result, everything takes so much more time to figure out on Ubuntu than it does on XP. 

A key element of XP's design philosophy is that it incorporates a much more deeply integrated GUI system, while in Linux the GUI is an optional add-on. The result is that the problem resolution process tends to be far more efficient on XP than on Linux. Also, XP's vast user community seems to have ready answers for just about any question.

Eventually I stopped using the Ubuntu box. Too much trouble, not enough reward.

Then the Windows 7 Beta came along. Why not resurrect the old machine and use it to try both Ubuntu 8.10 and Windows 7? One year on from the 7.10 I'd tried, the new and improved Ubuntu might work better on my old hardware. And maybe some new developments would have resolved some of its application shortfalls.

One way or another, Microsoft is going to eventually force me to stop using XP, so it made sense to try the two most viable alternatives. While I was at it, I could experiment with virtual machines and/or dual booting.

Windows 7 refused to recognize a SATA hard drive on my ancient Asus A7N8X Deluxe motherboard, so I scrounged a PATA drive. After that, the installation went smoothly. I found that I like some of the new features in Windows 7, but a lot of new glitz and a little new functionality weren't enough to persuade me that I just have to have Win7 the moment it's released. XP, like I said, just works.

The Ubuntu 8.10 installation went a little better at first. It detected the SATA drive attached to the A7N8X and installed itself on it slick as a whistle. The restricted nVidia driver was happy as a clam running the old 6800XT, even with a monitor with an oddball 1360x768 resolution. My Trendnet WiFi USB dongle worked. Firefox and Thunderbird sucked up my Windows profiles just as happily as they did on 7.10. I got the Compiz desktop working the way I wanted. I even wrote a little shell script to automatically back up my important files.

About that time my nephew decided to upgrade his ancient A7N8X-based machine, and the Ubuntu box turned out to be the only one that could extract the files from his SATA drive, which had been connected to and formatted by an add-in SATA controller in his machine. Sweet! I was getting more and more impressed.

Then I decided to try VirtualBox. At first I had some hassles. I installed the PUEL version but couldn't find a way to run it. I installed the OSE version and it ran okay. I created an XP virtual machine, which worked fine but couldn't deal with the WiFi USB dongle. I reinstalled the PUEL version and somehow got it to work, and the USB WiFi worked too, although only erratically.

Still, I felt I was making progress, and was actually considering putting this machine into active service. Then I rebooted - the first reboot since the VirtualBox install.

Splat. Compiz desktop effects didn't work any more. In fact, *all *advanced desktop effects were disabled. Ubuntu, for some reason, no longer recognized the nVidia restricted driver for my video card. No amount of fiddling would resurrect it. 

I've posted about this problem in detail, ***including detailed hardware specifications***, here:
[INDENT]
[http://ubuntuforums.org/showthread.php?p=6824461]("http://ubuntuforums.org/showthread.php?p=6824461")
[http://www.nvnews.net/vbulletin/showthread.php?p=1945747]("http://www.nvnews.net/vbulletin/showthread.php?p=1945747")
[http://forum.compiz-fusion.org/showthread.php?t=11059]("http://forum.compiz-fusion.org/showthread.php?t=11059")[/INDENT]

Several people kindly made suggestions, but unfortunately nothing worked. At this point the machine has been sitting for several weeks, problem unresolved. 

Granted, I could live without special desktop effects. The computer still works. But video replay is choppy, and I'm not sure if this is because Ubuntu isn't using the proper nVidia driver or the machine is just too slow. And playing video was one of this computer's key planned roles. (As a side note, an ancient iMac of about the same vintage plays the same videos beautifully.) The bottom line is that this OS install is broken, and I haven't been able to find out how to fix it.

The larger problem is the issue of system administration of this kind of machine. As I mentioned above, problem resolution on Ubuntu, despite its expanded GUI relative to other distros, is still much more time-consuming than on XP, and the vastly larger XP community has much broader experience with its OS. These two factors combine to make XP a much more sure bet for a reasoanbly competent user like me.

I think this is a sigificant part of the reason Ubuntu still hasn't gained much traction on desktops, particularly the home desktop market, where a free OS should be a big draw. It's probably also a big reason why Ubuntu is losing ground on netbooks, despite the fact that pairing cheap hardware with a free OS seems like a match made in heaven.

Objectively, I think I would seem to be an ideal target for Ubuntu. I used to be a software engineer on Unix systems, and I still know how to write shell scripts and use vi. I'm a fairly competent system administrator.

I'm also a serious computer enthusiast. I started haunting computer fairs over a decade ago and I still build computers for fun, for myself and my friends. I've tutored numerous people on how to use their own computers. 

In addition, I'm a real fan of open source software. I love the idea of a community working together to build software that enhances the lives of many of its members - and keeps our money out of the hands of the big, impersonal enterprises. I've had very positive experiences with many other open source products. 

When I began this experiment I really thought I might eventually transition most of my machines to Ubuntu, and I'd have been delighted to do so. I put a great deal of effort into this evaluation, hoping I'd find that I could walk away from Microsoft products for good.

But for now the experiment is over. In a few minutes I'm pulling the plug and dismantling the Ubuntu machine. I'm going to use some of its parts in a new computer with an Intel Core 2 Duo and a 9600GT - and this new machine is going to be running XP. Maybe I'll install the Windows 7 beta in a virtual machine, just for fun, and perhaps Ubuntu as well. 

For the foreseeable future, though, XP is going to be my core operating system. I have a couple of unopened copies in a drawer, and this experiment has made me very glad I've got them. 

Trying Ubuntu and Windows 7 have made me appreciate how good XP really *has become* - and how difficult it is to build a good, stable, broadly usable, community-supported operating system.

---

### Post by Therion on 2009-03-27
Quite the story; thank you for sharing it.

My Two Cent's:  Use what works for you.

---

### Post by jeremyjjbrown on 2009-03-27
I know it feels like you did, but it does not sound like you tired very hard. Add up all of the hours you spent learning Windows, really it's a lot more than you'd think. Then compare it to the 20-100 hrs is ounds like you spent on linux.

Or, read this [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Good luck.

---

### Post by wolfen69 on 2009-03-27
using xp has made me realise just how good ubuntu really is. but to each their own. i have not experienced any of the problems you have, but then again, i build my computers with linux in mind, and don't just blindly throw something together and hope it works. 

my xp experiment was over 2 years ago.

---

### Post by betrunkenaffe on 2009-03-27
So let me sum this up:

You installed virtual box, a known to be buggy program, it broke your machine and you threw up your arms and decided to go back to XP. Glad we're not talking unreasonable expectations or illogical thinking. Just because you've used Unix (or even if you have built your own OS) doesn't mean you in any way came to the right conclusion.

I just finished fixing an XP machine in which the installation of a remote desktop program broke the firewall software to the point that I couldn't uninstall and reinstall it. I had to reimage the entire machine from the last backup (which was not done recent enough for my tastes), reinstall the updates that were missing and reinstall the printer drivers that were also missing. I don't blame XP for this, I blame that software for being a POS.

I'd recommend reinstalling Ubuntu as a dual boot, get it working and stop fiddling with trying to get Windows programs to run in a non-native environment for them. Keep XP for the Windows programs and keep Ubuntu for the usability of it.

---

### Post by Riffer on 2009-03-27
Read one of your other threads.  The trick with re-installing nVidia drivers is to completely remove all the modules (not just disabling the driver) before re-installing.  Envy is a very good utility for removing and installing nVidia drivers.  Also nVidia is on a real charge these days with their Linux drivers and have vastly improved.  I too used the 177 driver and it was very buggy, now I use the 180 series (180.11 I think) and its so much better.

I tried virtual box and it never really worked for me, try VMWare.  There is also there is a few other virtulization software that might work better for you.

I know you are probably gone and won't be reading this, but on ever OS I've had problems (trying to network a win2000 machine to XP = grrrr).  I have found that the problems are less on Ubuntu/Linux then Windows.

---

### Post by MaxCarnage on 2009-03-27
I run Windows 7 on a VirtualBox machine on my Ubuntu 8.10 desktop, and everything works fine. I really don't care much for Windows, but I do care for iTunes and a few other pieces of software that there really is no Linux equivalent for so I keep a copy of Windows around for that. I love being able to load a saved state for Windows in Ubuntu rather than having to reboot into a different partition.

Anyway, when I tried installing VirtualBox the first time, I just used the package in Synaptic, and it was a chore. Nothing worked, some necessary packages were missing and I couldn't install them, and it was a pain. The next time I tried the non-free version:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and it worked perfectly.

A lot of times some of these problems seem insurmountable, but with persistence and an open mind you can almost always get it fixed. I thought your observation about finding a large XP community waiting to answer your questions ironic, since the Linux community is often one of the selling points I use to get people to switch. Frankly, though, with all the Windows-targeting viruses and malware and what-not, I'd just as soon the Linux community remained on the fringe and my computers stayed nice and safe. ;)

---

### Post by Tamlynmac on 2009-03-28
> wolfen69
using xp has made me realise just how good ubuntu really is. but to each their own. i have not experienced any of the problems you have, but then again, i build my computers with linux in mind, and don't just blindly throw something together and hope it works. 

my xp experiment was over 2 years ago. 	

Perfect response.

This so called experiment was obviously a joke. No specific information just a bunch of used parts (probably from old Windows machines) thrown together to make a comparison between a Linux based OS and of course Windows. Hmmmm let me think a Windows system that failed to provide Ubuntu with a compatible environment and the results were "unexpected". :)

This so called experiment doesn't even qualify for qualitative much less quantitative. Yet somehow the OP expects the reader to ignore all that and only focus on the erroneous results. Makes perfect sense to me.

Don't know about you, but I'm almost excited by the concept that 9.04 will be released soon and the complaints will again be directed at how the forced upgrade broken someones system.
:lolflag:

---

### Post by AlesUbu123 on 2009-03-28
Thank you for your balanced report. Like everything Linux is not perfect. I can't wait for more hardware and software to become linux compatible, and for Ubuntu/linux to become a bit more user-friendly.

---

### Post by 3rdalbum on 2009-03-28
"Deeply-integrated GUI means easier problem resolution"? Hmmm... not quite. If you visit the Microsoft Knowledgebase website and check out the solutions to problems with Windows XP, the first thing you'll be told to do is run a very long command at the MS-DOS prompt.

---

### Post by ugm6hr on 2009-03-28
Never mind.

XP does have its place on some computers.  If you've paid for it already, it is your prerogative to use it.

---

### Post by alisonnic on 2009-03-31
> **Riffer said:**
> Read one of your other threads.  The trick with re-installing nVidia drivers is to completely remove all the modules (not just disabling the driver) before re-installing.  Envy is a very good utility for removing and installing nVidia drivers.  Also nVidia is on a real charge these days with their Linux drivers and have vastly improved.  I too used the 177 driver and it was very buggy, now I use the 180 series (180.11 I think) and its so much better.

I tried virtual box and it never really worked for me, try VMWare.  There is also there is a few other virtulization software that might work better for you.

I know you are probably gone and won't be reading this, but on ever OS I've had problems (trying to network a win2000 machine to XP = grrrr).  I have found that the problems are less on Ubuntu/Linux then Windows.

Riffer, thank you so much for this helpful suggestion. It's too late to help with the problem I had, because I've rebuilt the machine with new hardware and XP, but I will definitely keep Envy and VMWare in mind the next time I start tinkering with Ubuntu.

It's great to know that nVidia's 180.xx drivers are so much better than the version I was using. It's too bad these new drivers (and Envy) weren't available under the Restricted Driver GUI when I was struggling with this problem.

Also, thanks to everyone else who made positive or helpful posts, both in this thread and in the problem threads I used to try to track down a solution.

---

### Post by alisonnic on 2009-03-31
> **jeremyjjbrown said:**
> I know it feels like you did, but it does not sound like you tired very hard. Add up all of the hours you spent learning Windows, really it's a lot more than you'd think. Then compare it to the 20-100 hrs is ounds like you spent on linux.

Or, read this [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Good luck.

Jeremy,

Thanks for the link to this page. I'd scanned it already, but after reading your post I read it in more depth.

I think the author of the article stated the root of my problem in a nutshell:

[INDENT][FONT="Times New Roman"][SIZE="3"]"Linux is not interested in market share. Linux does not have customers. Linux does not have shareholders, or a responsibility to the bottom line. Linux was not created to make money. Linux does not have the goal of being the most popular and widespread OS on the planet.

"All the Linux community wants is to create a really good, fully-featured, free operating system. If that results in Linux becoming a hugely popular OS, then that's great. If that results in Linux having the most intuitive, user-friendly interface ever created, then that's great. If that results in Linux becoming the basis of a multi-billion dollar industry, then that's great.

"It's great, but it's not the point. The point is to make Linux the best OS that the community is capable of making. Not for other people: For itself. The oh-so-common threats of "*Linux will never take over the desktop unless it does such-and-such*" are simply irrelevant: The Linux community isn't *trying *to take over the desktop. They really don't care if it gets good enough to make it onto *your *desktop, so long as it stays good enough to remain on *theirs.*"[/SIZE][/FONT][/INDENT]

I'm afraid I may have misinterpreted certain recent events in the commercial sector. Things like the decision of some mainstream computer retailers to begin supplying computers with Linux installed, including not only netbooks but desktops and laptops. Articles cheering the growth of Linux penetration of the desktop market to 1% or maybe even 2%. The development of Linux flavors like Ubuntu which target the desktop user. The emergence of companies providing support services to Linux users.

I also thought that Microsoft's Vista disaster created an opening for Linux (and open source software in general) to gain a large number of converts and perhaps actually become a significant threat to Microsoft in its principle market.

The optimism these events inspired in me was behind my decision to attempt this second go-around with Ubuntu.

Perhaps my optimism was ill-founded. Was the author of this article correct? Does the Linux community *really *not care whether more Linux users come on board? 

I don't know. Many of the responses to this thread suggest that is in fact the case. If that's true, I'm disappointed. And I'm sorry I wasted your time.

But some of the responses here suggest that there *are *people in the Linux community who care about the growth of this community. I find that heartening, and I hope that it's an indicator that the open source community will eventually be able to evolve an operating system that's somewhere near as broadly successful as Firefox has become.

I would like nothing better to see Linux, and other open source software, become the standard - and to be able to join a mass exodus from the greedy clutches of those suits in Redmond.

---

### Post by cariboo on 2009-03-31
If you are trying Linux because you don't like Microsoft, you are trying it for the wrong reason. I started using Linux because at the time there where things that I couldn't do in Windows. I don't dislike Microsoft, I use their products every day, right now I have a Microsoft Ergonomic keyboard sitting in my lap and a Microsoft Arc mouse in my hand. I have XPPro, Vista and Windows 7 in vms. The OS' don't get used every day or even every week, but they sure do come in handy when answering customer questions over the phone.

Use Linux because you want, to not because you dislike Microsoft.

Jim

---

### Post by inobe on 2009-03-31
yes use what you want' it's no big deal, it's the power of choice and let no one convince you otherwise......

---

### Post by ugm6hr on 2009-03-31
> **alisonnic said:**
> Perhaps my optimism was ill-founded. Was the author of this article correct? Does the Linux community *really *not care whether more Linux users come on board? 

The Linux community is open to anyone and everyone.

A large proportion of FOSS developers design software for themselves.  Hence the "poor" user interfaces; if you designed the software yourself, you'd know how to use it.  The good thing is that you get software tailored for specific purposes, designed by users rather than corporate programmers.

However, there are an equally significant number of corporate FOSS developers, in addition to corporate sponsored Linux distributions.  The corporations obviously have a vested interest in promotion of their own applications, even to users who do not pay for the software directly.

So that quote is partly true.

Canonical are hopeful that their software will challenge any other available desktop OS out there.  In some people's eyes, that is already a true statement; obviously in your opinion, they have more work to do.

---

### Post by Tamlynmac on 2009-03-31
> cariboo907
If you are trying Linux because you don't like Microsoft, you are trying it for the wrong reason. I started using Linux because at the time there where things that I couldn't do in Windows. I don't dislike Microsoft, I use their products every day, right now I have a Microsoft Ergonomic keyboard sitting in my lap and a Microsoft Arc mouse in my hand. I have XPPro, Vista and Windows 7 in vms. The OS' don't get used every day or even every week, but they sure do come in handy when answering customer questions over the phone.

Use Linux because you want, to not because you dislike Microsoft.

Jim 	


I suspect, many wind up here because they are sick of Microsoft. They go searching for an alternative and some may try Ubuntu. Reasons for switching to Ubuntu may vary, but I often wonder how many switch precisely for that motive. I doubt few new users that purchase their first computer (probably with Windows installed) immediately switch OS's.

Once they are indoctrinated to Ubuntu, I believe the motive for continued use may change and become more philosophical.

Just my $0.02

---

### Post by zenithdave on 2009-03-31
Totally understand about the Desktop breaking, it happened to me on a nvidea 6100 on-board graphics card, nothing i could do or read about helped and overwhelming frustration took over and i came here and denounced Ubuntu in a frothy frenzy, i was quite rude and country boy like, unlike your good original post (well restrained)

I gave up on it left it a bit and brought a eee900 which had a nasty linux preinstalled although having linux on it was why the buying impulse got me :D

I installed Hardy straight away and all video problems had gone and i was now seeing how elegant it can be :D only the wireless did my head right in then, for months!! that was down to me not reading the release notes!  *ashamed

So really the problems were down to hardware and my lack of knowledge not saying your the same way with knowledge :D

I have a 9500 graphics card now and its a delight to use compiz :D

Even if you leave it now something will call you back ;) it happens

---

### Post by solwic on 2009-03-31
> **alisonnic said:**
> I liked the idea of going back to a robust, stable operating system, and I loved the idea of getting away from paying for an expensive and frequently broken Microsoft OS - and I'd love to stop lining Bill Gates's pockets. 


There is a difference between switching *to* Linux, and switching *from* Microsoft.  Granted, I like the idea that old Gates isn't burning me anymore, but that's not why I use Linux.  That's just a side effect.  

In any case, good luck to you.  And as somebody has probably already said here, use whatever works.  Ubuntu/Linux are useless if they don't do what you need them to do.  :)

Good luck.

---

### Post by neodaemon on 2009-04-03
I agree with Tamlynmac's point of view. I am one of those who switched to Linux because of my frustration with Micro$oft. The list is a mile long, but at the top is ridiculous licensing costs & restrictions, vulnerabilities, and lack of "open" community.

I'm a 17 year veteran SE. I'm heavily Microsoft certified and still use M$ at home on occasion. I switched to Linux as my main OS BECAUSE of frustration with M$, but I STAYED with M$ because of the security, stability, variety, scalability, and "open" community. I think in the end it doesn't matter why you switch, but why you stay.

I think business and private sector penetration is important to the FOSS community because it pressures commercial hardware/software companies to tone down the greed and bloat. That benefits just about everyone.

---

