---
title: "Why 2 running windows opened by VirtualBox?"
date: 2011-05-21
forum: Virtualisation
---

### Post by Robbyx on 2011-05-21
How do I stop 2 windows opening when I run the winxp pro virtual machine via Virtual Box.

Host: Unbuntu 11.04
VB:4.0.8R71778


One window has the operating system in it, the other window is black. If I close the blacked out window, both windows close.

Any ideas how to stop the blank window opening?

Robin

---

### Post by Robbyx on 2011-05-22
There is the option to have 2 monitors running in the setup of VB. I have 2 so chose 2. Reducing it to 1 removed the blank window.

Although I have stopped the unnecessary blank window I do not understand why choosing 2 monitors should produce a second black window.

---

### Post by lmarmisa on 2011-05-22
> **Robbyx said:**
> There is the option to have 2 monitors running in the setup of VB. I have 2 so chose 2. Reducing it to 1 removed the blank window.

Although I have stopped the unnecessary blank window I do not understand why choosing 2 monitors should produce a second black window.

VirtualBox allows to define more than one virtual monitor. The behavior of the virtual monitors is very similar to the physical monitors. So, you have to configure them using System -> Preferences -> Monitors.

Do not forget to install the [VirtualBox GuestAdditions]("http://www.virtualbox.org/manual/ch04.html") if you want to use this feature.

---

### Post by Robbyx on 2011-05-22
Thank you for that very helpful reply.

Robin

---

