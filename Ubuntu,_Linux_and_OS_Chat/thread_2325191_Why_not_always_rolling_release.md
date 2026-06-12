---
title: "Why not always rolling release?"
date: 2016-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by bennylava2 on 2016-05-20
I'm hoping someone can explain some things to me about the way the distro-makers operate. I'm a bit confused as to why they do things the way they do. So as we all know, Microsoft practices rolling release. They release a particular OS, then they just release service packs and updates for it for 7 years. Well now I think they've said they're going to lower that to 5 or something, but you get the idea. For a good long time, you're going to see just the same OS, with any major changes needed, being done in the form of downloadable updates. 

Now I know that some distros do this, but most don't. IIRC Arch and Manjaro do rolling release. This appeals to me, because as a very new linux convert, it just fits in with what I'm used to. So why doesn't Ubuntu, or Mint, or all the other distros, do this as well? I mean I know that like Microsoft, yeah they'd eventually need to just release a full new OS. Or would they? If linux is so modular, and can just be gutted and rebuilt on the same install, why don't they just do "service packs" or something like M$ does? What is the point in releasing a new version of the OS every 2 or 3 years? Why not just wait a lot longer, and just do updates? 

The way it was explained to me, even major changes to the OS could actually be done without having to reinstall it or wipe the drive or anything like that. Why do some distros do rolling release, and not the way Ubuntu does it?

Also, another related question. When the next big Ubuntu comes out that you want to install, and you go to install it, will it be like going from XP to Windows 7? Do you have to pretty much wipe the old OS off, and install the new one? Or is it just like some kind of major upgrade, and you don't have to move everything you want to keep, off of that hard drive in order to do the install? I just find it all a bit confusing.

---

### Post by TheFu on 2016-05-20
Who are these MS/MSFT/Microsoft people you speak of?  Unix and the method of releases has been around longer than MS has been providing patches.  Microsoft patched by providing point-releases for many years.  There are cultural differences between the Windows and Unix worlds as well.  

Which is better rolling/point-upgrade is really a matter of opinion.  Try the rolling releases, see if you prefer it.  I do not for a number of reasons.  In the enterprise space, stability and retained functionality are MORE important than having the latest version of some software. I need for the same basic version of software to keep working and only get security patches for as long as possible. This makes my end-users happiest. They have a job to do and "new" isn't usually better in their minds.

The other questions can be answered by learning a little more about how and why Ubuntu does upgrades.   A websearch for "ubuntu upgrades" found 3 reputable sources of information for me. 2 from *ubuntu.com articles. Actually, the entire first page of results had reputable articles.

So, your questions are common enough that lots of people have asked them before.  In the Unix world, ususally a FAQ will be created to answer _Frequently Asked Questions_ like this.  If you plan to use Linux for long, it would be good to learn a little more about the OS.  Ask questions, but also do some research to show true interest.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has links to articles and resources for someone really new to linux.  The first few links should take 45 min to go over and will answer many questions in a way that someone from a Windows-centric perspective can appreciate.  Be certain to read the **Linux for Windows Users** and **Linux is not Windows** articles.  Please.

I realize that you are just asking honest questions, but referring to Microsoft's way can be seen as offensive to some people.  I could ask the same questions about why MSFT does patching the way they do it (which makes no sense to me), but I don't, since I haven't really paid much attention to what MSFT does since around 2007. 

How should you upgrade your Linux release?  As usual with Linux stuff, the answer is "it depends."  Far be it from me to tell you what can or cannot be accomplished.  Linux is extremely flexible, so you may well be able to do things that I haven't considered and everything may be just fine.  I dunno.  I don't know anyone who upgraded from WinXP to Win7. The computing power required in Win7 was 2-3x more than what WinXP would use, so everyone I know bought a new box.

In the Linux world, everyone is expected to perform backups.  It is relatively easy to do and they usually work well for all sorts of needs.  These are absolutely critical before doing patches or OS upgrades.  Trying to compare the output from a single company, with billions of USD behind their development of an OS with the 100,000 people spread all over the world working on the varied parts of every Linux system really isn't fair.  Things break sometimes.  If you want the MSFT-level of support, then you should probably pay a company at least as much as Windows costs for the same features included with any of the major distros to get that.

LTS-to-LTS upgrades have worked fairly well for Ubuntu since 8.xx.  I have a system that has been upgraded from 8.xx to 10.04 to 12.04 to 14.04.  I have many other systems where I've elected to wipe the OS and start over fresh.  Which you choose is really up to you, but please, please, please, make a backup first. Things sometimes do fail.

Anyway, hope I wasn't too scatter-brained.

---

### Post by user1397 on 2016-05-20
FYI, Windows is **not** a rolling release OS.  Each release was a static release, and you had to do a major upgrade to the next version.  Going from windows XP to Vista was like going from debian 5 to debian 6.  The latest Windows 10 is more rolling-esque, but still not quite a true rolling OS.  It mostly groups a bunch of updates together and releases those updates every now and then.  True rolling OS's like Arch have constant individual package upgrades, aka there are no update "packs" or service packs or anything like that.

The main reason most OS's and distributions are not rolling release is stability.  And before you hardcore Archers out there get your panties in a bunch, I do agree that for the most part, if maintained properly, even a distro like Arch can actually be incredibly stable.  But, and here's the big but, for an average casual non-geek user, which comprises most of humanity, a rolling release will most likely break something on their system at some point, and they'll have no idea or even care to attempt to fix the issue, and they'll probably just revert to whatever OS they were using before and call Linux "not ready for the desktop".  

So that is the main reason the static release model is used instead of rolling release...stability.  Some distros are far more conservative than others.  Debian doesn't release a new version for around 2 years (and in the Linux world, 2 years is an eon).  Ubuntu tries to keep a moderate stance by providing their ultra stable releases every 2 years, but also providing stable-ish releases every 6 months with updated software.  This model is "pretty good" and works for most people.  Most people simply don't care about having the latest updates for every program on their computer.  In fact, most people I know personally, hate updates period and always seemed bothered by them.  So imagine if Ubuntu or another major OS was rolling release...the number of complaints they would have would skyrocket.

