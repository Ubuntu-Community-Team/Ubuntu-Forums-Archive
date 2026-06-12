---
title: "AMD Radeon HD 6450 in Ubuntu 13.04 Beta 2"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by WillianRLD18 on 2013-04-19
So, hello everybody, greetings from Brazil.

I decided to test Raring beta 2, but had a surprise after installing the proprietary catalyst driver (version 9.010 from repositories, fglrx-updates package).

```
aticonfig --initial -f
```  outputs the following:

```
No supported adapters found.
```



But, here's the weird thing: 

If i restart the computer, except for the "AMD Unsupported Hardware" watermark, everything works fine. Even catalyst control center detects my card correctly.
Is this some kind of bug?

Sorry for my horrible english, still practicing. :)

---

### Post by jfernyhough on 2013-04-19
If it's working, don't worry about it. It's a beta driver (on a beta release OS) so there are still some kinks. You can try the latest 13.3 beta if you want to see if that makes a difference. :)

---

### Post by mcellius on 2013-04-19
Don't apologize for your "horrible english," as it seems quite good.

---

### Post by WillianRLD18 on 2013-04-19
Thanks for your quick replies.
So i think i'll just remove the watermark using the instructions from another thread.

Again, thanks!

---

### Post by pfeiffep on 2013-04-20
I have an AMD 6450 on my HP and am running a raring test installation --- perform daily updates and never saw this!

---

### Post by PendragonUK on 2013-04-21
I'm getting the "AMD Unsupported hardware" watermark...

GNOME Ubuntu 13.04
7970's in crossfire
fglrx (proprietary)

---

### Post by Maintech on 2013-05-03
I am getting the watermark as well. I am running a HP Pavilion DV6 with A8 APU quadcore. Had no issues with 10.04 or 10.10.

---

### Post by cariboo on 2013-05-03
This question may be better asked in the regular support forums, as Raring has now been released. Thread closed.

---

