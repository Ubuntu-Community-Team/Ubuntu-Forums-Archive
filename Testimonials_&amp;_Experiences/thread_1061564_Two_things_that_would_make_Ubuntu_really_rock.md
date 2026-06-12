---
title: "Two things that would make Ubuntu really rock"
date: 2009-02-05
forum: Testimonials &amp; Experiences
---

### Post by bobbo85 on 2009-02-05
Lately, I have been getting more and more calls for help from family and friends whose Windows machines are "sick."  Sometimes the same person gets a devastating spyware infection twice in a month.  Worse yet is when Windows itself gets corrupted, and they opt for the "let's wipe it clean and start over" routine.  The process itself of getting Windows (and all the software they need) back up and running can take forever!

Let me say this:
I have been DYING to just install Ubuntu and tell them to give it a shot.  

From my own personal experience over the last two years with Ubuntu/Kubuntu, it is more than good enough to use as an OS.  I love booting from a LiveCD and finding that everything just works.  I'm expecting to have to install everything from sound card drivers to network card drivers, and then I hear the boot sound!  And firefox works!  It even sees my printer!  Coming from Windows, I just feel like there's so much awesome going on it's overwhelming.

That being said, I cannot put Ubuntu onto a friend's machine and feel good about it until I see the following things:

1)  When I right click on a drive, I should see this option:
-Always mount this drive on start-up

Why?  Because my mother will never know how to edit /etc/fstab.  Anyone who thinks otherwise should be f-stabbed in the face.  Everyone wants to have access to their data - that includes everything on their Windows partitions.

1.1)  When I left click on a drive, and Windows didn't shut down correctly (which is effing unheard of I know), there should be a big button that will open it anyways.

As of now, this awful window says "If you want to open the drive, you need to tell me to 'force it' or I wont do it..." then when you say "OK, force it" in the terminal, it says "i still don't think you mean it... you didn't say sudo."  *face-palm.  Yes, it makes sense to a Linux user, but to anyone else that's pure evil.  Just let the button click run the command for the user in the background.

2)  We need a boot menu editor.  A GUI that lets you click and drag Operating systems into a list, and then pick one as the default.  

"I don't want no grub," a grub is a file that wont get no sudo gedit from my mom OR TLC.

2.1)  This grub menu.lst editor needs to be on the liveCD, and it needs to be able to write to the MBR.  It is the worst when Ubuntu is on one drive, and the MBR is on another drive that dies.  


Extra gripes:
--If I double-click the clock, show me an option to use a 12hr format.  Kubuntu makes this entirely too difficult - a restart?  honestly?

--Please give me proprietary nvidia drivers and the Adobe flash plugin by default.  Pretty please.



The bottom line is we just need more GUI ways to do things.  Important commands can be made into buttons; options and configurations can be put into windows.  Let the users make decisions, and let the GUI edit .conf files for them.  Keep the grunt work to a minimum!

---

### Post by wolfen69 on 2009-02-06
i accept linux for what it is. no more, no less. 

oh, btw, i now have 10 customers that love linux. most of them are running dual boots, but they tell me they rarely use windows anymore. and it doesn't matter if mom can't sudo gedit anything, because my customers can't do anything right in windows either. that's why they call me. if i'm going to give tech support, i'd rather do linux than windows. but so far, they all love it, and it just works.

---

### Post by betrunkenaffe on 2009-02-06
> **bobbo85 said:**
> 
That being said, I cannot put Ubuntu onto a friend's machine and feel good about it until I see the following things:

1)  When I right click on a drive, I should see this option:
-Always mount this drive on start-up

Why?  Because my mother will never know how to edit /etc/fstab.  Anyone who thinks otherwise should be f-stabbed in the face.  Everyone wants to have access to their data - that includes everything on their Windows partitions.


I can see the advantages, I haven't really had too many problems myself, I just load up my windows partition whenever I feel like accessing it (it's right there in Places, click and go)

> **bobbo85 said:**
> 
1.1)  When I left click on a drive, and Windows didn't shut down correctly (which is effing unheard of I know), there should be a big button that will open it anyways.

As of now, this awful window says "If you want to open the drive, you need to tell me to 'force it' or I wont do it..." then when you say "OK, force it" in the terminal, it says "i still don't think you mean it... you didn't say sudo."  *face-palm.  Yes, it makes sense to a Linux user, but to anyone else that's pure evil.  Just let the button click run the command for the user in the background.


