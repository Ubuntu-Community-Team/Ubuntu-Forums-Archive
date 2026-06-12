---
title: "Distro with good cpu scaling"
date: 2010-02-20
forum: The Cafe
---

### Post by Turnips on 2010-02-20
I was using backtrack and realized it had cpu scaling and everything else, I was wondering which distro would have the best processor scaling and is relatively minimal.  Thanks.

---

### Post by Gallahhad on 2010-02-20
Do you mean out of the box?

All distro's have decent CPU scaling available, some/most require it to be installed as an option, and perhaps a little tweaking.

Not sure what your exactly after.

---

### Post by 3rdalbum on 2010-02-20
CPU scaling is done in-kernel, I believe. With scaling, there are several 'governers' - Performance (full speed), Ondemand (default setting), Conservative (like ondemand, but takes longer to go to higher speeds) and Powersave (slow speed).

Scaling isn't something you should worry about. Ondemand is the best governor 99.9% of the time ("Powersave" actually doesn't save power, because it delays the processor's fall back to sleep state; and there's no noticable difference between Ondemand and Performance because with Ondemand you get the performance as soon as you need it).

All distros should be able to CPU scale because it's a kernel-level function. Some distros assume that you don't really want to know what speed you're running at, and they don't display any indication. It also prevents people from submitting bug reports saying "My CPU is a 3 GHz but your distro claims it's 1.8GHz!".

---

### Post by The Real Dave on 2010-02-20
Backtrack is actually based on Ubuntu....so Ubuntu :)




Sorry, easy answer ;)

---

