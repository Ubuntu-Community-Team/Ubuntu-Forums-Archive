---
title: "[SOLVED] Suggestion / Question; Virtualizing Windows"
date: 2008-12-27
forum: Virtualisation
---

### Post by mtreece on 2008-12-27
To the open-source community,

I have recently found an idea that don't think has been resolved yet:

Many of us Linux-users have a dual-boot configuration with our "favorite" (whatever that might suggest) version of Windows, and must often times reboot into Windows each time to make use of any of its features.

I understand there are ways to install Windows inside of Linux, but what if either 1) a user doesn't have the spare HD-capacity or 2) just doesn't want to re-install another copy of Windows?

My idea / suggestion / question is this: is it possible to run a virtual session of another OS (such as Windows) from an existing partition on the hard drive?

Personally, I don't have much HD-capacity left to install another copy of Windows (such as [this article]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux") mentions), but even if I did, anything I would want to access inside of my Windows-OS is already there, and thus re-installing another copy of Windows inside of Linux would be a tedious operation.

I've tried searching around on Google for similar ideas to what I have suggested, but alas, I cannot find anything similar.  Thinking about the topic, I don't see why it *couldn't* be done, so why hasn't it been done in the past?

Does anyone have any ideas or suggestions about how to do this?
I'd like to try and stick to Open-Source ideas (and thus avoid additional costs) if at all possible.

Thank you in advance! :)

---

### Post by bodhi.zazen on 2008-12-27
Yes this is possible, and I do it all the time with KVM.

There are how-to's referenced in the virtualization mega thread (there is a reason it is a sticky).

The "problem" with windows is the liscense is issued to a specific hard ware configuration, so when you boot it with KVM/VBox/VMWare it complains about lisensure ...

Again there are two how-to's linked in the virtualization mega thread.

If you still have questions on how to do this , I suggest you post in the thread in question.

---

### Post by mtreece on 2008-12-27
> **bodhi.zazen said:**
> There are how-to's referenced in the virtualization mega thread (there is a reason it is a sticky).

Aha, thank you!  Sorry for the blond-moment; I'm rather new to Ubuntu Forums, so I haven't mastered all of the common-sense stuff.

I have tried installing and setting up VirtualBox, but I received a few errors in doing so (something about the correct module for my kernel hasn't been loaded), but this was earlier today before reading anything you've pointed me to.

I'll give the sticky-thread a try!

Thank you again!

---

### Post by bodhi.zazen on 2008-12-28
:lolflag:

If you are having problems feel free to ask and we will do our best.

What version of VirtualBox are you using ? From your description I am guessing the OSE (from the Ubuntu repositories). In that case consider using the PUEL edition downloaded from the VirtualBox site, it tesnd to be more up to date (which can be good or bad), has a few additional feattures, and run (IMO) with fewer glitches.

---

### Post by Dedoimedo on 2008-12-28
If you don't have free space on your internal hard disk, you can place virtual machines on external devices, even network devices.

As to the installation itself, there are tools that can convert physical installations to virtual machines, but this may not always work.

Furthermore, it is possible to use physical partitions, but this can be risky and can result in serious data corruption if improperly used, therefore I very much advise against it.

Your best bet would be: an external device for vm storage, this gives you flexibility and scalability, and 1-hour bother of reinstalling windows...

Dedoimedo

---

### Post by mtreece on 2008-12-30
Everyone, thank you for the advice.

I think I might need a little bit of that help everyone it talking about though :-D.

I've managed to get everything set up to at-least a satisfactory status of operation, in that I have Ubuntu running and now, VirtualBox PUEL (per suggestion), and Vista (from  my other partition) running inside the VM.

The problem now is that when I try to load Vista "normally", aka minus the VM, I can see the Vista loading screen, and then when it's supposed to show the round Windows-logo & then the welcome-screen, it will now instead show a black screen with my mouse in the center of it - unable to move.  And at this point, the computer is in a frozen state.

The odd thing is that I can still run Windows Vista just fine from my VM - just not when I try to run it normally.

I have an Alienware system, and being the rarity it is, I might have some sort of hardware-software-compatibility-catastrophe.  I contacted Tech Support earlier today (yea I know - I was pretty desperate), and the guy wasn't much help.  I suggested him sending me some sort of copy of WinVista and then I could do a repair-install to see if that would help any.  Soooo... I should have a CD coming in the mail soon of a "Recovery" something or another.  I already have one, supposedly, but it is "misplaced" :).

Being an IT support person myself, I would think this to be perhaps a driver-issue, _but_ I have the same problem out of Vista even when I boot into Safe-mode (and Safe-mode with networking + safe-mode with command prompt + "Last known good configuration"), so that tells me that whatever the problem is, I cannot fix it via Vista alone.

Has anyone else experienced anything like this and/or has any suggestions to help?

Thank you again in advance! :)

---

### Post by mtreece on 2008-12-31
**Update**
I fixed the problem:

1) I booted into Vista using my Virtual-Machine, did a System-Restore back to the beginning of the month

At this point, I could then boot into Vista, but shortly after logging in, I would get the BSOD for some unknown reason.

2) I then booted Vista in Safe-Mode, launched MSCONFIG, and started randomly disabling unneeded startup items (as well as services).

And then this solution seemed to work.

It turns out my Semantic Endpoint Protection (that I use per suggestion at my University) was the cause of the BSOD.  I'm about to try and re-install it to see if that fixes the problem.

Thanks everyone for your help!

And I hope this helps someone in the future if they receive a similar error.

---

