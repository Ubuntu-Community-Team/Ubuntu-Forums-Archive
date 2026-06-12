---
title: "Where can I find a Gentoo ISO?"
date: 2010-03-30
forum: The Cafe
---

### Post by tm222 on 2010-03-30
I need an amd64 Gentoo ISO image, but I don't know what one to use. Can a Gentoo veteran direct me?

---

### Post by Bachstelze on 2010-03-30
> **tm222 said:**
> I need an amd64 Gentoo ISO image, but I don't know what one to use. Can a Gentoo veteran direct me?

Why would you need one? Gentoo does not need any specfic installation medium. You can use any Live CD, or an existing Linux installation, to install Gentoo.

---

### Post by tm222 on 2010-03-30
> **Bachstelze said:**
> Why would you need one? Gentoo does not need any specfic installation medium. You can use any Live CD, or an existing Linux installation, to install Gentoo.

How would you install using an existing distro? I already have a partiton.

---

### Post by swoll1980 on 2010-03-30
[here]("http://bouncer.gentoo.org/fetch/gentoo-10.0-livedvd/x86/livedvd-x86-amd64-32ul-10.0.iso")

---

### Post by Bachstelze on 2010-03-30
> **tm222 said:**
> How would you install using an existing distro? I already have a partiton.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

---

### Post by tm222 on 2010-03-30
> **swoll1980 said:**
> [here]("http://bouncer.gentoo.org/fetch/gentoo-10.0-livedvd/x86/livedvd-x86-amd64-32ul-10.0.iso")

Thank you so much!

---

### Post by dragos240 on 2010-03-30
If you want an iso, use the minimal install cd. That's the way I installed it. It also includes mirrorselect, which makes it easier to add mirrors. Make sure to follow the guide, and have some patience. It can be frustrating at times. Especially during the install. I should know, I use gentoo.

---

### Post by RedSquirrel on 2010-03-30
> **tm222 said:**
> I need an amd64 Gentoo ISO image, but I don't know what one to use. Can a Gentoo veteran direct me?

Start [here]("http://www.gentoo.org/main/en/where.xml").

You can use a Gentoo DVD if you want, but be advised that there is no graphical installer on the DVD; you will be following the [Gentoo Handbook]("http://www.gentoo.org/doc/en/handbook/") regardless of which installation medium you choose. Nothing from the CD/DVD ends up in your installed Gentoo system.

The Gentoo Minimal CD might be a better choice since it's much smaller. The Gentoo-based [SystemRescueCD]("http://www.sysresccd.org/Main_Page") is quite popular as well.

As mentioned above by **Bachstelze**, you can also use your existing OS. Just create a mount point:

```
# mkdir /mnt/gentoo
```and follow the Handbook.

---

### Post by dE_logics on 2010-05-16
You're asking such a question, I don't recommend installing Gentoo.

You wont like it, and then most probably curse the OS.

Furthermore, remember, there's nothing graphical in Gentoo prepare for command line.

Do the installation in installments - 

[http://forums.gentoo.org/viewtopic-t-824652.html](http://forums.gentoo.org/viewtopic-t-824652.html)

Finally, why are you installing Gentoo?...what's the purpose.

---

### Post by Shining Arcanine on 2010-05-16
> **tm222 said:**
> I need an amd64 Gentoo ISO image, but I don't know what one to use. Can a Gentoo veteran direct me?

Use System Rescue CD:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

> **dE_logics said:**
> You're asking such a question, I don't recommend installing Gentoo.

You wont like it, and then most probably curse the OS.

Furthermore, remember, there's nothing graphical in Gentoo prepare for command line.

Do the installation in installments - 

[http://forums.gentoo.org/viewtopic-t-824652.html](http://forums.gentoo.org/viewtopic-t-824652.html)

Finally, why are you installing Gentoo?...what's the purpose.

I think you might be jumping to conclusions. He could want to try a more custom-tailored distribution than Ubuntu, in which case Gentoo would be perfect for him, and does not know where to begin, which would cause him to ask such a thing.

---

### Post by dE_logics on 2010-05-16
Oh, :D...I see :popcorn:


Cause you need some serious search skills to work with Gentoo.

Anyway, I recommend downloading the latest stage3 tarballs from one of Gentoo mirrors and using your installed Ubuntu.

---

