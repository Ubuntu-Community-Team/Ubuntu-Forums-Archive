---
title: "Do you have sound with ALSA with Pluging several USB mics or devices at boot?"
date: 2010-07-27
forum: The Cafe
---

### Post by frenchn00b on 2010-07-27
Hello,

Try to plug USB mics at boot of your LINUX box, or USB webcam that have mic.

Usually ALSA recognized them for most reboot as first sound card.

This is annoying that no changes can be made to make LINUX have sound. We are in 2010 and visibly big issues are still existing under LINUX, such as Sound, come on man !

:popcorn::popcorn:

--
EDIT: By the way, PULSEAUDIO is a solution to something that is NOT working.

If possible, plz post the output of:
> cat /proc/asound/modules  

---

### Post by FuturePilot on 2010-07-27
Yes, my sound is perfectly fine and I have a USB webcam w/ mic.

---

### Post by frenchn00b on 2010-07-27
> **FuturePilot said:**
> Yes, my sound is perfectly fine and I have a USB webcam w/ mic.

could you paste your : ?
```
**cat /proc/asound/modules  **
```

---

### Post by FuturePilot on 2010-07-27
```
 0 snd_hda_intel
 1 snd_usb_audio
```

---

### Post by frenchn00b on 2010-07-27
> **FuturePilot said:**
> ```
 0 snd_hda_intel
 1 snd_usb_audio
```

Well, I can believe you do not have any problems.:D You have only 2 devices.
Look mine with lot of audio devices for music applications (well under Microsoft Windows, cuz LINUX is not mature enough for handling music hardwares)

```
# cat /proc/asound/modules  
 0 snd_hda_intel
 1 snd_usb_audio
 3 snd_usb_audio
 5 saa7134_alsa
 6 snd_emu10k1

```

---

### Post by Lucradia on 2010-07-27
Linux is not allowed to allow more than one hardware to use each type of audio stream, "Record" and "Play Back."

So if one audio hardware is taking up both playback and recording, none of the other devices can, this is how it should be; why do you want more than one device to use a stream?

---

