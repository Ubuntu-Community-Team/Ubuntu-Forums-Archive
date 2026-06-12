---
title: "Abstraction being the goal...(an Ubuntu Flame)"
date: 2009-02-24
forum: Testimonials &amp; Experiences
---

### Post by alabasterjones on 2009-02-24
I got into the idea of linux probably a year or so ago, but I'm really starting to see its limitations. Recently, (as in, for the last 2 weeks) I have been trying to install any stable linux distro onto an old 500Mhz HP PC of mine. I tried Debian, FreeBSD, Ubuntu, Xubuntu, Damn Small Linux, Puppy linux, WattOS, and 5 versions of my linux distro of choice Linspire/Freespire. 

The *only* operating system I could get to work on the machine was Windows XP. Not only was it the only OS to install successfully, but it could also run faster on 64 MB RAM than Windows 98 (the previous OS). 

So, to try to give linux a second shot, I ordered more RAM. The thing has a max of only 256MB according to the web. So now it has 256 in it and I tried all my linux discs again. The only one to work was my old Fesity Fawn unbuntu distro. BUT, there is this very common problem with Ubuntu not working with wired DSL/pppoe. So I can't connect to the internet.

What a pain! Windows XP worked more than fine and Ubuntu is nothing but disappointing. I've even gotten my wireless card in my laptop to work with Ubuntu, but this other problem is much more severe. 

What I'm starting to realize is this:
What the **** is the point of all these linux distros if none of them work on old machines with less than 256MB RAM and 500Mhz, and can't support standard essential items like _an ethernet card_! 
This is my other point: Earlier versions of Windows and Mac OS DO! And they don't require so much fiddling about on the command line. Why are all the people on these forums obsessed with command line arguments as if they are so cool by knowing them? You don't sell a car without a god damn frame and then expect the owner to fix all the problems themselves with a wrench by hand. If you guys were really so knowledgeable about how computers communicate you would do every thing in the lowest language possible: 100011010100101001. 

Why the hell do we have to type sudo for everything as well??
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by Simian Man on 2009-02-24
You are installing systems made in the last few years.  Try installing Vista on that machine and you will get worse troubles.  For a fair comparison, try installing something that is contemporary with Windows XP like Red Hat Linux 7.0.  That would probably work if better than XP or 98.

And the command line is part of Linux, if you don't want to learn it, Linux is likely not for you.

If you don't like sudo, just log in as root, but keep in mind that that is one of the reasons Windows is so unstable.

---

### Post by Tews on 2009-02-24
You could have avoided a lot of trouble and grief by checking the minimum requirements before going "flame on"

>  Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    *

      Sound card
    *

      A network or Internet connection 

Google is your friend!

---

### Post by jbysmith on 2009-02-24
Give Arch a spin.  Pretty easy to get going (especially if you follow the Wiki, which is excellent) and it only includes what you tell it to. I've never had driver issues with it. Getting it to boot into Linux itself with 256MB will be cakewalk.  (Shoot getting it to boot under 128 will be cakewalk too.)

Now keep in mind if you throw a large window manager on there, that requirement will go *way* up.  KDE4 for example on 256MB will be a painful experience. Gnome isn't as bad, but it's still going to want more memory than that to run smoothly. Pick an ultralight.  XFCE, or even lighter, AwesomeWM is really slick.  

You *can* get XP running on 256MB granted, but it's going to be pounding that swapfile something ugly once you load anything bigger than notepad.  Running XP with 64MB.. owch.  Granted, it *is* possible, I've seen it done, but with just 64MB you'll want to go even older than that just go get even an illusion of "performance".

As far as sudo goes, that's because by default you're running as a limited user account by default. You need a privilege escalation for anything system related. (Think UAC in Vista, it's similar.)  If it irks you that bad, you *could* run as root, but that leaves you wide open for a world of hurt.  (One of XP's biggest faults, god mode is dangerous.)  Its your system, just be aware of the risks of running as root.  If you screw up, it has the potential to be spectacular.

Edit: The post above me hits it dead on.  You're picking the wrong OS for those specifications.

---

### Post by alabasterjones on 2009-02-24
> **Simian Man said:**
> You are installing systems made in the last few years.  Try installing Vista on that machine and you will get worse troubles.  For a fair comparison, try installing something that is contemporary with Windows XP like Red Hat Linux 7.0.  That would probably work if better than XP or 98.


Right. Well, that's the thing. Microsoft keeps "upping the ante" on their hardware requirements so that people have to keep buying newer and faster computers. It's called planned obsolescence and it's how they make such a huge profit.

