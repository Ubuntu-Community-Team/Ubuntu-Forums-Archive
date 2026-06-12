---
title: "Ubuntu is a stable system for desktop end user?: NO"
date: 2022-06-15
forum: Ubuntu, Linux and OS Chat
---

### Post by WHK on 2022-06-15
I want to share my experience with ubuntu, I am a user since 2010 and I have read many articles that try to answer the question: why does linux not dominate the desktop market, today I am here to give my opinion on this, in addition to talking about ubuntu and canonical in general.

I want to start by saying that for me Ubuntu is not a productive system for end users on desktop computers, but for servers but not for desktops. A desktop computer should have **minimum usability requirements**, even canonical has spoken about this indicating that they would focus more on users, but over time this has not happened.

**For many years until today, users do not have a productive and native music player software:**
At present, canonical does not have official software to play music, but if there are third-party players, the problem is that the most used ones, such as vlc and audacious, have very basic interface problems and do not integrate correctly with gnome. , especially with wayland since most still make compatible applications for xorg but not for the official technology proposed by canonical. Currently there is gnome music development which is beta and has multiple bugs and is almost impossible to use. Windows 98 have a better music player than ubuntu 22.04.

**Ubuntu does not have a stable video display:**
Totem or the default video viewer of ubuntu is very unstable and not very configurable, in many cases since ubuntu 22.04 with wayland the videos do not play, the software is very unstable and we return to the same problem of music playback, the only alternatives Viable are third-party software that have multiple basic interface and usability issues.

**Ubuntu 22.04 LTS is not able to record screen at 60fps:**
Unfortunately ubuntu 22.04 under wayland uses PipeWire for screen recording, as is the case with OBS, the problem is that Wayland and Pipewire do not have support yet for recording at 60fps under any conditions, I use an amd radeon gt 6800 xt video card but apparently it's not enough for a simple screen recording.

**It is almost impossible and torture to connect a guitar to the pc:**
It is almost impossible to use jackd with guitarrix or any other software because the audio interface is very complicated to configure to do a simple task: that the microphone is heard through the speakers. This simple task leads to an answer like: You must install an entire operating system like Ubuntu Studio to get a single setup working. This means that if you use Ubuntu to play and program you must have a second computer or another disk with another installation and close everything to be able to raise an operating system that allows you to do this audio configuration. Even windows xp allows you to make this configuration with a simple click using same hardware. Could it be that Ubuntu 22.04 is even more unstable or bad experience than windows xp?

**Microphone jack not working in Ubuntu 22.04 LTS on one of the most used motherboards for AMD:**
It is not a strange case, the MSI x570 motherboard is the best known and used for new generation AMD processors, but apparently there is still no stable driver for it, despite the fact that almost 4 years have passed since its launch, soon New generations of AMD 7000 processors will come out with new motherboards and we still don't have a simple audio driver for the previous generation. A gaming user or streamer could not count on latest generation amd hardware using the latest version of ubuntu.

**Lack of basic UI features:**
It's ridiculous but Ubuntu 22.04 LTS for Desktop (default install using wayland) doesn't have a simple option to change screen brightness. In Windows 7 or Windows XP you can change the brightness no matter if the monitor supports backlight or not, in my case I suffer from headaches with high brightness and I have to move the monitor every day to press the back buttons to change the brightness. brightness and then in the morning turn them up a bit, instead of having a simple slider that allows me to change the brightness. This is ridiculously basic.
Another point against it is the elimination or discontinuation of compiz fusion effects, I think it was a very bad decision to keep only a few effects since many users tried ubuntu only to see fire effects or see how the desktop could rotate in 3d, but for some strange reason, when microsoft was intimidated by these features, the developer decided to end their support and canonical decided to omit these effects.

**There is no stable and efficient application for office:**
Most of my co-workers ask me: is there ms office for linux? I tell them: there is libreoffice, and they tell me that it is impossible to work with libreoffice, so they don't change the system. I have used Libreoffice for many years, the support is terrible, it has very basic bugs that are never fixed, the interface is terrible, the support of third-party extensions is bad. For example, if you open a document saved with a version of libreoffice from more than a few months ago, you will have multiple compatibility problems and manipulating tables is a nightmare. Everyone knows that libreoffice is the best option to msoffice on linux but everyone also knows that it sucks. I have tried multiple alternatives but none are really useful as a replacement. Is it impossible to make a document editor?: NO. Google Docs is a very efficient system that relies on html components to perfectly fit each object, so canonical could also spend time making a document editor based on electron and html, but it doesn't and probably never will and we'll stick with the same crap from libreoffice. Something similar happens with gedit, it doesn't support markdown and loading 2mb files ends up crashing.

