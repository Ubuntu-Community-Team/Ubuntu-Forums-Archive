---
title: "XanMod Kernel 4.4.0-xanmod2"
date: 2015-12-26
forum: The Cafe
---

### Post by xanmod on 2015-12-26
Hi Guys,

XanMod is a kernel version of pf-Kernel base with custom modifications.  Optimized for high performance workstations and desktops.
Supports all recent 64-bit versions of Debian and Ubuntu-based systems.
[TABLE="width: 50%, align: left"]
[TR]
[TD][IMG]http://xanmod.org/xanmod_logo.png[/IMG][/TD]
[TD][B] 







Features:
[/B]

[LIST]
[*]BFS CPU scheduler. 
[*]BFQ I/O scheduler. 
[*]UKSM realtime memory data deduplication. 
[*]Graysky's kernel GCC patch. 
[*]YeAH TCP congestion control. 
[*]x86_64 advanced instructions set support:
MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1,SSE4.2,
POPCNT, AVX, AES, PCLMUL, FSGSBASE, RDRND and F16C. 
[/LIST]
[COLOR=#008000]

[/COLOR][B]Download Here:[COLOR=#008000]
[/COLOR][https://xanmod.org](https://xanmod.org)[/B]

Community Forum
[http://forum.xanmod.org]("http://forum.xanmod.org/")[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
**Last Changes:**

4.4.0-xanmod2 revision 1.160122

[LIST]
[*]BFQ I/O-scheduler v7r11 from bfq's git, last commit [c53f28a]("https://github.com/linusw/linux-bfq/commit/c53f28ac108d738173b64dff1aede5c69070befd"). 
[*]Set timer interrupt frequency to 500hz. 
[*]GCC 5.3.1 20160119 r232387. 
[/LIST]
4.4.0-xanmod1 revision 1.160114

[LIST]
[*]Upstream from pf-Kernel pf-4.4, last commit [18520a9]("https://github.com/pfactum/pf-kernel/commit/18520a9f53e499e26654954729015645cfd27add"). 
[*]BFS CPU scheduler v0.466_1_vrq. 
[*]BFQ I/O-scheduler v7r10. 
[*]Set uksmd nice priority to 15. 
[*]GCC 5.3.1 20160112 r232261. 
[/LIST]
4.3.3-xanmod8 revision 2.160101

[LIST]
[*]YeAH TCP congestion control now is default. 
[/LIST]
4.3.3-xanmod8 revision 1.151231:

[LIST]
[*]Update GCC 5.3.1 20151219. 
[*]Set Swappiness to "10". 
[*]Set Zswap compressor to LZ4. 
[/LIST]
4.3.3-xanmod7 revision 1.151215:

[LIST]
[*]Upstream from [pf-Kernel pf-4.3]("https://github.com/pfactum/pf-kernel/tree/pf-4.3"), last commit [b8572cc]("https://github.com/pfactum/pf-kernel/commit/b8572cc98cca797b7e1b718fdd4b0b6a3f838f3c"). 
[*]BFS CPU scheduler v0.467. 
[/LIST]
4.2.8-xanmod11 revision 1.151215:

[LIST]
[*][Upstream merge 4.2.8]("https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/diff/?id=v4.2.8&id2=v4.2.7&dt=2") from mainline. 
[/LIST]
4.3.2-xanmod6 revision 1.151214

[LIST]
[*]Upstream from [pf-Kernel pf-4.3]("https://github.com/pfactum/pf-kernel/tree/pf-4.3"), last commit [d995559]("https://github.com/pfactum/pf-kernel/commit/d99555937d9bfaca8ebeea323b25701abfbe1686"). 
[*]BFS CPU scheduler v0.466. 
[/LIST]
4.3.2-xanmod5 revision 1.151211

[LIST]
[*]Upstream from [pf-Kernel pf-4.3]("https://github.com/pfactum/pf-kernel/tree/pf-4.3"), last commit [f9c49d8]("https://github.com/pfactum/pf-kernel/commit/f9c49d86c56fd74b1a1337090406f0ae841f5c3e") (VRQ1 patchset). 
[*]Update GCC 5.3.1 20151207. 
[*][Fix merge]("https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/diff/?id=v4.3.2&id2=v4.3.1&dt=2") from linux 4.3.2 mainline. 
[/LIST]
4.2.7-xanmod10 revision 1.151211:

[LIST]
[*][Upstream merge 4.2.7]("https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/diff/?id=v4.2.7&id2=v4.2.6&dt=2") from mainline. 
[*]Preemption set to "voluntary". 
[/LIST]
4.3.0-xanmod4 revision 1.151208

[LIST]
[*]Compiled w/ new GCC 5.3.1 revision 20151206. 
[*]Core compression set to XZ format. 
[/LIST]
4.3.0-xanmod3 revision 2.151119

[LIST]
[*]Upstream from [pf-kernel pf-4.3]("https://github.com/pfactum/pf-kernel/tree/pf-4.3"), last commit [dc19fc3]("https://github.com/pfactum/pf-kernel/commit/dc19fc3dad38157cef5a7565a4a46733d4110edb"). 
[*]New BFS v0.465 patchset VRQ0. 
[*]Timer interrupt frequency set to 1000hz. 
[/LIST]
4.3.0-xanmod2 revision 1.151113

[LIST]
[*]Preemption set to "voluntary". 
[*]Timer interrupt frequency set 300hz. 
[/LIST]
4.2.6-xanmod9 revision 1.151110:

[LIST]
[*]Upstream merge 4.2.6 from [mainline]("https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/diff/?id=v4.2.6&id2=v4.2.5&dt=2"). 
[/LIST]
4.3.0-xanmod1 revision 1.151109:

[LIST]
[*]Upstream from [pf-kernel pf-4.3]("https://github.com/pfactum/pf-kernel/tree/pf-4.3"), last commit [8973496]("https://github.com/pfactum/pf-kernel/commit/8973496f01a73e53575ff8bf66db439914c3d0fd"). 
[/LIST]
4.2.5-xanmod8 revision 6.151105:

[LIST]
[*]Rehabilitated gcc optimizations w/ inline-functions fix. 
[/LIST]
4.2.5-xanmod8 revision 5.151104:

[LIST]
[*]Reduced level optimization of GCC. Curiously, improves latency performance.  [IMG]http://xanmod.org/forum/Smileys/default/grin.gif[/IMG] 
[*]Fixed redundant config set's. 
[/LIST]
4.2.5-xanmod7 revision 2:

[LIST]
[*]New Debian packaging method and build. 
[*]New structure of kernel, more clean. 
[*]Fix problem w/ symbolic links. 
[*]Compiled w/ new gcc revision 20151022. 
[/LIST]
4.2.5-xanmod6 revision 151028:

[LIST]
[*]Set advanced instructions for modern CPUs. 
[/LIST]
4.2.5-xanmod6 revision 151027:

[LIST]
[*]Update to 4.2.5 from [mainline]("https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/diff/?id=v4.2.5&id2=v4.2.4&dt=2"). 
[/LIST]
4.2.4-xanmod6 revision 151026:

[LIST]
[*]Renew kernel config for more performance, stability and debugging support. 
[/LIST]
4.2.4-xanmod5 revision 151026:

[LIST]
[*]Fix smp_preempt bug of -gc and -vrq: v4.2_0463_3_vrq2 by Alfred Chen. 
[*]Rehabilitated debug preempt kernel config. 
[/LIST]
4.2.4-xanmod5 revision 151024~2:

[LIST]
[*]BFS CPU scheduler v0.463 by Con Kolivas. 
[*]BFS enhancement patchset v4.2_0463_2_vrq1 by Alfred Chen. 
[*]Upstream pf-Kernel [fix merge conflict]("https://github.com/pfactum/pf-kernel/commit/cf8d3d2709f0fb2fb192ce03668632520f8d6e16"), mainline 4.2.4 base. 
[*]Disabled debug preempt kernel config. 
[*]Update GCC to 5.2.1 20151010. 
[/LIST]

Please, send me your feedback for constant improvement.[ ;)]("https://mega.nz/#F%21wxdBGDoL%21lASl_94pKm1NDARNPNDyhA")

---

### Post by QIII on 2015-12-27
*Moved to the **Cafe***

Not a support request.

---

### Post by xanmod on 2015-12-30
Linux 4.3.3-xanmod8 released!

---

### Post by xanmod on 2016-01-14
Linux 4.4.0-xanmod1 released!

---

### Post by xanmod on 2016-01-22
Linux 4.4.0-xanmod2 released!

---

### Post by d.harkleroad on 2016-02-19
Thanks for this man, saves me time not having to compile pf-sources anymore now that no one packages pf kernel for Ubuntu/Debian anymore.  It's running great, I've always liked the BFQ/BFS combo.

---

