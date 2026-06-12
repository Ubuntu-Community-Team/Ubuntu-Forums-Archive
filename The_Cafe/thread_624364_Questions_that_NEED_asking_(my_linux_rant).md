---
title: "Questions that NEED asking (my linux rant)"
date: 2007-11-26
forum: The Cafe
---

### Post by Multi-Booter on 2007-11-26
OK, I'm sure many of you are far more "in the know" than me...

But anyways, my thoughts are these, and maybe you all can correct the error in my logic...

Installing 7.10 has by far been my best 'hardware' experience yet with any linux distro. I still need to go through everything and check what is being used for drivers, and make a few changes, etc... BUT EVERYTHING APPEARS TO WORK, AT LEAST FUNCTIONALLY RIGHT OUT OF THE GATE.

This sparked a thought process that had me asking myself questions.
So here is the main thought/point/rant...

It seems no matter what flavor of linux you are talking about, they all seem to be feverishly working towards the next version/update/release... it seems as soon as each new one is released. New ones roll out OFTEN.

I myself do not exactly understand this logic. It seems to me that it would be maybe better if one would instead slow down and build better upon and already working stable environment. And instead of working on the next new version, instead focus all this brain power towards building AN EXTENSIVE HARDWARE DRIVER BASE to vastly increase **NATIVE** hardware detection and support within the linux distro.

I'm not suggesting trying to include everything in the installation. Just functional after install is fine. Then for example, to optimize, you would for example go to Ubuntu's site, go over to the driver base, look up your hardware, download your specific Ubuntu drivers for your hardware items, install them and be done with it.

Surely there is a logical reason why nobody is doing this.
So enlighten me.

---

### Post by rsambuca on 2007-11-26
> **Multi-Booter said:**
> Surely there is a logical reason why nobody is doing this.
So enlighten me.

Do you mean "Please enlighten me"? :)

Anyways, not all distros have as an aggressive release schedule as Ubuntu.  In fact, Ubuntu has one of the quickest release schedules there is.  If you have issues with this schedule, then you probably don't agree with Ubuntu's core philosophy.  Perhaps you might be more interested in something like Debian stable (currently called Etch), which has a much slower release schedule.

Secondly, is it really the Ubuntu developers' job to create drivers for the entire opensource community?  The drivers are being written and worked on by many different groups, and the nice thing is, they all integrate nicely into the linux kernel.  They are working as fast as they can (most of it is developed by volunteer efforts, remember).  The drivers are already out there.

---

### Post by Multi-Booter on 2007-11-26
Give up my 7.10 for something else?... You gotta be kidding me :biggrin:
I am by far the most impressed with this fresh install of any ever.
Everything worked at least in some acceptable capacity at first boot.
No way I'm giving that up.


Where would I find all these drivers that are already out there?

---

### Post by jfinkels on 2007-11-26
Ubuntu as a project is not a make-as-many-drivers-as-possible project. It is a project with a broad-scope, so there is a lot of work to be done all the time. From the documentation at help.ubuntu.com:
> Ubuntu aims to create a distribution that provides an up-to-date and coherent Linux system for desktop and server computing.

[...]

By focusing on quality, Ubuntu produces a robust and feature-rich computing environment that is suitable for use in both home and commercial environments. The project takes the time required to focus on finer details and is able to release a version featuring the latest and greatest of today's software once every 6 months. 

---

### Post by aysiu on 2007-11-26
Debian focuses on stability.

And hardware detection is usually in the Linux kernel, which all distros share.

---

### Post by Multi-Booter on 2007-11-27
I'm not suggesting particularly that Ubuntu do it...

It would just be nice if someone would take interest in focusing on it...
Whoever did it would have the wildly popular 'flavor' for sure.

I just think it would possibly be one of the best things for 'progress' in the linux community.

A strong collaborative effort would work as well I guess.

---

### Post by aysiu on 2007-11-27
> **Multi-Booter said:**
> I'm not suggesting particularly that Ubuntu do it...

It would just be nice if someone would take interest in focusing on it... And I thought I already said that Debian does this.

