---
title: "choppy sound"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by lucazade on 2013-02-24
Opened a bug report for a choppy sound playback
There are a lot of rewind, the buffer seems full.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1132562](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1132562)

This happens with an Intel HDA soundcard.

---

### Post by lucazade on 2013-02-24
this temporary fixes the problem:
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

### Post by bettlebrox on 2013-02-25
> **lucazade said:**
> this temporary fixes the problem:
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

Thanks, that worked on my Lenovo T400 with a "Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)". :)

---

### Post by dino99 on 2013-02-25
Luca, bug need confirmation before proposing a patch, please set your comment to David asap

---

### Post by lucazade on 2013-02-25
> **dino99 said:**
> Luca, bug need confirmation before proposing a patch, please set your comment to David asap

Posted details ;)

---