I think this is something I would rather have to live with than to start moving admin privileges out to standard user.

> **bobbo85 said:**
> 
2)  We need a boot menu editor.  A GUI that lets you click and drag Operating systems into a list, and then pick one as the default.  

"I don't want no grub," a grub is a file that wont get no sudo gedit from my mom OR TLC.


How often do you actually edit grub?

> **bobbo85 said:**
> 
2.1)  This grub menu.lst editor needs to be on the liveCD, and it needs to be able to write to the MBR.  It is the worst when Ubuntu is on one drive, and the MBR is on another drive that dies.  


I'd like to see the ability to re-write the MBR straight off the install CD as well.

> **bobbo85 said:**
> 
Extra gripes:
--If I double-click the clock, show me an option to use a 12hr format.  Kubuntu makes this entirely too difficult - a restart?  honestly?

--Please give me proprietary nvidia drivers and the Adobe flash plugin by default.  Pretty please.

The bottom line is we just need more GUI ways to do things.  Important commands can be made into buttons; options and configurations can be put into windows.  Let the users make decisions, and let the GUI edit .conf files for them.  Keep the grunt work to a minimum!

The clock seems fine to me and while accessing the properties could be accessible via double click, right click and menu select works fine for the once I'll ever actually need to go in there.

As for the nVidia drivers, there should be an option to select which you
want to use with recommended (read default) being most recent ones. Would accomplish what you'd like and still allow users to pick a different driver at install.

Improvements to GUI are always good. There are definitely configurations that can be made into menus. If you want to assist, look at making them :)

---

### Post by cariboo on 2009-02-06
You have to remember that most Windows users use their computers the way it was setup when they got it. The only thing they really change is the wallpaper. They rarely do anything else, they may add a peripheral or two, but that's just a matter of sticking the CD in, clicking several times and waiting for the installation to finish.

Jim

---

### Post by wolfen69 on 2009-02-06
> **cariboo907 said:**
> You have to remember that most Windows users use their computers the way it was setup when they got it. The only thing they really change is the wallpaper. **They rarely do anything else**

that's part of the problem. they rarely do any maintenance either. between that, viruses, and spyware/bloatware, it becomes a real mess. it takes a concerted effort to muck up a good running linux machine. big difference there.

---

### Post by Martje_001 on 2009-02-06
Good points bobbo85. Unfortunately we cannot include the binary drivers of NVidia/ATi. It's against the philosophy of Ubuntu.

---

### Post by armandh on 2009-02-06
there is a kde gui grub editor that works great [Kgrubeditor]

as for my unsafe surfing brother in-law I gave him a computer with ubuntu. beggars can't be choosers.

so when they beg a fix install both dual boot and tell them it is a back up OS incase you are busy next time it breaks.

---

### Post by 3rdalbum on 2009-02-06
> **bobbo85 said:**
> 
--Please give me proprietary nvidia drivers and the Adobe flash plugin by default.  Pretty please.

No can do, buddy. It's illegal to ship a binary-only driver inside the Linux kernel - you have to install it yourself. The Nvidia installer is 20 megabytes and the Ubuntu CD is full.

Adobe prohibits Flash Player from being redistributed without permission, which is why the "Flash Player" package is just a script that downloads Flash Player from Adobe.com. I guess Canonical could get permission... but shipping proprietary software with Ubuntu is one of the things they guarantee they will never do with Ubuntu :-)

---

### Post by wolfen69 on 2009-02-06
> **3rdalbum said:**
> No can do, buddy. It's illegal to ship a binary-only driver inside the Linux kernel

there are distros out there that do ship with nvidia/ati and flash. mandriva and sabayon come to mind. i'm sure there are others too.

---

### Post by cb951303 on 2009-02-06
> **3rdalbum said:**
> No can do, buddy. It's illegal to ship a binary-only driver inside the Linux kernel

I don't think that's true. There *are* binary-only drivers in kernel. That's why GNU guys uses gNewSense.

---

### Post by jbysmith on 2009-02-06
> **3rdalbum said:**
> No can do, buddy. It's illegal to ship a binary-only driver inside the Linux kernel - you have to install it yourself. The Nvidia installer is 20 megabytes and the Ubuntu CD is full.

> **wolfen69 said:**
> there are distros out there that do ship with nvidia/ati and flash. mandriva and sabayon come to mind. i'm sure there are others too.

