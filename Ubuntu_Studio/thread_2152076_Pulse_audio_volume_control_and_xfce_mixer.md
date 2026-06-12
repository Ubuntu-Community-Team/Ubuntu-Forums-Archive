---
title: "Pulse audio volume control and xfce mixer"
date: 2013-06-06
forum: Ubuntu Studio
---

### Post by zealibib slaughter on 2013-06-06
Ok I got a strange problem, its more of an annoyance than anything but in Ubuntu Studio 13.04 pulse audio volume control ( the one on the panel) only halfway controls my sound card.  Xfce mixer seems to have taken full control.  Also the line capture device is now line 1 in xfce mixer but not listed in pulse audio, I haven't changed any hardware since upgrading and would love to get rid of the line 1 stuff and return full control to pulse audio volume control.  

this is the specs of my sound card 
*-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:fbe38000-fbe3bfff
how can I change the inputs back to how it use to be and make pulse audio control everything

---

### Post by zequence on 2013-06-06
pulseaudio mixers don't have all of the hardware controls. They only have controls for the pulseaudio specific stuff, which is partly an abstraction above the ALSA interface. Yes, it is a bit on an annoyance.

When using jack, you are using straight ALSA, in which case you are better off with an alsa mixer.

---

### Post by zealibib slaughter on 2013-06-07
I understand that Pulse don't control the hardware directly and from alot of googling I found out that the intel sound device sometimes does this on linux but there still should be a way to change line 1 back to line. 13.04 is the first release that has had this problem and Ive been using Ubuntu Studio since 9.10. My main reason for wanting to change this is because of the Pulse-jack sinks which seems to only be controled by pavucontrol.

---

### Post by zequence on 2013-06-07
There could very well be a regression in the release of pulseaudio 3.0. So, what you could do is file a bug report. Get yourself a launchpad account at [https://launchpad.net](https://launchpad.net), and then, in a terminal, do:

```
ubuntu-bug pulseaudio
```

The sink and source for jack are created by the jackdbus detect module, packaged as "pulseaudio-module-jack". There aren't really any gui controls for it, other than that you can select to use jack sink and source from a pulseaudio mixer.
Recently, the module defaults to two channels. Before the release of 13.04 it used as many channels as your audio device had channels in jack.

You can change channels manually in /etc/pulse/default.pa. That's about it, I think.

---

