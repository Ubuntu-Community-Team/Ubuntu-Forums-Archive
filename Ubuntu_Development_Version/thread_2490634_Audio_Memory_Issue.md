---
title: "Audio Memory Issue"
date: 2023-09-10
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2023-09-10
I've been testing Ubuntu and Xubuntu 23.10 for some time now and am surprised to see that the pipewire audio system uses such a large amount of memory:

- pipewire (16mb)
- pipewire -c filter-chain.conf (5.2mb)
- pipewire-pulse (10.1mb)
- wireplumber (31.1mb)

Is it necessary to use around 61.4mb just to play audio on a system ?

---

