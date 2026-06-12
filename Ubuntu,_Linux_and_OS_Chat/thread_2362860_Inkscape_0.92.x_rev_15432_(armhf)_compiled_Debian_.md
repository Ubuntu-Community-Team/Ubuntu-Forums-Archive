---
title: "Inkscape 0.92.x rev 15432 (armhf) compiled Debian Package here."
date: 2017-06-02
forum: Ubuntu, Linux and OS Chat
---

### Post by wulgulmerang on 2017-06-02
Dear Ubuntu,

Maren on Launchpad helped me to compile Inkscape 0.92.x rev 15432 on armhf and it runs much faster than 0.48 (the currently available package).

I have the Debian package created by checkinstall here: [https://www.dropbox.com/s/6i6mev8fc7hrd2h/inkscape_20170527-1_armhf.deb?dl=0](https://www.dropbox.com/s/6i6mev8fc7hrd2h/inkscape_20170527-1_armhf.deb?dl=0) but I don't know how to make this available for all armhf users on 14.04.5 LTS?

Best Wishes, David.

---

### Post by QIII on 2017-06-02
Hello!

You do understand that we are naught but poor Ubuntu users such as yourself and are not employed by Canonical, right?

You can create an account on launchpad.net and then create a PPA (Personal Package Archive) for distributing your package.  Is it compiled against a specific Ubuntu port (HardKernel, RPi, etc) or would it be suitable for any ARM port?  32 or 64 bit -- since there are 64 bit ARM processors?

You might look in to GitHub, etc.

(Moved to Ubuntu, Linux and OS Chat since it is not a request for support with Ubuntu per se.)

---

### Post by wulgulmerang on 2017-06-03
Hi, 
Thanks for getting back.
It was compiled on a 32 bit armhf platform (Tegra K1), I'm not sure about the specific Ubuntu port or how to find these details?
I'll look into GitHub etcetera.

---

### Post by QIII on 2017-06-03
Hello!

As to the port, where did you get the image for what you are running?  The specific architecture of the processor might be important.

In all likelihood things will be just fine for any hardware/port. 

But it might be worth just a bit more work to test the compiled version in other environments before releasing.  It would be disappointing for you and others if something you expected to "just work" didn't.  Trust me!  ;)

---

### Post by wulgulmerang on 2017-06-07
Hi, apologies for the late reply.

uname -a displays: 
"Linux humus 3.10.18 #1 SMP Mon Sep 26 14:28:25 PDT 2016 armv7l armv7l armv7l GNU/Linux"

lsb_release -a displays:
"No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty"

cat /proc/cpuinfo displays:
"processor    : 0
model name    : ARMv7 Processor rev 3 (v7l)
BogoMIPS    : 17.34
Features    : swp half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae 
CPU implementer    : 0x41
CPU architecture: 7
CPU variant    : 0x3
CPU part    : 0xc0f
CPU revision    : 3

processor    : 1
model name    : ARMv7 Processor rev 3 (v7l)
BogoMIPS    : 17.34
Features    : swp half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae 
CPU implementer    : 0x41
CPU architecture: 7
CPU variant    : 0x3
CPU part    : 0xc0f
CPU revision    : 3

processor    : 2
model name    : ARMv7 Processor rev 3 (v7l)
BogoMIPS    : 17.34
Features    : swp half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae 
CPU implementer    : 0x41
CPU architecture: 7
CPU variant    : 0x3
CPU part    : 0xc0f
CPU revision    : 3

processor    : 3
model name    : ARMv7 Processor rev 3 (v7l)
BogoMIPS    : 17.34
Features    : swp half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae 
CPU implementer    : 0x41
CPU architecture: 7
CPU variant    : 0x3
CPU part    : 0xc0f
CPU revision    : 3

Hardware    : NVIDIA Tegra SoC (Flattened Device Tree)
Revision    : 0000
Serial        : 000000000000000"

[B]Is  anybody reading this who has a armhf (ARMv7) 32-bit processor who could  attempt to install Inkscape 0.92.x rev 15432 on Ubuntu 14.0.5 LTS using  the Debian package link above and report back?

[/B]Thanks,
David.

---

