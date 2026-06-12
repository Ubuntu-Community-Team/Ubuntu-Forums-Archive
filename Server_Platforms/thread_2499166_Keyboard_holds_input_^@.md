---
title: "Keyboard holds input ^@"
date: 2024-07-16
forum: Server Platforms
---

### Post by exisss on 2024-07-16
After installing Ubuntu Server x64 for Raspberry Pi zero 2w I encountered a problem when connecting my keyboard. Apparently the keyboard constantly sends a key press that OS recognizes as '^@' and I have no idea why, as this does not happen on windows OS. Obviously no key is held, if do press a key, I just send 2 inputs: the key I pressed and ^@. The problem is only apparent with only this (Modecom volcano RGB) specific keyboard and I can't really use another one. Any ideas?

---

### Post by currentshaft on 2024-07-25
Try running "sudo dpkg-reconfigure keyboard-configuration" and see if it helps.

---