Someone correct me if I'm wrong, as I'm no expert on GPL requirements, FOSS and all that, but it's just an "ethical decision" made by the distribution right?  I know some distributions are highly against it, Fedora for example has a zero tolerance on proprietary code. You can get it, but they'll never include it.  Some others are much more relaxed, as he mentioned Sabayon is a good example.  Proprietary drivers right on the disc.  Fairly sure there's no actual legal (as in "I can get sued") requirements as long as the code in question is allowed to be distributed.  Of course some of them might require permission first, I believe Flash is one of these where a publisher would require getting a license before publishing.

I can see the "recovery console" type of thing being added though, that makes sense.  If you accidentally blast your boot loader, being able to pop in the LiveCD, and having a "Help! I broke my computer!" option right off the boot menu would be nice for those that don't know how to fix it manually.

---

### Post by kspncr on 2009-02-06
> **bobbo85 said:**
> --Please give me proprietary nvidia drivers and the Adobe flash plugin by default.  Pretty please.

People keep saying this, but it's not going to happen. Ever. How can you claim to be about freedom when you include proprietary drivers by DEFAULT? Ubuntu's not about being hypocritical.

Honestly, it's not that hard to get these things installed. If you can't figure it out yourself, that's what the forums are for.

---

### Post by wolfen69 on 2009-02-06
considering windows comes with absolutely **nothing** after a fresh install, i'd say linux is doing pretty well. if you want things preinstalled, there are a few distros out there to oblige.

---

### Post by solwic on 2009-02-06
> **wolfen69 said:**
> considering windows comes with absolutely **nothing** after a fresh install, i'd say linux is doing pretty well. if you want things preinstalled, there are a few distros out there to oblige.

Now wolfen that's not true!  You know as well as I do that Windows has all kinds of ***bugs*** that come with a fresh install!

And you say you do this for a living....

:razz:

---

### Post by Crafty Kisses on 2009-02-06
> **wolfen69 said:**
> there are distros out there that do ship with nvidia/ati and flash. mandriva and sabayon come to mind. i'm sure there are others too.

Sabayon indeed did! I love Sabayon!

---

### Post by jrusso2 on 2009-02-06
> **3rdalbum said:**
> No can do, buddy. It's illegal to ship a binary-only driver inside the Linux kernel - you have to install it yourself. The Nvidia installer is 20 megabytes and the Ubuntu CD is full.

Adobe prohibits Flash Player from being redistributed without permission, which is why the "Flash Player" package is just a script that downloads Flash Player from Adobe.com. I guess Canonical could get permission... but shipping proprietary software with Ubuntu is one of the things they guarantee they will never do with Ubuntu :-)

1. Nvidia is a kernel module and not inside the kernel
2. All you have to do is ask permission from Adobe to distribute flash its done all the time.

---

### Post by jrusso2 on 2009-02-06
> **wolfen69 said:**
> considering windows comes with absolutely **nothing** after a fresh install, i'd say linux is doing pretty well. if you want things preinstalled, there are a few distros out there to oblige.

Windows can play many formats out of the box even DVD now.

---

### Post by cariboo on 2009-02-06
An OEM Windows install does not play dvd's or mp3's out of the box. Companies like HP and Dell add the extra programs that are needed to play anything other than .wma and .wmv.

Jim

---

### Post by rzrgenesys187 on 2009-02-06
> **wolfen69 said:**
> there are distros out there that do ship with nvidia/ati and flash. mandriva and sabayon come to mind. i'm sure there are others too.

I think Mint might as well, it at least ships with flash.

---

### Post by solwic on 2009-02-06
> **rzrgenesys187 said:**
> I think Mint might as well, it at least ships with flash.

Flash and Java yes, but still have to download/install the drivers.  At least for nVidia.  

(Just installed Mint today...who knew it was so much *faster* than Ubuntu?) 

:)

---

### Post by Twitch6000 on 2009-02-06
> **jrock612 said:**
> Flash and Java yes, but still have to download/install the drivers.  At least for nVidia.  

(Just installed Mint today...who knew it was so much *faster* than Ubuntu?) 

:)

Not trying to bash or argue,but Mint is not faster.. I have tried mint many times(ever since version 4).

It is indeed a great distro,but is at the same speed as ubuntu or possibly slower.

---

### Post by solwic on 2009-02-06
> **Twitch6000 said:**
> Not trying to bash or argue,but Mint is not faster.. I have tried mint many times(ever since version 4).

It is indeed a great distro,but is at the same speed as ubuntu or possibly slower.

