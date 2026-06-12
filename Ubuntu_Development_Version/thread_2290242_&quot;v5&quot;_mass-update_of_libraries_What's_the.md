---
title: "&quot;v5&quot; mass-update of libraries: What's the meaning (resp. purpose) behind it?"
date: 2015-08-10
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-08-10
Perhaps some of you guys have noticed while upgrading that a huge number of system libraries now have a 'v5' suffix, e. g. libllvm3.6v5.
One of the hardest to tackle for me was the extremely important libsigc++-2.0-0v5, which I had to keep back until gparted moved from 0.19.0-3 to 0.19.0-3build1, otherwise I'd have "lost" a lot of essential tools that needed to have the NON-v5 one (whilst some others required it). Note that it is not possible to keep both a v5 and a non-v5 version in parallel to satisfy both "old" and "new" tool versions.

However, why the v5? What does it refer to, respectively: what is going on at the moment?

---

### Post by mc4man on 2015-08-10
The v5 mean built on gcc5, for the most part these packages are still in -proposed, ie. not ready for main.

---

### Post by syntaxerror74 on 2015-08-10
Ahhh...so this refers to gcc! Thanks, I had already excluded lots of less sensible explanations (e. g. KDE 5)

---

### Post by syntaxerror74 on 2015-08-10
> **mc4man said:**
> for the most part these packages are still in -proposed
Oh yes, that can be. Whilst I'd normally not let anything *-proposed* on my system, I was utterly forced this time because of the dire *lxappearance* bug which only got fixed a "proper" (and long-lasting) way by upgrading to openbox 3.6.0 from -proposed repos.

---

### Post by crcarson on 2015-08-12
Only a lowly user but some of my home grown gcc/gtkmm applications are now broken.  Can't recompile getting bad references to glib::ustring....    Haven't had the time to investigate you but will.  Any pointer accepted.

---

### Post by syntaxerror74 on 2015-08-12
> **crcarson said:**
> Can't recompile getting bad references to glib::ustring (...) Any pointer accepted.
[http://bugzilla.gnome.org](http://bugzilla.gnome.org) is where I would move my butt to next (well, if I were you). Because this is the bug tracker read by many of the glib main guys. This issue is very likely to not be caused by you but by the (still ongoing) gcc-4/-5 transition.

---

