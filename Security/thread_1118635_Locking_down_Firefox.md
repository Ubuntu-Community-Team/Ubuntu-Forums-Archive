---
title: "Locking down Firefox"
date: 2009-04-07
forum: Security
---

### Post by comandrei on 2009-04-07
I'm about to deploy an LTSP server which will serve about 25 clients simultaneously.
I don't want my users altering a custom-made (secure) Firefox profile I've prepared for them using AdBlock Plus, PublicFox and other extentions.
They could still bypass PublicFox's authetication mechanism just by creating a new firefox profile (with firefox -profilemanager ) and using the newly create profile.
How could I disable this Firefox option ?(preferably without having to recompile firefox, and disabling that option on compile-time, because I would like to use the same solution on other Windows machines and I'm not quite fond of compiling Firefox everytime a new version is released).

---

### Post by bodhi.zazen on 2009-04-07
It is a bit off topic, but you may be able to use apparmor to lock down firefox (and more) a bit.

---

### Post by comandrei on 2009-04-07
Not quite what I need. I just want to disable the -P (-profilemanager) option from  Firefox

---

