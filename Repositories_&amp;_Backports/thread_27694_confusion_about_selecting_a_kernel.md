---
title: "confusion about selecting a kernel"
date: 2005-04-17
forum: Repositories &amp; Backports
---

### Post by kcy29581 on 2005-04-17
Hi all,

I'm a bit confused when choosing a kernel in Ubuntu. There are a few choices where the respective descriptions are very similar.

I know what linux-image-686 does. It finds the latest kernel for 686, already configured and compiled and working for the system.

I would like some info on the respective packages available via synaptic:
linux-686
linux-headers-686
linux-restricted-modules-686

I would like to know all their differences, and usage. I will need to install ndiswrapper at some point and if I remember correctly I need the linux-headers package for it to work properly. I just need verification that I'm thinking correctly!

I think linux-686 is the kernel sources only, but I'm not sure.

I have no idea what the linux-restricted-modules package is for!

Thanks.

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=kcy29581]Hi all,

I'm a bit confused when choosing a kernel in Ubuntu. There are a few choices where the respective descriptions are very similar.

I know what linux-image-686 does. It finds the latest kernel for 686, already configured and compiled and working for the system.

I would like some info on the respective packages available via synaptic:
linux-686
linux-headers-686
linux-restricted-modules-686

I would like to know all their differences, and usage. I will need to install ndiswrapper at some point and if I remember correctly I need the linux-headers package for it to work properly. I just need verification that I'm thinking correctly!

I think linux-686 is the kernel sources only, but I'm not sure.

I have no idea what the linux-restricted-modules package is for!

Thanks.[/QUOTE]
 if you have a 686 class machine you should install the package linux-686 this is a metapackage that makes sure you have always the latest 686 kernel including restricted modules.

install linux-686-headers will always install the latest headers

I have never used ndiswrapper so I don't know anything about it

---

### Post by kcy29581 on 2005-04-17
Thanks for the reply but do you know what the resticted modules are? What are they used for?

The same question goes for the headers. Who needs them and why?

Thanks

---

### Post by mendicant on 2005-04-17
From their descriptions (aptitude show <package name>):

linux-686:
```

 This package will always depend on the latest complete Linux kernel available
 for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
```
It's just a convenience thing to get the latest (supported) kernel.

linux-headers-686
```
This package will always depend on the latest kernel headers available for
 Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.

```
Again, a convenience thing to pull in the headers (for compiling 3rd party modules, for instance).

linux-restricted-modules-686

```
This package will always depend on the latest restricted modules available for
 Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
```

It currently depends on linux-restricted-modules-2.6.10-5-686, which contains:
```
Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV
 This package provides restricted modules for Linux version 2.6.10 on Pentium
 Pro/Celeron/Pentium II/Pentium III/Pentium IV. Currently the following modules
 are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusba, fcpci,
   fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

 These modules are "restricted" because they are not available under a
 completely Free licence.

```

> 
I think linux-686 is the kernel sources only, but I'm not sure.

No, that's linux-source-2.6.x

---

### Post by kcy29581 on 2005-04-17
D'oh! I only read the description for the linux-restricted-modules-686! Thanks.

Thanks for verifying about the headers. That explains alot. I knew the headers were created after compiling a kernel, but not what they were for.

Thanks for the replies.

---

