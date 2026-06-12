---
title: "I'm missing 14.04 a bit"
date: 2016-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by pi.no on 2016-09-12
Hi.

What is your general feeling about the latest Ubuntu 16.04? I installed it when it came out. Afterwards, I was disappointed and hoped for some early bugfix updates, which never came :-/ Although I will stick to it because of all the new software versions, the 14.04 LTS made very much a better job here.

To be precise, I'm not using Ubuntu at all, but the Xubuntu variant. Not impossible that Ubuntu makes it better; but I wouldn't assume that...

It starts with small things. After booting, when the login screen appears, I can start entering my password and in the meantime, it always has one short outage. The screen flickers shortly and drops the character I typed in that moment. Never happened on 14.04. Maybe a systemd artifact?! GPU driver issue? No, I have that on three completely different machines, all with different GPUs from different vendors. Shutdown is more broken. Sometimes it works as it should, sometimes I have to trigger it two or three times until it actually does anything. I tried waiting for many minutes. Just triggering it again helps. Sometimes it breaks entirely, not shutting down, but telling me it would, when I try it again. The 'shutdown' command on terminal works fine in all situations. To make power management complete: Suspend to RAM has severe issues as well (worked really great 14.04, for 2 years with 0 problems; but this feature is sth I just use on one machine): Whenever I resume, the mouse pointer is gone. Not in the screen locker, but afterwards. Just temporarily jumping into a text vt helps. In some cases, the font rendering is entirely broken afterwards and only a reboot helps.

