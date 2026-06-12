---
title: "Turn Bluetooth off until needed?"
date: 2023-01-05
forum: Ubuntu/Debian BASED
---

### Post by Trent_Isaacson on 2023-01-05
Hey all, is there an easy way to keep Bluetooth turned off until I turn it on? I've noticed Pop!_OS has an easy way to disable BT, but on next boot it's enabled again, which is frustrating. If there's a way to keep this toggled off I'd appreciate learning about it!

---

### Post by howefield on 2023-01-05
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by #&amp;thj^% on 2023-01-05
```
systemctl disable bluetooth
```
that disables it on start-up
```
systemctl start --now bluetooth
```
starts it only for the session

---

