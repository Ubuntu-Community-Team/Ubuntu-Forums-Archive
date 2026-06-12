---
title: "A thought about FreeBSD and Mac Leopard"
date: 2007-12-16
forum: The Cafe
---

### Post by Black Mage on 2007-12-16
I'm not sure if I'm correct at all about this, so feel free to correct me if I'm wrong.

Mac OS X Leopard, like previous versions of Mac is Unix. Leopard is a version of Unix and FreeBSD and made for mac hardware. But since its FreeeBSD, if Leopard was installed on hardware that is not supported by Mac but uses the BSD drivers, like using an Asus motherboard with BSD drives, leopard should run on that hardware????

So to sum it up, if someone installed Leopard and used other BSD drivers, leopard should run on any hardware.....

Am I wrong?

---

### Post by jespdj on 2007-12-16
I'm not a Mac expert and I don't know, but it is most likely not that simple. Mac OS X is *based on* BSD, but it is not the same as BSD. I'm sure Apple has changed it in such a way that it cannot be easily installed on non-Apple hardware.

If you want to know more about running Mac OS X on non-Apple hardware, have a look at [OSx86]("http://www.osx86project.org/").

---

### Post by Xbehave on 2007-12-16
mac is based on darwin which IIRC is bassed on bsd but not freebsd

---

### Post by The Noble on 2007-12-16
> **jespdj said:**
> I'm not a Mac expert and I don't know, but it is most likely not that simple. Mac OS X is *based on* BSD, but it is not the same as BSD. I'm sure Apple has changed it in such a way that it cannot be easily installed on non-Apple hardware.

If you want to know more about running Mac OS X on non-Apple hardware, have a look at [OSx86]("http://www.osx86project.org/").

Yup, it's not that simple sadly. It's not a matter of drivers either, but the will off apple. They integrate some sort of chip into each of their parts that says it's from apple and the operating system does not talk if that is missing. OSX86 is a hack to remove that requirement.

---

### Post by DeadSuperHero on 2007-12-16
I'm always impressed when I look at the OSX86 project. The fact that they've gotten Leopard to MOSTLY work is a feat in itself.
It'd actually be really fun to build a Hackintosh.

---

### Post by Black Mage on 2007-12-16
Would that be illegal to sell, the Hackintosh? Or maybe call it the iHack, HackBook, or Hack Pro. Nothing can beat the HackMini.

But has no one sold it yet because that is somehow illegal?

---

### Post by samjh on 2007-12-16
I posted this answer in another Apple thread: [http://ubuntuforums.org/showthread.php?t=628225](http://ubuntuforums.org/showthread.php?t=628225)

> It's a bit of a stretch to say OS X is modified from BSD, even though it is technically true.

OS X uses the XNU kernel, which was developed by NeXT, a company founded by Steve Jobs (co-founder of Apple) and later bought by Apple.  XNU uses BSD's implementation of the POSIX standard, and uses the Mach kernel with performance and other improvements from BSD.

Hope that clears things up. :)

The XNU kernel is FOSS, by the way: released under the Apple Public Source License. :)

---

### Post by Sp4cedOut on 2007-12-16
It's not that OSX can't run on other computers, it's that it is designed not to.

Meaning that there is nothing about the operating system that's incompatible with non-Apple hardware, other than the fact that Apple engineered it to no work on non-Apple hardware.

---

### Post by Black Mage on 2007-12-16
But would it be legal with OSX86?

---

### Post by Rupertronco on 2007-12-16
> **Black Mage said:**
> But would it be legal is OSX86?

Unfortunately, no it is not legal.

---

### Post by Black Mage on 2007-12-16
Good ole' Apple, aka Microsoft with a smile.

---