Now, Chrome OS is an example of a rolling release OS which IS stable and very user friendly...but the difference is it is very stripped down (just the kernel, the chrome browser, and a few other things), apps are all located in an app store that is locked down tight, and people mostly buy them pre-installed on chromebooks so no hardware issues possible.

Most distros are generalist OS's, just like Windows.  They try to make them work for many different computer architectures and tons of different hardware configurations.  Being a bit buggier comes with the territory of a generalist OS.  

Btw, Linux Mint was actually doing what you said about why doesn't a distro just release service packs every now and then, with their LMDE (Linux Mint Debian Edition) version.  Not sure what its current status is, and I'm sure there's a few other distros out there that utilize this approach (can't remember any right now).

As far as your last question, Ubuntu is meant to be upgradeable from one release to the next, and although it usually works fine, it isn't foolproof.  I'd always recommend backing stuff up no matter if you're upgrading or doing a clean install, and just know that after upgrading if you encounter any issues, you may have to reinstall.  Going from a non-LTS version to the next version isn't usually a drastic change, but going from an LTS to the next LTS can be quite drastic sometimes, so that might be comparable to going from Windows XP to 7 (but it's hard to say that as they are so different in many ways).

---

### Post by grahammechanical on 2016-05-20
> So as we all know, Micro$oft practices rolling release. They release a  particular OS, then they just release service packs and updates for it  for 7 years.

I would not call that "rolling release." And there will be plenty of other people who will agree with me.

> If linux is so modular, and can just be gutted and rebuilt on the same  install, why don't they just do "service packs" or something like M$  does?

The Linux kernel may or may not be modular and I think that there are people who would argue over that matter. But it is not relevant to the issue of keeping a Linux distribution up to date with the developments to the kernel made by the Linux kernel developers.

The Windows operating system is owned and developed by one massive, mega rich corporation. Linux distributions are often constructed by a few programmers some of whom will be working unpaid. And it is a construction job as components are pulled together from many other Free & Open Source Software (FOSS) projects. 

The whole point of FOSS, as I see it, is not to be like Microsoft or Apple but for programmers to follow their own vision of what a computer operating system should be. And that also means that there are distributions that do things differently to the way things are done in Ubuntu and Fedora and other major Linux distributions. It is part of meaning of freedom.

As for your related question. Stick with an Long Term Support (LTS) release like 16.04 and you do not have to think about the matter of upgrading for almost five years. Upgrading one default installed version of Ubuntu to a newer version is indeed just like some kind of major upgrade. Problems come when we (the user) modify the desktop excessively. The developers cannot take into account every variation a user might make to their operating system.

And this is why some of us recommend backing up and doing a fresh install of the new version. Always back up what is important to us.

Regards.

---

### Post by Geoffrey_Arndt on 2016-05-20
Benny . . just for future reference when posting . . . no need to say that you're "confused" . . . believe me, after two or three sentences we will know if you're confused or not.

---

### Post by craig10x on 2016-05-21
Actually, as of Windows 10, it IS kind of a rolling release...aside from getting the cumulative updates once per month (which fix bugs and improve stability) there is a major build upgrade that will be done at least once a year (next one scheduled for this summer (on the anniversary date of the premier of windows 10)...with that, you get all kinds of new features as well...so, i guess you could say it doesn't roll on a daily basis but it does roll periodically...they haven't yet decided how often those build upgrades will occur but they could do it as much a 3 times a year, though that will probably vary...The insiders (testers) get quite a few new builds...

Although, i suppose some would say it is kind of like upgrading to the next version of ubuntu...But there will be no more new versions of windows (10 being the final one) and from this point it is just going to be called Windows...in other words, there will be no windows 11, 12, etc..

---

### Post by grahammechanical on 2016-05-21
If anyone wants to use a "rolling release" version of Ubuntu or any of the flavours, then install the development version of the next release of Ubuntu. That gets daily updates/upgrades to the packages that go to make up the Ubuntu distribution.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

[http://iso.qa.ubuntu.com/qatracker/milestones/360/builds](http://iso.qa.ubuntu.com/qatracker/milestones/360/builds)

And then when 16.10 is released convert the installation to the next version under development (17.04).
> 
graham@sdb7-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety

Regards.

---

### Post by kansasnoob on 2016-05-21
> They release a particular OS, then they just release service packs and updates for it for 7 years. Well now I think they've said they're going to lower that to 5 or something, but you get the idea. For a good long time, you're going to see just the same OS, with any major changes needed, being done in the form of downloadable updates. 

Ubuntu LTS is not that far from such a model, for reference look here:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You can see there that Ubuntu produces a new release every six months, but once every two years they produce an LTS (Long Term Support) version that's supported for 5 years. These LTS versions are initially released in April of even numbered years, eg; April 2012 = 12.04, April 2014 = 14.04, April 2016 = 16.04, etc. The interim "normal" releases are only supported for 9 months.

IMHO all of the "final" releases (both LTS and normal) are beta quality for the first couple of months following release so the average user is best served waiting for at least a couple of months following release to jump in, and then apply all available updates after installation before jumping to any conclusions regarding usability. Of course there are those who like to live on the bleeding edge but they typically don't mind tackling bugs.

The LTS versions also have 5 point releases, eg; 14.04.1, 14.04.2, 14.04.3, 14.04.4, and 14.04.5. The first of these point releases is typically released with bug fixes 3 to 4 months after the initial release (in July or August) and still uses the original series kernel with matching X-stack so IMO that's the version most average users should try first because the 2nd, 3rd, and 4th point releases present the user with HWE EOL upgrades shortly after the 5th point release comes out. For reference see here

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Just for example lets look at the Precise (12.04*) support cycle since all 5 point releases are already in existence:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A12.04.x_Ubuntu_Kernel_Support)

As you can see there those who installed using the 12.04.2, 12.04.3, and 12.04.4 installation media reached HWE EOL much sooner requiring an HWE upgrade:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Sadly both these HWE upgrades and standard release upgrades (eg: Precise -> Trusty) seem to be problematic for many users, especially those who have added software from sources other than the official repos. That's the reason I highly recommend always trying the first point release images first, and only if needed for newer hardware compatibility using the later point release images.

No better time than now to use as an example. I've sadly encountered too many bugs and usability issues with Xenial (16.04) to consider installing it for use by most average users. But if I install using the 14.04.1 (Trusty) media it's still supported until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

By then there will already be another LTS (18.04) so I can decide whether to upgrade those machines to 16.04 or skip 16.04 altogether and jump right from 14.04 to 18.04 :)

Note: the other Ubuntu flavors typically only provide 3 years of support for LTS versions rather than Ubuntu's 5 years.

Have I confused you yet? Please feel free to ask more questions.

---

### Post by bennylava2 on 2016-05-22
> **TheFu said:**
> Who are these MS/MSFT/Microsoft people you speak of? 
Which is better rolling/point-upgrade is really a matter of opinion.  Try the rolling releases, see if you prefer it.  I do not for a number of reasons.  In the enterprise space, stability and retained functionality are MORE important than having the latest version of some software. I need for the same basic version of software to keep working and only get security patches for as long as possible. This makes my end-users happiest. They have a job to do and "new" isn't usually better in their minds.

Makes sense. Never thought about it that way. Thanks for clearing that up! With windows it becomes like a sort of comfort zone, the way they do updates. I guess I shouldn't be comforted by it, cause they don't always address everything, and in the past the updates have been known to occasionally break things and or be an update that for whatever reason, you don't want. 

> **TheFu said:**
> 
So, your questions are common enough that lots of people have asked them before.  In the Unix world, ususally a FAQ will be created to answer _Frequently Asked Questions_ like this.  If you plan to use Linux for long, it would be good to learn a little more about the OS.  Ask questions, but also do some research to show true interest.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has links to articles and resources for someone really new to linux.  The first few links should take 45 min to go over and will answer many questions in a way that someone from a Windows-centric perspective can appreciate.  Be certain to read the **Linux for Windows Users** and **Linux is not Windows** articles.  Please.

I read the Linux for Windows users, because that one seemed like good material. It was quite helpful, I must say. I can't say I see the need to read "linux is not windows" because that much is very clear, and is in fact painfully obvious in my recent dealings with Zorin. Which I may now have to reinstall, for the 3rd time. It seems to be quite fragile and break fairly easily. 


> **TheFu said:**
> 
I realize that you are just asking honest questions, but referring to Microsoft's way can be seen as offensive to some people.  I could ask the same questions about why MSFT does patching the way they do it (which makes no sense to me), but I don't, since I haven't really paid much attention to what MSFT does since around 2007. 

This is hilarious to me for some reason. When I read that fist sentence I couldn't help but laugh. I guess my response to anyone who gets offended by someone elses experience with a computer program/s, would be "I don't care" and "they'll get over it". 


> **TheFu said:**
> 
How should you upgrade your Linux release?  As usual with Linux stuff, the answer is "it depends."  Far be it from me to tell you what can or cannot be accomplished.  Linux is extremely flexible, so you may well be able to do things that I haven't considered and everything may be just fine.  I dunno.  I don't know anyone who upgraded from WinXP to Win7. The computing power required in Win7 was 2-3x more than what WinXP would use, so everyone I know bought a new box.

I'm afraid they were doing it wrong. I am running windows 7 just fine on an HP from 2001. I did purchase $32 worth of RAM upgrade, and have since bought a bigger hard drive for more storage space, but the HDD wasn't a necessity for running W7. Makes a great shop computer for when I need to look something up about a car real quick. I have several old "junkers" like that for various tasks running W7. The wife's craft room, and an HTPC. I can't see why anyone would really need to buy a new box just to go from windows XP to 7. Or even 10, depending on the circumstances. Its not that, that I take issue with. Its the spying and the forced updates and M$'s general attitude towards the customer. They clearly view the customer as an obstacle, and not... a customer. 

> **TheFu said:**
> 
Trying to compare the output from a single company, with billions of USD behind their development of an OS with the 100,000 people spread all over the world working on the varied parts of every Linux system really isn't fair.  Things break sometimes.  If you want the MSFT-level of support, then you should probably pay a company at least as much as Windows costs for the same features included with any of the major distros to get that.

Yeah that is a very good point. I was just hoping for more I guess. But one that I wish was brought up more often, instead of people getting defensive. More stability, more easy of use, more intuitive...ness. And perhaps a layout that I was at least somewhat familiar to me, which is why I chose Zorin to help ease the transition. 


> **TheFu said:**
> 
LTS-to-LTS upgrades have worked fairly well for Ubuntu since 8.xx.  I have a system that has been upgraded from 8.xx to 10.04 to 12.04 to 14.04.  I have many other systems where I've elected to wipe the OS and start over fresh.  Which you choose is really up to you, but please, please, please, make a backup first. Things sometimes do fail.

Will do. Yet another thing I don't know about linux... can you upgrade from say... ubuntu 8 to 14 without having to wipe the hard drive and start over fresh? If so then unfortunately my OP was probably invalid. But hey, I'm almost completely ignorant when it comes to Linux. 

> **TheFu said:**
> Anyway, hope I wasn't too scatter-brained.

Not too scatterbrained at all, it was a very helpful post. Hopefully I can find a distro that I am comfortable with, and that is... durable? Can take a beating? Not real sure what my issue is.

---

### Post by mastablasta on 2016-05-23
> **bennylava2 said:**
> 
Will do. Yet another thing I don't know about linux... can you upgrade from say... ubuntu 8 to 14 without having to wipe the hard drive and start over fresh? If so then unfortunately my OP was probably invalid. But hey, I'm almost completely ignorant when it comes to Linux. 


you sure can: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


what you said about windows - they are not rolling they are basically LTS. you will sere that they have same kernel version and such even after service packs. ubtunu 14.04.1, 14.04.2 ... are all basically "service packs".

Red Hat will do this for 10 years with their LTS.

windows 10 is kind of semi rolling for now. but we will see how long they can do this. i mean what happens when they do the auto upgrade after 5 years and hardware stops working? or do they plan to provide full backwards compatibility?

for a user that wants to live onbleeding edge semi rolling like Mint LMDE, Manjaro or OpenSUSE Tumbleweed might be a better choice.

rolling releases basically get new features and just get pushed to user. minimum bug fixes - this means you computer can stop working. try arch, you will see that mostly all will work fine but every now and then be prepared to hunt for a workarround. in business environemnt this is not acceptable. imagine having 10.000 or more PC's all stop working at once. it's a nightmare in an environment where every lost second is lost money. costs can go into millions.

---

### Post by bennylava2 on 2016-05-23
> **mastablasta said:**
> In business environemnt this is not acceptable. imagine having 10.000 or more PC's all stop working at once. it's a nightmare in an environment where every lost second is lost money. costs can go into millions.

True but I think most businesses use windows for their desktops.

---

### Post by TheFu on 2016-05-23
> **bennylava2 said:**
> Makes sense. Never thought about it that way. Thanks for clearing that up! With windows it becomes like a sort of comfort zone, the way they do updates. I guess I shouldn't be comforted by it, cause they don't always address everything, and in the past the updates have been known to occasionally break things and or be an update that for whatever reason, you don't want. 

Updates in the F/LOSS world come from many different project teams. Many/Most of these teams are very informal and have nothing to do with any company. Some of the larger projects ARE formal and have corporate backing.  Usually, there isn't much difference in the quality of the software produced, so this isn't a way to measure or choose anything.  At least IME.  The corporate-backed projects tend to ignore suggestions from end-users.  They have a vision and perhaps it will be great, but not always.  
Smaller teams tend to listen to end-user feedback, provided it is constructive and along the lines of how that team believes it should work.  

> **bennylava2 said:**
> 
I read the Linux for Windows users, because that one seemed like good material. It was quite helpful, I must say. I can't say I see the need to read "linux is not windows" because that much is very clear, and is in fact painfully obvious in my recent dealings with Zorin. Which I may now have to reinstall, for the 3rd time. It seems to be quite fragile and break fairly easily. 

Actually, the *linux is not Windows* article would have helped with understanding the ***culture*** of Unix and Linux - that is at least as important as the mechanics.  Being insensitive to our culture can be seen as rude.  It will help you interact with people who are highly involved in that culture in a more productive way, for example. There are other items in that article which would be helpful to know as well.


> **bennylava2 said:**
> 
This is hilarious to me for some reason. When I read that fist sentence I couldn't help but laugh. I guess my response to anyone who gets offended by someone elses experience with a computer program/s, would be "I don't care" and "they'll get over it".   

They may have the information that you'd like to know, so productive interaction with them could be in your best interest.  Not everyone has used or seen Windows and if they have, they may not have followed it in many years.  I'm coming up on a decade of not-caring anything about Windows or Microsoft.

> **bennylava2 said:**
> 
I'm afraid they were doing it wrong. I am running windows 7 just fine on an HP from 2001. I did purchase $32 worth of RAM upgrade, and have since bought a bigger hard drive for more storage space, but the HDD wasn't a necessity for running W7. Makes a great shop computer for when I need to look something up about a car real quick. I have several old "junkers" like that for various tasks running W7. The wife's craft room, and an HTPC. I can't see why anyone would really need to buy a new box just to go from windows XP to 7. Or even 10, depending on the circumstances. Its not that, that I take issue with. Its the spying and the forced updates and M$'s general attitude towards the customer. They clearly view the customer as an obstacle, and not... a customer. 

They weren't doing it wrong, not for them.  They are end-users.  They are more concerned about their vehicles running so they can get to work than they are about some computer used to check sports scores.

IMHO, running a PC from 2001 today is foolish. Slow, high power use are just a few reasons NOT to bother.  It is amazing what a $100 PC upgrade can accomplish. That is a topic for a different thread.

> **bennylava2 said:**
> 
Yeah that is a very good point. I was just hoping for more I guess. But one that I wish was brought up more often, instead of people getting defensive. More stability, more easy of use, more intuitive...ness. And perhaps a layout that I was at least somewhat familiar to me, which is why I chose Zorin to help ease the transition. 

Linux is very easy to use, once you get a little knowledge about the non-GUI parts of the system. Unlike with Windows and OSX, the GUI is **not** the OS on Unix/Linux systems.  The GUI is just another program which can be swapped in or out as you like - just like a word processor. Pick what you like, install it. See if you really like it or not for yourself.  No need to use a different release just to have a different GUI.  I would say that anyone loading a different distro just to have a different GUI is "*doing it wrong*."

> **bennylava2 said:**
> 
Will do. Yet another thing I don't know about linux... can you upgrade from say... ubuntu 8 to 14 without having to wipe the hard drive and start over fresh? If so then unfortunately my OP was probably invalid. But hey, I'm almost completely ignorant when it comes to Linux. 

Any release from 2008 hasn't been supported in years, so anyone running that old of a release wouldn't be helped here. It is against forum rules to help non-supported releases. This is necessary for a number of reasons, which I happen to agree with.  Today, that means 12.04, 14.04, 15.10 and 16.04 are the only desktop releases supported. 15.10 support ends in a few months. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - note the different point-release support dates.

Linux is extremely flexible.  You can do *anything* you can make happen.  Whether that is a good idea or not, is a completely different question.  Try it. See how well or how bad it works.  If you've installed a bunch of 3rd party programs and tools, then the upgrade through all those releases will probably fail. OTOH, if you've been cautious and only used core Canonical repositories, then the upgrade will probably mostly work.

The main thing to understand for people coming from Windows is that you shouldn't download a package and try to install that directly. Really need to stay within the current package repositories provided by the installation and use those versions until a good understanding of the risks of using other PPAs or manual package installations is fully understood. There are real, significant, risks.  The problems don't show up immediately, usually it takes 6 months to a year for those difficult programs to show up.

With all this flexibility, there is a requirement that Linux users be a little more knowledgeable about their systems or risk massive failures.  After all, how many people would swap out the engine for their car without doing lots of research? 
 

> **bennylava2 said:**
> 
Not too scatterbrained at all, it was a very helpful post. Hopefully I can find a distro that I am comfortable with, and that is... durable? Can take a beating? Not real sure what my issue is.

Distros are just a short-cut to preload most of the things you want for the OS.  Nothing more.  Any distro can do 98% of the things that all the the other distros do.  Of course, there are some highly specialized distros - like for routers - which aren't as flexible, but all the big 15 distros can.  The main choice for picking a distro for me is which has predictable security patching and predictable schedules?  Which have had trouble with their repos being hacked and which have long-enough support for my needs with overlap so I can migrate systems on my time-frame.  For me, there are just 4 possible distros which meet my requirements.

Good dialog.

---

### Post by mastablasta on 2016-05-23
> **bennylava2 said:**
> True but I think most businesses use windows for their desktops.

exactly and they do not upgrade or update at will. the upgrades are uusally made by testing hardware first and software. for example we skipped windows vista completelly as it was not suitable.

updates are done in same way. first they are reviewed and tested and only then do the employees receive the update. they are not pushed to computers immediatelly when they become available by MS (unless they are urgent security patches). they have ot be reviewed and approved first.

so what will happen when windows goes rolling and they find out the updates woudl break numerous systems still in use? 1 they do not apply them, 2 the upgrade the hardware, 3 move away ofrm widnows (?!) i am not sure this is an option if you are so invested.

we were just forced into doing upgrade to office 365 from 2013 and already there is unhapiness and complaining among some IT regaridng this forcefull update. 

onthe other hand i find it silly that we do not use Linux desktop - majority of apps have good alternatives or work on Linux (linux clients). MS Office is still better than alternatives and i think if this got fixed or if really good or at least 100% compatible alt. existed in Linux they might move. eventhough MS office is still better (by better i mean to me personally it is easier to use) than say LO.

---

### Post by TheFu on 2016-05-23
> **bennylava2 said:**
> True but I think most businesses use windows for their desktops.

Most old-world business, yes.  Most people working in new-style, internet-centric, businesses use a mix with lots of OSX and Linux desktops.  

My last job didn't specify computers or OSes - each employee was paid sufficiently to provide their own computing devices.  We had a Windows terminal server that could be remotely accessed by anyone to use Windows document programs as needed, so they didn't need to be stuck with Windows on their systems. Plus it removed the need to track MS-Office licenses.  This was clear in the employment contract.  Some people used 10 yr old Windows and some people had a $2K new Mac yearly.  I had an 11in chromebook, $500 15in laptop and $400 desktop paid for by the company, but these were part of my compensation. Everyone treated their equipment like it was their own - er - because it was. This taught me that I didn't need a laptop anymore. Now I have a beautiful 13in chromebook (4G RAM, Core i3, 1080p screen) running Ubuntu Server with a lite-GUI and that same desktop (plus 5-ish other computers 'cause that's the way I roll). ;)

Actually, there are 9 computers in the room with me now - all have some form of Unix/Linux loaded
1) Chromebook
2) Raspberry Pi  (Kodi)
3) Android Phone
4) TiVo (powered off)
5) WD-TV Live HD (powered off)
6) mediaGate (powered off)
7) Android tablet
8) AMD E-350 (powered off, will be repurposed as a NAS)
9) new router ... ok - this will have pfSense (BSD) loaded, not Linux. [http://pcengines.ch/apu2c4.htm](http://pcengines.ch/apu2c4.htm)

No Windows computers in this room at all.  There is an old laptop in another room and a Win7 instance running under a virtual machine in another room too. Both of those other systems run Linux too - with the virtual machine system running 8 other VMs - all Linux. ;)   BTW, that other room has more computers than this one - all running BSD/Unix/Linux except those 2 specific Windows licenses.  About 30 Unix instances total in the other room.