**Ubuntu doesn't have a decent store:**
Currently the ubuntu package system is a mess, especially for a beginner. In the past you used aptitude and deb packages via apt-get, but today you have snap which has many official and unstable packages, which do not even have the basic configurations to work with external drives such as gimp and give many problems to access files of local configuration as is the case of libre office and the text fonts in ~/.fonts, in addition, flatpack has come to solve these things but canonical instead of using the best option for the end user continues to support a system outdated and poorly maintained to this day. The graphical application of applications is very unstable, the applications do not install well, it is not able to detect when you already have an application installed, it gives errors everywhere, sometimes it simply does not start, it does not have a reliable rating system, not even you know if the application that you will install works or not, it does not have a software quality process like play store, it has very few applications for the end user, it is a complete disaster. They could learn from the stores that already exist such as the play store (for me it is the best) and the app store. I would remove snap and focus on flatpak and deb packages.

**The support is lousy:**
I understand that there is a very large community working to make the system better and more stable, the base system and its kernel are very stable and appreciated, but the user experience in ubuntu desktop is terrible and is very neglected. It is very complicated to try to send feedback or report problems, many times I have had to wait more than 10 years for basic problems to be resolved. Open communities like these are official but not their members, which is why you only have community support but never official support and you can easily wait years for things as simple as the lack of a slider to control screen brightness to be heard, then you have to wait another long years for them to try to give you a solution.

**Canonical does not help gamers or streamers:**
Most decisions about configurations, drivers and packages do not help people who consume and use media content, we are still in the era of windows xp where audacity was the best option for professional audio editing, today packages and Drivers are oriented to stability and the avant-garde but not to usability, it is the case of the abandonment of audio and video configurations on wayland and little kernel optimization for low latency like as ubuntu studio.

**If I can give thanks:**
Many people help us with these problems every day without receiving money, others support professionally and it is greatly appreciated, it is also appreciated that canonical is supporting users without returning a direct benefit, but I think that many of canonical's decisions are not well-founded and much of its work team stayed in the past, we had to wait many years to have an interface that would compete in design with windows 7 and we have achieved it today 2022, now we will have to wait another 10 years to see a modern interface like osx or windows 11. The development environment of gnome is terrible, instead of using more flexible and open components like nodejs, rust, interface based on html and css instead of gtk, this would increase the number of developers, but for some strange reason they still maintain a scheme of little modern and little scalable work.

**Ubuntu Desktop should not be called stable:**
I think that ubuntu is still very far from having an orderly and efficient workflow, we are still fighting to have basic things like if you have windows xp, we don't even have an alternative to the old windows media player, much less with such a view nice as aero, until very recently we were able to have a decent settings app, even windows xp control panel was better than ubuntu 20.04. I consider that Ubuntu Desktop is alpha/beta but it is still very far from being stable, not even google dared to give a stable version to ubuntu studio despite how well it worked. It is only a matter of observing this forum, it has the design of a page from the 2000s, it is not even responsive, the libreoffice website seems to have been made by a 10-year-old boy who wanted to learn how to make web pages.

I have bought a new hardware of last generation, but the Operating System does not help me, i am a software developer, I work in cybersecurity, I like design, I use Krita a lot, I like to play guitar, I like to play, I have steam, on my PC I work, play and rest, and I have always done it with ubuntu, but for me the adaptation has been very difficult, not because I have personal adaptation problems, but because the canonical technology advances very slowly, what else awaits an inexperienced user.

I am making this post because I have had several compatibility problems and other basic problems that I have been having since I had the old hardware and today I felt overwhelmed and somewhat abandoned, I feel the support of people who enter the forum with all the good intentions to help, I read a lot of tutorials, I read a lot of the archlinux wiki (which is much better than the ubuntu documentation), but I still feel that the things that should be done canonical and the developers don't do it and prioritize other things leaving aside the users. I feel alone on this path, I would never go back to Windows, but I feel that I spend my time on modern technical knowledge and latest generation hardware, but I feel that the operating system is from many past generations and I cannot reflect that to the people I know. since I always try to show you how cool it is to use linux with ubuntu but I also recognize how difficult is this road.

I don't know if the people who will read this post are new or old, if it will be someone from canonical or not, what I do know is that I no longer have faith in changes, the only thing I hope is that over the years I can appear another entity that wants to maintain another distribution of linux and that does it better, I'm not saying that it does it perfect but that it does what it has to do correctly.

---

### Post by yancek on 2022-06-15
There was a thread here recently where a member asked how to request additional software features from canonical and that information was posted in the thread.  I don't have it bookmarked but you might find it with the search option on the forum.  That would probably be your most realistic option.  There isn't anything members here can do about it and I doubt very much the programmers/developers at Canonical will see your post.  I'm sure you are aware that the members here are all just volunteers trying to help people.

>  It's ridiculous but Ubuntu 22.04 LTS for Desktop (default install using  wayland) doesn't have a simple option to change screen brightness. 

I won't be using 22.04 until July at the earliest so I don't know about the above problem and why it would have been removed as on 20.04  I just go to Settings, Power,  Power Saving and Screen Brightness.

I don't use my computer often for music or video so have no interest or knowledge of that software.  I've not had problems with Libre Office but again, I don't use it often or for complicated documents.