> 
A strong collaborative effort would work as well I guess. There already is a strong collaborative effort. The hardware detection is through the kernel, and all Linux distros share the same kernel.

---

### Post by rsambuca on 2007-11-27
> **Multi-Booter said:**
> I'm not suggesting particularly that Ubuntu do it...

It would just be nice if someone would take interest in focusing on it...
Whoever did it would have the wildly popular 'flavor' for sure.

I just think it would possibly be one of the best things for 'progress' in the linux community.

A strong collaborative effort would work as well I guess.

You see - You have now gone from "Ubuntu should ... "  and now are saying the "linux community" should.

---

### Post by yatt on 2007-11-27
> **Multi-Booter said:**
> OK, I'm sure many of you are far more "in the know" than me...

But anyways, my thoughts are these, and maybe you all can correct the error in my logic...

Installing 7.10 has by far been my best 'hardware' experience yet with any linux distro. I still need to go through everything and check what is being used for drivers, and make a few changes, etc... BUT EVERYTHING APPEARS TO WORK, AT LEAST FUNCTIONALLY RIGHT OUT OF THE GATE.

This sparked a thought process that had me asking myself questions.
So here is the main thought/point/rant...

It seems no matter what flavor of linux you are talking about, they all seem to be feverishly working towards the next version/update/release... it seems as soon as each new one is released. New ones roll out OFTEN.

I myself do not exactly understand this logic. It seems to me that it would be maybe better if one would instead slow down and build better upon and already working stable environment. And instead of working on the next new version, instead focus all this brain power towards building AN EXTENSIVE HARDWARE DRIVER BASE to vastly increase **NATIVE** hardware detection and support within the linux distro.

I'm not suggesting trying to include everything in the installation. Just functional after install is fine. Then for example, to optimize, you would for example go to Ubuntu's site, go over to the driver base, look up your hardware, download your specific Ubuntu drivers for your hardware items, install them and be done with it.

Surely there is a logical reason why nobody is doing this.
So enlighten me.Because distribution maintainers tend to be poor driver developers and vise-versa. They require completely different skills and knowledge. A driver developer needs intricate knowledge of how the piece of hardware works, a distribution maintainer needs to know how different version of hundreds of software packages interact with each other. If Ubuntu were to say double the time between releases, it wouldn't be much better off hardware wise. Ubuntu's developers aren't driver developers so they would spend more time worrying about making the system as tightly integrated as possible. This could actually mean worse hardware support as the developers would be less inclined to upgrade packages as they had spent month(s) refining the last release and they do not want all the work to go to waste.

---

### Post by 23meg on 2007-11-27
Generally speaking, distribution developers don't work on the components that make up the distribution; upstream developers do that. In the case with the kernel, Linux developers do it. The distribution developers' job is to integrate new features that upstream developers develop, make sure they're working together, in a way that makes sense for the intended audience, and maintain them.

---

### Post by Nunu on 2007-11-27
I My self love Ubuntu to bits and i think its the best OS out there. but one thing that would be nice and I don't know if it is out there or not, is a site where if you have a driver that supports hardware that is not natively supported by ubuntu, you can upload it to and share it with the rest of the Linux community like for instance Lexmark drivers we all know there policy when it comes to open source. I am not a coder and have never even thought of developing my own driver, but i am sure there are people out there that can and has done this. hell maybe even make it apart of the Synaptic source repositories

---

### Post by Multi-Booter on 2007-11-27
> **aysiu said:**
> And I thought I already said that Debian does this.

 There already is a strong collaborative effort. The hardware detection is through the kernel, and all Linux distros share the same kernel.

I'm checking out Debian as we speak...
I haven't before because it never caught my interest.

As for the hardware detection... Gutsy seems pretty good at it in my experience.
I like that fact and I'm impressed.

Other distros I have experienced have not been as good at it.
Heck, for that matter, Gutsy did better than Dapper at detection on my system.
So this is another aspect I do not understand.


On the other hand, still the issue of drivers stands outside of this....
It's one thing to detect the hardware properly and yet another to have a driver assigned to each item to enable the ability to harness the full functionality of the hardware.

Am I making sense there?

