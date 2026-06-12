---
title: "386, 486, 586 what does it matter if....."
date: 2005-03-09
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-03-09
386, 486, 586 what does it matter if everything we install isnt setup for our architecture? Im usin a 686 kernal but everything I APT seems to be 386. Does it really matter? Seems it only would if you compiled everything yourself. This is something Ive wondered about for awhile. Alot of us nowadays have pretty beefy PCs but it seems like a waste if everything isnt compiled for 686 or whatever.

Let me also say this in no way is a criticism. In the end Im just wonderin if I would see a speed gain by compiling everything myself. ;)

---

### Post by DJ_Max on 2005-03-09
You pretty much got the right idea. If you downloaded a i386 package, it's been optmized for a i386 system, but will still run on any x86 system. It doesn't matter how "beefy" peoples PC's are per say.

---

### Post by Xian on 2005-03-09
[QUOTE=MetalMusicAddict]386, 486, 586 what does it matter if everything we install isnt setup for our architecture? Im usin a 686 kernal but everything I APT seems to be 386. Does it really matter? [/QUOTE]
I've run both the 386 and 686 kernels and noticed little if any difference.

---

### Post by MetalMusicAddict on 2005-03-09
Has anyone run the Ubuntu 64-bit and seen a difference from the 32?

---

### Post by jdodson on 2005-03-09
[QUOTE=MetalMusicAddict]Has anyone run the Ubuntu 64-bit and seen a difference from the 32?[/QUOTE]

yeah 32 bit stuff is hard to run and support is still lagging behind 32 bit.  beyond that, no.

---

### Post by jdong on 2005-03-09
Actually, the tag "386" is deceptive. Ubuntu packages are compiled "-march=i486 -mcpu=pentium4". Blind Gentoo-style "slap-on-the-friggin-cflags" 'optimization' leads to all sorts of trouble, like failed compiles and incorrect binaries. Did you know that i586 optimized code runs slower on 686's than i386-optimized code?

the true difference optimization makes is minimal, if at all....

---

### Post by MetalMusicAddict on 2005-03-09
[QUOTE=jdong]Actually, the tag "386" is deceptive. Ubuntu packages are compiled "-march=i486 -mcpu=pentium4". Blind Gentoo-style "slap-on-the-friggin-cflags" 'optimization' leads to all sorts of trouble, like failed compiles and incorrect binaries. Did you know that i586 optimized code runs slower on 686's than i386-optimized code?

the true difference optimization makes is minimal, if at all....[/QUOTE]
What about vs. 64-bit?

Ive been holding out till XP 64 comes out to upgrade but If I can see a real speed increase in Ubuntu I might go now.

---

### Post by TravisNewman on 2005-03-09
While you may experience a speed increase (dunno, haven't used a 64), you'll notice that a lot of things are hell to set up, which is why a lot of people who have Athlon 64s still use the 32 bit versions.

---

