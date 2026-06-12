---
title: "random hard crash freeze"
date: 2014-02-04
forum: Ubuntu Studio
---

### Post by tlwest on 2014-02-04
There seems to be a number of people who are having random problems - I and my daughter are some of them. The symproms are a hard freeze - no mouse, no ctrl-alt-Fx console, can't ping the machine or SSH in. The only recovery is to power-off/reset, which doesn't do anything positive for HDD integrity. There is the distinct posibbility that we are the few dozen people on the planet who have failing/degrading hardware, or that we are tickling a difficult bug - there doesn't seem to be a specific trigger. Sometimes the machine freezes while I'm working, sometimes I come back to it after a break and find it frozen. There are NO log entries that provide any information - ususally just the last hourly crontab entry. 

Anybody willing to help me work through a process to try to identify whether this is a hardware problem or a software bug?

My system info as provided by I-nex:

HP GN706AA-ABA a6242n
AMD Athlon 64 X2 
Mobo ECS Nettle2
Chipset AMD K8 IMC ECC disabled
BIOS Phoenix 5.20
memory 3G DDR2 128 bit 
memtest86+ reports setting: 358 Mhz (DDR717) CAS: 5-5-5-15
GPU NVIDIA C61 GeForce 6150SE nforce 430/Integrated/SSE2
Kernel driver in use: nvidia
resolution 1920x1080
Disk WD WD5000AADS-6
Ubunto Studio 13.10, xfce4, lightdm
kernel 3.11.0-15-lowlatency
network NVIDIA MCP61 Ethernet
Currently using Dell PS2 mouse and keyboard
lightdm and xfce4

Primary use of the machine is audio mixing and video editing - using Ardour, Openshot, and Jamin

I've just finished an 18 hour run of memtest86+ v4.20: 14 test cycles with 0 errors.

The machine has separate partitions containing Ubuntu-Studio 13.10, Ubuntu-Studio 12.04 LTS, Debian Wheezy, and Arch - all are current with updates. Arch is running VESA drivers 'cause I haven't got Xorg working well enough to find the right drivers, everything else is on Xorg and whatever driver it auto-configures - looks like "nvidia" from the Xorg log. All of these distributions have the freeze problem to some degree - Arch with the VESA driver is somewhat more stable but still freezes once a week of so. 

Suggestions?

---

### Post by tlwest on 2014-02-07
An update - I listed PS2 mouse and keyboard in the hardware config - that seems to be the STABLE configuration! I've been running several days now with no crashes. So it's looking like it might be the USB keyboard or wireless mouse that are the problem. I'll give this a week, and if it is still stable I will start adding the USB/wireless peripherals back in one at a time to see what is REALLY causing the problem.

UPDATE- false confidence - while the PS2 hardware is marginally more stable, ther are still hard freezes

---

### Post by tlwest on 2014-03-10
I'm marking this solved - While the system was more stable using the PS2 hardware than it was using USB, there were still hard crash problems. I built a new computer re-using the same disk drives that I had in the computer that had the hard freeze problem, using USB keyboard and wireless mouse with no problems - all seems well now. Still wish there was a better methodology for isolating hardware problems from software problems.

---

