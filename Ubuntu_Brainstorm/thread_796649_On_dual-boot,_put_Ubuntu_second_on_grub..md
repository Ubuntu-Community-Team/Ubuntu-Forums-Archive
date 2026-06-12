---
title: "On dual-boot, put Ubuntu second on grub."
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by Nirro on 2008-05-16
I think it is too pretentious that if one installs Ubuntu in addition to Windows, he wants to put it the default on the first run.

Add it to the fact that there is still no easy way to tweak the grub menu in Ubuntu, I think it is troublesome that Ubuntu puts itself first on installation.

I think that in the boot menu, Windows should stay the first and afterwards all the Ubuntu options.

If the user decide to change the default, then he will need to work (hopefully it will be easier in 8.10),
but for start lets not change the default without his permission.

What do you think ?

---

### Post by smartboyathome on 2008-05-16
I don't agree. I think that if someone is installing Ubuntu, they plan to use it. It is easy enough to allow them to choose Windows.

---

### Post by ghindo on 2008-05-16
> **smartboyathome said:**
> I don't agree. I think that if someone is installing Ubuntu, they plan to use it. It is easy enough to allow them to choose Windows.+1

---

### Post by turezky on 2008-05-16
Moreover, the more I use Ubuntu, the more I beleive double boot is some kind of uncomfortable. It's much easier to use VirtualBox, and have both systems at the same time.
This dual boot is temporary stuff.And I think there's some point in Nirro's words. It's the M$ style to put yourself on the top-line. The user can simply be prompted on which position would he place each system.

---

### Post by rlcomstock3 on 2008-05-16
I like that my linux distro is first, I think it is only in order of how well they work, and if you really don't like the order, then open your grub config file and change it...


vim /boot/grub/menu.1st

Imagine trying to change something like that in Windows!!!

---

### Post by Nirro on 2008-05-17
Don't understand me wrong.
I don't even have a Windows installed,
I just see a lot of people complaining about it.
Most of the people that install Ubuntu on the first place just want to try it first, not necessarily to put it the default.

I think that jumping to the first line is just arrogant and rude. at least let the user decide for himself.

Of course you think Ubuntu is better than Windows. I think also, but that's not the point.


BTW, "vim /boot/grub/menu.1st" is not so simple for a newcomer to linux, "gksudo gedit" is much better. and still, users should not be forced to edit system files. this is an old attitude, today things are different.

---

### Post by smartboyathome on 2008-05-17
If that is the case, recommend they use Wubi (included with 8.04). It will allow them to install it on Windows and boot it up when they want.

---

### Post by Nirro on 2008-05-17
I tried Wubi once.
Wubi indeed puts Ubuntu second after Windows in the boot menu.
IMO the regular installation should do this also, unless the user explicitly select otherwise.

---

### Post by smartboyathome on 2008-05-17
> **Nirro said:**
> I tried Wubi once.
Wubi indeed puts Ubuntu second after Windows in the boot menu.
IMO the regular installation should do this also, unless the user explicitly select otherwise.

That doesn't make sense though. It isn't tyrannical that Ubuntu puts itself first on grub, like stated above, if someone wants to install it on their hard drive, then it should be first. If they want to "try it out", tell them to install it using Wubi. Way it makes sense to me, imo.

---

### Post by Nirro on 2008-05-17
> **smartboyathome said:**
> That doesn't make sense though. It isn't tyrannical that Ubuntu puts itself first on grub, like stated above, if someone wants to install it on their hard drive, then it should be first. If they want to "try it out", tell them to install it using Wubi. Way it makes sense to me, imo.
OK, so we disagree.

---

### Post by Merk42 on 2008-05-17
I just took it as GRUB putting entries in alphabetical order...

No matter which one is first, people won't like it. So I think it should just be easier to edit the list.

---

### Post by esteckis on 2008-05-17
Use synaptic manager and download startup manager. It lets you set which OS will boot first automatically.

---

