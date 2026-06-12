---
title: "Problem with Audacity and sound devices"
date: 2008-06-03
forum: Ubuntu Studio
---

### Post by mechaxl on 2008-06-03
Hello, I've been having a problem with Audacity while trying to record. If I have "Play other tracks while recording new one" enabled, I get an error message:

```
Error while opening sound device. Please check the input device settings and the project sample rate.
```

This is the error message that pops up in the terminal:

```
Expression 'ioctl( component->fd, SNDCTL_DSP_SETFRAGMENT, &frgmt )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1024
Expression 'PaOssStreamComponent_Configure( component, sampleRate, framesPerBuffer, StreamMode_Out, master )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1135
Expression 'PaOssStream_Configure( stream, sampleRate, framesPerBuffer, &inLatency, &outLatency )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1232

```

I am recording from /dev/dsp1 and playing on /dev/dsp. When I try both playing and recording on /dev/dsp1, nothing gets recorded. When I try both on /dev/dsp, Audacity freezes, and I get the second error message in the terminal again.

I just installed audiooss while trying to fix it, which did not help.

Anyone know what's wrong? thanks

---

### Post by ajgreeny on 2008-06-03
Try** ALSA: Sound card name** as your playback and recording device.  Mine works for mic recording but since I upgraded to hardy from gutsy, I've lost the other inputs, eg Line in, etc etc.  I assume this is a kernel problem, but it's a darn nuisance.

---

### Post by Stochastic on 2008-06-03
Audacity is one of the only apps that doesn't play nice with pulse audio, and now that Hardy has pulse audio as default, you need to launch audacity via ```
pasuspender -- audacity
``` to suspend pulse audio while audacity runs.

---

### Post by mechaxl on 2008-06-03
Thanks for the help.

I ended up fixing it by running this command from the terminal:

```
aoss audacity
```

I guess ALSA has a specific problem with the chip that's inside my delta 44 recording card.

---

### Post by Bungo Pony on 2008-06-04
You can also get Audacity to behave if you fire up Jack Audio Control. That's how I've been getting it to work for me.

---

### Post by rab4567 on 2008-06-05
I'm still in audacity hell.

---