And is this not one of the top hurdles that exists?... As in one of the main reasons many try linux and give up on it?

---

### Post by achron on 2007-11-27
If the new versions of Ubuntu rolling out so "often" disturb you, then opt for the last Ubuntu Long Term Support distro (IIRC that is 6.06, which will be supported into 2009, unless memory fails me).

No-one is making you chase the latest releases.  I've gone the 6.06, 7.04, then 7.10 route myself.  6.06 lived the longest on my machine as it was my first Ubuntu installed at home. It was up probably 15 months before I upped to 7.04, but 7.10 got such good reviews that 7.04 lasted only a month or so before I stepped up to 7.10.

---

### Post by 23meg on 2007-11-27
[QUOTE=Multi-Booter]Other distros I have experienced have not been as good at it.
Heck, for that matter, Gutsy did better than Dapper at detection on my system.
So this is another aspect I do not understand.[/QUOTE]

Hardware detection is almost entirely a kernel issue. The other distros you tried probably had older kernel versions, and Dapper's kernel version is much older that of Gutsy's.

---

### Post by Multi-Booter on 2007-11-27
> **Nunu said:**
> I My self love Ubuntu to bits and i think its the best OS out there. but one thing that would be nice and I don't know if it is out there or not, is a site where if you have a driver that supports hardware that is not natively supported by ubuntu, you can upload it to and share it with the rest of the Linux community like for instance Lexmark drivers we all know there policy when it comes to open source. I am not a coder and have never even thought of developing my own driver, but i am sure there are people out there that can and has done this. hell maybe even make it apart of the Synaptic source repositories

There you go....
You have my general thoughts and feelings there in a nutshell.

Not natively supported?.... Just go here, find the hardware, download the driver... no ill side effects...

And also, that is what I am getting at. Most people don't have the ability to make their own drivers. So when people decide to give linux a shot... and their hardware doesn't work or work to it's potential... well there is seldom a second chance to make a first impression. People give up on it... so I think this is something that would boost 'progress'.

For me, it took me all of a few minutes in a fully operational linux system to decide I preferred linux enormously over windows. The same is true of the free software available. I'm also really impressed with Gutsy so far although I do still have some hardware/driver things to iron out.... the funkiest one being deciding what I want to do in regards to my ATI graphics card & widescreen display.

---

### Post by Multi-Booter on 2007-11-27
> **achron said:**
> If the new versions of Ubuntu rolling out so "often" disturb you, then opt for the last Ubuntu Long Term Support distro (IIRC that is 6.06, which will be supported into 2009, unless memory fails me).

No-one is making you chase the latest releases.  I've gone the 6.06, 7.04, then 7.10 route myself.  6.06 lived the longest on my machine as it was my first Ubuntu installed at home. It was up probably 15 months before I upped to 7.04, but 7.10 got such good reviews that 7.04 lasted only a month or so before I stepped up to 7.10.

I had 6.06 too. The handicap there was that my ethernet did not work... :lolflag:

Otherwise I would have stuck there... 

I held out for 7.10 to release and tried it... and I'm glad I did.
It's a much better choice for the system I put it on.

---

### Post by Multi-Booter on 2007-11-27
> **23meg said:**
> Hardware detection is almost entirely a kernel issue. The other distros you tried probably had older kernel versions, and Dapper's kernel version is much older that Gutsy's.

Thank you.

That clarifies the situation for me.
That makes logical sense.

So now I can also see the benefit of the work on newer kernel versions... #-o

---

### Post by Nunu on 2007-11-27
> **Multi-Booter said:**
> There you go....
You have my general thoughts and feelings there in a nutshell.

Not natively supported?.... Just go here, find the hardware, download the driver... no ill side effects...

And also, that is what I am getting at. Most people don't have the ability to make their own drivers. So when people decide to give linux a shot... and their hardware doesn't work or work to it's potential... well there is seldom a second chance to make a first impression. People give up on it... so I think this is something that would boost 'progress'.

For me, it took me all of a few minutes in a fully operational linux system to decide I preferred linux enormously over windows. The same is true of the free software available. I'm also really impressed with Gutsy so far although I do still have some hardware/driver things to iron out.... the funkiest one being deciding what I want to do in regards to my ATI graphics card & widescreen display.