It is a Linux world for some people.  That's all that I'm sayin'.  Visit your local LUG (Linux Users Group) and you'll find lots of people running mostly Linux systems for home and work.

---

### Post by bennylava2 on 2016-05-23
> **TheFu said:**
> They weren't doing it wrong, not for them.  They are end-users.  They are more concerned about their vehicles running so they can get to work than they are about some computer used to check sports scores.

IMHO, running a PC from 2001 today is foolish. Slow, high power use are just a few reasons NOT to bother.  It is amazing what a $100 PC upgrade can accomplish. That is a topic for a different thread.

Thanks for the long reply. Very helpful to me. I have learned a lot just from this one thread. This quote is the only thing I saw the need to address, from that reply. What I was saying was, that was their choice, they didn't have to. If they felt they had no choice, then I'd still have to say they were doing it wrong. As is evidenced by my age old computers that run windows 7 just fine. If they were just using the computer for home use as internet machines, which would seem to be the most likely scenario, then they could have easily just bought some RAM and installed 7 on their XP machine. If not and they were business people of some kind then I'd still say it would be a case by case basis. One of the things I do for side cash is fix people's busted windows machines. I must have put 7 on a xp computer 100 times, and never once had a problem. Now that's changed and I'm putting 10 on people's 8 machines, and giving it the W7 interface. 

