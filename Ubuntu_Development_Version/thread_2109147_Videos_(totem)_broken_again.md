---
title: "Videos (totem) broken again"
date: 2013-01-26
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-01-26
Certainly could be limited to some hardware/arch or overall.

The initial break was hardware/arch specific & affected more than totem, at least here was/is caused by pulseaudio/eglibc
[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1085342](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1085342)

After fixing here in libc6 Videos no longer becomes unresponsive but will consistently crash when adding or switching back & forth from audio files.
Less likely to happen with/when video files are in the playlist though eventually will
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937)

---

### Post by mc4man on 2013-03-11
fixed upstream, not yet in 13.04
so if these 2 are attended to then totem would be ok, grilo is likely not to happen soon (other than a ppa ver.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937)
[https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1132459](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1132459)

---

