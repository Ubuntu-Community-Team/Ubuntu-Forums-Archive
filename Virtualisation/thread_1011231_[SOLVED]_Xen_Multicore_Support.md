---
title: "[SOLVED] Xen Multicore Support"
date: 2008-12-14
forum: Virtualisation
---

### Post by HOLOGRAPHICpizza on 2008-12-14
If I were to install Xen on my machine with an Intel Core 2 Quad with VT extensions enabled, would a guest OS inside Xen see the exact same processor? Like, would it actually recognize and use all 4 cores, and would it be able to use SSE2 instructions and such? Or would it see it as some strange virtualized CPU?

And also, can it natively use the video card? Like could I install the actual Nvidia drives, or would it also be virtualised as some strange video card?

If Xen can't do this, does anyone know of a program that can?

---

### Post by bodhi.zazen on 2008-12-14
I do not know about XEN, Xen has always been more popular on Fedora, so you may want to check with the Fedora forums.

Xen is falling out of favor, even with Fedora.

At any rate, I am not sure if you are understanding virtualization. With virtualization technology the hardware is all emulated. This includes a hard drive, a network card, a video card, a sound card, etc. Guests in general do not directly use your hardware.

I do not know of any virtualization that will use your nvidia card directly.

---

### Post by PilotJLR on 2008-12-14
Xen supports vSMP, so you can present 2 or 4 logical processors (cores) to a guest.

CPU feature codes will also be visible to the guest, as most hypervisors don't fully virtualize the CPU; rather, they schedule guest access to it, like any other process.

Features like SSE2 and SSSE3 can be problematic in live migrations, precisely because these features are visible to a guest. In the recent past, doing a live migrate from a new CPU (for example, with SSSE3) to an older one without that feature code would cause the guest to crash. Intel and AMD are now shipping chips with FlexMigration, which will allow you to mask these feature codes to the guest and ensure a wider range of live migration flexibility.

Just one more thing... let's say you have a single quad CPU in the host. To present the whole CPU to the guest, you need to present 4 logical processors. The guest will perceive this to basically be 4 "Intel Core2Quad" CPU's. If the guest itself can't use 4 CPU's (i.e. Win XP), then you're out of luck!

---

### Post by HOLOGRAPHICpizza on 2008-12-14
Ok then, this will make my life a lot easier. If Xen is falling out of favor, then what is taking its place? What is the fastest possible virtualization software?

---

### Post by PilotJLR on 2008-12-14
Fastest is a really hard question to answer... it varies based on workload and how you measure it.

Ubuntu supports KVM. I personally would prefer KVM over Xen, but there are lots of opinions on this. The community docs have some really good KVM howto's out there.

Also... as bodhi.zazen pointed out, none of these hypervisors will let you use the video card directly...

---

### Post by HOLOGRAPHICpizza on 2008-12-14
I am actually going to do this on Gentoo, I just like the forums here. :)

And the video card was just wishful thinking, all I really need is the CPU.

---

### Post by bodhi.zazen on 2008-12-15
PilotJLR: Thanks for the great information.

---

