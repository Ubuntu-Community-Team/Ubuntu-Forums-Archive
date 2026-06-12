---
title: "What ACTUALLY is making Linux bloated?"
date: 2008-12-02
forum: The Cafe
---

### Post by skymera on 2008-12-02
Hello.

I've used Ubuntu since 7.04 and loved it ever since. But noticeably after every release it does use more CPU and RAM and generally becomes slower. But what EXACTLY is causing this?

When going through all the settings 8.10 and 7.04 aren't that different. Yet in terms of speed and resources they are very different.

7.04 could run using 100MB RAM and 200MB tops for me.
8.10 uses 300MB and 800MB tops!

Before you mention or spam this. I KNOW this is asked a LOT. But there ISN'T a definite answer on WHAT is causing the bloat.

I've hacked Ubuntu 8.10 to pieces before ripping out almost all junk i could and still couldn't match the performance of Feisty. Why is this? 

I could boot Feisty to desktop in 11 seconds on a computer slower than the once i'm on now. With Ibex, almost with everything at boot disabled i couldn't even get within 7 seconds of Feisty.

It's not Ubuntu in general, so far every distro i've tried has been a big fat blob. 

Surely this is very noticeable since a lot more threads are requesting "Speed up Ubuntu" or about memory usage.

You can move this thread, delete this thread. Whatever, but i'd just like clarification of what is ruining Linux. 

ciao

---

### Post by Martje_001 on 2008-12-02
I have no idea..

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

but read that, anyway ;).

---

### Post by skymera on 2008-12-02
Thanks for the link.

My experience:

1.86GHz Core2Duo, 1GB DDR2 533MHz, 7200RPM 8MB cache hard drive - booted 11 secs.

2.66GHz Core2Quad, 4GB DDR2 800MHz, 10,000RPM 16MB caceh hard drive - 20sec boot.

And that link is HIGHLY embarrassing.

---

### Post by smartboyathome on 2008-12-02
Part of the problem is Compiz, and another part is GNOME. Both are memory hogs.

---

### Post by Dr Small on 2008-12-02
> **skymera said:**
> It's not Ubuntu in general, so far every distro i've tried has been a big fat blob. 


I disagree. ArchLinux is the fastest distro I have ever tried.

---

### Post by Ub1476 on 2008-12-02
One thing is DEs becoming more advanced. Linux in itself isn't bloated. Also there's some other stuff which they mention on phoronix which is pretty important.

---

### Post by jomiolto on 2008-12-02
I can come up with several reasons, but I don't know if anyone has done any serious research on this, so I don't think anyone can say it for sure. One natural reason for the slowness and bloat is added cruft; with each release there are more and more daemons and services running on the background (bluetooth, wireless, etc.), whether those services are actually used or not. Usually applications also have a tendency to get more bloated during their life cycle, because more features and code is added with each release.

When it comes to memory usage, you must also remember that the more memory you have in your computer, the more of it is required for managing all that memory. This is why the memory usage can be very different between computers that have different amount of memory installed.

---

### Post by RiceMonster on 2008-12-02
> It's not Ubuntu in general, so far every distro i've tried has been a big fat blob.

What distros? You've only convinced me that Ubuntu is getting slower.

---

### Post by Twitch6000 on 2008-12-02
Well like the others have said its mainly just ubuntu's fault and a some of what it uses.

Gnome and Compiz are also at fault.

I know I have used PClinuxOS and Mandriva both in KDE and Gnome and I can say KDE is alot faster.

Now Compiz is still beta sooo hey its got bugs.

As for Ubuntu well they have said in 9.04 they are planning on getting the speed back into it.

However I do believe it won't be as fast as it use to be,but sure as hell better then it currently is.

Anyways I think you should try out something other then gnome.
I know KDE and XFCE are very very nice.

---

### Post by will1911a1 on 2008-12-02
What distros have you been using?  Arch is still as lean as ever.

---

### Post by billgoldberg on 2008-12-02
> **skymera said:**
> Hello.

I've used Ubuntu since 7.04 and loved it ever since. But noticeably after every release it does use more CPU and RAM and generally becomes slower. But what EXACTLY is causing this?

