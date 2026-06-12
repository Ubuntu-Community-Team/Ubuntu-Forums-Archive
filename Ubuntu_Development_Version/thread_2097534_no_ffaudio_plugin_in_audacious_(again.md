---
title: "no ffaudio plugin in audacious (again"
date: 2012-12-23
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-12-23
While this may be a self healing bug if libav in 13.04 goes to a new major or even minor version & aud is re-built there is the possibility it won't happen. 
(11.10 aud released without the ffaudio plugin & never got it afterwards.

Aud bases off of the real ffmpeg not libav so that can occasionally cause issue.
In this case it would have (& can be), fine if the maintainer had paid the slightest attention to the raring  buildlog. It could/can be fixed with a simple 2 char edit. But like a number of sources, particularly multimedia, not much attention is paid - if the build succeeds then good enough.
[https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/1080059](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/1080059)

---

### Post by andrew.46 on 2012-12-25
Early days yet I guess but have they also missed the audacious 3.3.3 release?

---

### Post by ronacc on 2012-12-25
just for grins I pulled the git of ffmpeg and built it against my amd64 install , threw a few warnings but nothing too scary , built and installed ok .
```
ron@ron-desktop2:~$ ffmpeg version
ffmpeg version N-48193-g1be8d0f Copyright (c) 2000-2012 the FFmpeg developers
  built on Dec 25 2012 08:58:33 with gcc 4.7 (Ubuntu/Linaro 4.7.2-16ubuntu1)
  configuration: 
  libavutil      52. 12.100 / 52. 12.100
  libavcodec     54. 81.100 / 54. 81.100
  libavformat    54. 50.102 / 54. 50.102
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 30.101 /  3. 30.101
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
[NULL @ 0x349a500] Unable to find a suitable output format for 'version'
version: Invalid argument
ron@ron-desktop2:~$ 

```

---

### Post by andrew.46 on 2012-12-25
Just had a proper look on my Raring VM, a much more fully featured set of plugins than my own build on slackware but of course missing the very useful ffaudio plugin :(. Now to chase up those extra plugins for my own build....

---

### Post by mc4man on 2012-12-25
> **andrew.46 said:**
> Early days yet I guess but have they also missed the audacious 3.3.3 release?
Maybe if/when that happens libav will be a higher version & the plugin will be built without anyone particularly caring one way or the other.

OT - 
here for self use build the 3.3 or git off of FFmpeg. Though recently (12.10/13/04) have not been able to statically link on 64 bit, always get a reallocation error.
Have you had any luck there, if tried?

Gotten around by building a decoding FFmpeg  as shared to /opt, then building aud in /opt also.

---

### Post by andrew.46 on 2012-12-25
I only really build audacious on Slackware and I use the git FFmpeg shared installation only...

---

### Post by mc4man on 2012-12-25
> **andrew.46 said:**
> I only really build audacious on Slackware and I use the git FFmpeg shared installation only...
shared does seem the best way & a FFmpeg shared in /opt doesn't 'interfere' with the default whatevers.

(at the end of the day a FFmpeg ffaudio plugin only extends the plugin a bit, wmal & maybe opus, never checked the repo aud for opus support.. but still will go with FFmpeg here whenever possible.

edit: far OT - am going to check out "Decay", dl'ing now.

---

### Post by andrew.46 on 2012-12-25
> **mc4man said:**
> edit: far OT - am going to check out "Decay", dl'ing now.

Further OT: A budget of $3,255, a PhD physics student as director, the Hadron accelerator as a setting + zombies...... what more would you need :)

---

### Post by ronacc on 2012-12-25
an approaching asteroid ?

---

### Post by mc4man on 2013-02-13
new audacious/plugins release (3.3.4) - SSDD

---

