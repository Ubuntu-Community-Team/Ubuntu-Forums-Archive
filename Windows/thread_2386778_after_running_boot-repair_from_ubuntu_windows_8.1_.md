---
title: "after running boot-repair from ubuntu windows 8.1 boot failed"
date: 2018-03-10
forum: Windows
---

### Post by jonnytobaios on 2018-03-10
hello 


i got a big problem hope someone knows what to do ,,,

after i run boot repair on ubuntu .windows ,at boot start, wont let me load windows , and says that the hard drive is locked and cannot do any repair 


anyone suggest me something clever ???

---

### Post by oldfred on 2018-03-10
What brand/model system?
What video card/chip?

From Ubuntu live installer run this:

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Did Windows do updates?
It may even have done updates in background which you did not see.
And then it may have turned fast start up back on, and changed UEFI settings.
We have seen Secure Boot turned back on, and drives changed from AHCI.

Can you directly boot Windows from UEFI boot menu. Often f10 or f12.

---

