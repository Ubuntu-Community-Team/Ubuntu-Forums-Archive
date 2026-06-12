---
title: "[Elementary OS - Luna] -- Can't get past GRUB"
date: 2014-12-04
forum: Ubuntu/Debian BASED
---

### Post by holt-jason on 2014-12-04
I have been trying to install Elementary OS on an ASUS G750:

Intel Core i7
Geforce GTX 860M
8GB of RAM

However, after selecting either to boot into the OS (try it out) or install it, I get stuck on a black screen with some text. Screenshot attached. This is not my first time installing Linux and I am able to installed other versions of Ubuntu on this PC just fine. Currently Xubuntu is installed. 

[ATTACH=CONFIG]258362[/ATTACH]

---

### Post by needhelp007 on 2014-12-05
Try this:

select install Elementary os but not press enter but press e-key to edit the code.
When the code appears you will see a code line that begins with linux and with --
delete -- and write: nomodeset xforcevesa
press F10-key to boot.

p.s.

I had the same problem, it worked for me

---

