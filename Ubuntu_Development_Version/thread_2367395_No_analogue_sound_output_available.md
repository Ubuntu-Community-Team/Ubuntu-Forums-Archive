---
title: "No analogue sound output available"
date: 2017-07-29
forum: Ubuntu Development Version
---

### Post by cariboo on 2017-07-29
After being away for almost 2 weeks, I updated my Gnome shell install, and Now I don't have any analogue sound output. HDMI and Digital output (S/PDIF) work OK. I'm currently using the speakers on my Samsung 32" TV, but the sound quality isn't the greatest. I have a set of Logitech 2.1 analogue speakers that I would like to use instead. Has anyone else run into this?

```
Audio:     Card-1 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-26-generic

uname -a
Linux skynet 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Yellow Pasque on 2017-07-30
I would try resetting the pulseaudio config and restarting pulseaudio:
```
rm -rf ~/.config/pulse*
pulseaudio -k
```

If it still doesn't give analog output option, get more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

