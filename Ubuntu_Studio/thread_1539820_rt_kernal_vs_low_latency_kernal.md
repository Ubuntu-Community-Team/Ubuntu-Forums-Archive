---
title: "rt kernal vs low latency kernal"
date: 2010-07-27
forum: Ubuntu Studio
---

### Post by jmfal on 2010-07-27
HI Studiofiles, I`m a newbie to studio and I would like to know what the difference`s are between the rt kernal and the low latency kernal.
  I`m transfering my vinyl to pc/cd and I need to know if Ineed either of these kernals or am able to use the generic kernal?

I`m sure this has been asked before but I can`t find it anywhere.
10.04 64bit
    thanks****

---

### Post by P4man on 2010-07-27
its kern**e**l rather than kernal. Not saying because im a spelling troll; but it might help your search. I also think low latency kernel has been superseded by the rt-kernel (real time).

Not an expert in this field; but rt kernel is supposedly better for low latency audio recording, but it does have some potentially serious issues, like not working with closed source videodrivers. Of course; if you install this kernel you can just select it from grub boot menu or select the generic kernel so there is no harm in installing it and testing it. If you dont like it or it doesnt work properly for you; just reboot and select the other kernel again

---

### Post by RaumTrug on 2010-07-27
for digitalisation of media the generic kernel should be enough!

you only need the rt/lowlat kernels, if you need a very reactive (i.e. fast reactions on input) and robust (stable) audio system, for things like using the computer as realtime digital effects box, or midi synthesizer, or also to keep many tracks of audio recorded simultaneously as stable (glitch-free) as possible.

---

