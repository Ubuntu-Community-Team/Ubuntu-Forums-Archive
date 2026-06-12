---
title: "Monitor Specification Tool for noobs"
date: 2007-01-30
forum: The Cafe
---

### Post by Yfrwlf on 2007-01-30
While there is a utility to configure your monitor, new users have to search forums to find out about it.  Wouldn't it be cool if Ubuntu, if it detected a generic monitor or the details of the monitor didn't exist, would ask you if your resolution/screen settings were OK and also contained the program in the menu as well, and if a "no" was given launched some sort of user friendly screen where you could put in your monitor's refresh rate and/or resolutions that the user knew their monitor was capable of, and it'd edit those simple things in xorg.conf?  I think adding such a simple program and system check into Ubuntu would cure the headaches of many noobs, especially many laptop users it seems.

Perhaps you could go further and have it send back that information to a central database to help widen Linux's supported monitors?

Does such a thing already exist, how could this be made possible, just, what do you all think about such a thing?  So far I've had three friends of mine run into this issue, and I have to explain to them how to edit xorg.conf.  Sometimes that doesn't help, but many times just giving those added specifications solves the problem.  I think ensuring that new users have as smooth a ride as possible is a good thing.

I know I'm touching on the problem of hardware vendors not providing details issue probably but if most solutions involve specifying refresh rates or resolutions then it seems like something that wouldn't be that hard to overcome, and if you can utilize the community by gathering that information from new users, that will help speed things up.

---

### Post by happy-and-lost on 2007-01-30
I feel your pain.

Ubuntu needs something like SUSE's SaX. That rocks.

---

### Post by Yfrwlf on 2007-01-31
> **happy-and-lost said:**
> I feel your pain.

Ubuntu needs something like SUSE's SaX. That rocks.

Fully agreed, in fact shouldn't it be mostly no problem to use SaX on Ubuntu since both conform to LSB specifications?  Maybe SaX itself uses a different system though, but that would be cool tho.  Running that if the user had problems with their screen would be a fairly good solution.  Maybe you wouldn't need something so complex as SaX though, but SaX could be a good backup monitor detection tool?  Until Linux gains better hardware support from the vendors, it might be a good solution for now. ^^

---

### Post by Yfrwlf on 2007-02-20
The ```
dpkg-reconfigure xserver-xorg
``` is another good tool btw.  It's annoying that a tool like SaX or this one is better at monitor detection than the default "normal" detection mechanisms.  I had another friend this last week install Ubuntu and he couldn't see his screen because his monitor flickered really badly in X.  He could have had access to the command line via alt-ctrl-f1 and such, but since he was a noob I remoted in and ran the configuration program for him which fixed his problem.  At the very least, putting in that recommendation to run the xserver monitor configuration program if, say, the user were to boot into safe mode perhaps (?) might be a super good idea until Linux gains more traction with hardware support. :)

---

