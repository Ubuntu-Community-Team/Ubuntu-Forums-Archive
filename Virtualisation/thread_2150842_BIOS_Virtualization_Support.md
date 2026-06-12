---
title: "BIOS Virtualization Support"
date: 2013-06-02
forum: Virtualisation
---

### Post by foberle on 2013-06-02
Hi:

I'm running Ubuntu 12.04 LTS and have Oracle VM Virtual Box 4.2.12 installed to allow me to run the few Windows programs I still haven't found reasonable substitutes for. Everything works just fine currently, but while wandering through my BIOS settings for something else, I came across a setting for Hardware Virtualization support - noting that it is currently turned off.

I was unable to find any documentation telling me what that does. Would turning that ON provide any benefits? Is it only intended for support of some additional hardware? Is it only for devoting the machine solely to Virtual Machines (which isn't at all what I want)?

In case it's relevant, I have a Gigabyte MA78LMT-S2 Motherboard with an AMD Athlon Athlon II X4 640 3.0 GHz Quad Core Processor (2 MB L2 Cache) and two Kingston KVR1333D3N9/4G 4GB DDR-3 DIMM Memory Units.

Is this BIOS setting worth looking into? Any advice would be appreciated.

Thanks.

---

### Post by ibjsb4 on 2013-06-02
If I remember correctly, it enables 3d acceleration.

---

### Post by Cheesemill on 2013-06-02
Enabling the option will increase the speed of your VM's as well as allowing you to install 64-bit guests.
[http://www.virtualbox.org/manual/ch10.html#hwvirt](http://www.virtualbox.org/manual/ch10.html#hwvirt)

If you have the option in your BIOS then turn it on, there is no reason not to.

---

### Post by foberle on 2013-06-02
Great - thanks for pointing me to this. I'll give it a shot.

---

