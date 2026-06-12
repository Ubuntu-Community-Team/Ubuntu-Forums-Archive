---
title: "Debian? CLI? What for?"
date: 2008-07-02
forum: The Cafe
---

### Post by odiseo77 on 2008-07-02
Hello people. Although I'm multiple booting Ubuntu, Debian Lenny, Arch and Windows on this PC, I've been using Debian Lenny exclusively for the last 2 weeks (without shutting down the PC, or rebooting, or exiting my current gnome session). Some minutes ago I happened to check my uptime and I realized something curious and funny: since my last login to my current gnome session (which was 2 weeks ago, as I said before), the only thing I have used the terminal for, is to check my uptime (see attached picture below. The terminal you see there is Guake, a terminal emulator for Gnome similar to KDE's yakuake). 

This made me think about the most common and terrible myth about Linux in general (and in particular, about Debian): the belief that it's hard to use, and you have to use the CLI for ***everything***. Don't misunderstand me here; I know the power and usefulness of the CLI for everything, specially for administrative tasks. I use linux almost exclusively at home, but I enjoy messing with the terminal, knowing and using new commands, knowing how the whole system works, etc (sometimes, when I have to, I compile/install some software from source, I've even compiled the kernel sometimes and I've installed drivers, etc.). What I'm trying to say here is: once a Linux install is finished, all the necessary programs and plugins installed and everything is properly set up, any ***regular user*** should perfectly be able to use it for anything he/she might need (like browsing the net, write documents, copy a file from some place to another, use a USB flash drive, etc.). Even my 58 years old mother, who is dual booting Linux and Windows, feels so comfortable with Ubuntu, that she uses it like in 90% of the times (or maybe even more than that) and just boots Windows when a project requires her to use some program named Visio I'm not sure what is for (I think it's used to create diagrams, or something like that). By the way, she is able to reboot her PC, wait for the grub menu and switch to windows (or linux) by herself (without any help from some geek or something). 

And to stress the point a little bit more and finish my idea: the above goes for Windows all the same (and, I'm almost sure, for OSX, although I have never used it). I mean, a regular, average user doesn't install and set up Windows on his/her PC. Sure, there are some things that are probably easier on Windows, like auto-installing browser plugins (and auto-installing viruses, etc.), installing some software by double clicking (something that you can do on Ubuntu, if you have the admin password). But, there will always be the need of some geek, sysadmin, IT guy, whatever you want to call him/her, to set up an OS (***any OS***) for a productive environment in which a regular user can do his/her daily work (and to take care of an eventual breakage). 

I guess all of the above has been said before in another ways probably one million of times, but these were the reflections and thoughts that came to my mind a while ago, when I saw my terminal. I just wanted to share them :). And, if this has been discussed here before, and a mod prefers to move this thread to "Recurring Discussions", he/she is welcome to do so (although I'd prefer this would stay here, on the "Community Cafe", but it's up to you :)).

Greetings.

---

### Post by eryksun on 2008-07-03
> **odiseo77 said:**
> But, there will always be the need of some geek, sysadmin, IT guy, whatever you want to call him/her, to set up an OS (***any OS***) for a productive environment in which a regular user can do his/her daily work (and to take care of an eventual breakage).

I don't think that's true or desired. And I blame all the little Napoleons in the Land of OSS, which is more of a resume building exercise than a coherent movement. Everyone seems to splinter into camps over personality conflicts, language barriers (both natural and computer), conflicting visions, and the desire to put more on their resume than 'team player'. Projects pop up like weeds and fork like trees. The Bazaar is simply too bizarre. Having thousands of packages in the repositories is not a sign of strength but rather a sign of weakness. 

A team of leaders at Canonical needs to step up to the plate and start defining a more coherent vision for the future of Ubuntu (and not Kubuntu, Edubuntu, or Ubuntu-of-the-Month for that matter) and push this vision to the upstream projects. Is the system toolkit GTK (Gnome) or Qt (KDE) or both? (IMO, it's ugly and wasteful having both on one system.) Is the Window manager Compiz or Metacity? Is window decoration handled by the toolkit, the window manager, or some helper program such as Emerald? Does the desktop manager draw the background for each workspace, or does it get treated as a window layer like the widget layer? If so, should there be a desktop layer or should this be absorbed into the widget layer (e.g. file stacker applets in place of /home/user/Desktop)? Are applets to be provided by Gnome Panel, Screenlets, gDesklets, Avant Window Navigator, or some combination? (like the GTK/Qt question, IMO, a combination is wasteful, ugly, and confusing) Is the language of choice for applets Python/Vala or Mono? Will Java and Flash be handled by proprietary or open source systems? If open source, what can be done to increase compatibility and performance? 

A small group needs to take charge of this mess so that operating system developers can start working on *quality* instead of spreading themselves so thin that the inadequacy is transparently obvious. Projects need to be merged, dropped, and refactored. If the project leaders don't want to play ball, they can take their software elsewhere. It's a big world; others will play.

The Linux community in general needs to rally more tightly around this central vision. Ubuntu has 30% of desktop Linux and climbing; it's the clear winner. The Debian distros should merge into Ubuntu Desktop -- providing a clear alternative to MS Windows. (Note: it should never be called "Ubuntu Linux" or "Ubuntu GNU/Linux", and definitely never "Ubuntu Linux, building upon Debian GNU/Linux" -- that's a confusing heap of adjectives dictated by Napoleons.)

On the enterprise side of the equation Red Hat needs to abandon Fedora and jump on the Ubuntu bandwagon as partner with Canonical. Together they can develop a coherent experience from desktop to server that will more than rival Windows 7.0/Server 2011.

---

### Post by ibutho on 2008-07-03
[QUOTE=eryksun]
On the enterprise side of the equation Red Hat needs to abandon Fedora and jump on the Ubuntu bandwagon as partner with Canonical. Together they can develop a coherent experience from desktop to server that will more than rival Windows 7.0/Server 2011.[/QUOTE]
Why would Red Hat want to partner with Canonical when their distro is the defacto Linux for the enterprise? Last I heard, Red Hat was actually making a lot of money from their server products and Canonical was barely getting by. I also don't see why they should abandon Fedora. Fedora provides them with a testing ground for technologies that may end up in RHEL. This is valuable for Red Hat because they will have an idea of what works or does not work before implementing it in RHEL. This testing and experimentation is one of the reasons why RHEL releases are very stable and trusted in the enterprise. Debian is quite similar because they test things extensively in Debian Unstable and Testing before a Stable release. 

A lot of the things in your other post just won't happen and I don't see the point of them. You can't force centralisation and cooperation on projects you do not control.

---

### Post by odiseo77 on 2008-07-03
> **odiseo77 said:**
> But, there will always be the need of some geek, sysadmin, IT guy, whatever you want to call him/her, to set up an OS (***any OS***) for a productive environment in which a regular user can do his/her daily work (and to take care of an eventual breakage).

> **eryksun said:**
> I don't think that's true or desired. And I blame all the little Napoleons in the Land of OSS, which is more of a resume building exercise than a coherent movement. Everyone seems to splinter into camps over personality conflicts, language barriers (both natural and computer), conflicting visions, and the desire to put more on their resume than 'team player'. Projects pop up like weeds and fork like trees. The Bazaar is simply too bizarre. Having thousands of packages in the repositories is not a sign of strength but rather a sign of weakness.

Well, first, I don't see any relation between what I said in my quote above (which you quoted as well, but I felt it was necessary to quote here), and what you said, except, maybe, that you called "little Napoleons" the people I was talking about in this quote; that is, the people who works with computers, specially sysadmins, or the guys who take care about the ***user's*** needs (as I understad, if I'm not lost here, or misunderstanding you). I don't see how they're "little Napoleons" or something like that, so *I guess* you're talking about the "elitist gurus who feel they have the only and absolute truth", or something of the sort. *If* this is the case, then I have an idea about this type of people as well, although I don't generally bother to pay too much attention to them. 

That said, I think maybe I should clarify the general idea I was trying to express in my first post (in case it's not clear enough). My main point was related to the interaction between the OS (in this case, Linux, which, according to some myth, or FUD, etc. is supposed to be hard), and the ***user***. I pretty much said that although a general, average user doesn't install and setup an OS (Linux, in this case), once everything is setup and working, any regular user (that is, someone who uses the computer for work, or browsing the net, listening music etc., but is not particularly interested in how the OS works -nor he/she has to), any regular user, I repeat, should, or could, easily work with Linux, with the same ease he/she uses the "supper-ubber easy Windows" (of course, at the beginning this person could feel the need to get used, or accustomed to another OS, but that's another point). 

So, pretty much, I was talking about Linux and it's usability in a desktop environment for the every day work (and I think it's not necessary here to enter in details like how much ground Linux currently has in the market, although, the above could be an indicator that *maybe* Linux could be used in the desktop in the same way as Windows, etc., but I can't predict the future as to know if it will ever happen, or when). Now, with all respect, I think the rest of your post was way too far from the general idea of my first post. And in case this might be of interest or pertinent here (I think it isn't, but maybe I should say it, to explain my point of view about this issue), I'm far from being a professional sysadmin. My profession is completely unrelated with Linux or computers, but I'm passionately interested in Linux and learning all I can about it (maybe it's a sort of hobby for me). So, this might explain my point of view about this issue, since I'm between a regular user and a sysadmin (rather, an amateur sysadmin).

Well, after all this seems to be becoming a recurring discussion, so, to the mods: feel free to move this thread where you think it's convenient :)

Regards.

---

### Post by eryksun on 2008-07-03
> **ibutho said:**
> Why would Red Hat want to partner with Canonical when their distro is the defacto Linux for the enterprise? Last I heard, Red Hat was actually making a lot of money from their server products and Canonical was barely getting by.  

I thought I stated my reason. A big reason that Windows is dominant (*) is because both end users and businesses can depend on a consistent interface and tools across the product spectrum, from a cheap basic desktop to an enterprise server. If there are bugs and security issues, at least they're reliable and consistent, and you know that most of your competitors have to deal with the same problems. In the Linux world, you simply don't get anything like that. The spectrum of tools and interfaces, and associated bugs and security issues, is splintered in countless directions. 

*(*) 60% of units shipped in the 2008 server market are predicted to be Windows, and in terms of money spent in the server market, Windows will account for 37% of the total, while Linux will grab 16%.*

> **ibutho said:**
> I also don't see why they should abandon Fedora. Fedora provides them with a testing ground for technologies that may end up in RHEL.... Debian is quite similar because they test things extensively in Debian Unstable and Testing before a Stable release. 

But having them use Fedora splinters development in the Linux community. There's so much parallel development that systems never get out of the 'good enough for geeks only' phase. Polishing a system to handle the thousands of use-case scenarios that makes it good enough for average users, who know nothing about how computers actually work and don't have the time or inclination to learn, is a monumental task. Getting something working is only 10% of the job. Getting it working easily, intuitively (for end users), consistently with the rest of the system, reliably and securely are the tough jobs. Also, if Debian is considered the testing ground for Ubuntu, I really think it should be controlled by Canonical. Otherwise you get the current mess. It's more like several, very different, operating systems, all smashed into a single distro/repository.


> **ibutho said:**
> A lot of the things in your other post just won't happen and I don't see the point of them. You can't force centralisation and cooperation on projects you do not control.

Yes you can, and should, if you have dominant market share. Its your responsibility to end users to do everything in your power to provide a coherent OS, and not just some hacked together sampling of countless half-baked tools.

---

### Post by RiceMonster on 2008-07-03
> **eryksun said:**
> Having thousands of packages in the repositories is not a sign of strength but rather a sign of weakness. 

Give me a break. You're acting like there isn't millions of software out there for Windows. Most Linux distributions just like to make them readily available for you. How the hell is that a weakness? You're just annoyed that you don't know what everything is yet.

> **eryksun said:**
> The Linux community in general needs to rally more tightly around this central vision. Ubuntu has 30% of desktop Linux and climbing; it's the clear winner. The Debian distros should merge into Ubuntu Desktop -- providing a clear alternative to MS Windows. (Note: it should never be called "Ubuntu Linux" or "Ubuntu GNU/Linux", and definitely never "Ubuntu Linux, building upon Debian GNU/Linux" -- that's a confusing heap of adjectives dictated by Napoleons.)

On the enterprise side of the equation Red Hat needs to abandon Fedora and jump on the Ubuntu bandwagon as partner with Canonical. Together they can develop a coherent experience from desktop to server that will more than rival Windows 7.0/Server 2011.

No, they shouldn't do that. First of all, Linux is about _choice_. Second of all, distros have different goals and ideas of how things should be done, meaning there would be a lot of in fighting if they were to merge. Third, I don't see why Linux should have to try and gain market share over windows. I certainly don't care if it does. As long as it continues to improve and keeps working for me, that's all I care about, and if more people want to come and use it, then that's great.

If you hate the amount of distros existing, either deal with it or use Windows or Mac.

---

### Post by p_quarles on 2008-07-03
> **eryksun said:**
> But having them use Fedora splinters development in the Linux community. There's so much parallel development that systems never get out of the 'good enough for geeks only' phase.
This is pure speculation. "Parallel development" has nothing to do with the usability of a particular project. Combining the teams working on Amarok and Exaile, for instance, wouldn't make either one inherently better.

The number of unfounded assumptions that your assertion relies upon make it essentially null. 

>  Polishing a system to handle the thousands of use-case scenarios that makes it good enough for average users, who know nothing about how computers actually work and don't have the time or inclination to learn, is a monumental task.
True. No one has ever accomplished this. The successful OSes have gotten around this by getting their product preinstalled on retail computers. 

> Also, if Debian is considered the testing ground for Ubuntu, I really think it should be controlled by Canonical. Otherwise you get the current mess. It's more like several, very different, operating systems, all smashed into a single distro/repository
If this happened, the vast majority of Debian users and developers would abandon it entirely. I think you should, perhaps, make an effort to understand how the F/LOSS ecosystem works before making proposals that so radically contradict its spirit and intentions.

---

### Post by sujoy on 2008-07-03
> **eryksun said:**
> I don't think that's true or desired. And I blame all the little Napoleons in the Land of OSS, which is more of a resume building exercise than a coherent movement. Everyone seems to splinter into camps over personality conflicts, language barriers (both natural and computer), conflicting visions, and the desire to put more on their resume than 'team player'. Projects pop up like weeds and fork like trees. The Bazaar is simply too bizarre. Having thousands of packages in the repositories is not a sign of strength but rather a sign of weakness. 

A team of leaders at Canonical needs to step up to the plate and start defining a more coherent vision for the future of Ubuntu (and not Kubuntu, Edubuntu, or Ubuntu-of-the-Month for that matter) and push this vision to the upstream projects. Is the system toolkit GTK (Gnome) or Qt (KDE) or both? (IMO, it's ugly and wasteful having both on one system.) Is the Window manager Compiz or Metacity? Is window decoration handled by the toolkit, the window manager, or some helper program such as Emerald? Does the desktop manager draw the background for each workspace, or does it get treated as a window layer like the widget layer? If so, should there be a desktop layer or should this be absorbed into the widget layer (e.g. file stacker applets in place of /home/user/Desktop)? Are applets to be provided by Gnome Panel, Screenlets, gDesklets, Avant Window Navigator, or some combination? (like the GTK/Qt question, IMO, a combination is wasteful, ugly, and confusing) Is the language of choice for applets Python/Vala or Mono? Will Java and Flash be handled by proprietary or open source systems? If open source, what can be done to increase compatibility and performance? 

A small group needs to take charge of this mess so that operating system developers can start working on *quality* instead of spreading themselves so thin that the inadequacy is transparently obvious. Projects need to be merged, dropped, and refactored. If the project leaders don't want to play ball, they can take their software elsewhere. It's a big world; others will play.

The Linux community in general needs to rally more tightly around this central vision. Ubuntu has 30% of desktop Linux and climbing; it's the clear winner. The Debian distros should merge into Ubuntu Desktop -- providing a clear alternative to MS Windows. (Note: it should never be called "Ubuntu Linux" or "Ubuntu GNU/Linux", and definitely never "Ubuntu Linux, building upon Debian GNU/Linux" -- that's a confusing heap of adjectives dictated by Napoleons.)

On the enterprise side of the equation Red Hat needs to abandon Fedora and jump on the Ubuntu bandwagon as partner with Canonical. Together they can develop a coherent experience from desktop to server that will more than rival Windows 7.0/Server 2011.

you really have no idea what you are saying, do you? you want canonical to take over control of debian? wtf? go and read about how the system works, kid.

---

### Post by OldTimeTech on 2008-07-03
Did you ever think that maybe the reason all of the programs that you're complaining about is in the repos is because we as a community, a people, a person...like to play with our computers, like to find, use and play with different options, have different numbers of computers in our households that need different types of setups...not all work on Hardy 8.04 with Gnome....that said...I learn by using all and different type of the programs in repos...I like the way our OS, our programs and our help is set up!!!

---

### Post by cardinals_fan on 2008-07-03
> **eryksun said:**
> I don't think that's true or desired. And I blame all the little Napoleons in the Land of OSS, which is more of a resume building exercise than a coherent movement. Everyone seems to splinter into camps over personality conflicts, language barriers (both natural and computer), conflicting visions, and the desire to put more on their resume than 'team player'. Projects pop up like weeds and fork like trees. The Bazaar is simply too bizarre. Having thousands of packages in the repositories is not a sign of strength but rather a sign of weakness. 

A team of leaders at Canonical needs to step up to the plate and start defining a more coherent vision for the future of Ubuntu (and not Kubuntu, Edubuntu, or Ubuntu-of-the-Month for that matter) and push this vision to the upstream projects. Is the system toolkit GTK (Gnome) or Qt (KDE) or both? (IMO, it's ugly and wasteful having both on one system.) Is the Window manager Compiz or Metacity? Is window decoration handled by the toolkit, the window manager, or some helper program such as Emerald? Does the desktop manager draw the background for each workspace, or does it get treated as a window layer like the widget layer? If so, should there be a desktop layer or should this be absorbed into the widget layer (e.g. file stacker applets in place of /home/user/Desktop)? Are applets to be provided by Gnome Panel, Screenlets, gDesklets, Avant Window Navigator, or some combination? (like the GTK/Qt question, IMO, a combination is wasteful, ugly, and confusing) Is the language of choice for applets Python/Vala or Mono? Will Java and Flash be handled by proprietary or open source systems? If open source, what can be done to increase compatibility and performance? 

A small group needs to take charge of this mess so that operating system developers can start working on *quality* instead of spreading themselves so thin that the inadequacy is transparently obvious. Projects need to be merged, dropped, and refactored. If the project leaders don't want to play ball, they can take their software elsewhere. It's a big world; others will play.

The Linux community in general needs to rally more tightly around this central vision. Ubuntu has 30% of desktop Linux and climbing; it's the clear winner. The Debian distros should merge into Ubuntu Desktop -- providing a clear alternative to MS Windows. (Note: it should never be called "Ubuntu Linux" or "Ubuntu GNU/Linux", and definitely never "Ubuntu Linux, building upon Debian GNU/Linux" -- that's a confusing heap of adjectives dictated by Napoleons.)

On the enterprise side of the equation Red Hat needs to abandon Fedora and jump on the Ubuntu bandwagon as partner with Canonical. Together they can develop a coherent experience from desktop to server that will more than rival Windows 7.0/Server 2011.
Why do you possibly assume that I (a Linux user) care about rivaling Microsoft?  Why should I possibly want to use Ubuntu on my desktop?  Why should I want a central vision?  Why should I want a "clear alternative to MS Windows" (I think that many already exist)?  And, perhaps most importantly, why do you think that you can tell me (a member of the Linux community) what to do?

Sorry if that offended anyone, but I'm really sick of "Why don't we all make one big distro to take on MS" threads.  Back to topic ;)

---

### Post by eryksun on 2008-07-03
> **odiseo77 said:**
> Well, first, I don't see any relation between what I said in my quote above (which you quoted as well, but I felt it was necessary to quote here), and what you said, except, maybe, that you called "little Napoleons" the people I was talking about in this quote; that is, the people who works with computers, specially sysadmins, or the guys who take care about the ***user's*** needs (as I understad, if I'm not lost here, or misunderstanding you). I don't see how they're "little Napoleons" or something like that, so *I guess* you're talking about the "elitist gurus who feel they have the only and absolute truth", or something of the sort. *If* this is the case, then I have an idea about this type of people as well, although I don't generally bother to pay too much attention to them. 

I was talking about the developers, the ones designing and coding the software packages the sysadmins use, though obviously there's a lot of crossover between the two in the OSS community. 'Napoleon' is a reference to the ego-driven competition fest in OSS. Ever heard the expression "too many cooks in the kitchen"? What I want is for the dominant distro to step up to the plate and take the reins. No one has worked out how the [[COLOR="Blue"]Bazaar[/COLOR]]("http://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar") model, while great for finding bugs and security issues, is to be used for *design*. And, in practice, OSS projects are more like anarchy than the kind of chaos you'd find in a real bazaar. I'm  arguing that at the level of the distro, the all-encompassing community, the system is too chaotic and needs to be more anarchic (anarchy, in its many forms, is *not chaos*).

> **odiseo77 said:**
> That said, I think maybe I should clarify the general idea I was trying to express in my first post (in case it's not clear enough). My main point was related to the interaction between the OS (in this case, Linux, which, according to some myth, or FUD, etc. is supposed to be hard), and the ***user***. I pretty much said that although a general, average user doesn't install and setup an OS (Linux, in this case), once everything is setup and working, any regular user (that is, someone who uses the computer for work, or browsing the net, listening music etc., but is not particularly interested in how the OS works -nor he/she has to), any regular user, I repeat, should, or could, easily work with Linux, with the same ease he/she uses the "supper-ubber easy Windows" (of course, at the beginning this person could feel the need to get used, or accustomed to another OS, but that's another point). 

IMO, Windows is far easier to install and configure. The system can't be customized as much as Ubuntu, which is a good thing, an its base installation is a generation ahead of Ubuntu. The default setup for Ubuntu feels more like working on Windows NT 4.0 back in the late 90s. And once you step beyond that with customization, you're presented with a million competing ways to do the same thing, all of them replete with bugs and hacks, finding and configuring trustworthy repos, editing configuration files at the CLI, and compiling software (dependency Hell). This is not ready for primetime.

---

### Post by eryksun on 2008-07-03
I apologize to all who are offended by my opinions. I guess I just want Ubuntu, its controlling body, Canonical, and the OSS community, to be something it's not and never will be. I'm not as in love with chaos as some, I suppose. I want to see the kind of anarchy present in individual OSS projects replicated at the distro level. It seems that will never happen, as just mentioning the idea brings out a wall of opposition. So I'll go crawl back under my rock. P.S. I'm not a kid; I have a BSEE, BSCEN, and MSEE specializing in DSP and Medical Instrumentation.

---

### Post by joninkrakow on 2008-07-03
> **eryksun said:**
> 
Yes you can, and should, if you have dominant market share. Its your responsibility to end users to do everything in your power to provide a coherent OS, and not just some hacked together sampling of countless half-baked tools.

Echos of Microsoft...

Sorry, but when it comes to things like this--and government, I'm a firm believer in decentralization. Isn't what you are proposing the very thing Microsoft is hated for? (keeping in mind that, for Microsoft, the "end user" is IT)

-Jon

---

### Post by RiceMonster on 2008-07-03
> **cardinals_fan said:**
> Why do you possibly assume that I (a Linux user) care about rivaling Microsoft?  Why should I possibly want to use Ubuntu on my desktop?  Why should I want a central vision?  Why should I want a "clear alternative to MS Windows" (I think that many already exist)?  And, perhaps most importantly, why do you think that you can tell me (a member of the Linux community) what to do?

Sorry if that offended anyone, but I'm really sick of "Why don't we all make one big distro to take on MS" threads.  Back to topic ;)

+1

I'm sick of those complaints too. If you hate it, use Windows/Mac (I know I said it already, but it needs to be said again).

> **eryksun said:**
> IMO, Windows is far easier to install and configure. The system can't be customized as much as Ubuntu, which is a good thing, an its base installation is a generation ahead of Ubuntu.

Yeah, but what if you're like me and don't like the Windows interface at all? What if, again, you're like me and want to be able to customize it? Yes, you can get stuff like Lite Step and BB4Win but it's not the same, and none of them would run on my Vista installation (which I no longer have). It's only a a goog thing that it can't be customized **for you**.

> **eryksun said:**
> The default setup for Ubuntu feels more like working on Windows NT 4.0 back in the late 90s. And once you step beyond that with customization, you're presented with a million competing ways to do the same thing, all of them replete with bugs and hacks, finding and configuring trustworthy repos, editing configuration files at the CLI, and compiling software (dependency Hell). This is not ready for primetime.

The complaint that you have to compile all the time is, as far as I'm concerned, a load of crap. I've compiled software about three times, and that was completely by my own choice. I never needed to. Furthermore, if there wasn't "a million ways to do the same thing" as you put it, Linux wouldn't be customizable, now would it?

I just don't get it. The amount of distros confused me at first, but it never bothered me. I just thought "this is cool; I can find the perfect flavour of Linux for me", and I did some reading.

Seriously, go back to Windows, or Mac if that's what you were using. You seem to hate what Linux is all about in the first place.

---

### Post by eryksun on 2008-07-03
> **joninkrakow said:**
> Echos of Microsoft...

Sorry, but when it comes to things like this--and government, I'm a firm believer in decentralization. Isn't what you are proposing the very thing Microsoft is hated for? (keeping in mind that, for Microsoft, the "end user" is IT)

-Jon

No, I don't think so. Microsoft is a typical corporation (replete with cronies, corruption, monopolization, and state interference) dictating to a community, with a handful of leaders creating the vision and getting rich and powerful beyond belief. I'm talking about self-organization within a community along the lines of libertarian anarchism. Without organization you're left with chaos, which, IMO, is never good.

---

### Post by eryksun on 2008-07-03
> **RiceMonster said:**
> I just don't get it. The amount of distros confused me at first, but it never bothered me. I just thought "this is cool; I can find the perfect flavour of Linux for me", and I did some reading.

Seriously, go back to Windows, or Mac if that's what you were using. You seem to hate what Linux is all about in the first place.

I don't hate Linux at all. I love open source on a project-by-project basis. It's the chaos at the distro level that makes me cringe. I don't think the average person responds to being flooded with choices the way you do. Some people like that; most people would rather choose between a couple of alternatives, both of which are well thought out, easy to use, coherent, and in comparison to each other, based on didactically opposed principles (e.g. Capitalism vs. Communism in the 20th century; you're with us, or against us). People don't want a continuum of choice all along the spectrum, unless it's something superficial like an eye candy theme or the color of their SUV. That's why Windows, and IE/Windows Media Player, are so dominant on the desktop, with Apple taking up a distant, though entrenched, second place.

---

### Post by p_quarles on 2008-07-03
> **eryksun said:**
> I apologize to all who are offended by my opinions.
Please don't impute offense to disagreement. That's frankly, umm, kind of insulting. 

> I guess I just want Ubuntu, its controlling body, Canonical, and the OSS community, to be something it's not and never will be. I'm not as in love with chaos as some, I suppose.

I want to see the kind of anarchy present in individual OSS projects replicated at the distro level.
Ubuntu does take responsibility for the entire experience that users have with their product. This is an enormous undertaking, of course, and the results are unlikely to be perfect at this stage, but Ubuntu has really done an amazing job of consolidating many of the resources available to it. 

What it cannot do, and never should do, is attempt to co-opt other people or projects. 

> It seems that will never happen, as just mentioning the idea brings out a wall of opposition. So I'll go crawl back under my rock.
People were pointing out to you that your suggestions are incompatible with the spirit of F/LOSS projects. That's not "opposition" so much as it is explaining to you why your idea is not a realistic proposition.

---

### Post by RiceMonster on 2008-07-03
> **eryksun said:**
> I don't hate Linux at all. I love open source on a project-by-project basis. It's the chaos at the distro level that makes me cringe. I don't think the average person responds to being flooded with choices the way you do. Some people like that; most people would rather choose between a couple of alternatives, both of which are well thought out, easy to use, coherent, and in comparison to each other, based on didactically opposed principles (e.g. Capitalism vs. Communism in the 20th century; you're with us, or against us). People don't want a continuum of choice all along the spectrum, unless it's something superficial like an eye candy theme or the color of their SUV. That's why Windows, and IE/Windows Media Player, are so dominant on the desktop, with Apple taking up a distant, though entrenched, second place.

Yes, that's why I think that people who are happy with Windows and the software they are using should just stick with it. Linux is not for everyone. Like I said before, I'm not concerned about whether Linux is going to conquer the desktop market or not. If it works for me, and keeps improving, then I'm happy, and if the result of its improvement means more people joining, then that's great, but I don't really care if people use Windows, Linux, or Mac OSX.

Remember, [Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)!

---

### Post by eryksun on 2008-07-03
> **p_quarles said:**
> Please don't impute offense to disagreement. That's frankly, umm, kind of insulting. 

Sorry but I construed statements such as the following as meaning I offended, to some degree at least:

[LIST]
[*]You're just annoyed that you don't know what everything is yet.
[*]And, perhaps most importantly, why do you think that you can tell me (a member of the Linux community) what to do?
[*]you really have no idea what you are saying, do you? you want canonical to take over control of debian? wtf? go and read about how the system works, kid.
[/LIST]
I'm not annoyed that I don't know everything. I may not like chaos, but I do like learning and am never annoyed by the prospect. Is that person offended? I don't know, but they're certainly condescending to me, and if they're not offended, why be rude? Further, I didn't know that expressing an opinion was telling someone what to do. The tone of the quoted sentence implies I'm dictating as if I have all the answers, and if I came off the way, I can see how that would be offensive, so I apologized. Finally, how is excessive condescension, calling me a kid, and cursing at me somehow *not* to be seen as taking offense?

---

### Post by eryksun on 2008-07-03
> **RiceMonster said:**
> Yes, that's why I think that people who are happy with Windows and the software they are using should just stick with it. Linux is not for everyone. Like I said before, I'm not concerned about whether Linux is going to conquer the desktop market or not. If it works for me, and keeps improving, then I'm happy, and if the result of its improvement means more people joining, then that's great, but I don't really care if people use Windows, Linux, or Mac OSX.

Remember, [Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)!

This was the basis for my apology. I want Ubuntu to be something that you, and apparently most users, do not want. I'm hoping to take on the corporate-controlled paradigm with self-organized anarchy, providing a diametrically opposed system (not just in design, but in philosophy) to Microsoft's corporate oligarchy. It's not just a matter of a pragmatic desire for a great OS. I'm an idealist.

---

### Post by cardinals_fan on 2008-07-03
> **eryksun said:**
> Sorry but I construed statements such as the following as meaning I offended, to some degree at least:

[LIST]
[*]You're just annoyed that you don't know what everything is yet.
[*]And, perhaps most importantly, why do you think that you can tell me (a member of the Linux community) what to do?
[*]you really have no idea what you are saying, do you? you want canonical to take over control of debian? wtf? go and read about how the system works, kid.
[/LIST]
I'm not annoyed that I don't know everything. I may not like chaos, but I do like learning and am never annoyed by the prospect. Is that person offended? I don't know, but they're certainly condescending to me, and if they're not offended, why be rude? Further, I didn't know that expressing an opinion was telling someone what to do. The tone of the quoted sentence implies I'm dictating as if I have all the answers, and if I came off the way, I can see how that would be offensive, so I apologized. Finally, how is excessive condescension, calling me a kid, and cursing at me somehow *not* to be seen as taking offense?
It's fine ;)

BTW, I'm fifteen, so being called a kid doesn't seem so insulting :)

---

### Post by koenn on 2008-07-03
> **eryksun said:**
> No,... I'm talking about self-organization within a community along the lines of libertarian anarchism. Without organization you're left with chaos, which, IMO, is never good.

It looks like "chaos" only to those who don't understand how it's organized. 

It's  too long to explain it all in detail, but in the open source ecosphere, people organize themselves in projects that develop software, then distributions distribute a selection of that software, with some added value such as easy access to software repositories, desktop integration, and so on, while some sort of darwinian selection keeps it all healthy

I don't know if that's anything along the lines of libertarian anarchism, but I wouldn't be surprised if there were strong similarities between the two. 

Before you start ranting and calling people names ("those little napoleons"), maybe you should do your homework. 
recommended reading :
[http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/)
[http://www.catb.org/~esr/writings/cathedral-bazaar/homesteading/](http://www.catb.org/~esr/writings/cathedral-bazaar/homesteading/)

---

### Post by adamogardner on 2008-07-03
the CLI is a view into a community of verbs moving nouns anywhichway I want because these verbs are my workers and I am leader and reign supreme in file village.  To answer "Why?," because it's good to be king, although you can't learn to do it in a day, I wouldn't want to because that would be boring.

---

### Post by eryksun on 2008-07-03
> **koenn said:**
> It looks like "chaos" only to those who don't understand how it's organized. 

It's  too long to explain it all in detail, but in the open source ecosphere, people organize themselves in projects that develop software, then distributions distribute a selection of that software, with some added value such as easy access to software repositories, desktop integration, and so on, while some sort of darwinian selection keeps it all healthy

I don't know if that's anything along the lines of libertarian anarchism, but I wouldn't be surprised if there were strong similarities between the two. 

Before you start ranting and calling people names ("those little napoleons"), maybe you should do your homework. 
recommended reading :
[http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/)
[http://www.catb.org/~esr/writings/cathedral-bazaar/homesteading/](http://www.catb.org/~esr/writings/cathedral-bazaar/homesteading/)

I am familiar with the bazaar analogy, which is something I poked a little fun at in the first post (the bazaar is too bizarre). You're right that the 'Little Napoleon' turn of phrase was too harsh. I wasn't intending to 'name call' the project managers. It was just kind of a summary catch phrase for how I view a lot of the ego driven project forks and excessive parallel development. 

Someone has stated that my negative view on excessive parallel development is based on unsupported assumptions and is unscientific. I think when it comes to problems this complex, methods of any kind, scientific included, are only applicable with a lot of unsupported, simplifying assumptions. We just don't know enough about how to design and manage complex systems. We know what we've done, and what has worked 'good enough' over the centuries, but there's a lot to learn. It's my intuition that, given the thousands of use-case scenarios that need to addressed, the more eyes addressing a narrower field of view, the merrier (which is in fact drawing a key point from the Bazaar argument itself). 

To reemphasize the point I was making about anarchy vs. chaos. In my opinion, most OSS projects function as a kind self-organized anarchy. If it were chaos, nothing would get done. But once you move up the latter to the community in general -- to the distros -- you don't have some kind of fractal reproduction of that anarchic structure, but rather something much more chaotic. I would like to see the OSS community self-organize beyond the project level up to the distro. That means the individual project managers have to voluntarily give up some degree of control in order to support the overall vision of the community. But this is idealism on my part and really reaches far beyond just making a 'great OS' to making a diametrically opposed alternative to the corporate oligarchy that average people are *likely* to choose.

---

### Post by koenn on 2008-07-03
> **eryksun said:**
> I am familiar with the bazaar analogy, ...
Most people who know someting about open source have heard the word bazaar. That's why I added "Homesteading the Noosphere" to the reading list. It explores things such as developer motivation, sharing code in a gift culture, forking and the taboo against it, ownership of projects and how it is established,  ... . It puts what you perceive as "ego driven project forks" and "excessive parallel development" in perspective and will make clear why e.g. your statement that " ... Ubuntu should take over Debian" is utter nonsense - or at least totally unrealistic. 


I don't see anything chaotic about distributions. there are a lot of them, yes. There are also lost of different makes and models of cars, and I don't hear anyone complain that the car industry should get its act together, that BMW should take over Ford and assume leadership and set the standards or call the shots, or whatever. 

Distro's are the marketing and distribution channel for open source software projects. If they offer something the market wants or needs, they'll continue to exists. If they don't, they'll become extinct. The system as a whole organizes itself. 

There *is* an overall vision in the community. It's embedded in the free software / open source definition, the customs and values of the community,  and in the craftmanship of developers : adhere to open standards, support interoperability, and create programs that easily interface with other pograms. 

So far, this seems to be working, and if something like more centralized control would be needed, the evolutionary forces would drive the ecosystem in that direction. My guess is that if two or more of those self-organized projects need coordination between each other, they'll coordinate, or work together the way Ubuntu works with Xorg or Gnome to get the features it needs as a distro, with both the upstream projects and the other disto's that use them, benefiting from it. 

And so it comes to pass that a reputedly "difficult" distro such as Debian automagically gets a user interface and provides a user experience that is not unlike the one in Ubuntu.

(and we're back on topic)

---

### Post by cardinals_fan on 2008-07-03
I was going to respond again, but koenn just said it all for me :)

---

### Post by RiceMonster on 2008-07-03
> **eryksun said:**
> This was the basis for my apology. I want Ubuntu to be something that you, and apparently most users, do not want. I'm hoping to take on the corporate-controlled paradigm with self-organized anarchy, providing a diametrically opposed system (not just in design, but in philosophy) to Microsoft's corporate oligarchy. It's not just a matter of a pragmatic desire for a great OS. I'm an idealist.

Alright fair enough. I'll apologize as well because I was being a little hostile. Reason being, a lot of people come by here suggesting what you are, and as you can tell, people around here do not agree.

---

### Post by thtrgremlin on 2009-05-17
I realise this is a really old discussion, but still wanted to drop my 2 cents.

As a hobby developer, Bazaar struck me, as said above, really bizarre. It took me quite awhile to get anywhere (A week maybe?). My biggest surprise was just how many projects and tools out there are the contributions of a single individual sharing what they found useful and gave to others because they thought others might like it and/or hoped others would make it better.

Linux Torvalds took on Linux as a hobby project. He didn't expect it to go anywhere, especially since Herd project took the place of a free kernel. He just thought what eventually became Linux would be fun, and initially sought out others that might think it would be fun to hack a kernel together. The rest is history.

Most of my forks have gone nowhere. In part, bazaar made it easy for me to have a central location for code, and if anything came of my work, or if others were interested, they would be free to see it, download, modify, and share.

But despite the "mess" that may appear on my code page, I have fixed minor bugs, and taken patch testing to completion, and even had my work merged into trunks. The first time that happened was SUCH a thrill.

I was originally sceptical about getting involved, and even afraid that my contributions wouldn't be significant enough, or that my questions in IRC would be a hinderence, but what I kept hearing was "do whatever you want, and don't worry, that is what branches are for". As I got used to the system, I began to see how EASY it is to do code comparisons, get reviews, and most people were excited I had noticed their project on a personal level.

Not to get too political, but I see the Linux sphere as the only true objectivist / free market system in existence; it is the only place where by design government has been unable to "regulate", forcing people to work together in some way against their will. Individual projects can be tightly regulated, but each developer has the free will do do so at their discretion, but GPL/OSS et al sends a certain message about the freedom of the work.

THANK ALL that Gnu/Linux has the minimal central control necessary to allow people to be free and aspire as they wish. That freedom has been passed to me, and with gratitude I selfishly contribute where I can for my own learning, and a recognition that strokes my ego... just enough.

That is why I contribute. The only thing that could happen with a tyrannical central authority, as suggested by some; fewer forks and fewer distributions; is fewer developers and fewer contributions, no matter how you may judge their futility. The last freedom embraced under such a system would be for those that contribute their time, energy, and intelligence freely, will be their freedom to walk away.

If you like a project whose constant forking and disagreement on project direction frustrate you, you have the freedom to organize your own team, on your own time, fork your own project, and provide that type of leadership. And to any end you are successful, your contribution will be appreciated and preserved.

To what good could it be to deny that freedom of choice to yourself, and to what good would it be to deny it to others? My heart breaks for those that do not understand, but for those that do, **I** have begun to see why people become so fanatical about Linux.

---

