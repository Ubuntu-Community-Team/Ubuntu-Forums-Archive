---
title: "Mackie Onyx Blackjack + Ardour3: does it work with Ubuntu Studio?"
date: 2016-01-06
forum: Ubuntu Studio
---

### Post by massimiliano-polito on 2016-01-06
Dear all,

I've installed Ubuntu Studio a few weeks ago, here are some information:

```
max@max-HP-Stream-Notebook-PC-13:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
```

After a bit of tuning it seems to work perfectly, now I'd like to move to the second step: starting recording musical instruments.

I'd like to use Ardour3 but since my netbook (HP-Stream) doesn't have anything like a mic input I have to buy a mixer. I found the Mackie Onyx Backjack ([http://www.sweetwater.com/store/detail/Blackjack/](http://www.sweetwater.com/store/detail/Blackjack/)), an USB mixer.

Does anybody know if it works well with Ubuntu Studio?

Does anybody use it?

Does anybody know about any other alternative to do what I'd like to do?

Thanks for your support.

Ciao,
Max

---

### Post by massimiliano-polito on 2016-01-07
OK it seems here nobody knows.

Anyway, I asked to their technical support and they said it works perfectly with recent releases of Linux.

I write it here just in case someone will pass looking for an answer. :)

Ciao,
Max

---

### Post by nik.charles on 2016-01-07
Hi max

I just got a Blackjack earlier this week.
Still testing it out with couple of microphones but sounds really clean and clear, lot more gain than most interfaces
Works great out of the box on most Linux, should be no problem on Studio

Shows as a device in ALSA but has no control options - all the levels are set on the box
Does show in PulseAudio, if you use it
Changed the setup in QJackCtl to the detected Mackie instead of my normal sound card and ran it on JACK @48kHz
I don't use Ardour, but had no issues running a few JACK apps and effects

---

### Post by massimiliano-polito on 2016-01-09
Thank you very much nik.charles, that's what I needed to decide to buy it.

Bye,
Max

---

