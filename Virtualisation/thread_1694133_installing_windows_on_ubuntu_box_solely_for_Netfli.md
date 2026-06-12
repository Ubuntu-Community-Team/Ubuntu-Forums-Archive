---
title: "installing windows on ubuntu box solely for Netflix Watch Instantly"
date: 2011-02-23
forum: Virtualisation
---

### Post by tlroche on 2011-02-23
How to make a fresh, pure Ubuntu Lucid box run Netflix? E.g., which VM to use (or dual-boot), is either W7 or winXP preferable, how to tweak audio, video, networking? Details:

My GF is getting a [Meerkat Ion nettop]("http://www.system76.com/product_info.php?products_id=95") with

[LIST]
[*]Atom 330
[*]4 GB RAM
[*]nVidia GeForce 9400M
[*]Intel High Definition Audio
[*]Intel Wi-Fi Link 5100
[/LIST]

on which, among other things, she wants to stream Netflix. I have windows experience and linux experience, but have not previously setup windows on a linux box, so would appreciate advice. Note that

[LIST=1]
[*]I have M$ DVDs for both Windows7 and XP SP3.
[*]Windows will probably only be used for Netflix, since she's been able to do all her work via web UIs on an ubuntu netbook (she just wants a "real keyboard" and bigger monitor).
[/LIST]

My guess is, I'd want to install VirtualBox and then install a W7 guest on that. Will that be adequately performant?

If so, are there configuration details of which I should be aware for installing on this hardware?

If not, what else should I try?

Pointers to docs appreciated, will cheerfully RTFM.

---

### Post by Hedgehog1 on 2011-02-24
> **tlroche said:**
> 
My guess is, I'd want to install VirtualBox and then install a W7 guest on that. Will that be adequately performant?

If so, are there configuration details of which I should be aware for installing on this hardware?

If not, what else should I try?

Pointers to docs appreciated, will cheerfully RTFM.

Sounds like a fun system (I just love hardware, don't you?).

Here is the thing - video playback is the least ideal thing to be doing in a Vbox instance.  Win7 in a Vbox on Ubuntu uses the Ubuntu video and audio drivers, and these layers add processing time.

The only way to really know if the performance would be acceptable as a Vbox instance is to try it.  XP takes less disk space, Win7 runs faster in many (but not all) hardware configurations.

Also - Amaz0n has just announced that anyone with the Amaz0n prime membership for 2nd day shipping can now stream videos, too. If you happen to have that, it is another option to watch movies - cheap.

Anyway, that is what little I know...

:KS

---

### Post by tlroche on 2011-02-24
> **tlroche said:**
> How to make a fresh, pure Ubuntu Lucid box run Netflix? E.g., which VM to use (or dual-boot),

> **Hedgehog1 said:**
> video playback is the least ideal thing to be doing in a Vbox instance.

So would you recommend dual-boot or another means of virtualization?

> **Hedgehog1 said:**
> I just love hardware, don't you?

No, it's just a means to an end. Maybe if I was better at it ...

---

### Post by Hedgehog1 on 2011-02-25
This is all a set of trade-offs.

Dual-boot will give you your fastest performance in Windows; BUT then you cannot stream a movie while you work in Ubuntu.

All things being equal, I would go Ubuntu as the installed/host OS, and then Vbox with Win7.

The day net-flicks offers a Linux player, you can delete the Vbox.

:popcorn:

---

