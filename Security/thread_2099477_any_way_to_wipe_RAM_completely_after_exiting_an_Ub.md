---
title: "any way to wipe RAM completely after exiting an Ubuntu live CD/DVD?"
date: 2012-12-29
forum: Security
---

### Post by qwsazx on 2012-12-29
Is there a way to completely wipe RAM every time I exit an Ubuntu live CD?

I've seen it done on other live CD's, I just don't know how.

---

### Post by GreatDanton on 2012-12-29
Whenever you shut down your computer RAM is completely wiped.

---

### Post by qwsazx on 2012-12-29
> **GreatDanton said:**
> Whenever you shut down your computer RAM is completely wiped.

Then why does the TAILS live cd have a RAM wiping feature, when you eject the CD?

---

### Post by gnush on 2012-12-29
Wiping RAM is impossible unless you have access to kernel code, so if you want to do it programmatically you'd have to hack whatever kernel you're using.

However, as far as I know RAM is cleared when the computer doesn't receive any power (all circuits are turned off). Although, there may be some types of RAM that keeps memory even after the power has been cut, but I don't really know much about that.

---

### Post by haqking on 2012-12-29
[https://tails.boum.org/contribute/design/memory_erasure/](https://tails.boum.org/contribute/design/memory_erasure/)

Edit: forgot link to sdmem [http://manpages.ubuntu.com/manpages/natty/man1/sdmem.1.html](http://manpages.ubuntu.com/manpages/natty/man1/sdmem.1.html)

---

