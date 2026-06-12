---
title: "Wine Dlls"
date: 2010-02-28
forum: Wine
---

### Post by compooper on 2010-02-28
Ok, so if I have a legit copies of Winblows from 3.1 to VD-ista that either came with my computers over the years or where bought in stores, and hate the speed of Qemu and native winblows, is there a list of files I should copy over from my other partition to run Wine better?

---

### Post by hikaricore on 2010-02-28
This varies from program to program and has been covered numberous times on this forum.
If a game/application requires a dll you add it otherwise leave the dll issue alone.

---

### Post by compooper on 2010-02-28
I understand that, but what I am asking about is if there exists a list of ALL the DLL / or similar files , that could potentially be required that do not have 100% implemented corresponding component already.

This would be very helpful, and I would appreciate any information on this that you could give me. Thank you once again.

Can wine work with Cab files too?

---

### Post by Brebs on 2010-03-02
> **compooper said:**
> This would be very helpful
No it wouldn't. Mixing DLL sources can mess things up, unfortunately. From [doc](http://sdconsult.no/linux/wine-doc/arch-dlls.html):

> 7.3.2. Cons of Native DLLs

Not every application performs better under native DLLs. If a library tries to access features of the rest of the system that are not fully implemented in Wine, the native DLL might work much worse than the corresponding built-in one, if at all. For example, the native Windows GDI library must be paired with a Windows display driver, which of course is not present under Intel Unix and WINE.

Finally, occassionally built-in WINE DLLs implement more features than the corresponding native Windows DLLs. Probably the most important example of such behavior is the integration of Wine with X provided by WINE's built-in USER DLL. Should the native Windows USER library take load-order precedence, such features as the ability to use the clipboard or drag-and- drop between Wine windows and X windows will be lost.

What *is* helpful, is the steps required to get individual apps to work. This is what [appdb](http://appdb.winehq.org/) is for.

> **compooper said:**
> Can wine work with Cab files too?
"Work with"? Your question is weird & vague. But the answer is yes, I suppose. Also see [cabextract](http://freshmeat.net/projects/cabextract/).

---

### Post by dino99 on 2010-03-02
i'm a wine user since 2001 and fully appreciate all the good work done by the winehq team. You have to understand that twice a month and every month, a new release come up with new capabilities and a bunch of bugs fix, so here is the answer for your question.

Just try it with your apps and report on bugzilla if you need a fix. Last release is 1.1.39 (found on wine-ppa) and it's working out of the box without any tweaks that was needed in the past (like adding dll or using winetricks or winedoors).

Install it, use it and enjoy it.

---

### Post by MisfitI38 on 2010-03-02
> **Brebs said:**
> No it wouldn't. Mixing DLL sources can mess things up, unfortunately. From [doc](http://sdconsult.no/linux/wine-doc/arch-dlls.html):



What *is* helpful, is the steps required to get individual apps to work. This is what [appdb](http://appdb.winehq.org/) is for.


"Work with"? Your question is weird & vague. But the answer is yes, I suppose. Also see [cabextract](http://freshmeat.net/projects/cabextract/).
Brebs, I am your biggest fan.
And, I think one of the main reasons is the monkey av. I just love that whole monkey thing. :popcorn:

---