Linux users should be Against that idea, and try to make linux as lightweight as possible!

---

### Post by Therion on 2009-02-24
> **alabasterjones said:**
> Linux users should be Against that idea, and try to make linux as lightweight as possible!
There are lightweight distros and more hardware intensive distros.  

There are spartan distros and bloated distros.  

There's a distro for just about everyone and all distinctly different in about as many ways as possible.  

How many really distinctly different flavors of Windows are there to choose from? 

Simply because you can't find a distro that runs on a 500Mhz processor doesn't mean the entire Linux community needs to be focusing on meeting your individual hardware profile.

---

### Post by Simian Man on 2009-02-24
> **alabasterjones said:**
> Right. Well, that's the thing. Microsoft keeps "upping the ante" on their hardware requirements so that people have to keep buying newer and faster computers. It's called planned obsolescence and it's how they make such a huge profit.

Linux users should be Against that idea, and try to make linux as lightweight as possible!

There are modern versions of Linux that will run on your hardware, but Ubuntu is not one of them.  Why should Ubuntu keep its minimum requirements so low when most users have computers that are much better than yours?  Why not add nice features instead?  My point was that it isn't fair to compare something released in 2001 to something released in 2007.

I have successfully installed Puppy Linux on a computer older than that.  What, specifically, were the problems you ran into?

---

### Post by alabasterjones on 2009-02-24
The problem, is that Windows XP was working fine (actually quite fast, I had 2 antiviruses running and opera *and* solitaire on 256) and most linux won't even install because it's too heavy. Ubuntu runs fine on the system and fast too, just won't connect to the internet. That's the problem. The fact that Ubuntu is HEAVIER than Windows XP yet a person *still* has to go to the command line to fix problems in ubuntu but not in XP. I don't see that as having any *extra* features...

Honestly, if I could watch youtube videos in DOS, I wouldn't use a windowed system at all.

---

### Post by wolfen69 on 2009-02-24
great.

---

### Post by jbysmith on 2009-02-24
> **alabasterjones said:**
> The problem, is that Windows XP was working fine (actually quite fast, I had 2 antiviruses running and opera *and* solitaire on 256) and most linux won't even install because it's too heavy. 

*Two* antivirus apps?  Biting my tongue on the flames, but that's a very bad idea.  I'm surprised the OS even boots.  You only *ever* want one resident, and to be honest I question the usefulness of a resident antivirus anyway, unless you're just not being careful. (I don't run one on my XP gaming partition, on-demand scans only plus Sandboxie if I'm unsure. Just slows the system down needlessly.)  Unless you mean one resident, one on-demand only, then I take that back.


> **alabasterjones said:**
> Honestly, if I could watch youtube videos in DOS, I wouldn't use a windowed system at all.

DOS can't, Linux can.  (Wellllll you can run Firefox or Opera without a window manager.)  

But see above, you're picking the wrong distro and/or window manager for the job.  It's like trying to get Vista or Win7 to run on that system.  Just not going to work with any degree of success.  Ubuntu uses Gnome by default, and it's just not geared for something that old.  Arch and Puppy is very nice, DamnSmall is absurdly light.. (50MB!) Run from a terminal, or throw on AwesomeWM for a super-light manager.  No reason it won't fly on your system.

---

### Post by alabasterjones on 2009-02-24
> **wolfen69 said:**
> what i'm starting to realize, is people like you, are not the computer geek you think you are.  i can install linux on a turd. i can make anything work, and take pride in it. don't blame linux for your own shortcomings.  go back to school and learn or just be quiet. you're making yourself look like a computer techie wannabe. if you were that good, you wouldn't be here complaining that a square peg won't fit into a round hole.

you'll never hear me complain that something doesn't work. i *make* it work. that's the difference between a computer person and a windows user. go back to school.

Dude, if there are more people other than me bringing this up maybe they have a point? 

I'm not really a computer geek extraordinaire. I'm talking about efficiency. Everything should run with maximum efficiency. *That's* what I learned in the 3 programming classes I took.

Even if you have the fastest, best computer in the world, wouldn't it be better for the operating system to use up 256MB instead of 2GB for instance? 
Why does the user interface need to be so heavy and clunky? Really all a computer is to most people is an internet browser and a word processor and that's all it ever will be for the next few thousand years, right? Unless something really weird happens...

---

### Post by jbysmith on 2009-02-24
> **wolfen69 said:**
> i can install linux on a turd.  

You *so* need to make that your signature.  (Really, no bashing intended, damn funny way of stating your skills.)

