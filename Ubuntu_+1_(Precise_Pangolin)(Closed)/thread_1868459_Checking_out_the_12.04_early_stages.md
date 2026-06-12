---
title: "Checking out the 12.04 early stages"
date: 2011-10-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lan3y on 2011-10-24
Just done a really early upgrade to 12.04 using the method mentioned in the stickies and other threads on this forum. the upgrade seemed to go very well, it boots (hoorah). there was only a few errors printed which ill include below.

```
Nvidia module in kernel 3.1.0-1

Error! Bad return status for module build on kernel: 3.1.0-1-generic (i686)
Consult /var/lib/dkms/nvidia-173/173.14.30/build/make.log for more information.

make.log: 

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1


Cups

cups start/running, process 3410
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
Updating PPD files for cups ...
```

Despite this error it seems the nvidia driver is still working after reboot.

guess we'll have to see what happens when the 'real' breakage starts now :popcorn:

---

### Post by cariboo on 2011-10-24
There isn't a lot going on right now, just moving the packages from Debian testing to the Precise repositories. There won't be much else happening until after UDS-P which runs from Oct 31 - Nov 5.

---

### Post by blackmail on 2011-10-24
I want the old interface back, why force-feed us the Unity desktop, they got it out they saw that most people hated it and now theya re doing it again, and all they achieve is to raise the number of unity changing related threads on ubuntuforums...

And because of the weak support regarding the Gnome3 desktop, when you try to play around with your desktop you brick your computer, and that is not cool... hope stuff will get changed in 12.04 - every installation requires people who actually configure that system to relearn steps, oh and automation will not work due to the major changes, a script tries or dies trying to change stuff on the interface...

Regards,
Blackmail

---

### Post by lan3y on 2011-10-24
> **cariboo907 said:**
> There isn't a lot going on right now, just moving the packages from Debian testing to the Precise repositories. There won't be much else happening until after UDS-P which runs from Oct 31 - Nov 5.

is this when to expect 'real' breakage then? :P

---

### Post by cariboo on 2011-10-24
> **blackmail said:**
> I want the old interface back, why force-feed us the Unity desktop, they got it out they saw that most people hated it and now theya re doing it again, and all they achieve is to raise the number of unity changing related threads on ubuntuforums...

And because of the weak support regarding the Gnome3 desktop, when you try to play around with your desktop you brick your computer, and that is not cool... hope stuff will get changed in 12.04 - every installation requires people who actually configure that system to relearn steps, oh and automation will not work due to the major changes, a script tries or dies trying to change stuff on the interface...

Regards,
Blackmail

If you're posting in this sub-forum, you know that Gnome 2 is no longer under development, and Precise is based on GTK-3 libraries so the old 2 panel interface no longer works.

With new interfaces, comes new ways of doing things, eventually you are going to have to learn a new interface, be it Unity, Gnome-shell, KDE, XFCE or LXDE, as the interface as you knew it with Gnome 2.X is not coming back.

The change from Windows to Linux is much larger, than an interface change, so I really can't see why there is such a reluctance to change the way you use the interface.

---

### Post by VinDSL on 2011-10-25
> **lan3y said:**
> is this when to expect 'real' breakage then? :P
Yes!

We're in the honeymoon phase, right now.  This is as good as it gets for testers.

Soon as the devs return from the bar, you can expect a thorough beating, honey!  LoL!  :D

Then, it's game-on...

---

### Post by VinDSL on 2011-10-25
> **cariboo907 said:**
> [...]I really can't see why there is such a reluctance to change the way you use the interface.
I suggest you go back and study that 'car analogy' blog post, that you linked to...  ;)

---

### Post by as2000 on 2011-10-26
> **VinDSL said:**
> 

Soon as the devs return from the bar, you can expect a thorough beating, honey!  LoL!  :D

Alrighty then! I think my frankensteined tester is up for the challenge. Except, I just can pin down the obvious smell of cooking electronics. Maybe a cap is about to vomit its internals all over the mobo. That should be fuuuun!

---

