---
title: "Grub Rescue Error  on Xubuntu 14.04 beta 2 install (for AMD64)"
date: 2014-04-02
forum: Ubuntu Development Version
---

### Post by Brother_Dave on 2014-04-02
Two days ago, on my AMD 64 desktop, I installed Xubuntu 14.04 beta 2  as dual boot with Win 7 Home 64 bit
I am a Linux newbie, but very technical.  At first, this dual boot worked fine. Now I get at boot up:

Verifying DMI Pool Data ...
error: no such device:
5b2b0455 -ca39-40c8-9547-30cfa9adc02
Entering rescue mode...
grub rescue>

There I typed  ls  and get:
(hd0), (hd0,msdos6) (hd0,msdos5) (hd0,msdos1) (fd0)

Temporary solution !  (I dion't know why this works, but it does, every time !)

When I go into the BIOS at startup, do nothing, and exit without saving, grub works !

I get  GNU GRUB  version 2.02 beta 2-7    and I can select these normally:

Ubuntu
Advanced options
Memory test ....
Memory test....
Windows 7 (loads on  /dev/ada1)


Should I wait until about April 17, 2014  when Xubuntu 14.04 LTS is released to upgrade my beta 2 version?

My beta 2 copy is burned onto a DVD +R  

Or is there a fairly easy fix ?    I don't know Linux Terminal commands or how to screen capture there to post results here.

THANKS for any help !

---

### Post by Brother_Dave on 2014-04-25
Update:  When I upraded in Xubuntu 14.04 beta 2 to 14.04LTS, the Grub 2 loader worked one time. But after running Windows 7 once, it failed again as before. So I go into the BIOS and exit without making an changes; and that makes the Grub boot choices work again. Later after a new flash drive commercial install of 14.04LTS it might work.

---

### Post by cariboo on 2014-04-26
Thread closed, as Trusty has been released.

---

