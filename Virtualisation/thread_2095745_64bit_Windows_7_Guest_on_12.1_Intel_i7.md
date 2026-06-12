---
title: "64bit Windows 7 Guest on 12.1 Intel i7"
date: 2012-12-17
forum: Virtualisation
---

### Post by gwilym on 2012-12-17
Hi,

I have VirtualBox on 64bit Ubuntu 12.1 running on a Lenovo x220 with i7-2640M 1.8ghz x 4.

I am trying to install a Windows 7 64bit guest from an .iso (I have a legitimate license that came with the machine I'd like to get virtual) but get an error as Windows is trying to start.

[B]Status: 0xc000035a
Info: Attempting to load a 64-bit application, however this CPU is not compatible with 64-bit mode[/B]

In Virtualbox VT-x is enabled and when I run "grep --color vmx /proc/cpuinfo" from the shell I get red VMX's highlighted I guess showing that side of things is ok.

Any ideas much appreciated.

---

### Post by gwilym on 2012-12-18
Figured this one out - I thought I had read somewhere that with a 64bit host OS it wasn't necessary to turn anything on in BIOS - anyway, I went and checked, turned on the virtualisation features and presto - all good :-)

---

