---
title: "PanP9 issues after 64 bit 13.04 fresh install"
date: 2013-04-26
forum: System76 Support
---

### Post by bmbiehler on 2013-04-26
Some issues I have noticed after a fresh 13.04 install.

No sound, Sound settings show "Dummy Output"
Hangs during restart.  It will shutdown fine, but will hang every time during a restart.

I think I am going to try a fresh download of the ISO and try another fresh install.  Something may have got corrupted with all the traffic yesterday. i will update this thread as things develop.

---

### Post by isantop on 2013-04-26
Let us know how it runs after a new fresh install. That sounds like a likely cause to me.

---

### Post by bmbiehler on 2013-04-26
After the new download and install, everything is working perfectly. WOW 13.04 is quick!!!

---

### Post by screaminj3sus on 2013-04-29
I wouldn't be suprised if you start running into this issue again because it sounds like this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

at random during boot you can get either a kernel panic or the audio device won't be detected. When the audio devices isn't detected that causes the reboot hang.

---

