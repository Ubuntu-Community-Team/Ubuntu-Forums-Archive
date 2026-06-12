---
title: "Does Ubuntu / Linux need periodic reinstallation like Windows?"
date: 2014-10-28
forum: Ubuntu, Linux and OS Chat
---

### Post by andrew145 on 2014-10-28
Hi! I've been using ubuntu for the last year after I was introduced via raspberry pi and having got fed up of windows. Needles to say but it's excellent! However, one thing has been bugging me. I know a windows PC needs the os to be reinstalled periodically to rid it of all the crap which accumulates from bad applications and drivers over time. This is mostly due to the unrestricted access we have to install absolutely anything from the internet onto it. 

However, with ubuntu, there's an official repository and it seems like a generally lower maintenance os e.g. Doesn't normally require defragmenting, no registry to mess up. So does Ubuntu also need regular reinstallation assuming you use the official repos and don't do anything stupid like removing stock apps and services or playing with loads of desktop environments? Thanks!

---

### Post by QIII on 2014-10-28
Assuming you do not make a mess (which can happen with any OS - and some of us do it on purpose to see what happens) an LTS version can go for 5 years (less in the case of some flavors like Lubuntu) without fail.

LTS versions go out of support after that time.

You can do an in-place upgrade of any release to the next indefinitely, but that often causes problems.  In my experience, fresh installations have always served me better.

Honestly, Windows can be just as stable long term.  I have only had to reinstall Win 7 once, and that was due to operator error.

---

### Post by cariboo on 2014-10-28
On my server, I upgraded from 12.04 to 14.04 recently, and even after running for almost 2 years, and adding quite a few things I don't really need, it still runs the way it did when I first installed it.

---

### Post by ian-weisser on 2014-10-28
> **andrew145 said:**
> So does Ubuntu also need regular reinstallation assuming you use the official repos and don't do anything stupid like removing stock apps and services or playing with loads of desktop environments?

No reinstall should be needed.
Ubuntu, and the other Linux distros I have tried, is quite good about keeping it's room clean.

---

### Post by mastablasta on 2014-10-29
> **andrew145 said:**
> 
However, with ubuntu, there's an official repository and it seems like a generally lower maintenance os e.g. Doesn't normally require defragmenting, no registry to mess up. So does Ubuntu also need regular reinstallation assuming you use the official repos and don't do anything stupid like removing stock apps and services or playing with loads of desktop environments? Thanks!

imagine google doing periodic reinstall of their servers :)

anyway even windows doesn't actually need that. depends how you maintain it. my winxp is running now for 9 years. it was reinstalled once 9 years ago due to disk error. so far so good.

---

### Post by bro2 on 2014-10-29
> **QIII said:**
> Assuming you do not make a mess (which can happen with any OS - and some of us do it on purpose to see what happens) an LTS version can go for 5 years (less in the case of some flavors like Lubuntu) without fail.

LTS versions go out of support after that time.

You can do an in-place upgrade of any release to the next indefinitely, but that often causes problems.  In my experience, fresh installations have always served me better.

**Honestly, Windows can be just as stable long term.  I have only had to reinstall Win 7 once, and that was due to operator error.**

This. Though Windows is a bit more prone to long term slowdown if you install a bunch of stuff that runs at startup/uninstall/install stuff all the time. Any OS would eventually slow down under that pressure (yes, if you don't clean the contents of deleted repositories those can accumulate just like leftover registry entries in Windows). If you want a stable OS, no matter what it is, don't impulsively install stuff all the time. The key to long-term stability is watching what you put on your system. 


Though really, as a reletivily new Linux user, I've managed to completely break it several times already, forcing a reformat. With OpenSUSE, if I uninstall the AMD proprietary drivers without doing a bunch of Terminal commands to reinstate the Xorg drivers before rebooting, OpenSUSE refuses to boot (it shuts down when it starts loading). Pretty damn annoying considering that Windows does not let broken/lack of GPU drivers cause a system failure.

ps: Yes, Ubuntu/Mint have a "drivers" option that automates the process (thank god) but I've still run into issues when updating Mesa from non official repositories and whatnot.

---

