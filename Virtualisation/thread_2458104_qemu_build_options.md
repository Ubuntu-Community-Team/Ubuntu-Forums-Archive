---
title: "qemu build options"
date: 2021-02-16
forum: Virtualisation
---

### Post by rreddy78 on 2021-02-16
How can I know with what configuation options qemu on my system is built.
I run a custom Xubuntu 20.04 on the jetson-nano, an ARM64 bit SBC. 

I would like to build the latest qemu from sources with those and some additional options.

---

### Post by TheFu on 2021-02-16
My first question would be whether qemu provides any useful emulation on an ARM platform at all.  Typical ARM CPUs are 100x slower than very low end x86 CPUs.

Does the manpage say can be used as an option to report build settings? 
Does 
```
{program} --help
```
provide any insight?

Most source packages should include a debconf file which contains the settings to be used. If you have the source, that file should be there.

Ignore:
I've not seen too much expertise for ARM-based Ubuntu in these forums. May have better luck elsewhere. I have 3 ARM SBCs and 1 AMD SBC, but none of those use Ubuntu.  In my mind, Ubuntu is about having reasonably current GUI stuff, but not bleeding edge stuff and only selected "Debian Testing" programs.  For headless systems with limited RAM/CPU, I choose a lighter OS or purpose built distro.

---

### Post by deadflowr on 2021-02-16
*Thread moved to **Virtualization** *

You can read about qemu on arm here: [https://wiki.qemu.org/Documentation/Platforms/ARM]("https://wiki.qemu.org/Documentation/Platforms/ARM")

The configure file has a listing of all available options (it's located somewhere in the middle of the file)

---

