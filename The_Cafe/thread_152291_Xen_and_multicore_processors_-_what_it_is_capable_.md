---
title: "Xen and multicore processors - what it is capable of?"
date: 2006-03-29
forum: The Cafe
---

### Post by sup on 2006-03-29
As probably many of you, I need windows now and then, either for some specific programs or for my scanner to work. I was able to set up qemu so I run several programs under it, but it is not very fast and it emulates all the hardware, so scanner does not work with it.

Now, Xen is supposed to be the fastest solution out there for virtualization (at least they claim it and I do not think I have heard anyone denying it), but it does not work with microsoft windows due to licensing reasons, but they mention somehow, that multicore processors shloud allow xen to run Windows - and that they are working on it. Now, do I understand them right? Does it apply for all multicore processors - now the intel core duo seems to be only one that is available for home use.
Moreover, how does virtualization with xen works? I somewhere read it allows unlike Qemu (maybe only with multicore processors?) even the guest OS to use computers hardware directly - so would it mean my scanner would work with xen and windos then?

---

### Post by aamukahvi on 2006-05-27
You need hardware support to run Windows on Xen. The newest AMD and Intel processors support this (but not Core Duo, I think).

About the other stuff, I just made a new thread.

---

### Post by sup on 2006-05-27
Nice to see someone else is interested about this. I subscribed to your thread, although I have nothing to add to it.

As for the Intel Duo, I just checked wikipedia and it seems virtualization technology (called vanderpool) is included, although it can be disable in bios sometimes: [http://en.wikipedia.org/wiki/Core_duo#Yonah]("http://en.wikipedia.org/wiki/Core_duo#Yonah")

---

### Post by aamukahvi on 2006-05-27
[QUOTE=sup]Nice to see someone else is interested about this. I subscribed to your thread, although I have nothing to add to it.

As for the Intel Duo, I just checked wikipedia and it seems virtualization technology (called vanderpool) is included, although it can be disable in bios sometimes: [http://en.wikipedia.org/wiki/Core_duo#Yonah]("http://en.wikipedia.org/wiki/Core_duo#Yonah")[/QUOTE]
I subscribed to this, too, in case someone replies :p
Duo supporting VT is new info for me. Interesting. I've been looking into AMD because of the memory controller which is on-die, it's supposed to give it superior performance when allocating memory between VMs.

---

### Post by aamukahvi on 2006-05-27
[QUOTE="wikipedia"]Intel calls its hardware assistance for emulation "VT" although it is often referred to by its codename "Vanderpool". It was officially launched at the Intel Developer Forum Spring 2005. It is available on all Pentium 4 6x2, Pentium D 9xx, Xeon 7xxx and Core Duo processors, though in the latter case it is sometimes disabled in the BIOS/EFI.

AMD calls its hardware assistance for emulation "Pacifica". AMD has announced that it will be available by the end of the first half of 2006 and in mobile, desktop, workstation, and server chips by the end of the year ([1]).[/QUOTE]
...

---