When going through all the settings 8.10 and 7.04 aren't that different. Yet in terms of speed and resources they are very different.

7.04 could run using 100MB RAM and 200MB tops for me.
8.10 uses 300MB and 800MB tops!

Before you mention or spam this. I KNOW this is asked a LOT. But there ISN'T a definite answer on WHAT is causing the bloat.

I've hacked Ubuntu 8.10 to pieces before ripping out almost all junk i could and still couldn't match the performance of Feisty. Why is this? 

I could boot Feisty to desktop in 11 seconds on a computer slower than the once i'm on now. With Ibex, almost with everything at boot disabled i couldn't even get within 7 seconds of Feisty.

It's not Ubuntu in general, so far every distro i've tried has been a big fat blob. 

Surely this is very noticeable since a lot more threads are requesting "Speed up Ubuntu" or about memory usage.

You can move this thread, delete this thread. Whatever, but i'd just like clarification of what is ruining Linux. 

ciao

Most likely it's gnome and compiz fusion.

If you like speed, Ubuntu isn't the distro for you. It's a modern distro for modern pc's.

That being said, switching to fluxbox and using alternative software like epiphany and pcmanfm instead of firefox and nautilus can do miracles.

---

### Post by Majorix on 2008-12-02
Try a barebones install of Ubuntu. Don't install Compiz or Gnome and all other large programs in the process. You will see a lot of improvement.

---

### Post by snowpine on 2008-12-02
It all depends what you mean by "bloated." The average computer gets faster and more powerful every year, and new versions of software add new features to take advantage of the resources. If you like the old software, it doesn't cease to exist simply because a new version with more features comes along. :)

I could also make the counter-argument that Linux is getting *less* bloated. A couple of years ago, if you wanted a nice lightweight system, you could download DSL at 50mb. But now, you can use SliTaz that is only 25mb. The conclusion one draws is dependent upon the examples one chooses to support it. :)

---

### Post by jimi_hendrix on 2008-12-02
xorg = bloat

---

### Post by skymera on 2008-12-02
Not installing Gnome and not installing Compiz is just excuses.
I used both on 7.04 and it was speedy.

I'm also not saying EVERY Linux distro is slow, i said every Linux distro I'VE tried has been slow.

billgoldberg - I understand Ubuntu is for modern PCs. But my PC is not ancient machine. Infact i built it just over a month ago and Ubuntu is still relatively slow.

I'm still distro hopping do you never know. I might find one that satify's me. Perhaps i'm too picky?

---

### Post by Rokurosv on 2008-12-02
Standard Ubuntu is filled with lots of stuff, and has GUI for almost everything, Gnome and KDE are both heavy DE compared to XFCE or any blackbox derivative. You should try purging the apps you don't need, turning off compiz, checking for the runlevel scripts, see what modules you don't need, etc. But if it's speed you're looking for try for a very minimal distro like Arch, Debian, sidux or maybe Crux.

---

### Post by init1 on 2008-12-02
> **skymera said:**
> 
It's not Ubuntu in general, so far every distro i've tried has been a big fat blob. 

Debian isn't

---

### Post by skymera on 2008-12-02
I tried Debian Lenny not so long ago.

Might try the latest, Sid?

---

### Post by markp1989 on 2008-12-02
> **skymera said:**
> Hello.

I've used Ubuntu since 7.04 and loved it ever since. But noticeably after every release it does use more CPU and RAM and generally becomes slower. But what EXACTLY is causing this?

When going through all the settings 8.10 and 7.04 aren't that different. Yet in terms of speed and resources they are very different.

7.04 could run using 100MB RAM and 200MB tops for me.
8.10 uses 300MB and 800MB tops!

Before you mention or spam this. I KNOW this is asked a LOT. But there ISN'T a definite answer on WHAT is causing the bloat.

I've hacked Ubuntu 8.10 to pieces before ripping out almost all junk i could and still couldn't match the performance of Feisty. Why is this? 