I'm testing out the Linux desktop for myself, and for my computer repair customers. Many of them really don't care what OS it is, as long is it feels familiar, and will internet and email. That is what attracted me to Zorin, but I don't think its ready for prime time. At least not if my experience with it is any indicator. 

> **TheFu said:**
> Most old-world business, yes.  Most people working in new-style, internet-centric, businesses use a mix with lots of OSX and Linux desktops.  

My last job didn't specify computers or OSes - each employee was paid sufficiently to provide their own computing devices.  We had a Windows terminal server that could be remotely accessed by anyone to use Windows document programs as needed, so they didn't need to be stuck with Windows on their systems. Plus it removed the need to track MS-Office licenses.  This was clear in the employment contract.  Some people used 10 yr old Windows and some people had a $2K new Mac yearly.  I had an 11in chromebook, $500 15in laptop and $400 desktop paid for by the company, but these were part of my compensation. Everyone treated their equipment like it was their own - er - because it was. This taught me that I didn't need a laptop anymore. Now I have a beautiful 13in chromebook (4G RAM, Core i3, 1080p screen) running Ubuntu Server with a lite-GUI and that same desktop (plus 5-ish other computers 'cause that's the way I roll). ;)


I'm a certified ac repairman, I've been to 100's of different businesses over the years to fix their air conditioners. Grocery stores, Walmart, Shopping malls, homes, high rises, I've done it all. I'm also well known for fixing windows machines in my area, so sometimes I can make a little extra at some of these places if I can offer some help. I got a free cart of groceries at HEB a year ago just for reinstalling M$ office for them. Of course I was already there to fix one of the air conditioners, but someone there knew I worked on desktops as well. Manager said it was a deal cause it was a lot less than he would have paid the IT company they use. In all of my travels, to 100's of different businesses, I have never once seen a Linux desktop. Not one time. Mac makes an appearance, rarely. If I had to put a percentage to it from my personal experiences, I'd have to say its been about 99% Windows, 1% Mac. This is in the Dallas Texas area.

