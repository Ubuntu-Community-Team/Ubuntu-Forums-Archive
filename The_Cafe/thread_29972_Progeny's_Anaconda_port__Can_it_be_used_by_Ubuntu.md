---
title: "Progeny's Anaconda port ? Can it be used by Ubuntu ?"
date: 2005-04-26
forum: The Cafe
---

### Post by idioteque on 2005-04-26
[I]Progeny had previously built its own Debian installer, PGI, which was derived from the original Progeny Debian installer. When Progeny's Platform Services began supporting Red Hat Linux, we were faced with the prospect of having to support two different installation technologies: PGI for Debian and Anaconda for Red Hat Linux. One goal of Anaconda for Debian is to lessen our support burden&#8212;rather than having to support two installers, we can support just one. Our APT project has similar objectives, but in the other direction&#8212;bringing best-of-breed technology from Debian to the Red Hat world.
Does Anaconda for Debian compete with debian-installer?

No, the goals of the two projects differ. Debian supports eleven architectures; of those, Progeny supports only IA-32 and IA-64, and a third Debian does not yet support, AMD-64. Debian supports only one distribution, and Progeny supports two (Debian and Red Hat Linux).

If anything, we view our Anaconda port as highly complementary to debian-installer. We hope it will be possible down the road to combine Anaconda with the debian-installer framework to allow Debian to be installed using the software that millions of Linux users already know. Meanwhile, our Anaconda port provides a familiar installation experience on the architecture in use by the majority of Linux users.[/I]

Is this an option for a better Ubuntu installer for the non-technical users ?

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=idioteque]

Is this an option for a better Ubuntu installer for the non-technical users ?[/QUOTE]

The ubuntu devs decided that it wasn't good enough after a lot of consideration. A home grown solution will be made sooner or later, and the installer is pretty easy to use now.

Its just not pretty.

EDIT: mods, please move this...

---

### Post by waspinator on 2008-02-13
> **poofyhairguy said:**
> A home grown solution will be made sooner or later, and the installer is pretty easy to use now. 

It's been 3 YEARS! Is a 'home grown' solution any closer in 2008? I know most people install ubuntu using the live CD, but It would be nice for the alternate cd installer to move into the 21st century.
I only ever use the alternate because its more flexible for installing the boot record. So if they  could add some support for that in the live cd then there wouldn't be a problem.

---

### Post by MethodOne on 2008-02-14
A better solution would be to use the graphical installer included with Debian Etch on the alternate CDs.

---

### Post by PryGuy on 2008-02-14
+1

---

### Post by az on 2008-02-14
A crazy idea would be to add whatever feature is missing to the live cd installer.

---

