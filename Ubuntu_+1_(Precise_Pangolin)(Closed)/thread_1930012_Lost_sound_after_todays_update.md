---
title: "Lost sound after todays update"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by brownknight on 2012-02-22
After todays update, I lost sound in my computer. Tried banshee, audacious, rythmbox and even youtube from firefox and no sound. Although, the drum sound works when the system first starts up and you need to log-in. After that no sound.

---

### Post by brownknight on 2012-02-23
This fix worked for me from launchpad:

rm -rf ~/.pulse*

(this command removes my personal pulseaudio config files. after that i logged out and logged back in)

Thank you Dave Lentz

---

