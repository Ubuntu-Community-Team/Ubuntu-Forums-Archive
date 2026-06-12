---
title: "Xen virtualization -- What is it capable of?"
date: 2006-05-27
forum: The Cafe
---

### Post by aamukahvi on 2006-05-27
Hi,

I've been looking into Xen for a while now, and while hardware-based virtualization seems really interesting, there are a few things I haven't been able to figure out yet.

1. Does Xen support AMD Pacifica extensions yet?
2. Does Xen allow enough control over hardware to client OSs, so that games can run (OpenGL, DirectX)?

TIA,
aamukahvi

---

### Post by nacs on 2006-06-05
1) Not yet (it supports Intels VT extensions though)
2) Not yet

---

### Post by sup on 2006-06-06
And when is it going to be? 
And is it a weakness of xen or today's processors?

---

### Post by foof on 2006-06-20
Is it possible to run Ubuntu 6.06 + XGL/Compiz in DomU as good as it normally is?

---

### Post by G Morgan on 2006-06-20
Xen has problems with Nvidia cards AFAIK and it only works for 64 bit processors though it can virtualise 32 bit OSes.

---

### Post by oscar on 2006-06-20
[QUOTE=G Morgan]Xen has problems with Nvidia cards AFAIK and it only works for 64 bit processors though it can virtualise 32 bit OSes.[/QUOTE]
I don't know where you heard that but I am pretty sure it is wrong.

---

### Post by G Morgan on 2006-06-20
[QUOTE=oscar]I don't know where you heard that but I am pretty sure it is wrong.[/QUOTE]

Which part, I heard from someone else there were issues with Nvidia cards. I've never tried it myself but I see no reason why to doubt the person in question.

Xen requires 64 bit processors since it works via paravirtualisation and the 32bit processors don't have the parallel ring to make calls to. Traditional virtualisation software works by taking calls from the guest OS which expect to run in ring0 then translating them. Paravirtualisation works because theres a second ring and the VM makes calls directly to this ring as opposed to a translated call boosting efficiency. Since this second ring only exists on 64 bit processors as it stands...

---

### Post by imagine on 2006-06-20
Xen runs on 32bit processors.

And AFAIK there is 3D support, however you'll have to hack some files to get it working and even then there are some issues left.

---

### Post by ember on 2006-06-20
[QUOTE=G Morgan]
Xen requires 64 bit processors since it works via paravirtualisation and the 32bit processors don't have the parallel ring to make calls to. Traditional virtualisation software works by taking calls from the guest OS which expect to run in ring0 then translating them. Paravirtualisation works because theres a second ring and the VM makes calls directly to this ring as opposed to a translated call boosting efficiency. Since this second ring only exists on 64 bit processors as it stands...[/QUOTE]

Well, that's not entirely true. At the moment, Xen requires modifications to the guest OS which are called paravirtualisation. This results from the x86 architecture which is (according to virtualisation theory) defective, because some commands behave different in ring 0 (supervisor mode) and ring 3 (user mode). 
This will be fixed as soon as the new virtualisation extensions appear, because they introduce a new ring (ring 1 - the virtualisation ring) which behaves like ring 3 does.

Yet, if all this is working one day, it should be possible to use guest OSs like Windows for gaming with little perfomance slowdown.

---

### Post by G Morgan on 2006-06-20
[QUOTE=imagine]Xen runs on 32bit processors.

And AFAIK there is 3D support, however you'll have to hack some files to get it working and even then there are some issues left.[/QUOTE]

Seriously its this that suggested otherwise [Wiki-Xen.]("http://en.wikipedia.org/wiki/Xen")

Specifically this part

[QUOTE="Wikipedia"]Hardware architectures

**Xen currently runs on x86, with P6 or newer processors, and x86 64 based systems.** Ports are currently underway to IA64 and PPC. Ports for other platforms are also technically possible and may be available in the future.[/QUOTE]

Prehaps I've misinterpreted but it qualifies that P6 and x86_64 are what run currently. If I've mislead anyone then I apologise.

---

### Post by syadnom on 2006-07-08
a)xen runs on ANY P6 OR GREATER processor including pentium pro and amd k6.

b)xen can use normal drivers in and domain on the system by passing direct access to that pci device(agp or pci-e ok).  xen has no problems with any device when allowing direct access.  note that direct access will disallow other domains to use that device.

c)i run xen with dapper and xgl works with my atix1400.  i can get windows xp running also when passing my video card to it's domain, but you do need a intel vt enabled(and soon pacifica) chip to run windows.  also, windows lacks some of the driver modifications required to use all devices so some things may not work.  i just pass usb ports to my windows-domain and it works well.

d)read the wiki for some enlightenment!

e)i have ubuntu in dom0 with my vid card passed to dom0(for fglrx driver!), i have sub-domains with freenas(replace with xen kernel! for best results, but it will install otherwise if you have vt), and i have smoothwall in another.  i have a dedicated ethernet on the smoothwall and use the vif pipe from dom0 and route freenas through dom0. cant tell you if its stable as it has only been up for about a week and i tend to mess around a lot on reboot.

---

