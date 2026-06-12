---
title: "Can virtualbox emulate CPU speed?"
date: 2008-09-27
forum: Virtualisation
---

### Post by nc_jed on 2008-09-27
Folks,
I have VirtualBox 1.6.2 set up on a 2.4 Ghz desktop machine with a couple of Linux and Windows VMs running.  I also have a very old laptop (233 Mhz, 128 MB RAM) that I am trying to decide the best *buntu variant to install to.  I am currently considering Ubuntu server and XFCE as an add on via apt-get (current Xubuntu has waaaaaaay too much Gnome to run on this machine - even Xubuntu 7.04 (last version I can tell that shipped w/o all the extra Gnome hooks) is a little resource heavy.

Anyway, I know that in VirtualBox, you can determine the amount of system RAM allocated to a VM (which I will do to emulate the target environment), but can you also emulate the host CPUs speed?  I feel like this would be a good apples to apples comparison to non-commitally test which distros would function best on my intended target hardware.

- Jed

P.S.  For what its worth, I've already tried Puppy and DSL via LiveCD and I just do not like the JWM or the overall layout/set up.  I know these are good choices for older HW specs, but please save your breath regarding these 2 options.

---

### Post by mishad on 2008-10-13
> **nc_jed said:**
> can [VBox] also emulate the host CPUs speed?


Did you find a way to do this?

> **nc_jed said:**
> ... considering Ubuntu Server + XFCE ...
I've already tried Puppy and DSL via LiveCD and I just do not like the JWM or the overall layout/set up.  I know these are good choices for older HW specs, but please save your breath regarding these options.

I'm in a similar situation, with a Latitude M233 (233 P-MMX, 128MB, 800x600). I tried opengeu/geubuntu -- the 7.10 version installed OK but was sluggish (might be OK with some of the E17 menu transition candy disabled).

The 8.04-1 version wouldn't install (incredibly slow on the "select a timezone screen", then the installation just died (out of memory? does Hardy need more mem to install than Gutsy did). opengeu 8.04 was also taking 70% CPU for enlightenment process when idle (just top in gnome-terminal), whereas 7.10 took about 10% (both also have 7-10% for Xorg and 0-10% for nm-applet).

I'd prefer a *buntu (the other Linux boxes I have are all Debian or Ubuntu based) -- have you tried server+XFCE yet?

Misha

---

