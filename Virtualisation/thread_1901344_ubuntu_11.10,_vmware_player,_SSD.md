---
title: "ubuntu 11.10, vmware player, SSD"
date: 2011-12-28
forum: Virtualisation
---

### Post by tekal on 2011-12-28
Hello,

im running "Ubuntu 11.10 32-bit" on "windows7 64-bit" with "vmware player".
"windows7" is already configured to work optimally with the "SSD".

How to configure the virtual "Ubuntu 11.10 32-bit" to also work optimally on the SSD?

or am i supposed to be the "Ueber-nerd" to confiure it? let me now please.


greetings
tekal

---

### Post by fjgaude on 2011-12-29
AFAIK, you don't do anything different than you would if on a platter HDD.

---

### Post by dcstar on 2012-01-11
> **fjgaude said:**
> AFAIK, you don't do anything different than you would if on a platter HDD.

Yep, a VM does not know (or care) about the host's physical hardware, a VM only knows of the Virtualized disk that is provided to it.

The host does **all** the work in regards to the physical devices connected to it.

---

