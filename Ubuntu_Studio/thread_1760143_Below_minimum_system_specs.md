---
title: "Below minimum system specs"
date: 2011-05-16
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2011-05-16
A friend of mine has a 7-8 year old PC which is below the Ubuntu minimum spec. It has 900 MHz AMD Athlon processor and 500 MB ram. It runs XP OK. I am trying to persuade him to change to Ubuntu but I am not sure if his hardware is up to it. 

He would mainly be using it for audio recording using Audacity and Ardour. Ubuntu Studio would be right up his street. Any advice welcomed.

---

### Post by sanderd17 on 2011-05-16
500MB of ram is enough, but maybe not very comfortable. A lighter version of Ubuntu (I am thinking about Lubuntu) should certainly work well.

Don't worry about studio or not, all applications they give in the Studio version can be installed in one click. But you could look on the Ubuntu Studio site to get an idea what application there are.

---

### Post by Pablo_F on 2011-05-16
Hi, 

As there is no much RAM and the system will be used mainly as a music studio, I recommend a distro where pulseaudio is not included, e.g., Tango Studio Karmasutra (which is based on ubuntu lucid). Another good one is AVLinux.

Note that oldish graphic cards can be problematic in recent kernels, but there are usually workarounds. 

Of course, the audio card compatibility is something to look into at these first steps.

Anyway, ubuntu / lubuntu / ubuntustudio / tango studio /AV Linux... all of them can be run from the CD/DVD without installing. 

Cheers, Pablo

---

### Post by shaunthesheep on 2011-05-24
Thanks for the responses. 

Some more info about his hardware. 

Motherboard: Asus A7V

His sound card is an M-Audio Audiophile 2496 (also has an ageing Sound Blaster of some sort).

---

### Post by Pablo_F on 2011-05-24
> His sound card is an M-Audio Audiophile 2496 

It works great and out of the box in jack with the alsa driver.

---

### Post by sgx on 2011-05-24
The sound card is a keeper, but try finding an avid gamer who will
horse-trade for an older 3 ghz P4, or dual core cpu and motherbord.

If Tango Studio or AVlinux are too slow, (not likely) Macpup might be a good interim option, a solid ubuntu repository based
Puppy linux, to which the common audio apps can be added by its package
manager, or manually, avoiding bloat.

Cheers

---