---

### Post by ZoiaGuyver on 2016-05-23
You don't see Linux on a desktop it's not what companies get a good deal on (or so they think) so they use Windows as a front end, but go to the tills and look at the PoS machines or any of the infrastructure behind it, It's probably Linux/Unix.

Looking at it from the outside most wouldn't see Linux, but believe me it's there, Banks, Stores, Online shops. Linux just isn't used as the forward facing stuff (unless its Android or the likes). A lot of that comes down to the choice of software that Linux has and how configurable it is across the spectrum. Companies think it's complicated (especially the higher ups that actually have to ok the costs). It's also a problem with how Linux is still perceived even today, it's still seen as a "geek/nerd" thing. 

You're question about why not a rolling release has been covered mainly by what others have said, It's about stability the LTS releases are great for that (looks at companies like Google who use the LTS releases). 

Trying to sell to a company and saying they can have support for the OS they run for 3/5 years, at a far reduced cost due to licensing (once you mention less money normally that perks the ears up) is far easier than going to them and asking them to take a risk on a rolling release that 9/10 can and will break at some point due to an update. It's also cost effective for the company supplying the support it means less overhead for them. The stability of distros like RHEL/SLED/Ubuntu which don't do a rolling release but have short release cadences (or constantly evolving community projects) with a Long Term release at set intervals also allows companies to plan their IT strategy. 