I could boot Feisty to desktop in 11 seconds on a computer slower than the once i'm on now. With Ibex, almost with everything at boot disabled i couldn't even get within 7 seconds of Feisty.

It's not Ubuntu in general, so far every distro i've tried has been a big fat blob. 

Surely this is very noticeable since a lot more threads are requesting "Speed up Ubuntu" or about memory usage.

You can move this thread, delete this thread. Whatever, but i'd just like clarification of what is ruining Linux. 

ciao

I have to agree, ubuntu is getting more bloated with time, and you cant blame compiz, or gnome, because 90% of the time i would use openbox, or icewm, i tried ibex, and i just didnt like it , i dont know why, so i decided to try out arch, and it is a lot faster .

---

### Post by lisati on 2008-12-02
I was happily using Ubuntu 7.04 on my laptop until 8.10 came out. Even with a switch to Xubuntu with its smaller resource requirements, it does sometimes seem to struggle more often (it only got 256Mb) Never mind, it works well enough for what I use that particular laptop for......

---

### Post by cmay on 2008-12-02
> **skymera said:**
> I tried Debian Lenny not so long ago.

Might try the latest, Sid?

i have been using lenny on a old computer with the specs 689 proccesor and 300 mb ram and it simply is lighting fast compared to any other distro that uses gnome. this is the cd 1 image full install and it works. i have then installed the cd 1 from base and up which in this sentence means uncheck everything and then add what i would like to have after. i got after-step and flux-box and it really is fast enough compared to the other computers i have tried with windows or ubuntu on it. i sometimes fix older computers for others but it is not that much i do but i have seen a pc at times that has twise the amont of ram and greater proccesor that is slow both on windows and after "fixin"it (install ubuntu) it is still slower sometimes than this old pc i am using lenny on.

---

### Post by klange on 2008-12-02
> **billgoldberg said:**
> Most likely it's gnome and compiz fusion.
> **smartboyathome said:**
> Part of the problem is Compiz, and another part is GNOME. Both are memory hogs.

Shenanigans.

Compositing saves countless CPU cycles and memory accesses by pushing virtually all aspects of window rendering to graphics hardware. It's not Compiz.

Gnome on the other hand...

---

### Post by kk0sse54 on 2008-12-02
> **WindowsSucks said:**
> Shenanigans.

Compositing saves countless CPU cycles and memory accesses by pushing virtually all aspects of window rendering to graphics hardware. It's not Compiz.

Gnome on the other hand...

Not so much compiz as it's compiz fusion

---

### Post by Koori23 on 2008-12-02
Compared to KDE and GNOME, XFCE is lighter on Hardy.. Not so much on Ibex. My laptop with 512MB sits at 280Meg at startup with Ibex.

I will say, you can lean down your install quite a bit more now than you could in the past. Dependancies are more modular. You can remove many things without blowing your whole system away with Hardy and Ibex.

Here's my Hardy install after running for 10 hours. You can see what I have open

---

### Post by blazercist on 2008-12-02
Its udev and the kernel me thinks.  All the distros have been slowing slightly over time as the kernel advances.  udev may be a ubuntu specific reason but not necessarily.

---

### Post by Dr Small on 2008-12-02
> **jimi_hendrix said:**
> xorg = bloat
I laughed when I read that.

---

### Post by billgoldberg on 2008-12-02
> **WindowsSucks said:**
> Shenanigans.

Compositing saves countless CPU cycles and memory accesses by pushing virtually all aspects of window rendering to graphics hardware. It's not Compiz.

Gnome on the other hand...

I can assure you the compiz fusion effects will cause slowdowns on older systems or slower systems.

---

### Post by Eisenwinter on 2008-12-02
> **Dr Small said:**
> I disagree. ArchLinux is the fastest distro I have ever tried.
+1. I am currently in the process of setting up an Arch installation, and mess around with it.
So far, I love it.

Now, for the topic, it's also worth mentioning that the Linux kernel caches things in RAM, so if you see "20mb free" in free -m, but you have 2GB - don't panic, it's not Ubuntu or whatever other distro you're using, it's the kernel caching items for quicker access.

This memory will be released should an application need it.

---

