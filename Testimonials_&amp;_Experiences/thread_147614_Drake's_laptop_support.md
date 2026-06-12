---
title: "Drake's laptop support"
date: 2006-03-20
forum: Testimonials &amp; Experiences
---

### Post by eurgain on 2006-03-20
Hi

I am completely blown away by the way that Drake supports "difficult" features on laptops.  This has led to me replacing SUSE10 on two "production" laptops with Drake, despite the present potential instability of the system.

I should say, that I think laptop "support" is not worthy of the name unless it provides the convenience of suspending (and suscessful resuming ;-) to and from RAM and DISC.

Machine 1 is a Dell I8600 "desktop replacement" with Pentium-M 1.5, NVidia graphics and a buggy BIOS.  This has multiple problems.  The NVidia graphics chip needs to be reset on resume, and X did not do this in the past.  With earlier distros, this meant major hacking of the ACPI event handlers to work at all.  Also, the original DSDT was badly broken, and needed to be replaced.

With Drake, all I did was compile a kernel with a revised DSDT, and suspend/resume just worked.

Machine 2 is a Dell Latitude X1, Pentium-M 1.1. This is a delightful little ultra-light machine, based on a Samsung.  It has only a 1.1GHz processor, but it never feels slow.

To get everyhinig working, all I did was install the 915resolution package and follow the instructions.  Installing the 686 kernel speeded things up.  Again, suspend and resume work as they should, unlike on SUSE10.

My only complaint is related, I think, to compiler optimisations.  I believe that Ubuntu is optimised for Pentium-4 but will also run on anything from a 386 onwards.  The Pentium-M (aka "Centrino") is basically a P3, with power-saving features.  I think therefore that Ubuntu is running in 386 mode on this processor, which means that it is not using many available optimisations.  I have found that setting DEBIAN_BUILDARCH to "pentium-m" and rebuilding xorg from source offers a major performance improvement.  Also, I do not know why the 686 kernel is not installed by default on these machines, but that is not an issue for me, bacause I always compile a custom kernel for every machine.

Great work, Ubuntu!
Regards
A

---

### Post by briancrutin on 2006-03-21
Nice Post!

I'm in college, and I couldn't agree more!

---

