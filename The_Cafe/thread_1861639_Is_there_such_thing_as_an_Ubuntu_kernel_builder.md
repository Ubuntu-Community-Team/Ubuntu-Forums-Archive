---
title: "Is there such thing as an Ubuntu kernel builder?"
date: 2011-10-15
forum: The Cafe
---

### Post by nolag on 2011-10-15
One of the things that I think is great about open source is that you can compile your own version of it.  With that in mind, I am thinking that there should be (if there is not already) a kernel compiler that will check your system settings and optimize the build for it with a simple click.  Is there anything like that?  So it can download the most recent stable kernel source and compile it for me and my computer, then switch my kernel to it.  If not, I wonder if it is doable.  Any thoughts anyone?

---

### Post by Frogs Hair on 2011-10-15
You could look into this project . [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

### Post by Bachstelze on 2011-10-15
That would be close to useless. Despite what some Gentoo fanatics will tell you, the benefit of compiling your own everything, including the kernel, is just not worth the hassle.

---

### Post by el_koraco on 2011-10-15
> **nolag said:**
> One of the things that I think is great about open source is that you can compile your own version of it.  With that in mind, I am thinking that there should be (if there is not already) a kernel compiler that will check your system settings and optimize the build for it with a simple click.

```
make oldconfig
```

---

### Post by Atamisk on 2011-10-16
> **Bachstelze said:**
> That would be close to useless. Despite what some Gentoo fanatics will tell you, the benefit of compiling your own everything, including the kernel, is just not worth the hassle.

Sure there's use. the only reason i was able to get full non-proprietary support for my wireless card was to compile kernel 3.1. Plus, it's fun.

---

### Post by Bachstelze on 2011-10-16
> **Atamisk said:**
> Sure there's use. the only reason i was able to get full non-proprietary support for my wireless card was to compile kernel 3.1.

You didn't have to compile it. ;)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc9-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc9-oneiric/)

> Plus, it's fun.

It gets old VERY quickly. In about 6 months.

---

### Post by Atamisk on 2011-10-16
Oh... well then yeah, use the PPA! didn't know it existed. 

I'll still compile though, because it's still fun for me.I get a perverse sense of satisfaction by appending strange things to the -custom part of the version string.

---