Not in my experience.  But speed aside, I like the set up.  Ubuntu is awesome, don't get me wrong, but I wish I'd given Mint more of a chance earlier.  

It boots faster, shuts down faster (though Ubuntu Ibex shuts down super fast), and runs faster.  Maybe it's just my hardware (AMD Athalon 64 2.0Ghz CPU, 1.5GB DDR RAM, nVidia 8400GS 512MB video card, 500GB SATA HDD), but it's definitely faster for me.

We won't even talk about the superior artwork....  :P

I like that it comes with the popular programs:  Thunderbird instead of Evolution, for instance.  The software packaging is definitely better out of the box with Mint (I know you can get the same stuff for Ubuntu, but none of it is pre-installed).  

IMO, anyway.  To each his/her own.  :)

I think it's key to remember, too, that Mint wouldn't be what it is without Ubuntu.  :biggrin:

---

### Post by mdsmedia on 2009-02-06
Please, if you're going to refer to the release by its name, it's Intrepid, not Ibex.

8.04 was (is) Hardy, not Heron and 6.06 was Dapper, not Drake.

I tried to install Mint but my magazine DVD had a corrupted ISO. I really wanted to give it a shot but I'm not going to download 650 MB or more just to try a distro. Thankfully every Ubuntu release has (eventually) arrived on DVD and worked well.

I'm running Mandriva One 2009 on my desktop and quite frankly it's awful. I installed DSL on my old Celeron desktop and the resolution makes it impossible to close it down lol. ZenWalk will find a home there :).

---

### Post by jrusso2 on 2009-02-06
> **cariboo907 said:**
> An OEM Windows install does not play dvd's or mp3's out of the box. Companies like HP and Dell add the extra programs that are needed to play anything other than .wma and .wmv.

Jim

Your wrong I have Vista ultimate and through a DVD in it cause I had no software and so far Windows Media Center plays them all.

---

### Post by solwic on 2009-02-06
> **mdsmedia said:**
> Please, if you're going to refer to the release by its name, it's Intrepid, not Ibex.

8.04 was (is) Hardy, not Heron and 6.06 was Dapper, not Drake.


True, but Ibex is easier to type.  I'm all about preventing RSI.  :)

> **mdsmedia said:**
> 
I tried to install Mint but my magazine DVD had a corrupted ISO. I really wanted to give it a shot but I'm not going to download 650 MB or more just to try a distro. Thankfully every Ubuntu release has (eventually) arrived on DVD and worked well.


The only CD I've ever ordered from any Linux distro was Ubuntu 8.04, and it was corrupted.  The one I burned I had to burn at 1x to make it work.  

I burned my Mint disk at 40x, and it worked perfectly.  Although I'm sure that's my hardware; I've always had an issue with burning CDs.  Just got lucky with the Mint disk....  :)

IMO, it's well worth the 650MB download.  I think you said once that bandwidth quotas were common in Australia, so I guess it depends on your quota, but in essence (on my hardware, anyway) Mint is Ubuntu with much better artwork and much handier shortcuts (like Gnome-Do, for instance, or being able to right click a program in the menu and uninstall it).  

Some say it's slower.  Again, I've had the opposite experience.   

I do have to admit, though, that the stupid little update lock icon flashing every five minutes is annoying as ^%$#!.  :)

> **mdsmedia said:**
> 
I'm running Mandriva One 2009 on my desktop and quite frankly it's awful. I installed DSL on my old Celeron desktop and the resolution makes it impossible to close it down lol. ZenWalk will find a home there :).

I've been considering trying ZenWalk.  Is it any good?  I wonder if it'll load up in a VM....  :)

---

### Post by Flimm on 2009-02-07
For editing /boot/grub/menu.lst you might want to try Startup Manager (in the repos, startupmanager).

---

### Post by carusoswi on 2009-02-07
Perhaps you should give your mom more credit if she has to have access to drives on another OS when she boots into Ubuntu.  How hard is it for her to learn to just double click on that drive?

Not being able to mount a drive that was shut down "uncleanly" can be a pain, but it is really a protection mechanism.

I've just been backing up some of my old drives that have resided in Maxtor firewire enclosures for five years or so (the translucent plastic cases you open by unsnapping the grey plastic bands that hold the two halves of the enclosure together).

These enclosures are notorious (with me, at any rate) for being prone to dropping the power source or being prone to other write-delay errors in XP that often caused the data on the drive to become inaccessible by XP.  I just messed one up because it was not id'ing itself to Ubuntu.  I unplugged it causing an "unclean" shutdown indication to Ubuntu.

