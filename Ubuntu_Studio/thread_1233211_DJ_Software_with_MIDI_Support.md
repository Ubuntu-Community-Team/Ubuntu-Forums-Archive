---
title: "DJ Software with MIDI Support"
date: 2009-08-06
forum: Ubuntu Studio
---

### Post by sonone on 2009-08-06
Hi,

I really like to use UbuntuStudio (64Bit Version) for Djing, but Mixxx makes a lot of trouble (the screen crashes during playback, and when i want to restart mixxx it makes trouble with accepting my USB soundcard and gives no more playback). I also have Problems with configiuring the monitor on JACK, so I cant run mixxx on JACK.

So I'm looking for an alternative to Mixxx. A DJ Software with Midi-Support. Does anynbody know a good one? I'm also open about using several programs together, aslong as i can use them with my midi-controller.

Thanks for your help

---

### Post by christophski on 2009-08-08
I don't know about other software, but you might have better luck with Mixxx and JACK by running the realtime linux kernel (You didn't say whether you were so i'm assuming you aren't).
just do

sudo apt-get linux-rt linux-headers-rt

restart and choose the linux-rt grub entry.

---