Try to plan an update schedule on a rolling release or an upgrade window, it's nigh on impossible, especially with larger contracts. 

From an "average" user point of view they see all the media/adverts about Windows and take it that is the "default" and only choice. Linux doesn't have that backing, or well it didn't. If you look now at the rise of Chromebooks, Android phones, Streaming boxes (like Roku/Chromecast/Kindle) I guess you could say companies have been successful in marketing Linux. It still isn't "mainstream" though, we need to get rid of that stigma (Linux being complicated) and tbh aslong as people in the free software/open source community keep arguing over minute details (while interesting) doesn't help the marketing at all.

---

### Post by Geoffrey_Arndt on 2016-05-23
Good response to post #15 from Zoia.    Often, people don't know what to look for regarding the OS interface.    Recently I noticed the "Lowes" Home Improvement chain in the US uses a Linux front-end and back-end on the POS terminals.   It's actually a modified XFCE desktop that also calls up an ncurses text window for the actual sales transaction.    Once you go into the colleges, the tech areas of NASA, CERN and so on - - you see lots more Linux desktops.

But what I don't like to read from the OP - - is the implication that because Linux is rare to non-existent on the desktops of the home & businesses he's attended to . . . therefore it must mean Linux is just not as "ready for primetime" as Windows is.  
That's clearly an incorrect conclusion.    There is a saying . . . build a better mousetrap and the world will beat a path to your doorstep.   Well, that's just not true.   When the laws of business physics are altered by "monopolies" . . . . the best (OS) doesn't always win.

---

### Post by RichardET on 2016-05-23
Linux was never meant to be a windows replacement OS;  it was meant to be a "free" version of Minix, and by extension, Unix.

---

### Post by bennylava2 on 2016-05-24
> **RichardET said:**
> Linux was never meant to be a windows replacement OS;  it was meant to be a "free" version of Minix, and by extension, Unix.

If I take your meaning correctly (and I may be wrong) that's not exactly true. I've been watching a lot of vids featuring Linus Torvalds, and he does express a desire to see a lot more desktops using linux. He wants to see the big sellers (like HP and Dell) shipping with a Linux OS preinstalled. So... he definitely believes it could be a windows replacement. I didn't hear him saying anything about wanting those computers to also have windows on them.

---

### Post by TheFu on 2016-05-24
> **RichardET said:**
> Linux was never meant to be a windows replacement OS;  it was meant to be a "free" version of Minix, and by extension, Unix.

I'm fairly certain that has been vastly extended.  Sure, Linus started out writing a terminal emulator, then a minimal OS with GNU stuff on top, but within a year after that, it was clear that Linux was going to be a general purpose, desktop and server.  