I copied that force mount command to the terminal, and the thing opened right up.  You cannot do that in XP at all.  I've had to use GetDataBack to rescue important info from those very same drives in my pre-ubuntu days when no other method would overcome those write-delay problems.  GetDataBack works most of the time, but the process is painfully slow compared to typing a single command in the terminal to solve the problem.
Now, granted, your mother probably isn't going to be able to accomplish that, but her son probably wouldn't have her relying upon shaky, error prone Maxtor external drive enclosures, either.

For me, in this regard, Ubuntu wins again.

I'm no boy scout for Ubuntu, mind you.  I have my fair share of complaints about some of the areas where it is not yet ready for prime time in my computer world, but, it does have its redeeming qualities, not the least of which is an excellent forum where you can find a lot of help with problems when you run into them.

Caruso



> **bobbo85 said:**
> Lately, I have been getting more and more calls for help from family and friends whose Windows machines are "sick."  Sometimes the same person gets a devastating spyware infection twice in a month.  Worse yet is when Windows itself gets corrupted, and they opt for the "let's wipe it clean and start over" routine.  The process itself of getting Windows (and all the software they need) back up and running can take forever!

Let me say this:
I have been DYING to just install Ubuntu and tell them to give it a shot.  

From my own personal experience over the last two years with Ubuntu/Kubuntu, it is more than good enough to use as an OS.  I love booting from a LiveCD and finding that everything just works.  I'm expecting to have to install everything from sound card drivers to network card drivers, and then I hear the boot sound!  And firefox works!  It even sees my printer!  Coming from Windows, I just feel like there's so much awesome going on it's overwhelming.

That being said, I cannot put Ubuntu onto a friend's machine and feel good about it until I see the following things:

1)  When I right click on a drive, I should see this option:
-Always mount this drive on start-up

Why?  Because my mother will never know how to edit /etc/fstab.  Anyone who thinks otherwise should be f-stabbed in the face.  Everyone wants to have access to their data - that includes everything on their Windows partitions.

1.1)  When I left click on a drive, and Windows didn't shut down correctly (which is effing unheard of I know), there should be a big button that will open it anyways.

As of now, this awful window says "If you want to open the drive, you need to tell me to 'force it' or I wont do it..." then when you say "OK, force it" in the terminal, it says "i still don't think you mean it... you didn't say sudo."  *face-palm.  Yes, it makes sense to a Linux user, but to anyone else that's pure evil.  Just let the button click run the command for the user in the background.

2)  We need a boot menu editor.  A GUI that lets you click and drag Operating systems into a list, and then pick one as the default.  

"I don't want no grub," a grub is a file that wont get no sudo gedit from my mom OR TLC.

2.1)  This grub menu.lst editor needs to be on the liveCD, and it needs to be able to write to the MBR.  It is the worst when Ubuntu is on one drive, and the MBR is on another drive that dies.  


Extra gripes:
--If I double-click the clock, show me an option to use a 12hr format.  Kubuntu makes this entirely too difficult - a restart?  honestly?

--Please give me proprietary nvidia drivers and the Adobe flash plugin by default.  Pretty please.



The bottom line is we just need more GUI ways to do things.  Important commands can be made into buttons; options and configurations can be put into windows.  Let the users make decisions, and let the GUI edit .conf files for them.  Keep the grunt work to a minimum!

---

### Post by carusoswi on 2009-02-07
One last thought . . . I love the file operations setup for Ubuntu.  I use two desktops, one set to browse the source, the other the destination, when I am backing up these old drives.  Ubuntu is so straight forward, never bogs down, and, I mentioned this somewhere else today, allows you to recover when, during the copying of a long list of files, a corrupt file interupts the process.  XP knocks you out of the copying process, Ubuntu offers to let you skip the offending file and continue the copying process . . . neat.

Caruso

---

### Post by mdsmedia on 2009-02-07
> **jrock612 said:**
> 
I've been considering trying ZenWalk.  Is it any good?  I wonder if it'll load up in a VM....  :)

I haven't managed to install it yet. Had a problem with "one of your partitions is full" on installation and haven't had a chance to sort that out yet.

Only a 10 Gig drive but that should be plenty, apparently. The partitioning tool isn't quite as intuitive as that of Ubuntu. I've got the feeling it's trying to install in the Swap partition.

---

### Post by thiebaude on 2009-02-08
Windows XP doesn't ship with flash and Java

---

