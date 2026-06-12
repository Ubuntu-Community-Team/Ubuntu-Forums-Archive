---
title: "Recommended setup to run several OSs on home server?"
date: 2009-06-09
forum: Virtualisation
---

### Post by Gustavo Narea on 2009-06-09
Hello, everybody.

I'm using my old laptop as a home server with Ubuntu 9.04 only, but now I need to make it Internet-accessible a few hours a week running several operating systems at the same time, so I need to use virtualization. I know what I want, but I don't know how to get it because I haven't found the answer to how set it all up the way I want it, so I hope some of you could help me out ;-)

I manage several VPSs/guest systems, but never a host system, so I want something that is easy to set up (read: that just works). I want to have the four guest systems below:
[LIST]
[*]Ubuntu, as the home server itself (print server + internal Web sites + many other things). This one is used very often. From time to time we use it as a workstation (i.e., WiFi, Firewire, audio and video should work).
[*]3 operating systems (Ubuntu, FreeBSD/OpenBSD/NetBSD and OpenSolaris). These will be used a few times a week, just to build the Free Software I develop to make sure it works on these platforms and report back to my online server.
[/LIST]

I want something that starts the four systems as the computer is turned on. It'd be annoying if I had to open the laptop's lid to select anything, given the place where the laptop is... I want to do it all via SSH, from my computer.

I'd love to use a virtualization software which allows me to shutdown the guests I'm not using easily. I don't want my home server to run slowly while I'm not going to use the other guests, for example.

FWIW, my CPU is a Genuine Intel(R) CPU T2400 @ 1.83GHz and I have 1246MiB of RAM. Please let me know if you need more information about the hardware.

Is this feasible? If so, what virtualization software you'd recommend me? Hope it's not too demanding :)

Thanks in advance!

---

### Post by puelly on 2009-06-09
In my opinion for the "Just's work" category, I find VirtualBox and VMWare to be the best solutions for multiple OSes.  Both have about the same performance, you may need some additional RAM if you want to virtualize that many machines.

---

### Post by Gustavo Narea on 2009-06-10
Thank you, puelly!

I tried VirtualBox but I found it a bit hard to set it up, so I gave KVM a try and it's mostly working as I wanted relatively quickly.

Cheers.

---

