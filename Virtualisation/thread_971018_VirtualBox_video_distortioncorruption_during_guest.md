---
title: "VirtualBox video distortion/corruption during guest install"
date: 2008-11-04
forum: Virtualisation
---

### Post by Rasputin_III on 2008-11-04
During the installation of a guest OS in virtualbox (and prior to the ability to install the guest additions) I have run into varying degrees of video distortion.

This has occurred when installing Windows 2000 Pro and Windows XP Pro (but it didn't seem to happen during the installation of Vista).  Because the corruption was relatively minor, I was able to complete the process and load the guest additions (which seemed to solve the problem).  Unfortunately, when installing Windows 95, the corruption is severe enough to prevent me from reading the error message halting the install.  I've attached a screenshot of what I'm talking about.

I've also been unable to find anyone else reporting a similar problem (with or without a resolution)--but it CAN'T be that I'm the only one with this combination of software/hardware or running into this.  I've tried tweaking various settings, but have found the pertinent options somewhat few in number.
Any ideas?

I am currently running the AMD64 version of Ubuntu 8.10 with all updates applied and a GeForce 8600M GT video chipset (with the restricted drivers activated).  This is happening in the synaptic provided version of VirtualBox OSE (2.0.4).  I also noticed it when running 8.04 (64-bit) with the latest Sun-provided version (probably 2.0.4 at the time).

Thanks,

Ras


[appended]  ----

Apparently something about the VT-x/AMD-V option causes the problem.  I tried tweaking a few other settings "just in case" and discovered that if I leave the VT-x/AMD-V unchecked (normally I enable it) while having all the other settings activated as I usually do--it works fine.  Go figure.

---

