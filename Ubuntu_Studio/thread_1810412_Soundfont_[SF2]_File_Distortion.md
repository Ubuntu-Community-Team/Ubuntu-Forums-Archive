---
title: "Soundfont [SF2] File Distortion"
date: 2011-07-23
forum: Ubuntu Studio
---

### Post by marseille on 2011-07-23
Hello Folks,

I've loaded up some soundfonts (I've used some of these in previous Ubuntu versions since they were recommended by Documentation) in Rosegarden via Fluidsynth and every last one of them are producing really hideous unwanted distortion. 

I went through my volume settings; I checked another application running with Jackd (IDJC); and I played a midi file with Totem without Jackd but for the life of me... I can't figure out what's causing the noise; and I've never seen this happen in previous Ubuntu OS/Rosegarden/Fluidsynth versions. Also, it seems to be Fluidsynth specific because ZynAddSubFX and Xsynth are producing quality sound output.

I'm currently running a 64bit UbuntuStudio Lucid 10.04 LTS and using Rosegarden v. 10.04.2 from a ppa suggested in a previous thread quite some time ago.


```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thank-you.

---

### Post by Pablo_F on 2011-07-23
Hi, 

There was a bug in fluidsynth. See [https://bugs.launchpad.net/ubuntu/+source/fluidsynth/+bug/659112](https://bugs.launchpad.net/ubuntu/+source/fluidsynth/+bug/659112)

---

### Post by marseille on 2011-07-23
Thank-you Pablo! You're my Ubuntu Hero of the Day! :guitar:

I read through the fluidsynth drama and now I'm freaking out because the latest release is for Natty and I can't remember how to do the SVN thing or even if I should... and just compile from source. I'm still on 10.04 LTS and don't want to leave the long-term-support, so I'm going to have to slow down for a hot minute and read some more or wait for you or another guru to chime in :popcorn:

---

### Post by Pablo_F on 2011-07-23
Hi, 

Please, confirm: Do you have the problem with fluidsynth-dssi (i.e., fluidsynth as a synth plugin in Rosegarden) or stand-alone fluidsynth or via qsynth?

What versions of fluidsynth and friends have you got? Do a:

dpkg -l  |grep fluidsynth

Cheers, Pablo

---

### Post by marseille on 2011-07-24
> Do you have the problem with fluidsynth-dssi (i.e., fluidsynth as a synth plugin in Rosegarden) or stand-alone fluidsynth or via qsynth?

Via Qsynth unknown. Confirmed problems, ie- same _[COLOR="Blue"][white noise]("https://bugs.launchpad.net/ubuntu/+source/fluidsynth/+bug/659112")[/COLOR]_ distortion in:
[LIST]
[*]Fluidsynth-DSSI stand-alone app
[*]Fluidsynth-DSSI Rosegarden plugin
[/LIST]

> What versions of fluidsynth and friends have you got? Do a:

```
dpkg -l |grep fluidsynth
```

```
$ dpkg -l |grep fluidsynth

ii  fluidsynth                            1.1.2-0ubuntu0+ppa3                                         Real-time MIDI software synthesizer
ii  fluidsynth-dssi                       1.0.0-lucid~ppa1                                            DSSI wrapper for the FluidSynth SoundFont-playing softwar
ii  libfluidsynth1                        1.1.2-0ubuntu0+ppa3                                         Real-time MIDI software synthesizer (runtime library)
ii  qsynth                                0.3.5-0ubuntu0+ppa4                                         fluidsynth MIDI sound synthesiser front-end

```

---

### Post by Pablo_F on 2011-07-24
Hi, 

You can try several workarounds:

1) Install calf plugins and use calf fluidsynth dssi.
2) Downgrade fluidsynth, libfluidsynth and fluidsynth-dssi to the original versions in lucid's repos.
3) Do as suggested in comment #17 in the bug report.

I recommend you should try 1) and 2) first. 3) only as a last resort.

For the second option, you can use synaptic package manager. Select a package, go to the menu: Package -> Force version... 

Cheers, Pablo

---

### Post by marseille on 2011-07-26
Thank-you again, Pablo :guitar:

I downgraded and everything is working fine.

---

