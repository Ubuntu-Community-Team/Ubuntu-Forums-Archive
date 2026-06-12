---
title: "Ubuntu dock: the background color does not cover the edges"
date: 2024-04-14
forum: Ubuntu Development Version
---

### Post by hectorsales on 2024-04-14
The ubuntu dock maintained by canonical the background color does not cover the edges. The original extension no have this issue because not add a css border.

---

### Post by hectorsales on 2024-04-14
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/2061287](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/2061287)

---

### Post by corradoventu on 2024-04-14
I'm unable to reproduce your problem, but I don't have an Nvidia gpu.
I think you should add that you have nvidia gpu

---

### Post by hectorsales on 2024-04-14
> **corradoventu said:**
> I'm unable to reproduce your problem, but I don't have an Nvidia gpu.
I think you should add that you have nvidia gpu

I try in another machine with only amdgpu and same behavior with xorg session and wayland session. Attached

---

### Post by hectorsales on 2024-04-15
Disable the extension 'blur my shell' the ubuntu dock now works fine!

---