I Agree. as soon as a noob comes along and install ubuntu one or two things like for instance sound cards or graphics cards wont' work properly, they don't always have the knowledge to figure things out . So they just give up and go back to windows because everything works there. and they have the drivers on a disc. I have that problem with my printer at the moment i can't scan or print through ubuntu. i have the option to boot to windows and do my  printing and scanning from there but ultimately i want to get rid of windows. I want to do the whole exorcisms thing on my machine and rid it of the evil that is Microsoft but until i have found the drivers for my printer i cant afford to do so. and that is what will put most new users of of using Linux.

---

### Post by yatt on 2007-11-27
> **Multi-Booter said:**
> There you go....
You have my general thoughts and feelings there in a nutshell.

Not natively supported?.... Just go here, find the hardware, download the driver... no ill side effects...

And also, that is what I am getting at. Most people don't have the ability to make their own drivers. So when people decide to give linux a shot... and their hardware doesn't work or work to it's potential... well there is seldom a second chance to make a first impression. People give up on it... so I think this is something that would boost 'progress'.

For me, it took me all of a few minutes in a fully operational linux system to decide I preferred linux enormously over windows. The same is true of the free software available. I'm also really impressed with Gutsy so far although I do still have some hardware/driver things to iron out.... the funkiest one being deciding what I want to do in regards to my ATI graphics card & widescreen display.
If a driver for it existed, it would be in the kernel/X/ALSA/Cups (forgot about cups, it has printer drivers), unless it is illegal to ship the driver that way (even then some distros still ship them). To have a webpage dedicated to drivers for people to download is rather silly as they should be included by the distro so they work out of the box with no hassle. The basic rule of thumb is, if it doesn't work with what the distro ships, it isn't going to work at all. The only real exception is wireless drivers that need nsdiwrapper, which requires the Windows driver install disk.

Ubuntu ships with as many drivers as its developers know about because the vast majority are included in four or five pieces of software. If they are not, then there is usually a legal issue surrounding it, but Ubuntu has usually found a way around it.

---

### Post by Multi-Booter on 2007-11-27
yatt,

I see you have an ATI Radeon card.

I do too, except mine is an X1300 Pro.

What are you doing for a driver for yours?

---

### Post by yatt on 2007-11-27
> **Multi-Booter said:**
> yatt,

I see you have an ATI Radeon card.

I do too, except mine is an X1300 Pro.

What are you doing for a driver for yours?I am using RadeonHD, which is experimental and a pain to setup.

I'd suggest using Restricted Driver Manager to install fglrx. I think it will also setup X to use it too. It'll say you have to reboot, but I think you can get away with just pressing CTRL+ALT+Backspace (after closing all open apps). After this it should say that fglrx is in use. You can also check by using typing fglrxinfo at the command line, which tends to be more accurate.

---

### Post by Harpalus on 2007-11-27
At the risk of being stoned, I'd like to point out that Linux in general moves fast. It's a very chaotic environment, with a number of groups working on various different things. Almost everybody's focus is "new features". Debian moves slowly - but it's still Linux. They're not directly responsible for maintaining and developing the majority of the code in their system, which still places them at the mercy of the "other groups", who tend to move quickly, as it was stated.

Although your post was primarily about hardware support, I should point out that if you feel development should slow down and concentrate on stability, then it sounds like you'd be more comfortable in BSD. OpenBSD in particular concentrates on a slow development pace and minor, incremental improvements. (As opposed to the sweeping changes in Linux - the new scheduler in the kernel wasn't even completed yet when it was imported and enabled.) FreeBSD moves faster then OpenBSD does, but their development cycle is still slower, and the developers worry more about stability then Linux developers tend to. (EG, unlike Linux, FreeBSD's new scheduler is not being implemented yet, as it's not quite done yet. Compare to Linux.) And unlike Linux, "ls" is FreeBSD ls. Or OpenBSD ls, etc. Not "Gnu ls". They're directly responsible for the creation and maintenance of most of their own code, allowing them to focus on stability better then Debian can.

