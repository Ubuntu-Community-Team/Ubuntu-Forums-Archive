---
title: "bit worried about the longevity of hardware support , in the  linux kernel"
date: 2007-11-20
forum: The Cafe
---

### Post by loell on 2007-11-20
there are many loadable module drivers for linux  and surely it gets piled up more and more at a faster rate than any OS, and because of these, its actually hard to maintain them all.


**there are signs, have a look around, that a hardware is working in previous ubuntu version and has not work in newer ones**


heh ;), don't tell those users to just stay at that specific working kernel version and not upgrade on the newer ones.


now, perhaps its time to look at microkernels? :)

what's your take on this?

---

### Post by wolfger on 2007-11-20
> **loell said:**
> what's your take on this?
My name is Bill Gates, and I think you should just upgrade your hardware. :lolflag:
Seriously... I've never experienced this problem. Can you be specific, or point to examples?

---

### Post by Nebby on 2007-11-20
[http://en.wikipedia.org/wiki/Tanenbaum-Torvalds_debate#.E2.80.9CLinux_is_obsolete.E2.80.9D](http://en.wikipedia.org/wiki/Tanenbaum-Torvalds_debate#.E2.80.9CLinux_is_obsolete.E2.80.9D)

Mono/Micro discussions have been around a long time, and, as ever, Linux is monolithic, so if you want a microkernel system, you're gonna have to go elsewhere.

---

### Post by igknighted on 2007-11-20
The problem is not with the kernel itself, but with distributions compiling it without support for certain devices.  In order to compile in support for various devices that are extremely rare (often old devices), it would come at the expense of slowing down the kernel for everyone.  So the distributions need to decide what they need and what they do not.  Sometimes you can get them as modules, so perhaps the module for the device in question is in the repos.  Otherwise, I would try recompiling the kernel from vanilla sources, making sure you compile support for the device you need when you run menuconfig.  I do not think the support is being dropped from the mainline kernel, but rather it gets dropped by a distro or perhaps it is just a bug.

What devices are you having trouble with?  Perhaps we could point you to the specific reason that it is not working.

Also, what's wrong with telling users to use an older kernel?  90% of the kernel is device drivers, and if they are running an older system with older devices, chances are the new kernel wont do anything for them that the older one cannot.

---

### Post by DoctorMO on 2007-11-20
This is the interesting thing, if a device no longer works in the newest kernel it's because it's been abandoned; pay the developer some money and he will happily maintain your driver for you.

What is this with people thinking that linux is free as in beer? development is _NOT_ free!

---

### Post by Erik Trybom on 2007-11-20
The problem is that most users just happily upgrade everything the update-notifyer tells them to, and that often include new kerne versions.

I suddenly lost my cpu-stepping due to such an upgrade (or perhaps it was during a dist-upgrade, can't remember). That module was in the repos though so I could fix it in the end, but it required some messing around in the terminal.

It would be cool with an automatic compability test telling the user "you're using hardware that's not supported by this new kernel. This is how to proceed..."

---

### Post by wolfger on 2007-11-20
> **Erik Trybom said:**
> It would be cool with an automatic compatability test telling the user "you're using hardware that's not supported by this new kernel. This is how to proceed..."
That would be awesome, but I think it would be very difficult (if not impossible) to implement. "Please plug in all peripherals for this test" is just the start of the headaches there...

---

### Post by Whiffle on 2007-11-20
I'd like to see some specific examples.  After digging through the kernel source and the options listed there, I find it very hard to believe that modules are disappearing.  There is still support for some of the most outdated hardware in there, like those old compaq quasi-ide cdrom drives and stuff.  If you're really worried about support disappearing, roll your own kernel!  its not as hard as it sounds.

As far as ubuntu not supporting older versions of hardware, maybe, although I doubt it is a kernel  issue and more of a "oops, we fixed one thing and something else broke" issue.   The ubuntu kernel config has just about everything compiled as modules and included.

---

### Post by juxtaposed on 2007-11-20
> 
This is the interesting thing, if a device no longer works in the newest kernel it's because it's been abandoned; pay the developer some money and he will happily maintain your driver for you.

What is this with people thinking that linux is free as in beer? development is _NOT_ free!

Just because it isn't free doesn't mean it isn't an issue.

---

### Post by loell on 2007-11-20
> **wolfger said:**
> My name is Bill Gates, and I think you should just upgrade your hardware. :lolflag:
Seriously... I've never experienced this problem. Can you be specific, or point to examples?

you haven't seen this , as you are still a bit new to this, I presume? ;)   Hang on to the forum in two years and you'll see some.

---

### Post by loell on 2007-11-20
> **DoctorMO said:**
> This is the interesting thing, if a device no longer works in the newest kernel it's because it's been abandoned; pay the developer some money and he will happily maintain your driver for you.

What is this with people thinking that linux is free as in beer? development is _NOT_ free!

true, devices are being abandoned, but at what rate?
how can one be sure that a device is being obsoleted in many parts of the world?

---

### Post by koleoptero on 2007-11-20
I was always more confident that with older hardware you have better chances that linux will work properly, not the other way around.... At least as far as I am concerned that's the case.

If indeed they are dropping support of some devices I suspect that they indeed must be very old, so an upgrade shouldn't be that bad a choice :P

But anyway, as on every other topic I've read here the final conclusion must be that whatever the problems are with hardware is the hardware's own manufacturer's fault.

---

### Post by jerrylamos on 2007-11-20
> **Whiffle said:**
> I'd like to see some specific examples.  After digging through the kernel source and the options listed there, I find it very hard to believe that modules are disappearing.  There is still support for some of the most outdated hardware in there, like those old compaq quasi-ide cdrom drives and stuff.  If you're really worried about support disappearing, roll your own kernel!  its not as hard as it sounds.

As far as ubuntu not supporting older versions of hardware, maybe, although I doubt it is a kernel  issue and more of a "oops, we fixed one thing and something else broke" issue.   The ubuntu kernel config has just about everything compiled as modules and included.

1. Older hardware support: Well, any number of us are having trouble with "shutdown" which started failing with Feisty see my launchpad bug #119308.  Some of us have found ways to get it done.  We get no clue that Ubuntu development is interested in looking at it.  This is an older 1.2 gHz Celeron which runs Ubuntu fine otherwise.

2. Another is Network Manager insists on disabling my Realtek interface card, see Bug #82927.  I can get by this by clicking on the Network Mangler icon and clicking on wired network, every time I boot up.  This works for Gutsy Ubuntu and Xubuntu but not Kubuntu since Kubuntu's icon is so smart it doesn't give me the option,  The Ubuntu Book's suggestion to do sudo dhclient gets the interface running, however the Kubuntu Network Mangler refuses to acknowledge and Konqueror only pays attention to the Network Mangler, not to Administration, Network.  That bug has been around quite a while with no developer action I can tell.

Obviously, no way Vista is going to run on this hardware at all.
Jerry

---

### Post by wolfger on 2007-11-20
> **loell said:**
> Hang on to the forum in two years and you'll see some.
Right. I may be new to Ubuntu, but I'm not new to Linux, and I've never seen a new kernel not support a previously-supported piece of hardware.
I'm also not new to the internet, and there's a word for folks who make claims but fail to provide examples, even when specifically asked for them.

---

### Post by loell on 2007-11-20
> **igknighted said:**
> 

What devices are you having trouble with?  Perhaps we could point you to the specific reason that it is not working.

I don't have any  specific problem with my hardware at all. And if  I will be having one , I'm pretty confident  to go search and fix the problem with little clues on the way.


however, have you seen those threads, when a user have only installed a previous version of ubuntu and is over hyped and over happy on how his system work flawlessly? then suddenly burst into madness after upgrading or installed the newer version?

and then will ask, why is my hardware X not working? when in fact it was working back then? this maybe are only a small fraction of a very wide array hardware, but still its a bit worrisome.

---

### Post by loell on 2007-11-20
> **wolfger said:**
> Right. I may be new to Ubuntu, but I'm not new to Linux, and I've never seen a new kernel not support a previously-supported piece of hardware.
I'm also not new to the internet, and there's a word for folks who make claims but fail to provide examples, even when specifically asked for them.

hmm, strange, have you tried 2.4.x? and the migrate 2.6.x  I think you'll see some hardware support droping.

if your asking for specifics,  the previous post before this post had a sample.

---

### Post by loell on 2007-11-20
> **loell said:**
> , why is my hardware X not working? when in fact it was working back then? this maybe are only a small fraction of a very wide array hardware, but still its a bit worrisome.

sorry, let me rephrase  something , as this will reflect mostly , in what i've read in the forum overtime.

> **why is my hardware X not working properly, when in fact its working flawlessly in the previous version**

---

### Post by Daveski on 2007-11-20
> **loell said:**
> there are many loadable module drivers for linux  and surely it gets piled up more and more at a faster rate than any OS, and because of these, its actually hard to maintain them all.

Have you seen the list of 'old' hardware that has been dropped by Vista? Actually, Linux supports more hardware than ANY other OS (so I am lead to believe). I do have sympathy if the newer version of Ubuntu does not support some hardware that the previous version did, but then that is why we must file 'bug' reports if this happens.

---

### Post by loell on 2007-11-20
> **Daveski said:**
> Have you seen the list of 'old' hardware that has been dropped by Vista? Actually, Linux supports more hardware than ANY other OS (so I am lead to believe). I do have sympathy if the newer version of Ubuntu does not support some hardware that the previous version did, but then that is why we must file 'bug' reports if this happens.

vista hardware support is non debatable as we all know it sucks.

yeah sure we can file bug reports in launchpad or even go directly to the kernel mailing list, yet how many people will do that?  I bet only the generous few.


wouldn't it be nice if those modules will stand the test of time, and can easily be used in newer kernels without any issue?

---

### Post by saulgoode on 2007-11-20
> **loell said:**
> however, have you seen those threads, when a user have only installed a previous version of ubuntu and is over hyped and over happy on how his system work flawlessly? then suddenly burst into madness after upgrading or installed the newer version?

and then will ask, why is my hardware X not working? when in fact it was working back then? this maybe are only a small fraction of a very wide array hardware, but still its a bit worrisome.

These are most likely Ubuntu development issues. I cannot think of a single piece of hardware for which the kernel developers have dropped support.

---