You don't need to use Snap packages and in fact can disable it as many have done and just use apt/apt-get or .deb packages.
 
You can get official support from Canonical but as with Microsoft, Apple and Red Hat support, you have to pay for it.

---

### Post by WHK on 2022-06-15
> [COLOR=#000000]I won't be using 22.04 until July at the earliest so I don't know about the above problem and why it would have been removed as on 20.04 I just go to Settings, Power, Power Saving and Screen Brightness.[/COLOR]

They haven't removed it, it's only available for notebooks, not desktops.

I do use libreoffice every day to work, I make templates, presentations and reports every day.

---

### Post by Holger_Gehrke on 2022-06-16
Don't know whether it works with Wayland, but on XUbuntu 22.04 - which doesn't ship with Wayland because XFCE doesn't yet support it - I use gddccontrol (uses the Display Data Channel / Command Interface, so it *should* work on Wayland) to control the brightness of my HDMI connected external display and I previously used it to control an external display connected via VGA. DDC/CI is basically an i2c bus hidden away in all modern display connections. gddccontrol is available from the normal Ubuntu repositories. There's also a command line tool named ddccontrol - which gets installed as a dependency of gddccontrol - so you can script changes to monitor settings - for example to change the monitor settings on a schedule. 

Yes, this is a kludgy workaround - but those are the norm ...

Holger

---

### Post by coffeecat on 2022-06-16
Not a support request. *Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by yancek on 2022-06-16
>  which is why you only have community support but never official support 

I'm not sure what you mean by that but there is 'official documentation' online for Ubuntu which I try to use whenever possible.  I imagine you are aware of the Ubuntu site at the link below which would be a good place to start for new users.  If you mean trying to contact Ubuntu/Canonical for individual support, that is possible also but like other OS's, you need to pay for it..  I'm sure it is frustrating but it may be that the things that are important to you (or others) may not be a priority for developers.  Good luck. 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by TheFu on 2022-06-16
Sometimes it feels good to carefully write a bunch (good and bad) and post it.  I completely understand.

Of course, nobody here can do anything about the complaints.  If you don't like Ubuntu, there are alternatives.  For me, the year of desktop Linux began around 1995, but I didn't go nearly 100% until 2008, though I'd been running Unix/Linux servers since 1993.

Some of the use cases in the OP are fairly specific.  What percentage of Ubuntu users would ever connect guitar?  0.005%?

I have a bunch of mostly niche needs in my systems and Windows can't touch what Linux does for me.  Perspective matters.  If you find a kid who's only used Linux, then throw MS-Windows at them, they get frustrated too.  Perspective.
About ten years ago, work sent me a Mac to use. It lasted 3 weeks before I sent it back due to frustration. So many things didn't work right.  I wanted to throw the $4000 machine against a brick wall a few times.  So much power, but I wasn't allowed to access it due to stupid GUI limitations.

GUI users confuse the OS with the GUI. How can they not?  But if you are just point-n-clicking, 80% of the power in any Unix/Linux system isn't being used.  Not everyone cares to learn that extra power and most people have 25 yrs of MS-Windows training (they were "trained", definitely) for how things work.  But Linux isn't Windows and Windows isn't Linux.  Expecting Linux to work like Windows is the wrong way to attack the issue.  Just like when I wanted MacOS to behave like any Unix and it didn't.  That was 100% my fault.  Stepping back, there was real genius in the MacOS GUI, but I couldn't see it because I wanted something else. I wanted a powerful Unix with X11.  That isn't Mac and that isn't MS-Windows, so of course I was frustrated.

BTW, Ubuntu doesn't control 90% of the software used in Ubuntu releases.  Most of that software is created and maintained by other projects, not Canonical.  Effectively, blaming Ford for a tire issue.  Complain to the tire people.  There are over 10,000 tires in Ubuntu.

Have you ever tried to get support from MSFT?  I have.  They get your $150 first, then say it isn't an issue.  

Worked at a huge enterprise. We had 4 full-time people from MSFT in our building to support architecture stuff and provide guidance for how to do X the best way.  They weren't there for server or desktop support people - just for enterprise-wide issues.  We had huge problems with time sync across the enterprise. MSFT statement was that time needed to be ±5 minutes and that was their target.  On Unix, time sync should be millisecond accurate at worst microsecond accurate is the expectation.  ±5 minutes?  That was a joke, right?   Nope.  Working as designed.

---

### Post by agentl074 on 2022-06-19
I haven't had ANY issues with mine. I did apt update and upgrade and installed Gnome tweaks, corefonts, and it's the best OS I've ever used.

---

### Post by kurt18947 on 2022-06-20
Use what works best. Ubuntu doesn't do what you need? Satya Nadella or Tim Cook will gladly take your money. For me, Ubuntu & Linux ecosystem do what I need to do. If they didn't I'd look elsewhere. One thing we should all keep in mind - Canonical is a for profit entity. How much money do they make off desktop linux? None? That seems correct. Server/Cloud/IoT keep the lights on at Canonical and pay for servers and bandwidth for desktop.

---

