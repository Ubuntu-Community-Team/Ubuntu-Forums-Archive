---
title: "WSL pulseaudio help"
date: 2017-06-21
forum: Windows
---

### Post by roxas2 on 2017-06-21
i'm running windows 10 redstone 2
i'm trying to get pulseaudio working with windows subsystem for linux

i already tried google

it keeps on running into this error and i don't know how to solve it...

```

Roxas@DESKTOP-MM27SNA:/mnt/c/Users/Roxas$ pulseaudio
E: [pulseaudio] module-udev-detect.c: Failed to initialize monitor.
E: [pulseaudio] module.c: Failed to load module "module-udev-detect" (argument: ""): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

```


btw, did i post in the right catagory??

---

### Post by howefield on 2017-06-21
Thread moved to the "*Windows*" forum.

---

### Post by roxas2 on 2017-06-21
lol i actually got it working 1 hour later,

looks like i have to use the pulseaudio in the trusty repository.
it works now

looks like you don't need to run pulseaudio in bash, it just links to the windows pulseaudio server
i use this one: [https://github.com/kitor/wsl](https://github.com/kitor/wsl)

---

