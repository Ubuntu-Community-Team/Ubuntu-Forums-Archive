---
title: "Qemu accelerated 3D"
date: 2013-05-21
forum: Virtualisation
---

### Post by MikeCyber on 2013-05-21
Hi
over at phoronix they say qemu to support fully 3D now? Could I run Windows or OSX on Ubuntu now with full 3D speed? 
Any tutorial on how to use qemu around as I've only used Virtualbox so far. (which doesn't support hardware acceleration for guest os)
Thanks

---

### Post by heiko_s on 2013-05-21
Haven't read the Phoronix report but you could try the following:

kvm:
[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)

Xen:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=112013](http://forums.linuxmint.com/viewtopic.php?f=42&t=112013)

I'm running Windows 7 in a domU (Xen term for a VM) with full graphics acceleration. BUT your hardware must meet certain requirements.

kvm is more bleeding edge though it seems to offer more options with Nvidia graphics cards. In any case you would probably need two GPU.

---

### Post by dppd on 2013-05-23
Is there any practical way to install qemu 1.5 in 13.04?

---

### Post by zeljkojagust on 2013-05-23
If by full 3D acceleration you mean using your GPU inside virtual machine, you have to make sure your CPU and mainboard both support VT-d (for Intel based CPU/Chipset combination). Than you can use a pci-passtrough Qemu function and "pass trough" your GPU for VM to use.

---

### Post by MikeCyber on 2013-06-04
Would that do:
[https://www.digitec.ch/ProdukteDetails2.aspx?Reiter=Details&Artikel=274798](https://www.digitec.ch/ProdukteDetails2.aspx?Reiter=Details&Artikel=274798)
[https://www.digitec.ch/ProdukteDetails2.aspx?Reiter=Details&Artikel=273464](https://www.digitec.ch/ProdukteDetails2.aspx?Reiter=Details&Artikel=273464)

I'll update my PC very soon. Windows and OSX?
Thanks

---

### Post by zeljkojagust on 2013-06-04
According to manual, that Asus mainboard supports VT-d, so that one is good, but CPU does not. Intel K series of CPUs don't support VT-d. You can check which CPU does support that on ark.intel.com.

---

### Post by heiko_s on 2013-06-04
Don't get the K version of the Intel CPU !!!

I don't recommend Asus, as they don't support any OS except Windows and if things don't work it'll be your problem (their support isn't helpful too). A better choice is ASrock.

---

### Post by MikeCyber on 2013-06-05
[**[COLOR=#000000]zeljkojagust[/COLOR]**]("http://ubuntuforums.org/member.php?u=1502220") thanks for the link. [**[COLOR=#000000]heiko_s[/COLOR]**]("http://ubuntuforums.org/member.php?u=553046") why not the k. That's exactly what I want as it's the only to be overclockable? Also I have never had any problems with Asus on any OS.

---

### Post by zeljkojagust on 2013-06-05
As I said K series dont support VT-d option you need to acomplish what you want. Yes they are overclockable but no features for VT-d virtualisation.

---

### Post by heiko_s on 2013-06-07
> **MikeCyber said:**
> [**[COLOR=#000000]zeljkojagust[/COLOR]**]("http://ubuntuforums.org/member.php?u=1502220") thanks for the link. [**[COLOR=#000000]heiko_s[/COLOR]**]("http://ubuntuforums.org/member.php?u=553046") why not the k. That's exactly what I want as it's the only to be overclockable? Also I have never had any problems with Asus on any OS.

Essentially the K versions are crippled CPUs with overclocking unlocked so people would buy them. As zeljkojagust already wrote: don't get the K version, except when you are talking about the 3930K.

For the Intel CPU options that support VT-d, check this: [http://ark.intel.com/search/advanced/?s=t&VTD=true]("http://ark.intel.com/search/advanced/?s=t&VTD=true")

---

### Post by T.J. on 2013-06-09
I've a quick question.  In using Xen have you had any luck with passthrough on AMD processors and chipsets?

---

### Post by heiko_s on 2013-06-10
> **T.J. said:**
> I've a quick question.  In using Xen have you had any luck with passthrough on AMD processors and chipsets?

I'm using an Intel 3930K CPU, but have read reports of success with some AMD CPUs / chipsets.

Your AMD CPU and chipset must support IOMMU. See also here [HOW-TO make dual-boot obsolete using XEN VGA passthrough]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") and follow the links re hardware compatibility. Also see [http://forums.linuxmint.com/viewtopic.php?f=18&t=130626]("http://forums.linuxmint.com/viewtopic.php?f=18&t=130626") about a problem with cpufreq and AMD CPUs - not sure it's solved yet.

Here is a very long thread on Xen VGA passthrough using Fedora with quite a few AMD success stories: [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine")

Hope it gets you started. Just remember: You must make certain that the CPU - chipset - motherboard/BIOS combination does support IOMMU (VT-d in Intel slang).

---

### Post by T.J. on 2013-06-19
Many thanks!

---

