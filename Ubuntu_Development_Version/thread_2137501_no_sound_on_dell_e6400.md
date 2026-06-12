---
title: "no sound on dell e6400"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by duckydisciple on 2013-04-20
After I installed ubuntu 13.04 a few weeks ago I could hear sound (such as a youtube video), but the volume slider was grayed out and my volume buttons did nothing. I tried sudo apt-get update and sudo apt-get upgrade a few days ago to fix a different issue. It turns out that this changed my volume icon so that the slider and buttons worked. Unfortunately the sound no longer works from youtube, rhythmbox, or even the sound test within the sound settings. I have tried adding the ubuntu-audio-dev ppa and then running sudo apt-get update and sudo apt-get dist-upgrade, but that didn't change anything. Any ideas?

---

### Post by wgarcia on 2013-04-21
I have almost your same hardware (6410 in my case) and it is working fine. Have you tried the most basic things like the sliders in alsamixer and such?

---

### Post by duckydisciple on 2013-04-22
Yes, the slider has been put all the way up to the top. The alsamixer only shows 2 bars, master and PCM. Both are all the way up and unmuted.

---

