---
title: "install on qemu"
date: 2020-07-19
forum: Virtualisation
---

### Post by mcyber4 on 2020-07-19
HI
did:
C:\Program Files\qemu>qemu-system-x86_64.exe C:\Users\Michael\Downloads\ubuntu-20.04-desktop-amd64.iso
what hangs with flashing bar.
How to install 20.04 with accelerated 3d opengl? I need to test a 3D app.
Thanks

---

### Post by deadflowr on 2020-07-19
Normally you'd probably need the virgl packages and double check that the version of qemu in use is built to support virgl.
But you're not using a normal version.
Exactly how are you using it?
What system is in use as the host?
It's easy to see it's not Ubuntu.

---

### Post by mcyber4 on 2020-07-19
Sounds good. Could you give me a link with 3D acceleration? I'm on Windows 10/Nvidia to install 20.04. Never tried that before, only virtualbox some years ago.
Thanks

---

