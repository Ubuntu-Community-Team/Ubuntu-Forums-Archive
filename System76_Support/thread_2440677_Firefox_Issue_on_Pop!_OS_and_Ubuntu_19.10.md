---
title: "Firefox Issue on Pop!_OS and Ubuntu 19.10"
date: 2020-04-13
forum: System76 Support
---

### Post by stephanie-s on 2020-04-13
I'm running Ubuntu 18.4 on my Galago Pro Laptop, with Firefox Quantum 68.7 installed.  Works great except that videos, and gifs don't play on all websites except You Tube.

The problem I'm having is with Pop!_OS 19.10 and Ubuntu 19.10.  Both OS's install Firefox 75 and both OS's have the same problem, in that neither will play videos or gifs.  However I installed Opera and it works perfectly, so I don't think it's an OS problem.

Any ideas?

---

### Post by EuclideanCoffee on 2020-04-14
Likely to do with your embedded content. This happens when I install Pop OS and try to browse Twitter.

Try this in your terminal:

```

$ sudo apt-get install ubuntu-restricted-extras

```

Restart and let us know if you have more problems or mark this as solved for others. Good luck.

---

### Post by stephanie-s on 2020-04-17
> **EuclideanCoffee said:**
> Likely to do with your embedded content. This happens when I install Pop OS and try to browse Twitter.

Try this in your terminal:

```

$ sudo apt-get install ubuntu-restricted-extras

```

Restart and let us know if you have more problems or mark this as solved for others. Good luck.

Thanks, I tried that but it didn't work.  I contacted System76 support and they gave me this and it worked.  

```
sudo apt-get update
sudo apt-get install ffmpeg gstreamer1.0-plugins-bad  gstreamer1.0-plugins-ugly gstreamer1.0-plugins-good libavcodec-extra  gstreamer1.0-libav chromium-codecs-ffmpeg-extra libdvd-pkg


```

---

