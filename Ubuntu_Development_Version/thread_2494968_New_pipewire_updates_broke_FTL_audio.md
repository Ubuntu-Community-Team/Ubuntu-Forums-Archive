---
title: "New pipewire updates broke FTL audio"
date: 2024-02-02
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2024-02-02
Using native linux FTL through steam, worked fine until yesterday.
Today pipewire updates broke audio on FTL:
```
Starting audio library...
Failed to open sound device
```
Sound devices show as normal, and work fine in native steam games and in proton games.
Any idea for investigation?

---

### Post by Wise Ferret on 2024-02-02
I think this might be related to a new [pipewire issue]("https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/3830"). A patch was committed, and I hope we see it here soon.

---

