---
title: "[SOLVED] Still no luck with some things...."
date: 2008-10-16
forum: The Cafe
---

### Post by SkittleLinux18 on 2008-10-16
There are some issues I have had with Linux since the beginning of my usage with it. I have mentioned most of them before and have gone to considerable lengths to resolve them, but all to no avail.

I don't know if it's memory leaks, faulty distro coding, or just plain bad luck; but my taskbar/kicker still reloads itself every morning at 4 am. All of my running apps in the system tray fail to redock and it's a real pain trying to redock them. I went through the PCLOS forums, Ubuntu forums, and Google trying to hunt down a solution. The only thing I came close to figuring out is that it may have to do with memory leaks. But that's not even for certain.

Memory leaks. ahhh... I need someone to clarify something to me. Is it true that all Linux Distros interpret RAM and Virtual Memory differently than MAC and Windows do?? Because I read [here]("http://en.wikipedia.org/wiki/Memory_leak") and [here]("http://www.linuxforums.org/forum/linux-kernel/70701-linux-operating-system-memory-leaks.html") that Linux purposefully uses 90% of the system RAM because it does read it differently. I also learned that this is the reason why programs like Firefox and Opera and OpenOffice will slow down and temporarily lock up, causing the window to grey out. So why is Linux considered such a lighter weight OS compared to say Vista when it can't even read the RAM correctly??

Speaking of Firefox. 3.0 is sluggish on Linux. But the package managers don't have the lastest version available. So I manually updated to 3.0.3 on my computer. Well..... now Flash Player isn't installed on 3.0.3. I tried reinstalling it in synaptic, but 3.0.3 doesn't have flash player on it yet. So either I use the broken 3.0 to have flash, or I use the better 3.0.3 without flash because I can't get Flash to install to the updated version of Firefox. I know flash isn't good, and I do have the blocker plugin enabled. But I need it for sites like [NHL.com - The National Hockey League](http://www.nhl.com), [www.homestarrunner.com](www.homestarrunner.com), [www.mlb.com](www.mlb.com), ect, ect, ect. 

*takes deep breathe*

Ok, iRiver. This is really annoying. BigTomRodney, heads up here because you where the one helping me with this before. I installed the libIFP packages to use iRiver manager with my iRiver mp3 player. Well, it didn't work. So I did some research. Turns out that my specific model: IFP-890 is incompatible with not only Linux, but the Linux packages used for iRiver. I ran a USB ls in a terminal and sure enough, Linux is reading my mp3 player when it is plugged in. Talk about some real sh***y luck for me.

Overall, it is amazing how much Linux users are at the mercy of programmers to keep up with the latest stuff. Especially when the entire OS slows down and is forced to close just because Amarok, Firefox, and Pidgin are open simultaneously. Opera is probably the worse. I can't go three pages of browsing without that browser freezing, greying out, and locking up my OS. I have tried and tried and do not understand why Linux is so difficult to understand and work with. 

Wine.... I'm not even going to go there. I will not be able to control my language. 

To end off, I remember a conversation I was having back in June. Me and some of my friends were discussing viruses. I said, "Convert to Linux and you'll never get another virus ever again."

My friend said, "Convert to Linux and you'll never do *anything* ever again."

.... sad day.:confused:

---

### Post by Pogeymanz on 2008-10-16
I'm sorry to hear about your bad luck. It may just be that Linux is not in the stars for your hardware. Have you tried other Distros?

I've never had freezes or anything like that. I can assure you that I've run Firefox, pidgin, openoffice, opera and deluge all simultaneously and had no lag. With just 1GB RAM.

With regard to the memory thing. Linux actually handles memory better than Windows. Linux does not "read" it differently. When you close a program in Linux, part will stay in RAM (if there is enough space), so that when you open the program again later, it will load faster. Over time, it will seem like you are using 90% of your RAM even when nothing is open. This is an ADVANTAGE, because unused RAM is wasted RAM. This will NOT slow down any new programs from  loading, because the "cached" RAM will just be overwritten if it is needed.

So, again, I'm sorry for your bad luck. That 4AM thing is weird. Have you tried using a different taskbar? If it happens with all taskbars, it may be a problem with one of the trayed apps or your hardware may be rebooting at 4AM.

