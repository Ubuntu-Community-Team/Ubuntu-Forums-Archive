---
title: "When will the 3rd digit in the kernel version number disappear?"
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sacridex on 2012-08-01
Hello,

when will the third digit (3.5**.0**) in the kernel version number disappear?
Cause its not an official number anymore and theoretically useless. Is there still Software out there, that is checking for 3 digits? Or any other reason?

---

### Post by jpeddicord on 2012-08-01
The third digit is for maintenance releases; those that don't bring new features but fix bugs on that kernel series. It won't be going away.

Example: look at the 3.4-series kernel (3.4.7): [http://kernel.org/](http://kernel.org/)

---

### Post by sacridex on 2012-08-01
Thats not the digit I mean.
My current kernel: 3.2.**_0_**-27 (or on QQ sth like: 3.5.**_0_**-6)
Thats the one I mean, actually its the "4th" digit, if you count the one for minor releases too. ;)
 It is never incremented and there for what reason?

---

### Post by jpeddicord on 2012-08-01
> **sacridex said:**
> Thats not the digit I mean.
My current kernel: 3.2.**_0_**-27 (or on QQ sth like: 3.5.**_0_**-6)
Thats the one I mean, actually its the "4th" digit, if you count the one for minor releases too. ;)
 It is never incremented and there for what reason?

We're talking about the same digit. :) The kernel has releases that use the 3rd digit to specify a maintenance release, just as for the 2.6 series there was a fourth digit used to signify the same thing.

I don't know exactly why it was chosen to make this number zero in Ubuntu, but it's probably because Ubuntu's kernel is based off of the initial release and not the maintenance releases. I've seen other distros use this number (Fedora 17 has 3.3.4, my VPS provider has 3.0.18 ).

---

### Post by sacridex on 2012-08-02
Ubuntu seems to [use the patched versions]("http://kernel.ubuntu.com/%7Ekernel-ppa/info/kernel-version-map.html").
There are actually 5 digits. ;)
But still, the 0 has no function and is therefore never incremented.

So I am wondering if this digit will be removed some day?
It's not really "bad", but it still kinda annoys(if it really has no function), at least me. ^^

---

### Post by jocko on 2012-08-03
> **sacridex said:**
> But still, the 0 has no function and is therefore never incremented.
Not true. It has as much function as any of the other numbers. The third digit in the kernel version is part of the kernel number from kernel.org, so removing it would remove information about exactly which kernel version it is. As an example precise uses a patched version of 3.2.0, so to name the ubuntu kernel version they keep the numbers from the source kernel (3.2.0) and adds a number to it to keep track of which ubuntu-specific version it is (currently -27).

---

### Post by sacridex on 2012-08-03
> **jocko said:**
> Not true. It has as much function as any of the other numbers. The third digit in the kernel version is part of the kernel number from kernel.org, so removing it would remove information about exactly which kernel version it is. As an example precise uses a patched version of 3.2.0, so to name the ubuntu kernel version they keep the numbers from the source kernel (3.2.0) and adds a number to it to keep track of which ubuntu-specific version it is (currently -27).
You sure?
In [this link]("http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html"), which I also posted above, Ubuntu kernel 3.2.0-29.46 bases upon the mainline kernel 3.2.24, but still, the third digit is 0.

---

### Post by t1497f35 on 2012-08-03
> **sacridex said:**
> You sure?
In [this link]("http://kernel.ubuntu.com/%7Ekernel-ppa/info/kernel-version-map.html"), which I also posted above, Ubuntu kernel 3.2.0-29.46 bases upon the mainline kernel 3.2.24, but still, the third digit is 0.

Yep, I also wonder why do they keep the zero.

Maybe no (Ubuntu) dev cares about removing the useless number?

---

### Post by jocko on 2012-08-07
> **sacridex said:**
> You sure?
In [this link]("http://kernel.ubuntu.com/%7Ekernel-ppa/info/kernel-version-map.html"), which I also posted above, Ubuntu kernel 3.2.0-29.46 bases upon the mainline kernel 3.2.24, but still, the third digit is 0.
I see your point. That's funny. It seems like they must have changed the naming conventions with the 3.0 kernel... It's probably a bug they haven't bothered to fix.

---

