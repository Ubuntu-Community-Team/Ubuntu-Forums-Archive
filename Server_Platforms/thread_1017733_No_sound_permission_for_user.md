---
title: "No sound permission for user"
date: 2008-12-21
forum: Server Platforms
---

### Post by hardysummer on 2008-12-21
Installed alsa.  But there is no sound for user nor can user access alsamixer.  I found out that user have no permission in /dev/snd/*.  Fixed it, but the problem resets after each reboot.

How do I solve this?

---

### Post by bluefrog on 2008-12-21
add them to the audio group. what are users doing on a server with sound by the way?

---

### Post by hardysummer on 2008-12-21
Thanks.

Actually, it is for myself. Just wanted to hear something else than spinning fans and hard drive as I do stuff. Playing audio as root just does not seem right.

---