### Post by klange on 2008-12-02
> **billgoldberg said:**
> I can assure you the compiz fusion effects will cause slowdowns on older systems or slower systems.

I can assure you that my "older systems" operate at significantly improved speeds with Compiz over Metacity.

---

### Post by jimi_hendrix on 2008-12-02
> **Dr Small said:**
> I disagree. ArchLinux is the fastest distro I have ever tried.

i love arch...like how simple it is to remove my KDE desktop and install xfce

---

### Post by bruce89 on 2008-12-02
I wonder what the depreciation of libgnome*, bonobo, gnome-vfs and so on will do memory-wise.

---

### Post by cardinals_fan on 2008-12-02
My system (SliTaz + dwm) uses 32 MB of RAM on boot.  Doesn't seem too bloated to me.
> **Dr Small said:**
> I laughed when I read that.
Actually, I just moved my systems (both SliTaz [which came with it] and Slackware) over to Xvesa.  It's very light and nice :)

---

### Post by samjh on 2008-12-02
As Linux distributions continue the trend toward ease-of-use and compatibility, they will become "bloated".  It's inevitable.

Distributions like Arch allow the user to customise much of the distribution to suit the individual needs of that user.  That's why it feels light.

Distributions like Ubuntu, Fedora, OpenSUSE, etc., cater for ease-of-use and maximum compatibility, so there are a lot of features - applications, services, drivers, and so on, that are enabled by default.  The end result is that it takes more RAM and CPU cycles than thoroughly customised distros.

What is "bloat" anyway?  It's a very subjective term that changes with the times.  One could argue that even bare-bones Linux is bloated compared to MINIX, early Unix, and even MS-DOS.  Five years from now, Ubuntu of today will seem fast and light.

---

### Post by CholericKoala on 2008-12-02
^^ thats true.  If you want to bash on things being bloated, just switch to MINIX3 and there you have a 25000 line kernel, as opposed to Linux's 2.5 million lines.

---

### Post by Polygon on 2008-12-02
firefox uses a lot of ram
 
if ubuntu is using 800mb of memory, then there is a memory leak somewhere in some program. I almost never go over 500 mb, and even then thats with firefox running and im doing compiling or something,

you can check the individual program memory usage in system monitor, its almost always gnome itself, firefox, other various common programs.

---

### Post by bruce89 on 2008-12-02
> **Polygon said:**
> if ubuntu is using 800mb of memory, then there is a memory leak somewhere in some program.

That's not necessarily the case. If the memory use of one program increases over a long time, then it's a leak. If it's high all the time, it is not being efficient with its memory allocation.

---

### Post by CholericKoala on 2008-12-02
800mb of ram!?

If I use over 400, there is a problem.  Granted I might run a VM or something, but thats an exception.

---

### Post by SomeGuyDude on 2008-12-02
In Ibex, something is very wrong with Nautilus. Before I switched away from Ubuntu and GNOME in general, my machine was showing Nautilus using upwards of 500MB of RAM most of the time. Even killing and restarting it only helped temporarily.

---

### Post by Tatty on 2008-12-02
That Phoronix article in post #2 seemed quite enlightening.  I have certainly "felt" a slight drop in performance between each release which seems to match up with their results.

Im glad some people have started to test and analyse this, hopefully it should lead to a few problems being uncovered and fixed.
Its certainly going to help more than endless forum debates in the form "Release X is slower than release Y" - "No its not" - "Yes it is" - "It works fine on my machine".

There has been such rapid improvement to open source over the last few years that there will surely soon be a need for some consolidation and refinement of the code.
I see it as another notch in the evolution of linux.

---

### Post by skymera on 2008-12-03
wow didn't think this'll have so many replies. Seems a hot topic on peoples minds.

Tatty, i agree.

I'm downloading Ubuntu 8.04 and going to see how much junk i can rip out etc.

Bruce89 - Yeah my memory did hit 800MB. Showed in htop and also system monitor.

Anyway time to go to college, got my Linux vs Windows XP assignment. Should be interesting.

---

