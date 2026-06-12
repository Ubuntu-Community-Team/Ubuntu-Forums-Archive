---
title: "Windows Vista restricts GNU GCC apps to 32 MB"
date: 2007-05-02
forum: Windows
---

### Post by BoyOfDestiny on 2007-05-02
[http://www.trnicely.net/misc/vista.html](http://www.trnicely.net/misc/vista.html)

I can't actually try this out for myself...
Nor do I know if MS did this on purpose or was honestly trying to prevent memory leaks... But it's dang weird...

---

### Post by davin on 2007-05-03
absolutely this is not fair man...

---

### Post by jclmusic on 2007-05-03
they've done this before to stop competition running on windows, just not with this method. windows is not a level playing field.

---

### Post by karellen on 2007-05-03
odd....at this momment all facts point to a deliberate "omission" (or should I say stabbing the open source in the back?...)

---

### Post by 3rdalbum on 2007-05-04
To be honest, I think this is possibly an unintentional problem.

GNU GCC produces Windows binaries with a 16-bit stub loader, according to the article. I think it's very possible that Windows then thinks that the programs are legacy 16-bit apps, and reduces the amount of memory available to them in order to stop a bug or incompatibility from madly filling up the system memory.

This explains why using the Win32 malloc (memory allocation) function doesn't trigger the problem - if a program is using the 32-bit Windows library, then it must be a 32-bit clean app, and not have any bugs to do with allocating memory past 32 megabytes.

---

### Post by M$LOL on 2007-05-04
There HAS to be something illegitimate about this.

---

### Post by steven8 on 2007-05-05
> **3rdalbum said:**
> To be honest, I think this is possibly an unintentional problem.

GNU GCC produces Windows binaries with a 16-bit stub loader, according to the article. I think it's very possible that Windows then thinks that the programs are legacy 16-bit apps, and reduces the amount of memory available to them in order to stop a bug or incompatibility from madly filling up the system memory.

This explains why using the Win32 malloc (memory allocation) function doesn't trigger the problem - if a program is using the 32-bit Windows library, then it must be a 32-bit clean app, and not have any bugs to do with allocating memory past 32 megabytes.

I don't believe anything MS does is unintentional.

---

### Post by 3rdalbum on 2007-05-05
> **steven8 said:**
> I don't believe anything MS does is unintentional.

I didn't say that the behaviour was unintentional - in fact, I said that restricting those applications to 32 megabytes is probably completely intentional. I just don't think it was done with the purpose of stopping legitimate 32-bit programs. It's not exactly a showstopper, is it - pretty much just a find and replace on the functions to switch it to the Win32 API's malloc, I'd think.

---

### Post by ronocdh on 2007-05-05
> **steven8 said:**
> I don't believe anything MS does is unintentional.
So they planned Vista to be a bomb? They wanted their computers to be fraught with security issues, leaving the company vulnerable to Mac versus PC ads? They wanted to drive Dell to offer Linux (and XP again, too!)?

I dunno. I think they've become a bunch of bumblers, and they are losing their iron fisted grip on the computing industry.

---

