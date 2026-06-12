---
title: "Vista very slow in virtualbox"
date: 2009-12-22
forum: Virtualisation
---

### Post by wildmanne39 on 2009-12-22
Hi everyone, can anyone tell me how to make vista 32 bit run faster in virtualbox? I am running 4 amd cpus 7 gigs of ram on a new hp desktop. It is so slow that it is unuseable at this point. I have done everything that virtualbox instructions told me to do. I saw a forum once that a person had a stripped down windows manager they used for xp, does anyone know if vista can be stripped down for speed and how I would go about doing it,or is there another answer? I have went through all of my old programs looking for xp because I have read posts that say it is faster in virtualbox, but I just could not find one. Any and all help is greatly appreciated.

---

### Post by James Dee on 2009-12-22
how many gb of ram did you dedicated to vista?

---

### Post by wildmanne39 on 2009-12-22
Hi, 3 gigs. Thanks for your reply, it is the cpu usage that stays high.

---

### Post by James Dee on 2009-12-23
i had a same problem just with windows xp. i was thinking that the problem was in to less dedicated memory, but now you change my opinion. my processor was also running in high usage.

---

### Post by djchandler on 2009-12-25
Have you turned on hardware virtualization in your BIOS? If you are running a Phenom X4 or Phenom II X4, there should be an item in the advanced BIOS settings to activate it. Since I don't run HP hardware, I can't tell you exactly where you'll find that menu item in your BIOS. But HP Support should be able to do that.

If you're running a quad core and running a guest OS in VirtualBox is slow, that has to be at least one of your problems. You may also want to [download the latest .deb package directly from Sun]("http://www.virtualbox.org/wiki/Linux_Downloads") and use version 3.1.

---

### Post by wildmanne39 on 2010-01-02
Hi, thank you for all your suggestions,virtualbox still has a problem when you allow access to all four cpu's when vista is ran as the guest, I changed the setting in virtualbox to show just one cpu to vista and know it is faster then when it runs native.

---

### Post by kungfupandda on 2010-01-05
> **wildmanne39 said:**
> Hi, thank you for all your suggestions,virtualbox still has a problem when you allow access to all four cpu's when vista is ran as the guest, I changed the setting in virtualbox to show just one cpu to vista and know it is faster then when it runs native.
That's a great idea, but does vista run as fast as before you installed virtualbox ?

---

### Post by Dayofswords on 2010-01-05
odd, my laptop has less specs than that and windows 7 worked ok, bit sluggish, but they, its windows

---

