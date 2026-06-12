---
title: "Best Linux distro for &quot;instant on&quot;"
date: 2009-05-14
forum: The Cafe
---

### Post by shatteredmindofbob on 2009-05-14
So, a first, a confession. Windows 7 has won me back to the dark side. That said, I do still intend to keep using Linux and I figure the best use for now would be to set up an ``instant boot`` partition on my laptop. 

I don`t really feel like shelling out the money for Presto (plus, I can`t say I`m too fond of their little `app store` model) so which free distro would be best for quickly booting, particularly when I want a secure connection (still don`t feel good about doing online banking from Windows)

---

### Post by billgoldberg on 2009-05-14
I only know of Splashtop and Presto.

The first you can't download or buy, the second costs money.

You could create your own.

Create a custom kernel for you machine, only install the bare minimum (not gnome or kde or xfce but something like JWM) and a light browser.

Something like that should boot in 20 seconds or less.

---

### Post by vonti on 2009-05-14
As an alternative, you can use Slackware and boot it from a pendrive.

---

### Post by Chilli Bob on 2009-05-14
Tiny Core live CD boots faster than anything else I've seen, but how hard it is to get a working desktop, I don't know.

---

### Post by sertse on 2009-05-14
Arch, with 5 second boot configuration. 

[http://bbs.archlinux.org/viewtopic.php?id=69086](http://bbs.archlinux.org/viewtopic.php?id=69086)

or I think [http://bbs.archlinux.org/viewtopic.php?id=71647](http://bbs.archlinux.org/viewtopic.php?id=71647) now

Obviously it means you need to read and work for it.

---

### Post by shatteredmindofbob on 2009-05-14
> **sertse said:**
> Arch, with 5 second boot configuration. 

[http://bbs.archlinux.org/viewtopic.php?id=69086](http://bbs.archlinux.org/viewtopic.php?id=69086)

or I think [http://bbs.archlinux.org/viewtopic.php?id=71647](http://bbs.archlinux.org/viewtopic.php?id=71647) now

Obviously it means you need to read and work for it.

Nothing wrong with reading and working

---

### Post by phrostbyte on 2009-05-14
You can do Puppy Linux too. It's not "instant on" (I don't think anything really is) - but it's pretty damn fast.

---

### Post by chris200x9 on 2009-05-14
you could do gentoo :P

---

### Post by floborg on 2009-05-15
Though it's basically useless and not Linux, ReactOS is the fastest-booting OS I have seen (intended for a PC).

---

### Post by myusername on 2009-05-15
moblin. its opensource. ive personally used it. and in the future you'll be able to install more apps thru free repos

---

### Post by Warpnow on 2009-05-15
Moblin is the easiest. I'll second that.

DSL/Puppy do boot fast.

But, ubuntu with a lightweight DE (LXDE) and no login manager, optomized to boot as quickly as possible with many tweaks can also cut under 10 seconds easily.

---

### Post by Sublime Porte on 2009-05-15
TinyCoreLinux is the fastest booting, functional desktop I've come across. About 10 seconds for me, and you're in a JWM desktop, with wbar and there's heaps of extensions, like Firefox, Skype, Pidgin etc.

> But, ubuntu with a lightweight DE (LXDE) and no login manager, optomized to boot as quickly as possible with many tweaks can also cut under 10 seconds easily.

Ubuntu booting in under 10 seconds?

---

### Post by Warpnow on 2009-05-15
> **Sublime Porte said:**
> TinyCoreLinux is the fastest booting, functional desktop I've come across. About 10 seconds for me, and you're in a JWM desktop, with wbar and there's heaps of extensions, like Firefox, Skype, Pidgin etc.



Ubuntu booting in under 10 seconds?

The lower resource Openbox version of Kuki Linux (Ubuntu derivative for the Acer Aspire One) booted in 8 seconds for many people on IRC. I never tweaked mine that much but was getting under 20 seconds.

Bearing in mund the AA1 has an underpowered CPU I bet faster could be achieved.

---

### Post by Phreaker on 2009-05-15
Asus express gate

---

### Post by Camilio on 2009-12-03
You should try **xPUD**. It is in heavy development. You can easily customize it to include your drivers.
It boots in less than 5 seconds, and stops in less than 1 second.
It is designed to boot from an USB stick, but can easily be set on HDD and booted via Grub.

[http://www.xpud.org/](http://www.xpud.org/)
[http://wiki.github.com/penk/mkxpud](http://wiki.github.com/penk/mkxpud)

---

