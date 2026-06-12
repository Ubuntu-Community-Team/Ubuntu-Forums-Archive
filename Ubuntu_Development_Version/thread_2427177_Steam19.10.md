---
title: "Steam/19.10"
date: 2019-09-18
forum: Ubuntu Development Version
---

### Post by quantum802 on 2019-09-18
I'm wanting to upgrade to 19.10 early.  Is Steam functioning on Ubuntu 19.10 yet?

---

### Post by deadflowr on 2019-09-19
*Thread moved to **Ubuntu Development Version***
19.10 is still under active development.

---

### Post by P-I H on 2019-09-19
I use Steam on 19.10, installed as a flatpak. Performance and UI is as usual. I have only played CIV6 and Torchlite II.
To make them start you have to set this game launch-option: **LD_PRELOAD=/usr/lib64/libfreetype.so.6 %command%**
Information about how to enable flatpaks are found on [https://flathub.org/home](https://flathub.org/home).
When all steps are performed you may use Software to install Steam.
I also use flatpak versions of Kodi, VLC and Spotify.

Edit: I checked on my system instead of my instructions and the launch option is: **LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libfreetype.so.6 %command%**

---

