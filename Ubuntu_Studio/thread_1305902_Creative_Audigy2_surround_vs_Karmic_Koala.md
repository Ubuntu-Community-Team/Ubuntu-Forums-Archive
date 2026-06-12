---
title: "Creative Audigy2 surround vs Karmic Koala"
date: 2009-10-30
forum: Ubuntu Studio
---

### Post by Pedric on 2009-10-30
Hi,

In Ubuntu 9.04, I could enable the 7.1 channels of my Audigy2 ZS easily by setting

```
default-sample-channels = 8
```

in /etc/pulse/daemon.conf. I would then no longer see the card as a stereo output device in PulseAudio, but an 8-channel device that correctly addressed the 7 speakers and the subwoofer I have connected.

However, in Ubuntu 9.10, things have changed. Regardless of the default-sample-channels entry in PulseAudio's daemon.conf, I now need to set a profile for the hardware device in the GUI, and the only ones that produce any output are Analogue Stereo outputs. If I choose a 7.1 multichannel profile, the device goes missing in the Outputs section.

Is there an easy solution to this or do I need to post this as a bug in launchpad?

[edit] Yes of course, I have unmuted any relevant ALSA channels! The "new" gnome-alsamixer seems kinda... unfinished, though.

---

### Post by lakscoordination on 2009-10-31
Exact same problem here: there are a subset of hardware configurations for my card that, when selected, make the card disappear as an output.  Quite bizarre and frustrating given that it worked flawlessly for me on an alpha release of Karmic.

---

### Post by Pedric on 2009-11-02
As a first guess (I currently don't have the time to look deeper into the issue) would be that PulseAudio fails to map channels correctly and thus disables output on the device. With the Audigy2 (and possibly other multi-channel devices), Alsa exposes very many channels and switches, some of which are redundant or without any functionality.

Now, if there was a way to debug the channel mapping procedure...

---

### Post by zamrg on 2009-11-03
I think I probably have the same problem as you.

see my post @ [http://ubuntuforums.org/showthread.php?t=1309759&highlight=audigy](http://ubuntuforums.org/showthread.php?t=1309759&highlight=audigy)

---

