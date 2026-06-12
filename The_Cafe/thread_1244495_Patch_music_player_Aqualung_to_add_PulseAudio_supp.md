---
title: "Patch music player Aqualung to add PulseAudio support"
date: 2009-08-19
forum: The Cafe
---

### Post by PCMan on 2009-08-19
Several months ago, I just found a great music player very suitable for use with LXDE named Aqualung. It’s lightweight, written in pure C, gtk+2 only, desktop-independent, and feature-rich at the same time. The user interface is more or less similar to that of LXMusic, but it’s much more feature-complete. So, personally it’s my favorite player now. Here are some screenshots: [http://aqualung.factorial.hu/screenshots.html](http://aqualung.factorial.hu/screenshots.html)

However, it has a major drawback, not supporting pulse audio, which is widely used in modern distros today. In the latest release of Fedora or Ubuntu, even the ALSA emulation provided by PulseAudio cannot work correctly with Aqualung due to unknown reasons. So I haven’t use it for quite a long time due to this unresolved issue. Nevertheless, I still miss this great player. So, finally I do it myself.

I hacked the latest svn source code of Aqualung tonight, and then patch it to add PulseAudio support. Now it supports PulseAudio and work nicely under Ubuntu 9.04. I have sent the patch to the developers and hope it can be accepted and included soon.

For those who are interested, here is my patch: [http://people.linux.org.tw/~pcman/aqualung/](http://people.linux.org.tw/~pcman/aqualung/)

This patch is created against svn rev 1072 of Aqualung. PulseAudio support can be turned on with configure option –with-pulse. Cheers!

---

### Post by mrgnash on 2009-08-19
Great work! I'm a cmus user myself, but if I were to use a graphical music app this would probably be the one.

---

