---
title: "Compiz in a Linux Guest on a Windows Host?"
date: 2009-09-08
forum: Virtualisation
---

### Post by Levander on 2009-09-08
From Googling around, it's doable.  You get graphics hardware acceleration in the guest.  But, how usable is it?

Someone on IRC told me hardware acceleration in the guest may even slow things down?  And, I should just have all the graphics done in software?

I have a C2D E6300, an nVidia 7300 LE card, and 4 GB of RAM.  Is it worth considering running Compiz in a guest on that hardware?  Should I try software graphics instead of hardware accelerated graphics?  Maybe I should use a different virtualization application?

I am considering upgrading the graphics card.  Would that improve the situation in the guest in any configuration?  It may not because the way I'm reading it now, hardware accelerated graphics in a guest doesn't really take advantage of the graphics card itself?

---

### Post by thegreatsnafu on 2009-09-09
Hi,

It look like you have a very capable computer and it MIGHT be possible. It usually depends on what Virtual Machine you are using. You could try it, but it may lead to disaster and you may end up reinstalling Ubuntu on the Virtual Machine. But is that really too much trouble?

---

### Post by dk06 on 2009-09-09
> **Levander said:**
> From Googling around, it's doable.  You get graphics hardware acceleration in the guest.  But, how usable is it?

Someone on IRC told me hardware acceleration in the guest may even slow things down?  And, I should just have all the graphics done in software?

I have a C2D E6300, an nVidia 7300 LE card, and 4 GB of RAM.  Is it worth considering running Compiz in a guest on that hardware?  Should I try software graphics instead of hardware accelerated graphics?  Maybe I should use a different virtualization application?

I am considering upgrading the graphics card.  Would that improve the situation in the guest in any configuration?  It may not because the way I'm reading it now, hardware accelerated graphics in a guest doesn't really take advantage of the graphics card itself?

Your VM only sees the set of hardware that the vitualization software uses....which I doubt includes the nVidia graphics card.  If you install the guest tools/add-ons, you can enable 3d hardware acceleration (directx9 w/VMware) and maybe get compiz fusion working. I haven't tried to use compiz in a VM but it won't  hurt to try...maybe take a snapshot before you do in case it takes a dump.

So no, upgrading your graphics card will only help your host.

---

### Post by Levander on 2009-09-09
Oh damn.  I forgot to mention I wanna use VirtualBox.  You guys know VirtualBox has hardware accelerated graphics for guests now, right?

I just don't know enough about how it works to know if it accesses the video card directly or not.

---

### Post by Levander on 2009-09-09
Well, according to this thread on the virtualbox forums:

[http://forums.virtualbox.org/viewtopic.php?f=3&t=20884](http://forums.virtualbox.org/viewtopic.php?f=3&t=20884)

the 3.0 release of VirtualBox actually degraded performance of 3D graphics somehow.  But, if you downgrade to 2.2.x which was the latest release series before they bumped the version number up to 3, then it works fine.

I'm gonna have to go see what features your miss out on if you only use 2.2.

Not gonna mark this thread solved yet in case anyone wants to add anything.

---

### Post by thegreatsnafu on 2009-09-10
I only noticed Degraded performance while running Windows Vista on Virtual Box. I don't know if it's just Windows that lacks the   	 	 	 	 	compatibility with the Virtual Machine Add-ons, or a problem with Virtual Box itself. But did you try activating Compiz yet? Make sure that the settings are correct first, and that hardware 3D acceleration is turned on. If it doesn't work, it will tell you. :)

---

### Post by Levander on 2009-09-11
No, I'm doing research prior to messing around with it.

snafu, you don't mention any version numbers.  You only noticed degraded performance in what versions?

Are you saying that Jaunty in a guest VM with VirtualBox 3.0, Compiz worked fine, without 3D being slow and no ghosting?

If so, do you have 64 MB VRAM configured for the Jaunty Guest?  It seems like some people were saying if you have that much or less VRAM for a Linux guest, while running on a Linux host, you would be fine.  But, I'm not going to be running on a Linux host.

---

### Post by thegreatsnafu on 2009-09-11
> **Levander said:**
> Are you saying that Jaunty in a guest VM with VirtualBox 3.0, Compiz worked fine, without 3D being slow and no ghosting?

Yeah pretty much, and Compiz will work fine with 64mb of vram, Even when running on Windows. You may be able to get away with 32mb (But I haven't tried it yet).

---