> **alabasterjones said:**
> Even if you have the fastest, best computer in the world, wouldn't it be better for the operating system to use up 256MB instead of 2GB for instance? 
Why does the user interface need to be so heavy and clunky? 

It's not Linux at "fault" there, that would be Gnome.  Ubuntu is two parts; the Linux kernel doing the work, and the Gnome desktop that you work with.  Linux is very light and efficient; if Gnome is too big for your system, replace it.

It's just like any operating system.  More features come with a cost, namely some performance and memory.  (See my previous post.)  Gnome is a nice mid-range desktop.  It's not an ultra-light, but not a full blown feature-gasm like KDE4.  Plus, not only Gnome, but by default Ubuntu throws in a lot of extra services; file indexing, bluetooth, pulse audio and the like.  Plus you got background servers running for the virtual consoles, probably have an SSH server, maybe Samba, and so on.  Memory goes fast, and all that alone already has Ubuntu by default running a lot more than a nekkid XP installation.  As Ubuntu matures, it's just going to get bigger.  That's the natural progression of operating systems; new features means more overhead.

Or, if it helps any, think of it like old-school Windows.  You had DOS under the hood, which would be the Linux kernel and the GNU stuff.  Then you slapped on Windows 3.1, which was pretty damn light.  Or you could throw on 95, which had a lot more features, but took significantly more memory.  Same deal.  The window manager throws on a lot of overhead.

The Ubuntu requirements clearly say what's bare minimums for the out of the box installation.  If your system is under that, it's not the distro for you.  Or, go with the alternate install.  Install the console version and pick a window manager that's lighter than Gnome, that'll run a lot better on what's available memory wise, but you'll still have access to the Ubuntu repositories.  You're only going to be able to cram so much into 256MB of memory, once you get past that you're in swap hell and just hurting performance.  XP is going to be in the same boat.  Sure it'll run, but you'll sit there watching your hard drive grind away at the swap file while it's doing anything.

---

### Post by Keyper7 on 2009-02-24
I don't get several points of your post.

1) Why did you randomly decide to "order more RAM"? I'm seeing your previous posts and you posted nothing about the problems you are having during install. What prompted you to think that more memory was the solution? This sounds like a "blowing air into the floppy drive" solution.

2) The "very common problem with Ubuntu not working with wired DSL/pppoe" never happened to me or any of my friends who use DSL/pppoe. And I use Ubuntu since Dapper. Furthermore, I've just installed Xubuntu in a laboratory machine with 128mb: it's working smoothly. A single personal experience is not enough evidence for you to say "Ubuntu does not work with..."

3) Command-line solutions are usually the fastest way to reach a solution. "Open a terminal and copy-paste X" is much more fast than "Open X, now go to button Y, not go to tab Z, now select...". People tend to dismiss the command line as something low-level, when in fact it can be much more efficient and fast than GUI solutions. Most Windows system admins can't live without PowerShell.

4) Sudo is not an inherent characteristic of Linux. You can disable it and several distros don't use it.

5) If you are needing sudo for everything, you're doing something wrong. Your comment makes me think you didn't get XKCD's joke at all.

---

### Post by pirate_tux on 2009-02-24
> **alabasterjones said:**
> The problem, is that Windows XP was working fine (actually quite fast, I had 2 antiviruses running and opera *and* solitaire on 256) and most linux won't even install because it's too heavy. Ubuntu runs fine on the system and fast too, just won't connect to the internet. That's the problem. The fact that Ubuntu is HEAVIER than Windows XP yet a person *still* has to go to the command line to fix problems in ubuntu but not in XP. I don't see that as having any *extra* features...

Honestly, if I could watch youtube videos in DOS, I wouldn't use a windowed system at all.

In order to do a fair comparasion you must install a 2000 or 2001 GNU/Linux distro.

I think someone has already told you that.

If you don't want to install a 2000 or 2001 GNU/Linux distro then you are forced to compare a recent GNU/Linux distro with Windows Vista.

As a matter of fact, I'm surprised you weren't able to understand something so simple as this by yourself...

So go install a 2000 or 2001 GNU/Linux distro and post your results. 
Or install Windows Vista on your computer and also post your results.

I'll be here waiting.

---

### Post by alabasterjones on 2009-02-24
> **Keyper7 said:**
> 
2) The "very common problem with Ubuntu not working with wired DSL/pppoe" never happened to me or any of my friends who use DSL/pppoe. And I use Ubuntu since Dapper. Furthermore, I've just installed Xubuntu in a laboratory machine with 128mb: it's working smoothly. A single personal experience is not enough evidence for you to say "Ubuntu does not work with..."



