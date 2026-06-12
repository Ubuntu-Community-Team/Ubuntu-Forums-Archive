---
title: "turn off HDMI audio on Galago UltraPro"
date: 2014-02-04
forum: System76 Support
---

### Post by bugi00 on 2014-02-04
HDMI audio is the first sound device on Galago UltraPro, according to "aplay -l".  Instead of fighting with the various subsystems' ideas of how to specify the audio device, I just turned it off:

```
su
echo 'options snd_hda_intel enable=0,1' >> /etc/modprobe.d/$(hostname).conf
reboot
```

(Or rather, I post here to save the next person the frustration of fighting with it instead of simply turning it off.)

---

