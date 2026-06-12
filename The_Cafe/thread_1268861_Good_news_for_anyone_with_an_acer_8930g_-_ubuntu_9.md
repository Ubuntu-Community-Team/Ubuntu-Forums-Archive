---
title: "Good news for anyone with an acer 8930g - ubuntu 9.10"
date: 2009-09-17
forum: The Cafe
---

### Post by ade234uk on 2009-09-17
I just booted the live CD of Ubuntu 9.10 Alpha 5 and sounds works out of box.

---

### Post by sena_akada on 2009-09-17
what if youre deaf? does it cure that?

---

### Post by aaaantoine on 2009-09-17
What's the sound hardware for the 8930g?

---

### Post by ade234uk on 2009-09-17
If I have used the correct command lspci this is what I found in my list. So glad it picked this up on the live CD. 

**Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)**

And also the command lshw -c multimedia gave me

[B]description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=oss_hdaudio latency=0[/B]

---

