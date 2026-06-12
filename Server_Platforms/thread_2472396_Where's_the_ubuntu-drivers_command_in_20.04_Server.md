---
title: "Where's the ubuntu-drivers command in 20.04 Server?"
date: 2022-02-25
forum: Server Platforms
---

### Post by 98cwitr on 2022-02-25
Have build-essential installed, just want to make sure I have all the latest as far as drivers, but the command doesn't work.

>sudo: ubuntu-drivers: command not found

---

### Post by 98cwitr on 2022-02-25
duh

>sudo apt install ubuntu-drivers-common

---

### Post by TheFu on 2022-02-25
```
sudo apt install ubuntu-drivers-common
```

It is mainly for GPU drivers and server installs don't have GPU dependencies. On a Ryzen system here, only nvidia GPU-related drivers are listed.
On a different Ryzen with AMD iGPU/APU here, no drivers are listed.

---

### Post by MAFoElffen on 2022-02-26
To expand on that answer--

You are running Server Edition, which is console based. In console, there is nothing beyond basic console graphics. The Linux Graphics Layer is not even there, just TTY sessions. No third party graphics drivers needed, because there is no Display Server there for it to interact with...

ubuntu-drivers-common, which includes the utility ubuntu-drivers, tests hardware and recommends and/or installs third party graphics drivers for Desktop Edition, where you are using the Linux Grahics layer, of a Display Server, with Graphics Drivers, a Desktop Manager , and a Desktop Environment.

So installing that package and utility is not going to be of any use for what you are running.

---