At least, that's my interpretation. When somebody complains about fast release cycles and "features, features, features!", the first thing that leaps to mind for me is stability, not hardware support. Perhaps you weren't worried about stability at all. :)

(As a side note to the off-topic banter, one of my laptops has an ATI Mobility Radeon x1400 card. It's a widescreen laptop, and I can't get a widescreen resolution running no matter what I do. Only solution would be to install the proprietary driver, which I'm not willing to do. So, I'll have Windows on it until such time as the radeonhd driver becomes stable, as the stretched display I currently get is completely unreadable. :()

---

### Post by igknighted on 2007-11-27
> **Multi-Booter said:**
> OK, I'm sure many of you are far more "in the know" than me...

But anyways, my thoughts are these, and maybe you all can correct the error in my logic...

Installing 7.10 has by far been my best 'hardware' experience yet with any linux distro. I still need to go through everything and check what is being used for drivers, and make a few changes, etc... BUT EVERYTHING APPEARS TO WORK, AT LEAST FUNCTIONALLY RIGHT OUT OF THE GATE.

This sparked a thought process that had me asking myself questions.
So here is the main thought/point/rant...

It seems no matter what flavor of linux you are talking about, they all seem to be feverishly working towards the next version/update/release... it seems as soon as each new one is released. New ones roll out OFTEN.

I myself do not exactly understand this logic. It seems to me that it would be maybe better if one would instead slow down and build better upon and already working stable environment. And instead of working on the next new version, instead focus all this brain power towards building AN EXTENSIVE HARDWARE DRIVER BASE to vastly increase **NATIVE** hardware detection and support within the linux distro.

I'm not suggesting trying to include everything in the installation. Just functional after install is fine. Then for example, to optimize, you would for example go to Ubuntu's site, go over to the driver base, look up your hardware, download your specific Ubuntu drivers for your hardware items, install them and be done with it.

Surely there is a logical reason why nobody is doing this.
So enlighten me.

Hardware support comes from the kernel.  The way to upgrade the drivers is to upgrade the kernel.  Upgrading the kernel mid-release can cause instability for users.  Therefor, it is this quick release cycle that keeps users up to date with drivers.  If you go back to these "slower releasing distros", you will likely find that their hardware support is nowhere near as good, because the newest and best drivers are in the newest kernel.

The reason drivers come with the kernel is because the linux kernel is a monolithic kernel, not a microkernel.  Check wikipedia for the difference.  But in this instance, it can make distributing new drivers to older kernels a pain.

---

### Post by DoctorMO on 2007-11-27
I was working on a hardware database, but lack of interest and help from the community really killed it off; there is a lot of interest but not enough really productive people dedicating time to it.

[www.dohickey-project.com](www.dohickey-project.com)

---

### Post by igknighted on 2007-11-27
> **Harpalus said:**
> (As a side note to the off-topic banter, one of my laptops has an ATI Mobility Radeon x1400 card. It's a widescreen laptop, and I can't get a widescreen resolution running no matter what I do. Only solution would be to install the proprietary driver, which I'm not willing to do. So, I'll have Windows on it until such time as the radeonhd driver becomes stable, as the stretched display I currently get is completely unreadable. :()

You won't run one proprietary driver, so you instead run an entire proprietary OS (with a proprietary ATI driver built in)?  That hardly makes sense...

Besides, AMD/ATI cards run better on OpenGL games on the linux drivers than the windows ones (sometimes by significant margins too), so I would strongly recommend checking them out.

info on latest prop. driver: [http://www.phoronix.com/scan.php?page=article&item=922&num=1](http://www.phoronix.com/scan.php?page=article&item=922&num=1)

Also, the radeonHD driver is usable for 2d use in pre-release form.  See here: [http://www.phoronix.com/scan.php?page=news_item&px=NjIxOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjIxOQ)

And finally, benchmarks of ATI's windows drivers vs. their linux drivers: [http://www.phoronix.com/scan.php?page=article&item=897&num=1](http://www.phoronix.com/scan.php?page=article&item=897&num=1)

---

### Post by Harpalus on 2007-11-27
> **igknighted said:**
> You won't run one proprietary driver, so you instead run an entire proprietary OS (with a proprietary ATI driver built in)?  That hardly makes sense...

Besides, AMD/ATI cards run better on OpenGL games on the linux drivers than the windows ones (sometimes by significant margins too), so I would strongly recommend checking them out.

info on latest prop. driver: [http://www.phoronix.com/scan.php?page=article&item=922&num=1](http://www.phoronix.com/scan.php?page=article&item=922&num=1)

Also, the radeonHD driver is usable for 2d use in pre-release form.  See here: [http://www.phoronix.com/scan.php?page=news_item&px=NjIxOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjIxOQ)

And finally, benchmarks of ATI's windows drivers vs. their linux drivers: [http://www.phoronix.com/scan.php?page=article&item=897&num=1](http://www.phoronix.com/scan.php?page=article&item=897&num=1)

If I'm running Unixen, then I'm doing serious work. I don't use proprietary code on systems I do serious work on. Wine isn't compatible enough to run all my games - so I just meant that I may as well use it as a gaming system, and do serious work elsewhere. But this is rather off-topic, by now...:popcorn:

---

### Post by igknighted on 2007-11-27
> **Harpalus said:**
> If I'm running Unixen, then I'm doing serious work. I don't use proprietary code on systems I do serious work on. Wine isn't compatible enough to run all my games - so I just meant that I may as well use it as a gaming system, and do serious work elsewhere. But this is rather off-topic, by now...:popcorn:

Fair enough.  Just thought I'd point out the strides the AMD drivers have made this fall, because they are eons better than they used to be, and many still assume they behave like the old ones.

But your point is valid, and if it's got an x1400, it must be a decent rig, so why not, right?

---

### Post by tdrusk on 2007-11-27
Debian does this. They have a new stable release every one and a half years (I think?).

---

### Post by aysiu on 2007-11-27
> **tdrusk said:**
> Debian does this. They have a new stable release every one and a half years (I think?).
Sometimes it's three years between releases. I don't believe there's a set schedule for Debian.

---

### Post by tdrusk on 2007-11-27
> **aysiu said:**
> Sometimes it's three years between releases. I don't believe there's a set schedule for Debian.

Yeah I love how they just take their time and make it closest to perfect.

---

### Post by quinnten83 on 2007-11-27
> **Multi-Booter said:**
> 

On the other hand, still the issue of drivers stands outside of this....
It's one thing to detect the hardware properly and yet another to have a driver assigned to each item to enable the ability to harness the full functionality of the hardware.

Am I making sense there?

And is this not one of the top hurdles that exists?... As in one of the main reasons many try linux and give up on it?

Agree.
butthis is because hardware vendors completely snub linux users.
This is what it is like to belong to a minority.

---

### Post by Multi-Booter on 2007-11-28
Well, I ended up downloading Debian. I haven't done a thing with it yet, but in my system there is still room to add something new to play with. I might end up trying it out to see what it's like.



> **DoctorMO said:**
> I was working on a hardware database, but lack of interest and help from the community really killed it off; there is a lot of interest but not enough really productive people dedicating time to it.

[www.dohickey-project.com](www.dohickey-project.com)

...and that's really cool...

Glad to see someone else recognized the need... sorry it hasn't boomed for you though...

---

### Post by 23meg on 2007-11-28
[QUOTE=Multi-Booter]I might end up trying it out to see what it's like.[/QUOTE]

It's like Ubuntu :)

---

### Post by inversekinetix on 2007-11-28
> **quinnten83 said:**
> Agree.
butthis is because hardware vendors completely snub linux users.
This is what it is like to belong to a minority.


Do hardware vendors stand to make much money from linux/linux users?

---

### Post by Multi-Booter on 2007-11-28
> **inversekinetix said:**
> Do hardware vendors stand to make much money from linux/linux users?

Well, with the number of linux users throughout the world... and give the caliber of user most are...
If one company like AMD were to heavily support their hardware for linux.....

I would have to say yes.... I think they would stand to profit significantly.

---

### Post by popch on 2007-11-28
> **inversekinetix said:**
> Do hardware vendors stand to make much money from linux/linux users?

That is a bit hard to say. 

Consider that most 'Linux users' also are 'Windows users' and possibly even 'Mac users', perhaps using the Linux box at home and the other one at work.

Also consider that at least some of those Linux users are involved in purchasing decisions far surpassing the few machines they are personally using.

A vendor which signals that he does not care about curstomer's needs just might find himself serving fewer customers in the long run.

---

### Post by toupeiro on 2007-11-28
> **popch said:**
> That is a bit hard to say. 

Consider that most 'Linux users' also are 'Windows users' and possibly even 'Mac users', perhaps using the Linux box at home and the other one at work.

Also consider that at least some of those Linux users are involved in purchasing decisions far surpassing the few machines they are personally using.

A vendor which signals that he does not care about curstomer's needs just might find himself serving fewer customers in the long run.

Amen!

It was this signal that switched me from an ATi fan to an Nvidia fan.  I still believe to this day that ATi makes a better graphics card from a hardware perspective, but unfortunately, at times, hardware can only be as good as the software controlling it. Trying to get GL support with ATi during the advent of compiz is what really opened my eyes to Nvidia's support model for linux.  Granted, they are making progress, but having worked much closer with Nvidia now, its likely I will not turn my attention back to ATi for my own personal use, unless I reach a physical limitation with an Nvidia card.  I actually may be there [with one particular project]("http://www.panoramtech.com/products/pixelblaster.html") I am working on, but that is yet to be determined, and I actively watch the changelog on ATI's drivers to see their progress.  I want to leverage what I have come to know is better hardware on linux, like I can with Windows.

---

### Post by gn2 on 2007-11-28
> **Multi-Booter said:**
> <snip> the funkiest one being deciding what I want to do in regards to my ATI graphics card & widescreen display.

Have you tried using Envy? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by inversekinetix on 2007-11-28
> **popch said:**
> That is a bit hard to say. 

Consider that most 'Linux users' also are 'Windows users' and possibly even 'Mac users', perhaps using the Linux box at home and the other one at work.

Also consider that at least some of those Linux users are involved in purchasing decisions far surpassing the few machines they are personally using.

A vendor which signals that he does not care about customer's needs just might find himself serving fewer customers in the long run.


Fair point, but by the same token, hardware vendors probably think the same way, people using linux are probably using something else as well.  The vendors will make their money anyway so why invest money in development for linux.



off topic but.....

......why in a linux OS does the real time spell checker mark LINUX as being incorrect?

---

### Post by quinnten83 on 2007-11-28
> **Multi-Booter said:**
> Well, with the number of linux users throughout the world... and give the caliber of user most are...
If one company like AMD were to heavily support their hardware for linux.....

I would have to say yes.... I think they would stand to profit significantly.

There seems to be a 6mill linux userbase, and growing.
If they support the hardware on linux platforms, more users will come.
more profit for them.

Yes, I know chicken-egg!

---

### Post by popch on 2007-11-28
> **inversekinetix said:**
> off topic but.....

......why in a linux OS does the real time spell checker mark LINUX as being incorrect?

For the same reason that in MS Office (German language version) 'Microsoft' is considered missspelt.

---

### Post by popch on 2007-11-28
> **inversekinetix said:**
> The vendors will make their money anyway so why invest money in development for linux.

Some of those few Linux users are responsible for buying very many Windows boxes for the places where they work. And they may not be willing to buy from vendors which blatantly refuse to supply open source drivers or indeed any drivers at all for use with Linux.

---

### Post by yatt on 2007-11-28
> **inversekinetix said:**
> Do hardware vendors stand to make much money from linux/linux users?
Intel did, now pretty much everything is open-source.

---

### Post by Multi-Booter on 2007-11-28
> **gn2 said:**
> Have you tried using Envy? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

No... I tried just using the restricted driver manager yesterday. It worked, but I only have one useable screen resolution for my wide screen display... which I do not like.

But dang it, I think I might just try Envy to see where that gets me.
Looks nice... thanks for the link.

---

### Post by gn2 on 2007-11-28
> **Multi-Booter said:**
> I tried just using the restricted driver manager yesterday. 

Problem with the restricted driver manager is it will only point you to the driver that is in the repositories. 
The driver that is in the repositories may not be the most recent and will not be updated until the next distro release.
The major advantage of Envy is that it will install the most recent driver for your card and I believe it can be used to update if a new driver is released.

---

### Post by yatt on 2007-11-28
> **Multi-Booter said:**
> No... I tried just using the restricted driver manager yesterday. It worked, but I only have one useable screen resolution for my wide screen display... which I do not like.

But dang it, I think I might just try Envy to see where that gets me.
Looks nice... thanks for the link.
Should be able to use ATI Catalyst Control Center to set pretty much any resolution.

---

### Post by yatt on 2007-11-28
> **gn2 said:**
> Problem with the restricted driver manager is it will only point you to the driver that is in the repositories. 
The driver that is in the repositories may not be the most recent and will not be updated until the next distro release.
The major advantage of Envy is that it will install the most recent driver for your card and I believe it can be used to update if a new driver is released.ATI is recommending distros NOT uses the latest fglrx, as it is a regression. Mostly related to AMDCCCLE not working properly and video playback issues. Granted, Ubuntu is using a fglrx from the old code base, but that is because it had way less bugs.

---

### Post by popch on 2007-11-29
> **gn2 said:**
> Problem with the restricted driver manager is it will only point you to the driver that is in the repositories. 
The driver that is in the repositories may not be the most recent and will not be updated until the next distro release.

That might actually be a good idea. What I would like to be installed on my system is not necessarily the most recent driver but the one which tested out with the fewest problems. I trust the maker of the distros and the repos to at least perfunctorily test those drivers.

---

### Post by regomodo on 2007-11-29
sounds like you are using the wrong distro.

Use Debian stable (etch) if you want almost all bugs to not exist within a distro. If you don't want a distro that has regular releases go for Arch. There are none. Just 1 updated continuously.

---

### Post by Multi-Booter on 2007-11-30
Well, for the record, I tried Envy...

When it finished it said I was already using the same version.

There is a newer ATI driver available on the card's website (I think)

---

### Post by Multi-Booter on 2007-11-30
> **Harpalus said:**
> At the risk of being stoned, I'd like to point out that Linux in general moves fast. It's a very chaotic environment, with a number of groups working on various different things. Almost everybody's focus is "new features". Debian moves slowly - but it's still Linux. They're not directly responsible for maintaining and developing the majority of the code in their system, which still places them at the mercy of the "other groups", who tend to move quickly, as it was stated.

Although your post was primarily about hardware support, I should point out that if you feel development should slow down and concentrate on stability, then it sounds like you'd be more comfortable in BSD. OpenBSD in particular concentrates on a slow development pace and minor, incremental improvements. (As opposed to the sweeping changes in Linux - the new scheduler in the kernel wasn't even completed yet when it was imported and enabled.) FreeBSD moves faster then OpenBSD does, but their development cycle is still slower, and the developers worry more about stability then Linux developers tend to. (EG, unlike Linux, FreeBSD's new scheduler is not being implemented yet, as it's not quite done yet. Compare to Linux.) And unlike Linux, "ls" is FreeBSD ls. Or OpenBSD ls, etc. Not "Gnu ls". They're directly responsible for the creation and maintenance of most of their own code, allowing them to focus on stability better then Debian can.

At least, that's my interpretation. When somebody complains about fast release cycles and "features, features, features!", the first thing that leaps to mind for me is stability, not hardware support. Perhaps you weren't worried about stability at all. :)

(As a side note to the off-topic banter, one of my laptops has an ATI Mobility Radeon x1400 card. It's a widescreen laptop, and I can't get a widescreen resolution running no matter what I do. Only solution would be to install the proprietary driver, which I'm not willing to do. So, I'll have Windows on it until such time as the radeonhd driver becomes stable, as the stretched display I currently get is completely unreadable. :()

Oh, and I forgot to respond to you....

Thanks... I peeked at BSD a good while ago, but that was it. Since you mentioned it, I've been back sniffing around their site... try to learn more...

---

