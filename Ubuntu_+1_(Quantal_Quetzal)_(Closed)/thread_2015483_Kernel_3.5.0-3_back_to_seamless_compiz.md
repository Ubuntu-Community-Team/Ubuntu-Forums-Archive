---
title: "Kernel 3.5.0-3 back to seamless compiz"
date: 2012-07-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-03
I just wanted to make a note  that the new kernel update has brought back with it seamless windows movement in compiz (as it was with earlier precise alpha testing) <wobbly windows> and also cube rotation flicker is absent and also with Expo.  Just beautiful work. I wonder how long it will stay this way.

 However .. another side note is that nvidia-current and other updates came with the kernel also .. so I am just curious of where to apply the credit for this nice graphical work.  I hope the devs take a good snapshot of this for future reference.

---

### Post by fjgaude on 2012-07-03
Well, 3.5.0-3 still goes into kernel panic when trying to load it on my Dell mini-10n netbook. More work required to get it up to 12.04 levels. <smile>

---

### Post by ventrical on 2012-07-03
Have you tried the alternate install or are you using desktop-i386..oh .. you have another thread ... :)

---

### Post by ScislaC on 2012-07-03
> **ventrical said:**
> I just wanted to make a note  that the new kernel update has brought back with it seamless windows movement in compiz (as it was with earlier precise alpha testing) <wobbly windows> and also cube rotation flicker is absent and also with Expo.

I think it may be due to the recent compiz update, not the kernel update. (that's when I noticed it)

---

### Post by ventrical on 2012-07-03
> **ScislaC said:**
> I think it may be due to the recent compiz update, not the kernel update. (that's when I noticed it)

Thanks. I do notice that the kernel is a little more snappier also. 

The same thing happened with Precise Alpha Testing. They had compiz working like a champion racehorse and then it started to regress come release day. It perplexes me that they get these awesome milestones and then trash them , however unintentionally.

---

### Post by balloons on 2012-07-03
> **fjgaude said:**
> Well, 3.5.0-3 still goes into kernel panic when trying to load it on my Dell mini-10n netbook. More work required to get it up to 12.04 levels. <smile>

Perchance are you willing to check do 12.10 kernel on 12.04 testing? I'm curious if the kernel is causing you issues or if it's the xstack -- running the new kernel on precise should tell us, since everything works on precise ;-)

[http://www.theorangenotebook.com/2012/07/call-for-testing-1210-kernel-on-1204.html](http://www.theorangenotebook.com/2012/07/call-for-testing-1210-kernel-on-1204.html)

---

### Post by ScislaC on 2012-07-03
I still haven't rebooted into the new kernel yet (just about to). And yes, the compiz regressions last cycle were very disappointing. It's a small thing, but I'm most excited that I can finally have my windows burn on close again! :)

---

### Post by fjgaude on 2012-07-03
> **guitara said:**
> Perchance are you willing to check do 12.10 kernel on 12.04 testing? I'm curious if the kernel is causing you issues or if it's the xstack -- running the new kernel on precise should tell us, since everything works on precise ;-)

[http://www.theorangenotebook.com/2012/07/call-for-testing-1210-kernel-on-1204.html](http://www.theorangenotebook.com/2012/07/call-for-testing-1210-kernel-on-1204.html)

Is it simply okay to run 3.5.0-rc5-quantal on 12.04?

My plate is pretty full with obligations. <smile>

Luca might be a better person to ask.

---

### Post by balloons on 2012-07-03
> **fjgaude said:**
> Is it simply okay to run 3.5.0-rc5-quantal on 12.04?

My plate is pretty full with obligations. <smile>

Luca might be a better person to ask.

We don't want to overwhelm you :-) Of course it's ok, and any bugs you file will still be useful, etc. It's an option if your curious and want to help out. The testing will be going on all-cycle, so perhaps if not now, later :-)

---

### Post by fjgaude on 2012-07-03
> **guitara said:**
> We don't want to overwhelm you :-) Of course it's ok, and any bugs you file will still be useful, etc. It's an option if your curious and want to help out. The testing will be going on all-cycle, so perhaps if not now, later :-)

Okay I installed 3.5rc5, along with linux-generic meta-package, No kernel panics, but the boot got the grub menu, then to a blank purple screen. Nothing else, had to cold boot to get back to a usable system. I think I tried rc1 when it was first released, but maybe it was for 3.4, and all worked fine.

---

### Post by lucazade on 2012-07-03
> **fjgaude said:**
> Is it simply okay to run 3.5.0-rc5-quantal on 12.04?

My plate is pretty full with obligations. <smile>

Luca might be a better person to ask.

Lol and Luca will answer you... I have just installed 3.5 on 12.04 via xorg-edgers ppa.
It runs really well ;)

---

### Post by fjgaude on 2012-07-03
> **lucazade said:**
> Lol and Luca will answer you... I have just installed 3.5 on 12.04 via xorg-edgers ppa.
It runs really well ;)

How do I get to xorg-edgers ppa? Please!

---

### Post by lucazade on 2012-07-03
> **fjgaude said:**
> How do I get to xorg-edgers ppa? Please!

if you want to add the xorg-edgers ppa repository:
```
sudo add-apt-repository -y ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

but be aware this will upgrade also the entire Xorg and video drivers stack beside kernel 3.5.
I've tested it on Nvidia and Intel GPUs and there are no problem at the moment.

otherwise you can download directly the kernel 3.5 .deb without adding the ppa (and w/o upgrade xorg).. this way:
```
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-image-3.5.0-3-generic_3.5.0-3.3_i386.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3-generic_3.5.0-3.3_i386.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3_3.5.0-3.3_all.deb
sudo dpkg -i *.deb
```

or this for 64 bit:
```
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-image-3.5.0-3-generic_3.5.0-3.3_amd64.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3-generic_3.5.0-3.3_amd64.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3_3.5.0-3.3_all.deb
sudo dpkg -i *.deb
```

---

### Post by fjgaude on 2012-07-03
Thanks, Luca. You are talking about 12.04, eh?

---

### Post by lucazade on 2012-07-03
> **fjgaude said:**
> Thanks, Luca. You are talking about 12.04, eh?

yep, 12.04 Precise ;)

---

### Post by fjgaude on 2012-07-03
I did the second option:

```
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-image-3.5.0-3-generic_3.5.0-3.3_i386.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3-generic_3.5.0-3.3_i386.deb
wget https://launchpad.net/~xorg-edgers/+archive/ppa/+files/linux-headers-3.5.0-3_3.5.0-3.3_all.deb
sudo dpkg -i *.deb
```

And it went just like 3.5rc5, got past the grub menu and then to the purple screen, lock-up!

It point to not having what you have, the xorg-edgers stuff. I guess I shouldn't try that, don't have time... will wait until 12.10 gets finished to start over. 12.04 works so good the way it is. I would like to help to get the latest kernel into 12.04 though. So be it. Thanks as always for your assistance.

---

### Post by ventrical on 2012-07-03
whopps :) nevermind:)

---

