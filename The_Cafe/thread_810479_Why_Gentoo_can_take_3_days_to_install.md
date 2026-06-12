---
title: "Why Gentoo can take 3 days to install?"
date: 2008-05-28
forum: The Cafe
---

### Post by Kosimo on 2008-05-28
I don't have any knowledge about compiling stuff... I'm just a everyday linux user.

But my question regards Gentoo.  I'm really impressed about the installation time... Why can it take about 3 days to install? What does it do? I mean... Can someone just give me a simple idea about why can it be "good" to compile and compile during 3 days in order to install an os? 

Thank you guys, and sorry for my ignorance.

---

### Post by LaRoza on 2008-05-28
> **Kosimo said:**
> I don't have any knowledge about compiling stuff... I'm just a everyday linux user.

But my question regards Gentoo.  I'm really impressed about the installation time... Why can it take about 3 days to install? What does it do? I mean... Can someone just give me a simple idea about why can it be "good" to compile and compile during 3 days in order to install an os? 

Thank you guys, and sorry for my ignorance.

Gentoo is unique in its approach. It basically compiled everything even the kernel. Compiling can take a while, especially for major things. When you are compiling everything, it adds up.

---

### Post by Trail on 2008-05-28
Because you can customise the optimisation options to make software run only on your own machine (instead of, for example, ubuntu kernels which are generic enough to run on a variety of architectures). This way, software can take advantage of specific hardware optimisations etc to run faster (for example, some CPU might have a trick to copy stuff from memory faster, and your software can take advantage of it; but a generic one cannot).

Also, you compile stuff yourself, so you have total control of what is installed in your system. No unneeded applications.

Lastly, and more importantly, because it's fun :)

---

### Post by justin whitaker on 2008-05-28
> **Kosimo said:**
> I don't have any knowledge about compiling stuff... I'm just a everyday linux user.

But my question regards Gentoo.  I'm really impressed about the installation time... Why can it take about 3 days to install? What does it do? I mean... Can someone just give me a simple idea about why can it be "good" to compile and compile during 3 days in order to install an os? 

Thank you guys, and sorry for my ignorance.

It takes only about an hour on a fast machine to get the base installed (kernel, gcc, etc...), and get a snapshot of portage. 

Once you emerge KDE or GNOME, then it sets about compiling everything you need to run them, including Xorg, ALSA/OSS/Pulse Audio, etc...

The whole point of it is that you get a set of software compiled specifically for your machine, with whatever optimizations you want to have. 

Contrast that to Debian. You download a binary package, it installs, and you are done. It's not optimized for your system, it may contain debugging symbols, etc., that take up space on your HD...you don't know what the packager included, or did not include in the .deb. 

So, Gentoo is about control. You know what you are getting because you are telling it what to install and how to install it.

---

### Post by Kosimo on 2008-05-28
Thank you all you guys for the answers. That gives me  an idea about why can it be good to compile. As you said, total control of any option of a specific software (or kernel) then the optimization for your architecture and even your own computer.  That should be really fun, having 100% control of every single peace of software in your computer.  I guess that booting times should be really good on a distribution like Gentoo.

I hope that some day I'll be prepared to build my own totally compiled gentoo.


Thank you again for the answers!  8-)

---

### Post by notwen on 2008-05-28
> The whole point of it is that you get a set of software compiled specifically for your machine, with whatever optimizations you want to have.

> So, Gentoo is about control. You know what you are getting because you are telling it what to install and how to install it.

This is what separates Gentoo from other distros.   I personally place it in a class of it's own.  I personally enjoy compiling a package or two here and there, but compiling a whole distro from scratch is not my cup of tea.  To each his/her own though.  =]

---

### Post by Ub1476 on 2008-05-28
Is Gentoo fast? Cause I use Arch, which I even hear from Gentoo users is fast. I'm still interested in putting Gentoo on my laptop if it's faster though.

---

### Post by regomodo on 2008-05-28
> **Ub1476 said:**
> Is Gentoo fast? Cause I use Arch, which I even hear from Gentoo users is fast. I'm still interested in putting Gentoo on my laptop if it's faster though.

If you want noticeable speed differences, stay with arch. If you want complete control over practically every aspect of your install, go with Gentoo (or LFS).

---

### Post by Retrograde77 on 2008-05-28
Have used Gentoo in the past, great distro, yeah it can take ages to compile but thats half the fun :)

Problem was, I was into installing all the latest stuff from ~arch and killed the distro quite alot.

But is really good for learning alot more about linux, doing your own kernel is an adventure in itself :)

---

### Post by Barrucadu on 2008-05-28
> **Retrograde77 said:**
> doing your own kernel is an adventure in itself :)

Definitely, it took me three attempts to compile a kernel - but shaved 7 seconds off boot time when I was finished :)

---

