---
title: "is this enough of a system?"
date: 2010-10-19
forum: Ubuntu Studio
---

### Post by RasterBurn on 2010-10-19
hello, i am wondering if my computer is enough to run ubuntu studio 64bit

the computer has an AMD Sempron 64bit processor running at 1.8GHz single core, 512mb ram, 120gb hdd, 128mb radeon 9550 video card with onboard audio, i am not fully sure of the audio card, its built into the mobo i think the mobo is an ASUS K8U-X mobo if im not mistaken it uses the Realtek audio drivers

i would like to use this computer as a DAW and possibly for some games while my son is around

the reason for setting up a 3rd computer is for several reasons, i cant use my wifes computer cause well simply put, she would rather use hers then mine, as for my computer, well i cant get JACK to run properly

I figure at least with a dedicated DAW all the apps will be there that i need to use, anyways i plan to use the mic input for analog instrument input (guitar, bass guitar) and a usb midi cable for the midi equipment (Roland D50, yamaha MEP4). so is my computer with the above specs good enough to run Ubuntu Studio with very little latency if any?

---

### Post by trulan on 2010-10-19
Maybe - but with only 512 Mb ram and an onboard video card, it's going to take pretty much everything just to run Gnome, and there won't be much left for anything else.  You'll stand a much better chance of getting something useful if you use a lighter desktop environment, like LXDE.

If you prefer a ready-made solution, check out AVLinux:
[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)
It's built on Debian, uses LXDE, and will do a lot better on a machine like yours than a full-blown Ubuntu Studio install would.  It comes with the same great programs (and a few more) that Ubuntu Studio includes, and it will boot up to a working desktop using around 100Mb, whereas standard Ubuntu Studio with Gnome uses over 350 Mb.  Give it a try!

Or, if you'd rather stick with Ubuntu, I would install Lubuntu (LXDE) and then add the studio apps you want (like Ardour and Jack).

Good luck!

---

### Post by RasterBurn on 2010-10-20
well, the machine doesnt have onboard video, its an AGP video card (it costs memory to have an onboard video card) the sound is what is onboard, when i upgrade my wifes computer the video card will have a boost to 256mb (I think the one in my wifes computer is a radeon 9650) and the ram will have a boost to 1.5gb, if that isnt enough ram for the system there is always swap :D

---

### Post by trulan on 2010-10-20
Oh sorry, misunderstood about the video card.  You should be good then.  Sure there's always swap, but if the system spills over into swap while trying to do low latency audio - that'll hurt for sure...

The weak link in the system, when you put it that way, will probably be your soundcard's mic preamp and A/D converter.   Latency shouldn't be a problem, but the quality may be a little less than pristine.  But there's no harm done in trying it.

---

