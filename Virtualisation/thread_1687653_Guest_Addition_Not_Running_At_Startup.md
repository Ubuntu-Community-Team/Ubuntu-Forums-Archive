---
title: "Guest Addition Not Running At Startup"
date: 2011-02-14
forum: Virtualisation
---

### Post by yunring on 2011-02-14
I am running Ubuntu 10 latest with VirtualBox latest. Installation went fine.

When I try creating a shared folder, I find I had to install guest addon on every bootup for the mounting to work.

for example, if i type:

ting@Ubuntu:~$ sudo mount -t vboxsf ubuntu /home/ting/ubuntu

it would say:

.../mount.vboxsf: mounting failed with the error: Invalid argument

Now if I run the autorun.sh (from GUI and type in password), then it would run successfully and the mounting would work.

I tried reinstalling Guest Addon by running the autorun.sh script and everytime it would say removing old one and installed new one successfully.

any ideas would be appriciated.

---

### Post by Joeb454 on 2011-02-14
*Thread moved to **Virtualization**.*

Are you running VirtualBox-ose or the non-free VirtualBox?

---

### Post by yunring on 2011-02-14
> **Joeb454 said:**
> *Thread moved to **Virtualization**.*

Are you running VirtualBox-ose or the non-free VirtualBox?

ose free one.

---

