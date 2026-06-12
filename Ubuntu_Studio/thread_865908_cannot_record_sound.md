---
title: "cannot record sound"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by beN..87 on 2008-07-21
i'm trying to get up and running recording what is coming out of my speakers, i've tried using the ubuntu sound recorder and gtl desktop capture and also audacity, i can't seem to get anywhere with this

i'm not trying to record from microphone, but what is playing on the web ect

heres some info 

audacity recognises inputs

ALSA - default
OSS /dev/dsp
ALSA: HDA ATI SB: ALC262 Analog (hw:0,0)


i have tried selecting inputs  as digital, capture, Mic boost PCI , and the like  - and yet i cant seem to get anywhere

heres my sound card


description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

any ideas as to how to go about getting going with this?

thanks in advance

---

### Post by thorgal on 2008-07-21
hello.

Let me understand : you want to record the audio stream the flash plugin is outputting to your soundcard ?

So you need a software that can intercept that stream and dump it to disk. What I have in mind is jackd. But the jackd server and flash plugin are not directly compatible, you need an extra piece of software that can make them talk to each other. oss2jack is such a module. So what would happen if you get this running is :

1- the flash plugin sends its audio data to the fake oss device (fake /dev/dsp created by oss2jack). 
2- the audio data is actually handled by the jackd server which can route the data on demand to any app that has jack ports opened. Audacity can work with jackd so it would just require that you patch up oss2jack output ports to audacity jack input ports and voila :)

You could also use other capture app (ardour, timemachine, etc, all jackd compliant).

BUT! and I really mean BUT! getting oss2jack up and running is no easy task, not to mention jackd which is very sensitive to all sorts of things (it's a low latency audio server which will challenge yoru audio hardware if not tuned correctly). 

There may be ways to achieve the same thing with other audio servers (pulseaudio for example, or even ALSA) but I never used them for that kind of purpose. Have you maybe tried VLC ? I think it can capture PCM data from other apps but again, it could be a misunderstanding from my part. All in all, if you can get jackd and oss2jack up and running correctly, it's a breeze to do what you want and much much more, like adding cool effects in the audio signal path before recording it (with jack-rack and the ladspa effects, or with VSTs and dssi-vst, etc). IF you're a newbie, it could be a real challenge to get these things running. Good luck :)

---

### Post by thorgal on 2008-07-23
someone was kind enough to detail an installation guide for oss2jack :

[http://ubuntuforums.org/showthread.php?t=867329](http://ubuntuforums.org/showthread.php?t=867329)

you can always try it and see if it suits your needs.

---

