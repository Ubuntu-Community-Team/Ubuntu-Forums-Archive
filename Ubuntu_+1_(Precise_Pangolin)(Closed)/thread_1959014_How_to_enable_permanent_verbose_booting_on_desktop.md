---
title: "How to enable permanent verbose booting on desktop ubuntu?"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by georgelappies on 2012-04-15
how can I disable the silent boot. i.e. I want to see the messages running up the screen of the system booting until X kicks in?

---

### Post by dino99 on 2012-04-15
- set the bios to get it
- remove "quiet splash" from /etc/default/grub, then: sudo update-grub

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by xebian on 2012-04-15
Additionally you need to uncomment also the GRUB_TERMINAL=console for better terminal experience:p  Especially when your graphics card is not set properly - you see those garbage/unreadable chars on white background.

---