### Post by Giant Speck on 2008-12-03
> **SomeGuyDude said:**
> In Ibex, something is very wrong with Nautilus. Before I switched away from Ubuntu and GNOME in general, my machine was showing Nautilus using upwards of 500MB of RAM most of the time. Even killing and restarting it only helped temporarily.

I had that happen when I first used Ibex.

I was noticing that Nautilus was using almost 200 MB of RAM (more than Firefox!).  I really couldn't figure out how to stop it from using that much RAM.  So I went into the preferences and told it not to preview pictures or audio files.  Nautilus's RAM usage dropped down to 25 MB.

---

### Post by mihai.ile on 2008-12-03
Well to answer directly to the topic: simple, all the things I do not use and come installed.
You see Ubuntu is not a personalized per user distro but per community. A large community with many tastes so it's not easy to add things that all will use.

---

### Post by Dragonbite on 2008-12-03
> **Martje_001 said:**
> I have no idea..

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

but read that, anyway ;).

Wow, that really shows a difference.

I didn't think much of it but yeah, my Edubuntu 7.10 boots up faster than my Ubuntu 8.04 but I attributed it to Desktop vs Laptop and system difference (2.0 GHz vs 1.4 GHz, 7200 RPM HDD vs 5400 RPM HDD, etc.)

Didn't know about the preview taking up so much RAM, gotta try that sometime though that isn't going to speed up the bootup time.

Another suggestion I've read was to turn off, extend the time of or totally eliminate the finders and anything that indexes the system.

Xfce is a little faster but not a save-all. I have noticed KDE has been doing a wonderful job of managing memory and speed.  It has actually REDUCED it's memory use in some (pre-4.x) iterations.

I don't know about Arch but my first inclination is if you want speed then install Gentoo and optimize it for your system.  Of course, then you loose the ease-of-use that Ubuntu is known for.

I would not be surprised if it is a factor of a lot of systems and apps taking just a little more resources with each update to facilitate new features and these resources add up to a lot; nautilus, compiz, evolution, bluetooth, kernel, indexing, etc.

I only have a little room to complain, though, because my work computer has so many start-up scripts that it takes (literally, I have timed it) 15 minutes to boot up!  I had to time it because my boss wants us to send an email when were come into the office and I realized it was giving an incorrect view because even if I get to work on time the email can't be sent until 15 minutes later!

---

### Post by earthpigg on 2008-12-03
dragonbite, what in gods name do you do on that computer?

---

### Post by Dragonbite on 2008-12-03
> **earthpigg said:**
> dragonbite, what in gods name do you do on that computer?

It's a laptop. If I boot it without it being connected to the network and then plop it onto the docking station and it connects to the network then I can have Outlook (2007) open in about 5-6 minutes.

I reduced the time for getting Outlook to be responsive by offloading my RSS news feeds to a local PST file instead of having it try and updated all of those from the Exchange server.

Other than that.. I dunno!  I've tried turning off services and setting up shortcuts to turn them on only when I need them (like IIS and VMWare Server).

We're trying to convince the "powers to be" to run Linux but it isn't going so well.  All 3 of us in IT are open to the idea of running Linux or BSD.  Maybe they'll be more open when we have everybody moved off to a virtualized thin client system?

---

### Post by rnevins82 on 2008-12-03
I'm kinda stunned here people. You've all been given this super wonderful gift,, a free OS that completely blows away any other OS anywhere. Since I switched last week from Windows to Ubuntu/Kubuntu, it's like waking from a coma, it's just so amazing! And you're complaining...I just don't get it.

You say it's slower than it used to be, and that may be true, I don't know, but it's so much better than any of the alternatives in my opinion, and it could be worse, and it's free ffs!!! 

This is so much faster than anything I've ever used before. My PC is very stable, and runs faster and better than it ever has before. 

I could be mistaken though, and you're not really complaining (( i hope!), just discussing issues, and if so I apologize for getting up on my soapbox. Feel free to email me and yell at me. I'm pretty outspoken,, and often overstep my bounds. 

Just adding my two cents!


~Robyn

---

