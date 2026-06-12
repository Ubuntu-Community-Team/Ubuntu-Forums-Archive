---
title: "VLC And Non-Autenticated Pakages"
date: 2009-04-21
forum: Security
---

### Post by Nosophorus on 2009-04-21
Hi!

I have installed VLC through "sudo apt-get install vlc" and after listing all the extra packages I would need, I got a message saying that the following packages are not autenticated:

libavutil1d
libavcodec1d
libavformat1d
libpostproc1d

I am a little worried about security issues related to those packages and I would like to hear from you if there are any kind of problem I may have because of those packages. I am using Ubuntu 8.04 Hardy Heron.

Thank You!

---

### Post by oldos2er on 2009-04-21
You need to determine which repository contains those files, then download and install the public key for that repository.

---

