---
title: "LemU2 heats up ~10 °F playing audio"
date: 2012-12-09
forum: System76 Support
---

### Post by Geremia on 2012-12-09
My LemU2's internal temp increases ~10 °F and fan runs at higher speed whenever I play audio, although the CPU usage is very low. I think it might have something to do with my having a wrong video card driver (cf. [this thread]("http://www.linuxquestions.org/questions/linux-software-2/cpu-fan-runs-when-playing-audio-4175436307/")). It's annoying hearing the fan screaming when I'm trying to listen to my audio. Thanks

Here's my LemU2 info:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: CLEVO/KAPOK Computer Device 3100
        Kernel driver in use: snd_hda_intel

``````
Linux alan 3.2.29 #1 SMP Mon Sep 17 13:38:05 CDT 2012 x86_64 Intel(R) Core(TM) i3 CPU       U 330  @ 1.20GHz GenuineIntel GNU/Linux
```Video card and driver:```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
        Subsystem: CLEVO/KAPOK Computer Device 3100
        Kernel driver in use: i915
```I use KDE and have tried different Phonon backends, too, but the same problem occurs, so perhaps it is a hardware issue. (The same problem occurs even when using XFCE instead of KDE.) I've also heard that ALSA emulates; is that true?

Thanks for the help

---

### Post by joe4ska on 2012-12-10
Is it all audio or a specific application? I see about a 5 degree increase running Cinnamon and Pithos in Ubuntu. (with firefox in the background) from 49-56 depending on the CPU core.

I'd suggest  
# apt-get install lm-sensors
type sensors in terminal and get some temp readings. Could be the file format or some other related background package is boosting the temp. MP3, Ogg Vorbis etc.

---

### Post by Geremia on 2012-12-10
> **joe4ska said:**
> Is it all audio or a specific application?All audio> **joe4ska said:**
> I see about a 5 degree increase running Cinnamon and Pithos in Ubuntu. (with firefox in the background) from 49-56 depending on the CPU core.

I'd suggest  
# apt-get install lm-sensors
type sensors in terminal and get some temp readings. Could be the file format or some other related background package is boosting the temp.Are you using ALSA, too?> **joe4ska said:**
> MP3, Ogg Vorbis etc.I thought it was a codec issue, too, but I get the same ~10 °F heat-up with increased fan RPMs regardless what type of audio I play, even if I play uncompressed audio.

Thanks for the help

---

### Post by isantop on 2012-12-10
You defintely don't have the wrong video driver, please don't attempt to replace it!

Now that that is out of the way, what is the overall temperature before and while playing?

---

### Post by Geremia on 2012-12-10
> **isantop said:**
> what is the overall temperature before and while playing?I'm not sure if my sensor is calibrated correctly, but my internal temp reads ~140 °F, and it increases to ~150 °F when playing audio, which kicks the fan into a higher speed. When not playing audio, my fan in generally on low speed. When I stop playing audio, the temperature and fan speed go down almost immediately, and when I start playing audio, they take a bit longer to go up.

Also, it never used to do this when I first got my Lemu2, so perhaps it is a software issue.

Thanks

---

### Post by isantop on 2012-12-12
> **Geremia said:**
> I'm not sure if my sensor is calibrated correctly, but my internal temp reads ~140 °F, and it increases to ~150 °F when playing audio, which kicks the fan into a higher speed. When not playing audio, my fan in generally on low speed. When I stop playing audio, the temperature and fan speed go down almost immediately, and when I start playing audio, they take a bit longer to go up.

Also, it never used to do this when I first got my Lemu2, so perhaps it is a software issue.

Thanks

That's very warm for idle temps. Can you blow an air duster through the vents/fan to ensure that they aren't blocked?

---

### Post by Geremia on 2012-12-12
> **isantop said:**
> That's very warm for idle temps.Which is why I think it's not calibrated accurately. It doesn't feel very warm. Perhaps a bad sensor is tricking it into thinking it's warmer than it really is? Is that possible? Regardless, relative temperatures should be accurate (i.e., that it's a ~10 °F heat-up).

I'll trying blowing it out again and see if that helps.

---

### Post by pqwoerituytrueiwoq on 2012-12-12
are you able to look up the temp in the bios?

---

### Post by isantop on 2012-12-13
> **Geremia said:**
> Which is why I think it's not calibrated accurately. It doesn't feel very warm. Perhaps a bad sensor is tricking it into thinking it's warmer than it really is? Is that possible? Regardless, relative temperatures should be accurate (i.e., that it's a ~10 °F heat-up).

I'll trying blowing it out again and see if that helps.

The sensors don't have calibration. The way the system is designed, it won't feel hot on the bottom until it's overheating. While warm, your temps aren't critical.

That said, poor cooling can increase temperature deltas between certain task.

---