Linux is worth it for some people, but if you can't even get your browser to function, it's probably not for this computer. Maybe try again later, on different hardware.

EDIT: Your flash problem is easily solved. Uninstall the flash plugin via synaptic. Then goto adobe.com and download the latest flashplayer from them. Follow the instructions they give you. Done.

---

### Post by Bakon Jarser on 2008-10-16
Firefox 3.0.3 is definitely in the repos.  In fact Ubuntu had the update before it was officialy released.  Flash 10 was just released.  I'm still on the RC2 version but it works great.  One solution for your mp3 player would be to load [Rockbox]("http://www.rockbox.org/") on it.  Also here's a link to someone who got your mp3 player to work Ubuntu 7.04
[http://koorenneef.nl/node/35](http://koorenneef.nl/node/35)
Ubuntu doesn't 'use' 90% of the RAM.  One of the links you provided had a link to a page with good info.  That page seemed to be down but here is the cached page from gooogle. 
[http://64.233.169.104/search?q=cache:NTbJIE_J-5kJ:gentoo-wiki.com/FAQ_Linux_Memory_Management+Linux+Memory+Management&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a](http://64.233.169.104/search?q=cache:NTbJIE_J-5kJ:gentoo-wiki.com/FAQ_Linux_Memory_Management+Linux+Memory+Management&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a)
You haven't stated any system specs.  If your machine is slow or doesn't have a lot of RAM then maybe a more lightweight version of linux like Xubuntu would solve some of your problems.  Also, the latest version of Ubuntu is coming out in about 2 weeks.  Maybe a clean install would solve some of your problems.  The panel problem you describe sounds like it may be a gnome bug.  Ubuntu 8.10 will be using a new version of gnome.  It is also possible that your RAM itself is the problem.  Pop in the live cd and try running the memory test.

---

### Post by SkittleLinux18 on 2008-10-16
> **Bakon Jarser said:**
> Firefox 3.0.3 is definitely in the repos.  In fact Ubuntu had the update before it was officialy released.  Flash 10 was just released.  I'm still on the RC2 version but it works great.  One solution for your mp3 player would be to load [Rockbox]("http://www.rockbox.org/") on it.  Also here's a link to someone who got your mp3 player to work Ubuntu 7.04
[http://koorenneef.nl/node/35](http://koorenneef.nl/node/35)
Ubuntu doesn't 'use' 90% of the RAM.  One of the links you provided had a link to a page with good info.  That page seemed to be down but here is the cached page from gooogle. 
[http://64.233.169.104/search?q=cache:NTbJIE_J-5kJ:gentoo-wiki.com/FAQ_Linux_Memory_Management+Linux+Memory+Management&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a](http://64.233.169.104/search?q=cache:NTbJIE_J-5kJ:gentoo-wiki.com/FAQ_Linux_Memory_Management+Linux+Memory+Management&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a)
You haven't stated any system specs.  If your machine is slow or doesn't have a lot of RAM then maybe a more lightweight version of linux like Xubuntu would solve some of your problems.  Also, the latest version of Ubuntu is coming out in about 2 weeks.  Maybe a clean install would solve some of your problems.  The panel problem you describe sounds like it may be a gnome bug.  Ubuntu 8.10 will be using a new version of gnome.  It is also possible that your RAM itself is the problem.  Pop in the live cd and try running the memory test.

I am a huge KDE fan. So tell me, how does Kubuntu 8.10 Intrepid Box compare to Ubuntu??

---

### Post by cardinals_fan on 2008-10-16
> **SkittleLinux18 said:**
> 
Wine.... I'm not even going to go there. I will not be able to control my language. 

WINE shouldn't work.  If it does, consider it a fluke.

---

### Post by SkittleLinux18 on 2008-10-16
> **Pogeymanz said:**
> I'm sorry to hear about your bad luck. It may just be that Linux is not in the stars for your hardware. Have you tried other Distros?

I've never had freezes or anything like that. I can assure you that I've run Firefox, pidgin, openoffice, opera and deluge all simultaneously and had no lag. With just 1GB RAM.

With regard to the memory thing. Linux actually handles memory better than Windows. Linux does not "read" it differently. When you close a program in Linux, part will stay in RAM (if there is enough space), so that when you open the program again later, it will load faster. Over time, it will seem like you are using 90% of your RAM even when nothing is open. This is an ADVANTAGE, because unused RAM is wasted RAM. This will NOT slow down any new programs from  loading, because the "cached" RAM will just be overwritten if it is needed.

So, again, I'm sorry for your bad luck. That 4AM thing is weird. Have you tried using a different taskbar? If it happens with all taskbars, it may be a problem with one of the trayed apps or your hardware may be rebooting at 4AM.

Linux is worth it for some people, but if you can't even get your browser to function, it's probably not for this computer. Maybe try again later, on different hardware.

EDIT: Your flash problem is easily solved. Uninstall the flash plugin via synaptic. Then goto adobe.com and download the latest flashplayer from them. Follow the instructions they give you. Done.

Sweet, I'll try that with Flash. Thanks man. I forgot to mention that I am using PCLinuxOS MiniMe 2008. I've only had the taskbar problem with this Distro. The reason I posted in Ubuntu Forums is because I am seriously considering Kubuntu 8.10. It may be hardware, but I prefer to try another distro first. idk... working it out in my mind and on other forums. Thanks for all your replies.

---

### Post by Bakon Jarser on 2008-10-16
Looks like they are switching to kde 4 which is still in its infancy and not feature complete.  Many KDE fans still find KDE 4 unusable because it is missing features that they are used to in KDE 3.x.  I guess the best way to find out if it's good enough for you is to download a live cd and try it out.

---

### Post by SkittleLinux18 on 2008-10-16
> **cardinals_fan said:**
> WINE shouldn't work.  If it does, consider it a fluke.

That is actually the most useful info anyone has ever given me on WINE. Thanks dude. I'm definitely done with it.

---

### Post by SunnyRabbiera on 2008-10-16
> **SkittleLinux18 said:**
> I am a huge KDE fan. So tell me, how does Kubuntu 8.10 Intrepid Box compare to Ubuntu??

Well if you are using KDE3 now say goodbye to it next version as KDE4 will take over.

---

### Post by Bakon Jarser on 2008-10-16
> **cardinals_fan said:**
> WINE shouldn't work.  If it does, consider it a fluke.

Wine works great with simple apps.  The more complicated the program the less likely it is to work with wine.  That's because complicated programs often take advantage of obscure parts of the windows API that aren't implemented yet.

---

### Post by SkittleLinux18 on 2008-10-16
> **Bakon Jarser said:**
> Looks like they are switching to kde 4 which is still in its infancy and not feature complete.  Many KDE fans still find KDE 4 unusable because it is missing features that they are used to in KDE 3.x.  I guess the best way to find out if it's good enough for you is to download a live cd and try it out.

Maybe I'll just use Kubuntu 8.04 then since they still have a KDE 3.x version. I still would like to know if anyone can tell me if it is a good idea?? if Kubuntu is as reputable as Ubuntu. Sorry, I am just big on KDE.

---

### Post by earthpigg on 2008-10-16
you may want to consider linux mint. it does flash out of the box.

read [this ]("http://linuxmint.com/forum/viewtopic.php?f=90&t=12159")thread about where it came from and what/how it is based on Ubuntu.

[http://linuxmint.com/]("http://linuxmint.com/")

they do not have nearly as active a forum community as ubuntu, and FOSS purists do not approve of it.

---

### Post by SkittleLinux18 on 2008-10-16
> **Bakon Jarser said:**
> Wine works great with simple apps.  The more complicated the program the less likely it is to work with wine.  That's because complicated programs often take advantage of obscure parts of the windows API that aren't implemented yet.

It's funny because StarCraft worked great on Wine, but MSN messenger and Windows Media Player worked horribly. ??? I hate WINE. it's not going on my next install.

---

### Post by SkittleLinux18 on 2008-10-16
> **earthpigg said:**
> you may want to consider linux mint. it does flash out of the box.

read [this ]("http://linuxmint.com/forum/viewtopic.php?f=90&t=12159")thread about where it came from and what/how it is based on Ubuntu.

[http://linuxmint.com/]("http://linuxmint.com/")

they do not have nearly as active a forum community as ubuntu, and FOSS purists do not approve of it.

i actually used to have Mint 4.0-KDE on this very computer and it worked very, very well. Maybe that is the solution then. It does help to talk this all out though. So thanks everybody!

---

### Post by SkittleLinux18 on 2008-10-16
Ok, I am thinking either Mint-5.0-KDE or Kubuntu 8.04 (KDE 3.x edition). Any suggestions/input/preferences/experiences anyone has to offer?? With everything I have to do once I reinstall Linux (probably 30+ hours), I only want to do this once! So please, anything will be much appreciated.

---

### Post by Bakon Jarser on 2008-10-16
Download both of them and try out the live cd for a little while to see which one you like better.  When you get your system the way you want it make a backup with remastersys.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by wolfen69 on 2008-10-17
> **SkittleLinux18 said:**
> 
My friend said, "Convert to Linux and you'll never do *anything* ever again."

.... sad day.:confused:

i have news for you. a small % of hardware configurations won't work with linux. you just happen to be in that small percentage. there are millions of people using linux happily. if your experience was the norm, well, there *wouldn't* be millions of people using it. get compatible hardware or move on. end of story.

---

### Post by oldsoundguy on 2008-10-17
> **SkittleLinux18 said:**
> ........

I don't know if it's memory leaks, faulty distro coding, or just plain bad luck; but my taskbar/kicker still reloads itself every morning at 4 am. All of my running apps in the system tray fail to redock and it's a real pain trying to redock them. I went through the PCLOS forums, Ubuntu forums, and Google trying to hunt down a solution. The only thing I came close to figuring out is that it may have to do with memory leaks. But that's not even for certain.



This sounds more like a bad memory chip than a memory leak. Or your controller chip on board .. that should be stress tested. I have a self booting version of Ultimate Boot Disk (free) that has programs on it that you could check out. And, are you running a background program such as BOINC?

There are several programs you can use to test that memory.  One is on the Ubuntu disk when you boot up.  Or you can go to the Windows site and get the Windows MemTest which works quite well on a self booting disk. or you could select one of the programs on the Ultimate disk.  (very handy disk to have around, regardless of the operating system that you use.)

Your Firefox issues have been addressed. There IS a new FF in Beta right now (3.1) that holds some great promise to be much faster .. and it looks cool on top of that!

BTW, I installed Elissa (Linux Mint) on and old 466 celeron with 512 ram and an 80 gb hd on an old People PC Toshiba MB .. it installed in less than an hour COMPLETELY.  set up the onboard video, audio and ethernet out of the box .. later I put in a D-Link 520 G wireless and it installed on re-boot .. only change was the fact I prefer Amarok to Rhythm Box, so changed that out in the package manager.  
A check of the installed items shows that most everything you could use on a basic Linux computer is installed and at your fingertips in the menus.
No, it is not a gaming machine .. no VM is set up .. (Wine IS) .. but it sure works great for what it is!

---

### Post by SkittleLinux18 on 2008-10-18
Ok, after some long, tedious perseverance, I finally got somewhere. I just couldn't accept the fact that Kubuntu would not install on my computer. So I kept researching my old nemesis and learned that the problem was in my BIOS. I went in there and disabled the Floppy Drive (that doesn't exist in my computer?). From there, I was able to get rid of the Buffer I/O error on fd0, but not sr0. So some illegal research led my friend and I to the knowledge that it was an issue with my DVD-ROM drive. I am not good at explaining this stuff, but basically, the bottom line was a conflict with SCSI emulation being turned on. So I swapped out ROM drives and was able to install Kubuntu 8.04. Once the install was done, I restored my computer configuration and everything is working great!! It's fast, stable, other issues are being resolved, and I will probably wake up at 3:59 AM just to watch my taskbar NOT reload at 4:00 AM... hahaha!

Anyway, thanks again to all of you! And to my friend who finally put some of the final missing puzzle pieces together.

P.S. Sometimes moving on is NOT the end of the story. It's not even a story. It's just quitting. I will use Linux 'til the day I die. That does not mean I, or anyone for that matter, won't have moments of frustration.

---

