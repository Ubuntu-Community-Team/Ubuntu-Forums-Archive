---
title: "Linux installation needs little attention"
date: 2010-09-08
forum: The Cafe
---

### Post by shahdharmit on 2010-09-08
Hello,

I am a happy Linux, specifically Fedora, user since almost 2 years. But I've tried various flavors of Linux till now. I've been telling my friends to use Linux and ditch Windows. Some of them have given a shot to Linux as well. But there is one thing that confuses many.

During installation everything except partitioning is simple. For experienced Linux user, it is not an issue at all. But I've seen many newbies getting confused when it comes to partitioning. They generally use default option and at times it wipes out the entire hard disk. Windows' installation gives a very simple layout of partitions on the hard disk which makes its installation very simple for dumb computer users as well. The wiping out of data makes people feel like Linux is too tough to install. Even worse thinking that some people around me have developed is that Linux takes up entire hard disk in installation. On the contrary, we - the Linux fans, know that it hardly requires 5 GB of disk space.

I think there needs to be little change or modification to the installer in order to make the installation bit more newbie-friendly.

PS - I am not being harsh to Linux installation. I am die-hard Linux fan and want to see Linux flourish day-by-day. So this is a simple suggestion from my side.

---

### Post by Naiki Muliaina on 2010-09-08
I cant help but feel if somebodys that computer illiterate they should either read up before installing or ask for help. The ubuntu installer is pretty clear all the way through imho.

---

### Post by limestone on 2010-09-08
eh. The Ubuntu install is as newbie friendly as it gets...
Its easier then windows install m8...

If they have problems with the install/partitioning there's a guide on Ubuntus website.
And probably on many other sites.

---

### Post by m4tic on 2010-09-08
I can't resize, move multiple partitions in windows installer. and if you have linux it will override grub.

---

### Post by DougieFresh4U on 2010-09-08
> **Naiki Muliaina said:**
> I cant help but feel if somebodys that computer illiterate they should either read up before installing or ask for help. The ubuntu installer is pretty clear all the way through imho.

Partition is pretty straight forward as all one needs to do is LOOK at what it's telling them, their choice usually being, install side-by-side or the wipe entire disk and use or one can go 'custom'

---

### Post by Johnsie on 2010-09-08
Restricting yourself to just one operating system isn't always the best answer.


If people have problems understanding partitioning then a Wubi install is the best option. It will create a dual boot system without messing around with any partitions. It just installs Ubuntu in c:\ubuntu like a normal application that can be uninstalled easily if the user doesn't like it. I do this on all the machines I work on to give people the opportunity to at least try Ubuntu. Most people stick with Windows because it's what they know and feel comfortable with.

