---
title: "Studio 12.04 64B doesn't boot"
date: 2013-02-19
forum: Ubuntu Studio
---

### Post by andreazzz on 2013-02-19
Hi everybody!
Since a year I am a Linux enthusiastic, you all know why: it's great, fast and safe. I started using Mint LMDE but when I connected multiple screens, it freaked out. Therefore I made the switch to Ubuntu Studio, where I have 3 cloned screens (in Windows it's eyefinity, but that 's for gaming) attached to my Ati 6850. Until yesterday I haven't had any problems using Ubuntu, but (after installing updates, I think) now my pc doesn't boot anymore in Ubuntu Studio. I can boot into Windows and in the recovery mode, but the previous Linux versions aren't working either. I tried several things, a.o. [this]("http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes") (it worked on another pc with a Ati 4650) and some other things (which I cannot find anymore). It might help to say that the screen becomes black and I won't see the Studio icon and that only 2 of 3 monitors get a "black" signal.
Does anybody know a solution for this problem? If you need more information, just ask!

Thanks for everything so far!

AndreazZz

P.S. I tried all the recovery options in the recovery menu...

System specs:
AMD Phenom II x6 1045T
ASRock N68-GE3 UCC
8gb RAM Icudu
Ati XFX 6850


edit: I tried booting with only one monitor connected to my pc, but that doesn't solve anything. Also booting in older versions doesn't solve anything (3.0.23 ; 3.0.32). Besides that, booting in recovery mode and starting X from terminal doesn't work either.

---

### Post by andreazzz on 2013-02-20
SOLVED!
I deleted the Ati driver using ```
/usr/share/ati/amd-uninstall.sh --force
```, after that I tried DPKG, but it gave a lot of errors, then I rebooted in recovery mode and turned network on and tried "Fix broken packages". Now I finally can use my loved Ubuntu again!

---

