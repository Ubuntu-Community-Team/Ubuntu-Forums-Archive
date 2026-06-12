---
title: "Quality Assurance Team?"
date: 2007-03-01
forum: The Cafe
---

### Post by justin whitaker on 2007-03-01
Does Ubuntu actually have one?

This question comes out of my recent experience with my USB drives. I use my USB Traveldrive and my Maxtor USB HD for moving files between systems, archiving, etc. And 90% of the time, I can't use them unless I reboot my system. 

I have done all of the things that people in the forum have recommended, so I'm not looking for help: it's clear that until the Dev team does something new to the kernel, or I break down and compile it myself, USB is broken. 

Now, I have a workaround: take the system down, reboot, and there they are. That is as annoying as anything, because I thought that we passed that sort of crap with Windows 95. 

What it seems like, from this users perspective, is that the Devs find a bug fix, or change their security approach, or want to make things easier for themselves for the next upgrade, so they commit a patch, and if no bugs are reported, it gets pushed. 

A better way to handle that is, prior to release or patching, certain things should be checked off:

Does X work on a variety of cards and systems?
Do USB peripherals work as they should? 
Does sound work properly on a variety of systems?
Does the patch break any commonly installed applications?

I'm sure that the list could be extended quite easily. The point is, each patch or update seems to bring the same problems to the community, and yet, the process keeps repeating itself. 

A little quality control would go a long way.

---

### Post by frodon on 2007-03-01
Simple question, did you filled a bug report ?

Details here :
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

The only way to get a bug fixed is to fill a bug report.

---

### Post by justin whitaker on 2007-03-01
> **frodon said:**
> Simple question, did you filled a bug report ?

Details here :
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

The only way to get a bug fixed is to fill a bug report.

My problem is already reported in all of the following unresolved bugs:

21449, 54419, 34316, 40561

How does bug reporting help with the quality of user experience?

---

### Post by frodon on 2007-03-01
> **justin whitaker said:**
> How does bug reporting help with the quality of user experience?:confused: , it informs devs of the bugs so they can fix them.

Maybe it's not as fast as you expect but they fix the bugs, obviously they fix major bugs first.

BTW, the bug report you gave tells that it got fixed in latest kernel versions.

---

### Post by Tomosaur on 2007-03-01
As I'm sure you're aware - the sheer number of possible combinations of hardware and software mean that bugs which are consistent on your machine may well be completely non-existent on others. This makes it very difficult for developers to fix rare bugs - particularly when the bug reports are not verbose (ie - you need to list ALL of the hardware you have connected to your machine, any modifications you have made to your version of Ubuntu, etc etc). In most cases (mine included), all of my USB stuff works perfectly well. I can understand your frustration - but these things happen. There's not much else you can do but to file a bug report and hope it's fixed next release.

Just a question - do the devices actually get mounted once you plug them in, or do they just sit there? If the devices are mounted by aren't usable, then this certainly sounds like a bug. If, however, they're just not being mounted, then you could try mounting them manually. I haven't seen your other threads so I don't know what you've tried, sorry.

---

### Post by DoctorMO on 2007-03-01
> Does Ubuntu actually have one?

Yes: justin whitaker is a member of the QA team and a long standing helper with usb problems.

---

### Post by 23meg on 2007-04-02
[QUOTE=justin whitaker]Does Ubuntu actually have one?[/QUOTE]

Two, actually:

[https://launchpad.net/~ubuntu-qa](https://launchpad.net/~ubuntu-qa)
[https://launchpad.net/~bugsquad](https://launchpad.net/~bugsquad)

---