Software installation (another battlefield for 16.04, isn't it?) has it's regressions. Why is it not possible to simply install .deb files anymore? The GUI just makes erratic crap and ignores me afterwards. It works fine without that GUI, e.g. on terminal via 'dpkg'.

From time to time, after login, it tells me about software crashes. 14.04 did that as well from time to time. And this is one place where I had hope for improvement in 16.04. I don't think it should regularly happen with a mature OS that (even unimportant and even when respawning) tools crash after login or during shutdown (and, even if this is really designed this way, it should bother the user with it). In 16.04 on my machines, it happens more often.

All the other smaller glitches I've seen in 14.04, or in the older Xfce version, bugs in integration of the desktop environment, performance, hopes for some visible steps towards touch (or even multitouch) aware interfaces, some more convergence between Qt4,Qt5,Gtk2,Gtk3 (rlly, its lousy how that looks so far!); everything I took a look at was in 16.04 as it was in 14.04, or worse. They even managed to make it a big deal to configure my touchpad to have a usable configuration; including click-on-tap with three-button support.

Admittedly, some of the last points are not Ubuntu things, but also about desktop environments and the user tools as well. But I would be interested in reading about your feelings about it after some months. Is it as great as 14.04 was? Even better? Or do you also see degradations in some must-work features?

---

### Post by buzzingrobot on 2016-09-12
16.04  Unity here has been good.  

I've seen that flicker and dropped character problem on several Ubuntu-based and non-Ubuntu-based distros.  What they had in common was lightdm as the display manager.

I've used all sorts of Linux flavors for years and almost everyone has exhibited changed suspend behavior, sooner or later, after a kernel upgrade. If it was working, it would break.  Or vice versa.

Desktop integration is an issue for XFCE because it remains GTK2-based (and GTK2 is essentially dead), while users typically want to use GTK3 apps, which are invariably theme-able with only one specific version of GTK3 (assuming someone has created/upgraded the theme they want to use to work with the version of GTK3 used in the distro they're running).

Since you're using Xubuntu and have some serious problems, probably best to open individual threads about each. If you've added non-default pacakges (like QT-based) mention that, too.


Don't recall what GUI software manager Xubuntu ships with at the moment?  Synaptic?  In any case, ability to install .deb files has not been removed.

---

### Post by RichardET on 2016-09-13
"Sometimes it breaks entirely, not shutting down, but telling me it  would, when I try it again. The 'shutdown' command on terminal works  fine in all situations. To make power management complete: Suspend to  RAM has severe issues as well (worked really great 14.04, for 2 years  with 0 problems; but this feature is sth I just use on one machine):  Whenever I resume, the mouse pointer is gone. Not in the screen locker,  but afterwards. Just temporarily jumping into a text vt helps. In some  cases, the font rendering is entirely broken afterwards and only a  reboot helps."

I have seen similar issues with Xubuntu, and now I use Mate, which seems better.

---

### Post by pi.no on 2016-09-13
> **buzzingrobot said:**
> 
I've seen that flicker and dropped character problem on several Ubuntu-based and non-Ubuntu-based distros. What they had in common was lightdm as the display manager.


Okay, this is interesting indeed. I haven't seen this in 14.04, and now in 16.04 its on all my machines. But of course it could be that the lightdm guys introduced the bug. It's a mess nevertheless - how can you release a display manager this way? - but then I have to blame others in the first place :)

> **buzzingrobot said:**
> 
I've used all sorts of Linux flavors for years and almost everyone has exhibited changed suspend behavior, sooner or later, after a kernel upgrade. If it was working, it would break. Or vice versa.


Really? I typically saw that just in one way before. I agree that suspend generally seems to be a hard thing. Don't know why. Some people tell wild theories about microsoft intentionally broke the specs. Maybe yes. Maybe the hardware implementations are broken for other reasons. Or maybe the OS. What I know is that you really can be glad if it works, and that it often does not (i.e. on many machines). My desktop machine fails and falls in some weird 'I let my standby light blink but dont react on your actions anymore' mode. Okay. But in 14.04 I've seen a working implementation (on my notebook where I actually use suspend). It failed never in any regard in all the time. And now, when I resume the machine, the mouse cursor comes back, but disappears later on when I entered the password. This doesn't really seem like a 'ohh the acpi tables are broken' issue, but much more like a 'hey, look, I patched this new $INSERT_RANDOM_USELESS_CRAP feature into the infrastructure last night and it still compiles!!' one. But, yes, might be a lightdm issue as well. I will test it with kdm later.

> **buzzingrobot said:**
> 
Desktop integration is an issue for XFCE because it remains GTK2-based (and GTK2 is essentially dead), while users typically want to use GTK3 apps, which are invariably theme-able with only one specific version of GTK3 (assuming someone has created/upgraded the theme they want to use to work with the version of GTK3 used in the distro they're running).


I don't use Xfce because of weak hardware or so. I use it because I don't like that Gnome3/Gtk3 world (and KDE is as mature as an egg makes a good brick). This is a different discussion admittedly, but Gnome3 is like Microsoft in a way I can't love: They try to raise share or relevance by segregation. They try to build an isolated ecosystem, which tries hard to give foreign applications an alien look&feel and which tries to let parts of it look&feel alien in foreign desktop environments. But what I expect from a Linux distribution is a common style amongst those toolkits. At least to a large degree. But here not even the background colors of windows match! How can you make it worse?

> **buzzingrobot said:**
> 
Since you're using Xubuntu and have some serious problems, probably best to open individual threads about each. If you've added non-default pacakges (like QT-based) mention that, too.


I'm not interested in help about the particular problems. I think, I can solve on my own what's solveable when I have some time, and many other things are maybe not fixable in a _feasible_ way, so I have to live with them as long as I use Xubuntu 16.04 (and maybe even in Ubuntu, or even in all Xfce environments). I'm just wondering if I am the only one, which would line up the release notes by just this annoyances, or if I just had bad luck somehow.

> **buzzingrobot said:**
> 
Don't recall what GUI software manager Xubuntu ships with at the moment? Synaptic? In any case, ability to install .deb files has not been removed.


Synaptic is great. Well, no... It was for my grandpa. I actually use it for package installation from the Ubuntu repositories, since it actually shows all the packages and provides all the basic operations. What I see here when I click on a .deb file is probably the same crap as the Ubuntu guys would see. At least it also uses the design-bug-technology what Gnome guys call Client Side Decorations. It has a title bar which isn't really a one, and the title is just "Software" (well, the taskbar title; the actual text in the window title shows something completely different of course).

---

