---
title: "Speaker muted despite sudo alsactl store"
date: 2012-01-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-01-08
OK, so this problem keeps cropping up for me in development versions, then somewhere towards the end of the cycle everything works properly (without me changing anything!). It's not critical as I simply have to run alsamixer and un-mute and raise the volume of my Speaker channel.

However, I want to know what causes this at the start of every cycle!

I've tried a '$ sudo alsactl store' once I've adjusted settings in alsamixer but it doesn't seem to have had any effect. What's a good next step?

---

### Post by sonicb00m on 2012-04-10
I added

```

amixer set "Speaker" unmute 100% > /dev/null

```

To my .bashrc file and it solved it for now.

---

### Post by jfernyhough on 2012-04-10
Nice.

---