[http://ubuntuforums.org/showthread.php?t=1010888](http://ubuntuforums.org/showthread.php?t=1010888)

^ This is the problem. Actually, I've seen dozens of posts just like it with no solutions. Just because things always worked for you the first time does not mean "Ubuntu works with all..." Maybe you have ideal hardware!

---

### Post by Keyper7 on 2009-02-24
> **alabasterjones said:**
> Just because things always worked for you the first time does not mean "Ubuntu works with all..."

Sarcasm fail.

The difference between you and I is that I did **not** claim that Ubuntu always works.

Compare my post to your "can't support standard essential items like an ethernet card" over-general statement.

> **alabasterjones said:**
> Maybe you have ideal hardware!

Yes, I do. You know why? Because I *researched* before buying. Linux has a smaller market share and smaller vendor support. Not everything works. Deal with it.

---

### Post by wolfen69 on 2009-02-24
> **alabasterjones said:**
> 

Even if you have the fastest, best computer in the world, wouldn't it be better for the operating system to use up 256MB instead of 2GB for instance? 

no. i bought 4gb of memory to actually use it. things open instantly when memory is used like it should. why would i want it to use only 256mb? that is defeating the purpose of having mega ram. granted, if you only have 256, then your options are somewhat limited. first, i would suggest getting more ram, or just use a distro that is optimized for a low spec machine. puppy linux will run like greased lightning on 256mb ram. ubuntu is not the only distro in the world, ya know. do some research, be patient, and good things will happen.

---

### Post by wolfen69 on 2009-02-24
> **alabasterjones said:**
> [http://ubuntuforums.org/showthread.php?t=1010888](http://ubuntuforums.org/showthread.php?t=1010888)

Just because things always worked for you the first time does not mean "Ubuntu works with all..." 

you are right. no OS works with everything. that's why it is a good idea to keep your options open, and use what *does* work.

---

### Post by wirelessmonkey on 2009-02-24
Did you try [https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

If so, it'd be interesting to see what the logs show...

---

### Post by stchman on 2009-02-24
Ubuntu is a much newer OS than XP.  XP is a 2001 OS.  Ubuntu Intrepid is a 2008 OS.

Ubuntu has more hardware requirements than XP.  I tell you what try to install Vista on that old laptop and tell us how it goes.

I tried to install Ubuntu on a P3 450 with 256MB RAM.  It installed, but was not very usable.

I installed Puppy and it flew.  I would recommend at least 512MB but go with 1GB RAM.

---

### Post by alabasterjones on 2009-02-25
So, to put a capper on this thread and tie up any loose ends (yuk yuk yuk, thread, right?) I am typing this in Ubuntu Feisty Fawn on the 500Mhz 256MB RAM (upgraded from 64 orig.) HP Pavillion I received from Staples some 9 or so years ago.
And it works! :p Beautifully, I might add.
So with a feather in my cap, and the collective caps of everyone who responded...We were both wrong.
I got Puppy linux to run, but couldn't connect via PPPoe with that either...So...I just took a look at the Verizon supplied cable and noticed the USB. Plugged that in instead of the cat5...and voila, internet.

It was the ethernet card, or possibly linux's reaction to the ethernet card, or a little bit of both.

---

### Post by jbysmith on 2009-02-25
Glad you got it worked out.  256MB is still going to be a little tight, but hey if it runs, it runs.

And as a side note, Feisty is the bomb, until I toyed with the latest 9.04 build it was my favorite release. It was fast, and it just worked. Just keep in mind it's officially retired and won't be getting updates, security or otherwise.  (You typically can do it yourself however..)

---

### Post by zero244 on 2009-02-25
Go to puppy Linux and download one of the puplets called NOP Puppy Linux 4.12
If its not there do a google search and find it.
NOP also has a puppy linux version 3.01 that comes installed with compiz.
It is in the puplets section as well.

I'm running it right now with compiz.
I'm running it on a 2gig ram machine but it should run fine on 256 megs.
It comes with a very nice setup, including opera and other nice programs.
Good luck.

---

### Post by Name change on 2009-02-25
As some mentioned before: Try Arch with LXDE I think it will do the trick.
And even though I never tried Xfce I feel that LXDE is still better at least at being lightweight...

---

### Post by kspncr on 2009-02-25
> **wolfen69 said:**
> i can install linux on a turd.

And believe me, it *can* be done. ;)

---

### Post by solwic on 2009-02-25
> **wolfen69 said:**
> i can install linux on a turd. 

You speak like a man with personal experience.  :P

---

### Post by Tamlynmac on 2009-02-25
> jrock612
You speak like a man with personal experience.  :razz:
:lolflag::lolflag::lolflag:

---

### Post by 3rdalbum on 2009-02-26
You don't have to "type sudo for everything", only for things that need to be run as an administrator. It's part of a practice called "separation of user and administrator" and it's the way operating systems are these days. Windows XP predates the idea of doing this on desktop computers, and this must be why you are not familiar with it.

---

### Post by jbysmith on 2009-02-26
> **3rdalbum said:**
> You don't have to "type sudo for everything", only for things that need to be run as an administrator. It's part of a practice called "separation of user and administrator" and it's the way operating systems are these days. Windows XP predates the idea of doing this on desktop computers, and this must be why you are not familiar with it.

That's a very good point.  Until Vista came around, every Winders OS had you running in administrator mode by default, and that taught some *very* bad and unsafe computing habits.  Old habits will die hard too, look at how many complaints there are against UAC in Vista, and I'd bet most people just turn the thing off.  (Granted, it *is* a little too chatty.)  

It's just keeping your system more secure.  Granted, if you don't think and type "sudo ./installmytrojan.sh" it's not going to bail you out, but you shouldn't be using sudo or su unless you know what the ramifications are anyway.

---

### Post by solwic on 2009-02-26
> **3rdalbum said:**
> You don't have to "type sudo for everything", only for things that need to be run as an administrator. It's part of a practice called "separation of user and administrator" and it's the way operating systems are these days. Windows XP predates the idea of doing this on desktop computers, and this must be why you are not familiar with it.

Besides, if you need to do a lot as root, just run ```
sudo -i
``` and then run your commands, using ```
exit
``` when you're done to go back to your user account.  

Only have to type sudo once, that way.  :)

---

### Post by alabasterjones on 2009-03-12
Double Success!
BTW, I just got this HP Pavillion 6630's ethernet card working too (which was my main complaint) with Feisty!

[http://forums.fedoraforum.org/archive/index.php/t-20962.html](http://forums.fedoraforum.org/archive/index.php/t-20962.html)

This ^ being the key. You have to go into your "BIOS" and change the specified operating system to Other. Your 3 choices? Win95 Win98/NT and "Other". Yay Ubuntu!

---

### Post by stchman on 2009-03-12
> **alabasterjones said:**
> I got into the idea of linux probably a year or so ago, but I'm really starting to see its limitations. Recently, (as in, for the last 2 weeks) I have been trying to install any stable linux distro onto an old 500Mhz HP PC of mine. I tried Debian, FreeBSD, Ubuntu, Xubuntu, Damn Small Linux, Puppy linux, WattOS, and 5 versions of my linux distro of choice Linspire/Freespire. 

The *only* operating system I could get to work on the machine was Windows XP. Not only was it the only OS to install successfully, but it could also run faster on 64 MB RAM than Windows 98 (the previous OS). 

So, to try to give linux a second shot, I ordered more RAM. The thing has a max of only 256MB according to the web. So now it has 256 in it and I tried all my linux discs again. The only one to work was my old Fesity Fawn unbuntu distro. BUT, there is this very common problem with Ubuntu not working with wired DSL/pppoe. So I can't connect to the internet.

What a pain! Windows XP worked more than fine and Ubuntu is nothing but disappointing. I've even gotten my wireless card in my laptop to work with Ubuntu, but this other problem is much more severe. 

What I'm starting to realize is this:
What the **** is the point of all these linux distros if none of them work on old machines with less than 256MB RAM and 500Mhz, and can't support standard essential items like _an ethernet card_! 
This is my other point: Earlier versions of Windows and Mac OS DO! And they don't require so much fiddling about on the command line. Why are all the people on these forums obsessed with command line arguments as if they are so cool by knowing them? You don't sell a car without a god damn frame and then expect the owner to fix all the problems themselves with a wrench by hand. If you guys were really so knowledgeable about how computers communicate you would do every thing in the lowest language possible: 100011010100101001. 

Why the hell do we have to type sudo for everything as well??
[http://xkcd.com/149/](http://xkcd.com/149/)

It would seem you are basing the success of Linux on installing it on some old a$$ HP PC.  Whatever.  I gave a PC with similar specs like that one away and it ran XP like dog cr@p.

Yes, install Windows Vista on that machine and tell us how it goes.

While you are at it try installing OS X on it as well.

So when you fail to install Vista and OS X I want to see your abstraction threads on that subject matter.

Ubuntu needs a minimum of 256MB to install properly.  Puppy would have been a perfect candidate for that old junker.

---

