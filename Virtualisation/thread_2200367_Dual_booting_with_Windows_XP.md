---
title: "Dual booting with Windows XP"
date: 2014-01-18
forum: Virtualisation
---

### Post by ilikecolors on 2014-01-18
So im going to dual boot with Windows XP via virtualbox, but before I do, I have some questions.
1) How much RAM should I give it? Its a tight subject for me since my netbook only has 2 GB of RAM.
2) I want to bring some files that I have on Ubuntu to XP. That means I select to use the same hard drive, right?
3) Will doing this slow me down even if im only using Ubuntu?

---

### Post by deadflowr on 2014-01-18
2GB is a tight one.
Running a vm isn't as much a dual-boot, but more like two system running at once.
If you feel you have to run XP this way, then don't give it any more then half the available ram.
Probably 512MB of ram should be fine, hopefully.

Your other point on Sharing files
[here]("https://forums.virtualbox.org/viewtopic.php?t=15868") and [here]("https://help.ubuntu.com/community/VirtualBox/SharedFolders")

---

### Post by Bucky Ball on 2014-01-18
*Thread moved to **Virtualisation**.*

---

### Post by ilikecolors on 2014-01-19
So even when Im JUST using Ubuntu and not Windows XP, will my computer still be slower?

---

### Post by QIII on 2014-01-19
Hello!

If Ubuntu is the host and XP the guest, resources for XP will only be used when you have the guest running.

Whether or not that slows down your host will depend on whether the the combined resources used climb to near the limit of your physical resources.

If the guest is not running, there will, of course, be no problem.

Cheers!

---

### Post by deadflowr on 2014-01-22
> **ilikecolors said:**
> So even when Im JUST using Ubuntu and not Windows XP, will my computer still be slower?

No.
The Xp would be part of the virtualbox program.
If the virtualbox program isn't running then XP won't be either.

Like any other program.
I guess you COULD have it running in the background, but why?

---

### Post by sudodus on 2014-01-22
I was running VirtualBox with XP in Ubuntu 10.04 and later in Lubuntu 12.04 with 2 GB RAM, and used around half of the RAM for the virtual machine. It worked. But I would not do it in any current Ubuntu with Unity, because the desktop environment needs more RAM to run well.

Now I run VirtualBox with XP in Ubuntu 12.04 with xubuntu-desktop, that is 'almost' Xubuntu 12.04, in a machine with 4 GB.

---

### Post by mastablasta on 2014-01-23
install lighter desktop enviroment or windows manager. for example icewm, logout login under icewm (ugh will look like win95, but doesn't matter as you will have plenty of RAM left for virtual maschine), asing 1.3GB ram for winXP guest, give it 64MB for GPU and enjoy. i think windows needs at least 1 GB to run smooth.

another option (since you probably won't use antivirus etc.) you just use Ubuntu, give it about 800MB ram, asing 16 MB for GPU, and use classic view in windows xp to reduce ram/system usage further. you could also try to stop/not load services in windows you won't need. you should have about 300, 400 MB ram left in guest maschine (winXP). enoguh to run firefox or outlook etc. or soem programme that can do with that kind of RAM

---

### Post by TheFu on 2014-01-24
> **ilikecolors said:**
> So im going to dual boot with Windows XP via virtualbox, but before I do, I have some questions.
1) How much RAM should I give it? Its a tight subject for me since my netbook only has 2 GB of RAM.
2) I want to bring some files that I have on Ubuntu to XP. That means I select to use the same hard drive, right?
3) Will doing this slow me down even if im only using Ubuntu?

**Dual boot** generally means no virtualization is being used, so your terminology is a little off.  I'll assume you really mean that you intend to boot into WinXP - call that the "hostOS" - then run virtualbox to load Ubuntu inside a virtual machine environment - call that the "guestOS" or "VM".

So you have a few challenges.
* Netbook usually means a low end CPU.  Often an Atom, so CPU will always be slow. Heck, it is already slow without running a 2nd OS.
* 2G of RAM is a little tight, but as long as you don't give the Ubuntu VM more than 768MB and never run 2 VMs at the same time, that should be fine.  Don't forget that VMs use more RAM than you tell them - they have VM overhead AND for a desktop OS, it is important to give 128MB of video DRAM to the clientOS.
* WinXP goes out of support in a few months (9th April 2014?), so virus writers have been waiting for that date eagerly. The day of the last patches released is the day I stop using WinXP on any networked device.  I'll probably keep WinXP inside a VM that doesn't have any networking. Running any unsupported, unpatched OS, even on a LAN, is dangerous. 
* Ubuntu can be a hog these days (since 11.04). It is especially noticeable when running inside a VM and on lower CPU equipment.
* Choose the 32-bit version of Ubuntu LTS - better, choose the 32-bit version of Lubuntu 12.04. This will limit the bloat and provide support until 2017. Moving a VM from your netbook to another PC is pretty easy too.

I don't have VMs on anything slower than a Core 2 Duo CPU. It is just too painful otherwise, IMHO.
[See this,]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") for tips on tuning virtualbox.  You'll definitely want to defragment WinXP before starting too, unless your real HDD is an SSD.  I wrote those tips after seeing Ubuntu make a Core i7 running under virtualbox take 20 minutes to show a login screen after the 1st post-install reboot.

Don't think I answered all your questions. Don't worry if you make mistakes. Blowing away Ubuntu and restarting isn't a big deal. Plus, if you follow my guide, then really the only thing you must do the first time is fully, pre-allocate the vHDD for the guestOS. All the other settings can be modified later with a minimal level of effort - if any.  This is one of the times where "just do it" is better than over thinking it.  So - get started and "just do it" already. ;)

---

### Post by sudodus on 2014-01-24
Great advice *TheFu* :-)

But I have to comment on one tiny bit: Lubuntu 12.04 has no LTS. It has already passed end of life. It means that the Lubuntu specific packages receive no security updates. There are other light-weight alternatives based on Ubuntu 12.04 LTS that still receive updates including security updates. See [this link]("http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646").

---

### Post by deadflowr on 2014-01-24
Re-reading this thread I realize the OP should clarify which will be the vm and which will be the host OS.
I was thinking the vm would be XP but if it's reversed, then my ram assumptions would need to increase,
or I would add to the advice on installing a lighter window manager in ubuntu(openbox, fluxbox, maybe?)

---

### Post by TheFu on 2014-01-24
> **sudodus said:**
> Great advice *TheFu* :-)

But I have to comment on one tiny bit: Lubuntu 12.04 has no LTS. It has already passed end of life. It means that the Lubuntu specific packages receive no security updates. There are other light-weight alternatives based on Ubuntu 12.04 LTS that still receive updates including security updates. See [this link]("http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646").

That just sucks!  I don't actually use Lubuntu. 
For someone new to Ubuntu ... perhaps the Xubuntu LTS would be a good? 3 yrs of support. Enough to cover the next LTS release.

When I need a desktop, I load Ubuntu Server LTS, then LXDE or Openbox or fvwm as a GUI.

---

### Post by sudodus on 2014-01-24
Yes Xubuntu is one of the good alternatives.

---