[http://wubi-installer.org/](http://wubi-installer.org/)

I have a usb stick with the wubi exe on it and an iso of the latest Ubuntu. Wubi installs alot faster if you have the iso in the same directory as wubi.exe and unplug your internet connection during the installations process (to stop wubi checking the internet for updates)

---

### Post by sandyd on 2010-09-08
> **shahdharmit said:**
> Hello,

I am a happy Linux, specifically Fedora, user since almost 2 years. But I've tried various flavors of Linux till now. I've been telling my friends to use Linux and ditch Windows. Some of them have given a shot to Linux as well. But there is one thing that confuses many.

During installation everything except partitioning is simple. For experienced Linux user, it is not an issue at all. But I've seen many newbies getting confused when it comes to partitioning. They generally use default option and at times it wipes out the entire hard disk. Windows' installation gives a very simple layout of partitions on the hard disk which makes its installation very simple for dumb computer users as well. The wiping out of data makes people feel like Linux is too tough to install. Even worse thinking that some people around me have developed is that Linux takes up entire hard disk in installation. On the contrary, we - the Linux fans, know that it hardly requires 5 GB of disk space.

I think there needs to be little change or modification to the installer in order to make the installation bit more newbie-friendly.

PS - I am not being harsh to Linux installation. I am die-hard Linux fan and want to see Linux flourish day-by-day. So this is a simple suggestion from my side.

check maverick installer. Unless you want "wipe hard drive" selected by default, theirs not much easier it can get.

---

### Post by CharlesA on 2010-09-08
> **carlee said:**
> check maverick installer. Unless you want "wipe hard drive" selected by default, theirs not much easier it can get.

+1 to that.

---

### Post by t0p on 2010-09-08
Ubuntu installation partitioning used to be pretty confusing.  When I was a newbie (2007-8) I tried to do a Ubuntu/XP dual-boot and my noobishness combined with (IMHO) unclear instructions resulted in me formatting the entire hard disk and devoting it to Ubuntu.  Not good.

But nowadays partitioning during installation is a breeze.  The installer is pretty good at working out what's on the existing partitions, and asks very clear questions about what you want to do before destroying anything.

I don't know what other distros' installers are like, as I haven't installed another distro in ages.  But the Ubuntu installer is really clear and self-explanatory.  I think too many people believe in rumours and problems in earlier versions as another reason to stick with what they know.  Check it out: download a recent Ubuntu iso; and run through the partitioning/installing procedures without actually telling the installer to install.  It really is simple.

Note: my comments on how easy it is to install Ubuntu comes from the installation of 9.04.  I haven't installed Ubuntu since, though I'm planning to install Lucid on my current Hardy desktop.  I don't foresee any difficulties... (famous last words?).

---

### Post by Khakilang on 2010-09-08
I find installing Ubuntu dead easy. If you have Window already installed it will ask to install Ubuntu side by side and if you want the whole hard disk to be Ubuntu than you can select wipe the whole disk. If I remember correctly you can use the mouse to click and drag the partition separator. The last will choice will be the custom option. Since I already decided to use the whole hard disk for Ubuntu, I just wipe the whole thing. If I need anything in Window than I just use a Virtual box and install Window XP.

---

### Post by Paqman on 2010-09-08
> **shahdharmit said:**
> 
I think there needs to be little change or modification to the installer in order to make the installation bit more newbie-friendly.


That's exactly what Wubi was invented for. If you've got Windows on the machine already, you can install without doing any partitioning at all.

---

### Post by sdowney717 on 2010-09-08
I have a fair amount of experience installing windows and linux and dual booting setting up partitions still has a small fear factor to me, as in LOSING the system you want to keep. And then your toasted. 
The other issue for me is reinstalling or fixing grub. Like when grub has foobared itself, or windows has or the boot sector is somehow altered.
It can be easy or very frustrating to fix and it is not simple, the process is not user friendly. I recall it being very geeky.

---

### Post by shahdharmit on 2010-09-09
> **sandyd said:**
> check maverick installer. Unless you want "wipe hard drive" selected by default, theirs not much easier it can get.

Maverick is still in Beta stage. I am not talking about the Linux community who tries a distro right from its Alpha stage. I am talking about people who are trying Linux.

---

### Post by Spice Weasel on 2010-09-09
The new Fedora installer is pretty simple too.

---

### Post by Frogs Hair on 2010-09-09
I used this for 10.04 and something similar for 9.10 [http://www.youtube.com/watch?v=Taq_3LlTW_I](http://www.youtube.com/watch?v=Taq_3LlTW_I)

---

### Post by Hobgoblin on 2010-09-09
> **shahdharmit said:**
> But I've seen many newbies getting confused when it comes to partitioning. They generally use default option and at times it wipes out the entire hard disk. 

I have been through many installations of Ubuntu on systems already running Windows and it **does not** do this without the user jumping through a few hoops.

OTOH Windows will wipe out an existing Linux installation very easily.

---

### Post by drawkcab on 2010-09-09
I agree with the OP.  You have to keep in mind that some people are like, "partitioning, what's that??"  It'll be interesting to see if the new installer addresses these issues.

At any rate, years ago I had no idea either so I googled a howto guide on dual booting.  Find a good guide that explains the partitioning aspect of installation and send it to your friends.

---

### Post by murderslastcrow on 2010-09-09
Check out the 10.10 installer- it's the friendliest thing evar. Seriously, how much simpler can you get? I guess you could change the terminology a bit, but it's dead simple.

In contrast, can you tell me that the installation CDs for Windows or OS X are nearly as friendly? Windows 7's advanced features for disk management are totally confusing and don't give any real options.

For how versatile and flexible that section of the installation is, as it should be, it's very simple. I honestly think the issue your friends have is with the fact that you have to deal with moving things around when you install, or wiping everything out.

I mean, look at Wubi. How is installation so hard these days? I started with 8.10 and I thought it was dead simple BACK THEN. Drag a slider, it's labelled with Windows and Ubuntu- what is there not to understand?

*facepalm* People who can't do something that simple probably don't install any applications on their previous OS either, and have issues finding their email. Such people should buy Ubuntu preinstalled, as they could never install an OS for the life of them.

I'm not kidding here- I firmly disagree with your assertion that it's too difficult as it is. I hope that doesn't bother you- I see why people would find it difficult, but I don't think you have to be experienced by any means to understand it.

Of course, we can always improve, and I encourage the developers to make installation as simple and effective as possible in the future. Friendlier is certainly what we want, even though Ubuntu's already a bit too easy it seems.

I mean, they're even working on a feature to install and migrate features from Windows programs on your hard drive that have a Linux version, or are closely related enough to import settings from(IE to Firefox, iTunes to Rhythmbox, uTorrent to Transmission, etc.).

It's only going to get better as time goes on. I hope the people who would benefit most from Ubuntu (most people) can find it.

---

### Post by sandyd on 2010-09-09
> **shahdharmit said:**
> Maverick is still in Beta stage. I am not talking about the Linux community who tries a distro right from its Alpha stage. I am talking about people who are trying Linux.
I know, but we do not modify the installer in the middle of a release.

Maverick will have the lovely new installer, and 99.9% of people will figure out how to use it.

---

### Post by juancarlospaco on 2010-09-09
> **sandyd said:**
> 99.9% of people will figure out how to use it.

**+1**
:)

---

### Post by rockager on 2010-09-10
linux isn't for idiots, besides the Ubuntu installation process is very easy. you only have to mark the partition you want to install ubuntu to as  / (that's where i got stuck while installing ubuntu for the first time).

---

### Post by cariboo on 2010-09-10
> **sandyd said:**
> I know, but we do not modify the installer in the middle of a release.

Maverick will have the lovely new installer, and 99.9% of people will figure out how to use it.

Actually they are modifying the Maverick installer, there have been quite a few complaints about missing features, we should see some changes within the next couple of days.

---

### Post by Naiki Muliaina on 2010-09-10
> **rockager said:**
> linux isn't for idiots

I know a few people who never touch terminal anymore. 'Ubuntu' is good for idiots. I know a few 'idiots' who use it and get on better with it than with Windows.

*dribbles a lil*

):P

---