### Post by Martje_001 on 2008-12-03
rnevins82, I completely agree. But, on the other hand, if we go this way on (use more memory, making more CPU cycles) we'll be worse than Windows in the future..

---

### Post by Vince4Amy on 2008-12-03
> You say it's slower than it used to be, and that may be true, I don't know, but it's so much better than any of the alternatives in my opinion, and it could be worse, and it's free ffs!!!

So what if it's free, if nobody complains about these things, then the developers will never be aware of them. Sure an OS from 2008 is going to be slower than XP from 2001. But there are some distros which are much slower than XP and not much better off than Vista. Vista runs great for me.

On the other hand OpenSUSE is still really fast for me.

---

### Post by sdowney717 on 2008-12-03
auto hardware detection and configuration at boot in real time eats up more time, but gives better results.
my xp boot is around 4 minutes people!
same system booting ubuntu is under a minute.
I still like Ibex, even though it has slowed since Feisty.

---

### Post by Icehuck on 2008-12-03
> **Dragonbite said:**
> It takes a long time for my laptop to boot, etc, etc, etc.


I had a similar problem with an XP laptop. It turned out the cached user profile was bad. I deleted the profile and recreated it and I had no problem after that.

---

### Post by earthpigg on 2008-12-03
> **rnevins82 said:**
> I'm kinda stunned here people. You've all been given this super wonderful gift,, a free OS that completely blows away any other OS anywhere. Since I switched last week from Windows to Ubuntu/Kubuntu, it's like waking from a coma, it's just so amazing! And you're complaining...I just don't get it.

...

~Robyn

just because we are grateful doesn't mean we shouldn't air our feelings on certain issues. linux and ubuntu developers **seek **feedback and input.

no one is forced to use linux, much less ubuntu. everyone here knows that if ubuntu is to slow, there are much **much **faster alternatives.

recall the thread title, "what is actually making linux slower?"

very valid question!

why? because linux and ubuntu are open source and transparent.

if that question ("what is making linux slower?") gets an answer, then you can simply remove that from your system if you dont use it and get what you want, how you want it, when you want it... and nothing more... **that **is the strength of linux. **that **is why us recent converts find it so much snappier and more stable than windows - because people smarter than us ask questions like the one that started this thread, and find answers, and bums like me can ride their coat tails to get a great home desktop experience for free.

discussion and community are a key asset that makes linux in general, and ubuntu in particular, what it is.

so we should all think twice before using whatever influence we have (or dont have, in my case) to stifle discussion. ;)

---

### Post by Dragonbite on 2008-12-03
> **rnevins82 said:**
> I'm kinda stunned here people. You've all been given this super wonderful gift,, a free OS that completely blows away any other OS anywhere. Since I switched last week from Windows to Ubuntu/Kubuntu, it's like waking from a coma, it's just so amazing! And you're complaining...I just don't get it.

It's kinda like "Why do we Americans make fun of our President? Because we CAN!".  There are places where criticism gets you shot. Are we grateful for this freedom? We should be. Being part of such a large country we are bound to have somebody with conflicting ideas and they are allowed to air them just as much as you and I and this way ideas do get passed along and can reach the people who are able to make a change.

With Linux, there is (even the slightest) chance that this grip will be moved up to people with the power to change it and capable developers may even be able to provide the solution as well.

With Windows and Apple you can cry all you want but you have to convince "their majesty" that it is an issue worthy of their attention!

---

### Post by skymera on 2008-12-03
Very good replies guys.

This topic isn't going unnoticed. A lot of people say Linux is getting slower.
They need to optimise the source code now, it's friendly enough

---

### Post by mentallaxative on 2008-12-03
> **skymera said:**
> Very good replies guys.

This topic isn't going unnoticed. A lot of people say Linux is getting slower.
They need to optimise the source code now, it's friendly enough

Source code for what? ;)

While I'm all for making operating systems as fast as they can be, I think the bloat will continue to grow as people request more features and more hardware support. Make Ubuntu user-friendly first and consider speed second (as opposed to other, more advanced, distros which have the reverse idea).

Deja vu... I swear this thread is a duplicate of one a month or so ago, where I said almost exactly the same thing as above.

---