Certainly for the last 15-20 yrs, Linux has been targeted for use by computing devices of any sort.  95% (I'm guessing) of the HPC systems run Linux. The other competitors running other OSes are completely sponsored by the OS maker just to save face. Microsoft and IBM are usually in the mix with the best HW money can buy. Nobody in the real world would ever deploy those systems without much free software and drug use for the decision makers ... which explains why the USGov has some.

HEB - I miss HEB.  Publix is nice, but nowhere near the same variety.  OTOH, Publix doesn't charge for plastic bags. Can't even get a good Shiner Premium where I live now. ;(  UT alumni here.  Don't get me started about state income taxes.  At least we don't have water rationing here.  Much to miss about Texas, but I prefer the climate here.

Dell does ship Linux on their machines.  A friend of mine got an XPS-13 (beautiful, but expensive) machine with the infinite display, core i7, Linux preinstalled. 

Mom and Pop companies seldom have non-MSFT solutions. This is because they often buy computers from the big-box stores and don't have a true polyglot IT person.  Just like I never recommend Windows to my clients, other people doing IT work only recommend **the devil they know** - usually MSFT.  Cannot blame them for that.  If you know how to make a tuba sing, you aren't likely to push a clarinet.  I wouldn't expect an Oracle DBA to push Postgress either.

---

### Post by grahammechanical on 2016-05-24
> XPS-13 (beautiful, but expensive) machine

Perhaps that comes from the assumption that anyone who wants to buy a machine with Linux/Ubuntu pre-installed must surely be a developer and that they want/need powerful hardware. From a business point of view, Dell may be right. They certainly do not see Ubuntu machines as having mass market appeal. And they may be right about that as well.

Any Ubuntu developer will know how to install Ubuntu on a Windows machine. But why pay for an OS that you do not want to use? As an ordinary user whose wife wants a laptop I know that the most reasonably price, readily available, over the counter purchased, machines come pre-installed with Windows. But I do not want to pay for something that I would not use. So, if we buy a laptop then Windows is what will get used.

Regards.

---

### Post by RichardET on 2016-05-24
> **bennylava2 said:**
> If I take your meaning correctly (and I may be wrong) that's not exactly true. I've been watching a lot of vids featuring Linus Torvalds, and he does express a desire to see a lot more desktops using linux. He wants to see the big sellers (like HP and Dell) shipping with a Linux OS preinstalled. So... he definitely believes it could be a windows replacement. I didn't hear him saying anything about wanting those computers to also have windows on them.

Most Linux advocates, including myself, would like to see a greater Linux desktop market share, but my point is that those who like and use Linux, and who advocate for it, should avoid these discussions about why Linux is a 2.5 inch diameter circle compared with Windows 20 inch circle.

---

### Post by TheFu on 2016-05-24
> **RichardET said:**
> Most Linux advocates, including myself, would like to see a greater Linux desktop market share, but my point is that those who like and use Linux, and who advocate for it, should avoid these discussions about why Linux is a 2.5 inch diameter circle compared with Windows 20 inch circle.

Better marketing, better shelf placement, and more use in educational institutions.  We've seen this before with other OSes - SunOS ruled the University workstation market for years because they discounted the HW and SW to those institutions.  Apple learned from this and did the same, gaining a foothold which exists today.  Microsoft has done the same thing the last 10 yrs and they've also gotten a foothold.

There aren't any Linux companies pushing Linux solutions into educational environments. It is always grass-roots.  A nearby school district deployed all Linux servers about a decade ago.  When the contract was up, that team left.  At the first problem, the responsible person called an "IT Company" who knew ZERO about Linux/Unix and proceeded to apply Windows-thinking to Unix issues.  Rather than admit they didn't have the correct skills, they wiped all the servers, installed Windows OSes, and charged the district threw-the-nose.  I'm certain there is a different take on this - those linux guys should never have been allowed in, look at all the time and money we've wasted fixing the problems they created.

You'd think I'd be thrilled when schools deploy chomebooks?  I am not.  This is trading 1 master (Apple/Microsoft) for another (Google).  At least the HW is cheaper, though ChromeOS does have a habit of tracking everything done on those devices.  I'm all for open-data formats and using federated services based on standards.  Centralized services and proprietary data are just as much an issue as proprietary OSes to me.

If you start a 7 yr old out on Linux, not Windows, they will grow up to be a cross-OS user.  
If you start a 7 yr old out on Windows, they will become a Windows user, because that is all they will ever see.

It is just like a foreign language.

---

### Post by Geoffrey_Arndt on 2016-05-24
Linux advocate or NOT . . . that's really not the point.   

 If anyone logically thinks it remotely acceptable to have 1, 2 or even 3 "closed - black box systems" (Apple, Google and MS) controlling 98% of the desktop/laptop market . . . that's just nuts because we've traded freedom, security & technical excellence  for lower entry costs and mind-numbing standardization.   This eventually leads to stagnation - - remember IE 6 if doubtful.    

ps note - - Google is kind of a hybrid in the scenario painted above.   Not totally closed, but skirting the edge (but that jury is still out at this time).

---

### Post by bennylava2 on 2016-05-24
> **RichardET said:**
> 

I disagree. It helps iron out the differences and problems for new users like myself. Not talking about it, isn't going to help. 


[QUOTE=TheFu;13494226]Better marketing, better shelf placement, and more use in educational institutions.  We've seen this before with other OSes - SunOS ruled the University workstation market for years because they discounted the HW and SW to those institutions.  Apple learned from this and did the same, gaining a foothold which exists today.  Microsoft has done the same thing the last 10 yrs and they've also gotten a foothold.

There aren't any Linux companies pushing Linux solutions into educational environments. It is always grass-roots.  A nearby school district deployed all Linux servers about a decade ago.  When the contract was up, that team left.  At the first problem, the responsible person called an "IT Company" who knew ZERO about Linux/Unix and proceeded to apply Windows-thinking to Unix issues.  Rather than admit they didn't have the correct skills, they wiped all the servers, installed Windows OSes, and charged the district threw-the-nose.  I'm certain there is a different take on this - those linux guys should never have been allowed in, look at all the time and money we've wasted fixing the problems they created.

You'd think I'd be thrilled when schools deploy chomebooks?  I am not.  This is trading 1 master (Apple/Microsoft) for another (Google).  At least the HW is cheaper, though ChromeOS does have a habit of tracking everything done on those devices.  I'm all for open-data formats and using federated services based on standards.  Centralized services and proprietary data are just as much an issue as proprietary OSes to me.

If you start a 7 yr old out on Linux, not Windows, they will grow up to be a cross-OS user.  
If you start a 7 yr old out on Windows, they will become a Windows user, because that is all they will ever see.

It is just like a foreign language.

In 1995 my school was given over 50 gateway desktops running windows 95. A free gift from microsoft. I still remember the teachers and librarians and such talking about how it was a great thing because kids could learn computers and be more ready for the world now. Probably true for that time. 

But I see a lot of opinions out in this thread, that are starkly contrasted by many of the real people involved with linux, and not just end users. Linus being one. He said we should all be damn glad Google made android. It was a great day for linux. I'm seeing a lot of counter productive logic in here. Its also widely accepted, that too many cooks spoils the dish. Mac, M$, and Android all have one cook that is superb at their jobs. Absolutely superb. To get the OS out there and widely used. Linux has 50,000 cooks and if my recent experience just trying to get it installed is any indicator, that's a bad thing. Now obviously I'm not saying we should have one distro like Ubuntu and that's it. (although I'd still like to see the result of that from an alternate universe) But it would be cool if everyone worked on just say, a total of 5 distros, and those distros eventually had to compete and the best one won and the others died. Or, instead of that, since linux is so modular and so much like a lego set, just still have the one main distro, and if you want it to be like arch, or mint, or whatever, you can carve it up like a roast and put whatever you want in there. But everyone works on and starts with ubuntu. And you have to make your mods (like say arch or manjaro) work very easily with ubuntu, getting it all installed and going. Or insert best choice for that here, but since this is the ubuntu forum and its the most popular, my guess is that it should be ubuntu.

---

### Post by Geoffrey_Arndt on 2016-05-25
One reason (of several) Linus said what he did about Google & Chromebooks is - - the marketing & design $$$ that Google injects into new users running the "Linux Kernel" . . . the kernel was/is the main point of focus for Linus.

Re too many cooks - if 50,000 system folks were just working on one, two or a few aspects of Linux - there would be an issue.   But that''s not remotely the case - - especially concurrently.    Windows & Apple actually have more hands in the "same" part of the kitchen by a substantial margin.

MS in particular, but Apple also, must think Linux is superb, _as each has emulated Linux in many ways since 2003/2004_.    The concept of live rescue iso's, the use of virtual desktops, the use of centralized repositories for software, the use of the Linux CLI (much more flexible and powerful than MS shell), the concept of device/OS "convergence" and the list goes on and on.    How about Open Stack - Cloud - Juju - Joomla, WordPress, etc..   _Linux owns the internet_, owns the 3 classes of mainframes, and has over half of the server market.    As Snappy Core starts to be adopted more & more - - it will also own the IoT environment.    Satya (a fellow alum) is sharp enough to know these things, and that's why he's orchestrated the recent partnerships with Canonical and Redhat.

Time to do a head-check on some of your off-base assumptions - - use and learn Linux for about a year and come back to revisit those assumptions (most of which are incorrect - - such as "everyone works on and starts with Ubuntu".)

---

### Post by bennylava2 on 2016-05-25
> **Geoffrey_Arndt said:**
> One reason (of several) Linus said what he did about Google & Chromebooks is - - the marketing & design $$$ that Google injects into new users running the "Linux Kernel" . . . the kernel was/is the main point of focus for Linus.

Re too many cooks - if 50,000 system folks were just working on one, two or a few aspects of Linux - there would be an issue.   But that''s not remotely the case - - especially concurrently.    Windows & Apple actually have more hands in the "same" part of the kitchen by a substantial margin.

MS in particular, but Apple also, must think Linux is superb, _as each has emulated Linux in many ways since 2003/2004_.    The concept of live rescue iso's, the use of virtual desktops, the use of centralized repositories for software, the use of the Linux CLI (much more flexible and powerful than MS shell), the concept of device/OS "convergence" and the list goes on and on.    How about Open Stack - Cloud - Juju - Joomla, WordPress, etc..   _Linux owns the internet_, owns the 3 classes of mainframes, and has over half of the server market.    As Snappy Core starts to be adopted more & more - - it will also own the IoT environment.    Satya (a fellow alum) is sharp enough to know these things, and that's why he's orchestrated the recent partnerships with Canonical and Redhat.

Time to do a head-check on some of your off-base assumptions - - use and learn Linux for about a year and come back to revisit those assumptions (most of which are incorrect - - such as "everyone works on and starts with Ubuntu".)

That's not actually what I said. That was an example given, in a hypothetical scenario. And really I wasn't even talking about anything else but the desktop, so lets please keep the discussion limited to that. I'm well aware of all the other places you'll find it. Almost everywhere else. But that isn't what I'm asking about or talking about.

---

### Post by RichardET on 2016-05-25
Even Linus has criticized the non-standardization of Linux.  He says this is holding back serious application development.  For instance the BOINC project - it works flawlessly on Ubuntu, but setting it up for other systems is touch & go.  Why?

---

### Post by Geoffrey_Arndt on 2016-05-25
Linus is very specific with his pros & cons (especially cons).    Certain aspects of the kernel update process, and userland tools in particular is what he is concerned about (developer, & packaging tools).   But Linus has also "forked" projects when needed (e.g., Git).    And most of the influential Linux developers have stated diversity and freedom is one of the main benefits to Linux (particularly insofar as innovation).   When you have Freedom, you have diversity.

The other reality is - - even though Distrowatch has tracked over 800 distributions - - only 10 to 15 actually have widespread adoption and use.   And most of those are offshoots and "1st cousins" of each other (debian/ubuntu,  redhat/fedora/centOS, etc.)

---

