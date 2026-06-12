---
title: "Should I install Ubuntu 14.04 Now?"
date: 2014-03-04
forum: Ubuntu Development Version
---

### Post by DaLazySapien on 2014-03-04
Hello all and thanks in advance for the answer to my question. I've been using Linux off and on for about a year now and have finally made the 100% switch over to the OS. I'm currently running Linux Mint 16 (Cinnamon) and want to move over to Ubuntu. I know that Ubuntu 14.04 LTS will be officially releasing next month but would like to switch over as soon as possible.

Would it be relatively "safe" to just install the Beta of 14.04 now as my daily driver or should I install 13.10 for a month? I don't mind dealing with the occasional bug and see it as a learning experience but I don't want to use something that is going to fight me every step of the way because its not ready for heavy use :-).

If it helps bring clarity to my question, here are a few things that I use on a daily basis and need to work well in 14.04.

Nvidia Drivers
Steam
Vmware
Chrome
Libre Office
Wine (PlayOnLinux as well)
VLC
I also connect to a networked external drive thats connected to my router so I'd need that to work as well.

Thanks again for your insight and no matter what the answer I'll be making the switch to Ubuntu 14.04 at some point :guitar:

---

### Post by david98 on 2014-03-04
I would recommend installing 13.10 and then upgrading in due course. This is partly because as you well know 14.04 is still in development and there will be bugs which could leave your system useless and you might have to do a fresh install. If you don't mind the possibility of having problems which could render your system useless go ahead. If like me you are curious and want to have a play about may I also  recommend having a duel boot system with 13.10 and 14.04 until the final release is available this will give you the option to have a play about with the latest development release and always have a working system you can use until the final lts is released then do a fresh install this therefore gives you the best of both worlds Hope you have fun :guitar:

---

### Post by grahammechanical on 2014-03-04
It is your decision. You take responsibility. I would not advise anyone who posts into the Absolute Beginners section of this forum to install a development version of Ubuntu. And I have been using Trusty Tahr (Ubuntu 14.04 under development) daily since the first week of its development cycle. And I trust Trusty but I expect it to break and I have taken precautions.

We have a section of this forum dedicated to discussing the Ubuntu development branch. It is called Ubuntu+1.

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

Browse through the posts. See, what others have noticed in their testing of Trusty Tahr. Make your choice.

Regards.

---

### Post by endlessinstant on 2014-03-04
I definitely wouldn't recommend going to a beta/testing platform as your only/primary environment.   Linux has lots of good ways to do dual boots so if you want to muck around with new features, that's probably the way to go.   It's never fun when you need your computer for something but realize it's broken by a buggy OS and  you've got to spend half the day installing something else.

---

### Post by David D. on 2014-03-04
+1 for waiting until next month.  Dual boot is you want to try it until then, having to fix things is often a good learning experience.

---

### Post by 3rdalbum on 2014-03-04
You can install 14.04 now. By the time an Ubuntu release gets to beta it is pretty well tested and fairly stable. When the final release comes out it will be a normal update for you (no reinstallation necessary).

---

### Post by monkeybrain20122 on 2014-03-04
> **3rdalbum said:**
> You can install 14.04 now. By the time an Ubuntu release gets to beta it is pretty well tested and fairly stable. When the final release comes out it will be a normal update for you (no reinstallation necessary).

Well I disagree. Based on past experience new releases are always kind of buggy and I would not even install a new release right after it comes out especially if you use proprietary drivers. I would wait **at least** for a month for the post installation bug fixes and third party repositories to be properly set up (if you use those, like steam) So my timetime for OP is not even April, but maybe May or June.

---

### Post by monkeybrain20122 on 2014-03-04
I would recommend installing 13.10 with a separate /home partition. When it is time for installing 14.04 (optimistically sometimes in May or more realistically probably mid -late June), do a clean install of 14.04 and do not format /home. That way you won't lose your data and settings.

I would emphasize that you should avoid "upgrading" with the update manager becayse it will prompt you for upgrade the day 14.04 is released and 'upgrading' takes hours and likely to break if you have Nvidia driver and third party repos such as steam (the system has to be restored to a 'clean' state for 'upgrade' to work and the restoration itself is more work than doing a 20 minute clean install) 

So to avoid upgrading by accident (and breaking the system consequently) I would just disable the prompt for upgrade in the update-manager. Go to update-manager's settings to set "Notify me when a new Ubuntu is released" (something like that) to "never".

---

### Post by 3rdalbum on 2014-03-05
Even with /home on the same partition, you can do a clean install without losing your /home.

---

### Post by DaLazySapien on 2014-03-05
Thanks to all for the replies. I've gone ahead and installed Ubuntu 13.10 earlier today and its running great. I was impatient about the new release but that kind of behavior can get you into more trouble than its worth ;)

---

### Post by buzzingrobot on 2014-03-05
> **monkeybrain20122 said:**
> Well I disagree. Based on past experience new releases are always kind of buggy and I would not even install a new release right after it comes out especially if you use proprietary drivers. I would wait **at least** for a month for the post installation bug fixes and third party repositories to be properly set up (if you use those, like steam) So my timetime for OP is not even April, but maybe May or June.

I agree with this disagree.:)  The essence of releases in development is that things change.  Sometimes those changes cause problems.  Might be a minor bug.  Might be you can't boot.  Might work today.  Might not work tomorrow. 

It's impossible to test everything on every possible hardware setup, so new bugs are often uncovered by users as soon as a new release hits. You can get a decent feel for how things are going by hanging around this place. 

