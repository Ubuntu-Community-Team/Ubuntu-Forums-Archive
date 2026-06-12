---
title: "No sound from built-in speaker, but available on headset"
date: 2017-12-25
forum: Ubuntu/Debian BASED
---

### Post by vanronsenburg on 2017-12-25
Hello all, I'm new to Linux. I installed Elementary OS on my ASUS N43SL laptop, but I realized that it doesn't produce sound (except from headset). I am sure that that the sound wasn't muted (checked it with alsamixer and sound setting on GUI). 

I have tried reinstalling alsa-base and pulseaudio, with this command but it still doesn't produce sound:
```

sudo apt remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

```

I also tried to add this line to /etc/modprobe.d/alsa-base.conf but still doesn't work:
```
options snd-hda-intel model=auto
```

Here is the log of alsa-info.sh
[http://www.alsa-project.org/db/?f=6c489c1e34707d0d9c6921b51e475ec411e10c17](http://www.alsa-project.org/db/?f=6c489c1e34707d0d9c6921b51e475ec411e10c17)

I tried to fix it for several days, but still no result. Any help would be appreciated :)

---

### Post by vasa1 on 2017-12-25
Moved here since the OS is a Ubuntu derivative and not an official Ubuntu flavor.

---

