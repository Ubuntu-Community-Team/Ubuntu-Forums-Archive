---
title: "[SOLVED] 8.10 in VMware vista"
date: 2008-10-31
forum: Virtualisation
---

### Post by FreyD_EndZ on 2008-10-31
ok, only by force am I running a MS-POS(proprietary operating system). I need ms compatibility for online school.

I am running MS Vista Home-Pro 64bit on a XFX Nvidia 750a, with an AMD phenom x3 8400 (2.1GHz), 4GB Ram.  I need to use Xen client, which will not install on my system.  I figured I could use my fav Linux Distro, Ubuntu, in a VMware as my access point to my school's citrix server. Instead of using some pirated Winxp POS.

so I do as all the how-to's for vmware on windows states and set up a new virtual machine, set the HD at like 20GB, the ram at like 512 or so, and when I boot it, either using a disk or .iso image, I've tried multiple ways and versions, i386, and AMD64, Ubuntu 8.04, ubuntu 7.10, Ubuntu 8.10, but always seem to get the same msg.

> This kernel requires an x86 CPU, but only detected an i686 CPU.
Unable to boot-please use a kernel appropriate for your CPU.

The only thing I can think of is that I have an option for visualization in my bios and it is set to secure, should this be changed.  Is there anything I can do, or should I run a different distro all together? If so, the distro needs to support FireFox, as any other browser will not access this Citrix server.
:confused:

---

### Post by fjgaude on 2008-10-31
I would think it is the secure virtualization option in your BIOS that needs changing... Ubuntu is great with vm but I can't say anything about your 3x AMD.

---

### Post by FreyD_EndZ on 2008-11-05
sorry for the delay, I turned off the secure virtualization feature within my bios, still had no luck, I then decided to try virtual box, still no luck, both virtual servers give me the same output, "requires x86 CPU, detected i686..."


I then decided to try an older Inside Security, "INSERT" disk, which booted inside of virtual box with no problems or hesitations, my CLI is a little rusty, but I did get a kernel version of 2.18.6 on i686,

---

### Post by FreyD_EndZ on 2008-11-06
ok, solved my own problem somehow.  I downloaded a fresh intrepid 32 bit version, just for shiz & gigz, tried the install again on virtual box and low and behold, it worked.  installed the guest updates for VB (I am running the newest version as well), and am allowing ubuntu to update as we speak.

so maybe it is something to do with a 64bit guest on a 64bit host. also I will attempt to turn my bios virtualization back to enabled and let anyone know if it still works or not...

thanks

---