(Descriptions of the new bits in 14.04 are widely available. It's your call on whether or not they are so enticing that jumping in pre-release is worth the risk.)

---

### Post by howefield on 2014-03-05
Thread moved to Ubuntu+1.

> **DaLazySapien said:**
> Would it be relatively "safe" to just install the Beta of 14.04 now as my daily driver or should I install 13.10 for a month? I don't mind dealing with the occasional bug and see it as a learning experience but I don't want to use something that is going to fight me every step of the way because its not ready for heavy use :-).

I've been using the development release as a "daily driver"since 13.04 but not without the safety of 12.04 on a second disk and symlinked /home folders on a third. :)

> Nvidia Drivers
Steam
Vmware
Chrome
Libre Office
Wine (PlayOnLinux as well)
VLC
I also connect to a networked external drive thats connected to my router so I'd need that to work as well.

Of your list, I have no issues with any of it, but don't use Steam and Virtualbox not Vmware. 

None of this matters anyway, good luck with 13.10 and hope you get to 14.04 when released.

---

### Post by artie3 on 2014-03-05
I tried 13.10 briefly, and found it to be horribly unstable. I finally gave up and installed 14.04. I've been using it as my primary system in my laptop and in my desktop.

I don't use it for some of the applications you run, but everything I use it for runs and runs....I have 1 install on my desktop and one on my Dell laptop, the Dell laptop install runs from a usb flash drive and it runs well after doing some enhancements (move /tmp and logs to ram, change to ext 4 format with journaling turned off, install preload).

14.04 fixes my video by installing the mesa video drivers by default, and the wireless now works-previously I had to run a usb wireless plug in unit.

I'm thrilled with 14.04-and look forward to the official release in April.

Artie

---

### Post by andrew.46 on 2014-03-05
> **DaLazySapien said:**
> Would it be relatively "safe" to just install the Beta of 14.04 now as my daily driver or should I install 13.10 for a month? I don't mind dealing with the occasional bug and see it as a learning experience but I don't want to use something that is going to fight me every step of the way because its not ready for heavy use :-)

I would suggest that you not only wait for the actual release but wait for another month after this. By then the dust will have well and truly settled...

---

### Post by craig10x on 2014-03-05
I've been running 14.04 as my main (and only) system for 2 months now and aside from a few minor bugs, it's been rock solid...i don't think he would need to wait a month after release to install...
I'd say most of the "dust" has already settled :D

---

### Post by OGpmpdog on 2014-03-06
> **craig10x said:**
> I've been running 14.04 as my main (and only) system for 2 months now and aside from a few minor bugs, it's been rock solid...i don't think he would need to wait a month after release to install...
I'd say most of the "dust" has already settled :D

+1, but I will also echo the other dudes in expecting the unexpected with development software.

I've been using TT (UG versoin) since last year, and it's been fairly stable.  The most recent updates were quite hairy; before that, I borked a few installs during the Gnome 3.8-3.10 transition, and Nvidia-331 jusssst became my friend.

Today, my systems (Ivy Bridge, MSI Mobo, Nvidia 210 +T61 (Nvidia laptop) are stable as we near feature freeze.

---

### Post by u2nTu on 2014-03-06
Good points here, but first I would ask you to assess how picky you are. That is, **how much do you customize?**

If not much (as it seems), then only a small investment of time has been made in configuration. If things break, you only need to preserve any data files because *whichever* system can be easily reinstalled.

But if a substantial amount of your time has been spent in tweaks and setups, then you'd want to be sure to have updated backups of ~/ and any new or edited system-side files.

In either case or in-between, it comes down to saving all your work.  Then the version won't much matter: You're free to play.

(Tip: Create a reinstall.txt file and keep commands used in system setup, along with any notes, in there.)

---

### Post by TeamRocket1233c on 2014-03-06
Since it's only a few weeks until 14.04 LTS comes out, I recommend just waiting until it's officially released, as you wouldn't have any stability concerns then unless you break it yourself somehow.

---

### Post by monkeybrain20122 on 2014-03-06
> **TeamRocket1233c said:**
> Since it's only a few weeks until 14.04 LTS comes out, I recommend just waiting until it's officially released, as you wouldn't have any stability concerns then unless you break it yourself somehow.

You are very optimistic. I would wait a month or two for post release bug fixes before I use 14.04 as my "real" system. IMO It is highly irresponsible to tell not very experienced users to trade in their working system for a new release at the first opportunity (that's why the notification for new release should be disabled in update-manager)

---

### Post by andrew.46 on 2014-03-06
> **monkeybrain20122 said:**
> You are very optimistic. I would wait a month or two for post release bug fixes before I use 14.04 as my "real" system. 

Exactly. It is one thing for a* relatively* small number of alpha and beta testers to look at a growing release, it is a quite another thing for many, many thousands of installers with a myriad of different hardware configuration and software needs (and widely varying Linux skills)  install a new release version. This is where many problems become apparent.

---

### Post by Ultra Cronic on 2014-04-19
:-({|=Ubuntu 14.04 was thee most combative linux os yet, can not run shell scripts from the desktop, krusader suffered locked config files and no cure in site from the developer.
have to run as root :-( ;  plagued with security stepping on users feet all the time with add-on software. I am now trying the latest Mint 64 bit and so far so good, to early to say 5 stars but it's doing well so far. Try and add a launcher or widget in the 14.04 task or launch bar ? HA!! What a joke the right mouse button menu options are stripped bare. Terrible loss of user control. Tried different desktops no luck, made things worse. 

Ubuntu 12.04 LTS blows away the 14.04 in my opinion.

---

