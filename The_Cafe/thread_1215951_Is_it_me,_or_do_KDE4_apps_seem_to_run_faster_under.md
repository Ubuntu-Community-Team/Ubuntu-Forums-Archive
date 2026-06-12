---
title: "Is it me, or do KDE4 apps seem to run faster under Gnome?"
date: 2009-07-17
forum: The Cafe
---

### Post by L815 on 2009-07-17
I installed a few kde4 apps the other day under gnome, and I noticed that they run quite a bit faster, and start quite a bit faster than they felt on KDE4. Even with Compiz enabled on gnome and compiz disabled on KDE4, it felt faster.

Could there be an explanation for this, or is it just me :p?

---

### Post by pluviosity on 2009-07-17
I've only even had the opposite experience:  KDE apps do better in their native environment.

---

### Post by swoll1980 on 2009-07-17
It's you.

---

### Post by L815 on 2009-07-17
:(, not that it matters though.

---

### Post by TBOL3 on 2009-07-17
No, I have the same experience too.

I love the gnome desktop, but when it comes to apps, I love them to be qt.  Weird, I know.

---

### Post by Skripka on 2009-07-17
Why were you doing using Compiz under KDE?  If you're going to rag on KDE apps run them in their fully native environment before making assertions.

---

### Post by T.J. on 2009-07-17
Honestly, Compiz is designed primarily for the Gnome environment, and it's also BETA software.  If you want proper graphics performance on KDE 4, please try KWin first.

Good luck!

---

### Post by L815 on 2009-07-17
> **Skripka said:**
> Why were you doing using Compiz under KDE?  If you're going to rag on KDE apps run them in their fully native environment before making assertions.


My mistake. I was under the impression 'desktop effects' under KDE4 was using compiz as the underlying engine.

I like a mix of qt apps and gtk apps. As long as they both can co-exist under any environment, I'm happy :D

---

### Post by T.J. on 2009-07-19
Oh no, KWin (KDE 4's window manager) has its effects completely native to the environment, although some distributions or users install Compiz on KDE and experience poor performance as well as graphics glitches.  

I found that apps co-exist better under KDE than Gnome, especially WINE - because the Gnome settings daemon has some very bad habits - including overriding the X server settings. For example, don't type "xset r off" (a standard X utility) in a terminal under Gnome. You will freeze or worse.  If you do the same in KDE, it's fine with it and works as intended.  All that does is disable key repeat on the keyboard, which is necessary for certain WINE applications to run properly (WINE keeps its own keyboard buffer it seems).

---

