---
title: "Virtualization &amp; the CPU"
date: 2008-08-17
forum: Server Platforms
---

### Post by 4xjbh on 2008-08-17
I am putting together a new PC as a home server. I want to use virtualization for different reasons.... I was reading somewhere that not all CPU's can be used in a virtualised environment. Is this the case?

I was looking at a Intel Core 2 Quad Q6700 CPU for this system.

Thanks

---

### Post by tangibleorange on 2008-08-17
> **4xjbh said:**
> I am putting together a new PC as a home server. I want to use virtualization for different reasons.... I was resding somewhere that not all CPU's can be used in a virtualised environment. Is this the case?

I was looking at a Intel Core 2 Quad Q6700 CPU for this system.

Thanks

yes this is indeed the case. my CPU certainly doesn't :(. if a CPU supports virtualisation, it needs to have output from this command:
```
grep -E '^flags.*(vmx|svm)' /proc/cpuinfo
```
although that's not much use if you haven't actually purchased it yet...

---

### Post by 4xjbh on 2008-08-17
I get all my pc gear from the same company that supplies the company I work for. Excellent rates. They cannot even tell me if it will support virtualization.

---

### Post by tinny on 2008-08-17
> **4xjbh said:**
> I am putting together a new PC as a home server. I want to use virtualization for different reasons.... I was resding somewhere that not all CPU's can be used in a virtualised environment. Is this the case?

I was looking at a Intel Core 2 Quad Q6700 CPU for this system.

Thanks

Depends on what virtualization software you plan on using.

e.g. [KVM]("http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine") requires a CPU that provides either [Intel VT]("http://en.wikipedia.org/wiki/X86_virtualization#Intel_Virtualization_Technology_.28Intel_VT.29") or [AMD-V]("http://en.wikipedia.org/wiki/X86_virtualization#AMD_virtualization_.28AMD-V.29"). If you get one of these processor types you will be fine.

---

### Post by scorp123 on 2008-08-17
> **4xjbh said:**
> I am putting together a new PC as a home server. I want to use virtualization for different reasons.... I was resding somewhere that not all CPU's can be used in a virtualised environment.  You're mixing apples and oranges here.

The things you mention is only valid if you want to do virtualisation on a CPU-level, e.g. you want virtualisation support in the CPU hardware itself. But you'd still need a hypervisor (= virtualisation software) such as the newer Xen releases that can make use of it.

But with software such as VMware Server, VirtualBox, QEMU, KVM, Xen, and probably many others software-based virtualisation will work just as well on ordinary CPU's. Depending on the CPU that is used and what the virtual machine is used for it doesn't have to be much slower than CPU-implemented virtualisation.

With a Quad-Core Intel CPU you should be quite happy no matter what.

---

### Post by windependence on 2008-08-17
Scorp is correct here. I just installed VMware ESXi (now free!) on a dual Pentium III box and it's fine. You will find everyone has their favorite VM solution but be careful. Some require a VT enabled CPU and can't do paravirtualization. I have found VMware to be the most flexible, and they now have two free solutions to choose from - Vmware ESXi which is a bare metal hypervisor and VMware server which is software that runs on top of Linux or Windows (not recommended) and then runs guests within itself. While this is the most flexible solution, it also takes the most resources. VMware also supports the widest variety of guest OSs from Windows to BSD to Linux and Solaris. 

To find out which CPUs support hardware virtualization, you can go to their websites. If you tell me more about what VM software you want to use I can help you more. 

You really should look at AMD processors. Their technology for multi-core is far superior to Intel IMHO (no flames please). They also have more processors that support native hardware virtualization and as an added bonus, they're cheaper too! 

-Tim

---

### Post by scorp123 on 2008-08-17
> **windependence said:**
>  You really should look at AMD processors. Their technology for multi-core is far superior to Intel IMHO (no flames please). They also have more processors that support native hardware virtualization and as an added bonus, they're cheaper too!  Absolutely correct. Most of my servers are AMD "Opteron" based and they work tip top no matter what I throw at them. I use VMware Server a lot and given enough RAM and enough CPU firepower you can run dozens of virtual machines on a single server without feeling any lags or delays. Intel lost my respect when they started that "IA-64 Itanium" nonsense.

---

### Post by fjgaude on 2008-08-17
> **scorp123 said:**
> Absolutely correct. Most of my servers are AMD "Opteron" based and they work tip top no matter what I throw at them. I use VMware Server a lot and given enough RAM and enough CPU firepower you can run dozens of virtual machines on a single server without feeling any lags or delays. Intel lost my respect when they started that "IA-64 Itanium" nonsense.

Well, all the benchmarks I've seen in the last year or so clearly show Intel duals and quads to be better than AMD's. The new 45 nm chips are very fast, set new standards... AMD is really behind the power curve when it comes to top performance. They cost the same as Intel for the same performance though. Simply AMD doesn't have anything to compare at the top end of the scale.

frank

---

### Post by 4xjbh on 2008-08-17
Thanks everyone for the info. I have a windows server background and the home linux server is a step out of my comfort zone. I have been watching too much TV lately so I thought I would expand my knowledge a little/alot.

I intend to permanently setup a web/ftp and a file and print server as 2 virtualised servers. I am also doing web development work for some clients so I want to also have a couple of temp server environments to  to test and develop on. 

As this is my first dip into linux (Yes I am patient, love reading manuals and forums and don't expect everything handed to me, etc) I am unsure as to what flavour (VMware Server, VirtualBox, QEMU, KVM, Xen) of virtualisation I would use. I figured why not try them all....

As I am buying & building a new PC from scratch I figured that I might as well get a CPU with virtualisation support. If it realy is not going to make a big difference from a learning, experimenting, playing point of view I might as well save some dollars and stick with the quad.

Base Spec so far is Quad Core, 8GB RAM, 2/160GB Mirrored for vservers etc. I will add large data array at a later date. I am using addon card for raid that supports 8 channels. 

Regards, J

---

### Post by scorp123 on 2008-08-18
> **fjgaude said:**
>  Well, all the benchmarks I've seen in the last year or so clearly show Intel duals and quads to be better than AMD's  Benchmarks are one thing. Real life in "the trenches" is another. To be honest with you: I don't give a d**mn anymore about benchmarks anymore. What matters to me is that the software I throw at the server works tip top as expected and that I don't get any complains from my users about the software and/or the network being slow or anything like that. The other thing is that we are more or less a 100% SUN shop when it comes to servers. And the many SUN Fire X4000's (X4200, X4500, X4600, etc.) servers we have here just happen to be Opteron-based, and I really love to work with those servers. So yes, I am biased. :)

> **fjgaude said:**
>  The new 45 nm chips are very fast, set new standards...  Show me a SUN server that has those CPU's and I'll take a test-ride ;)  But right now I am very very happy with the Opteron-based systems that I have :)

> **fjgaude said:**
>  AMD is really behind the power curve when it comes to top performance. They cost the same as Intel for the same performance though.  OK, valid points if they happen to be true. So if OP wants to hand-build his own server he should take those points into consideration.

---

### Post by scorp123 on 2008-08-18
> **4xjbh said:**
>  I have a windows server background and the home linux server is a step out of my comfort zone.  Not to bash Ubuntu or something ... but given your background you might find Novell's "SUSE Linux Enterprise Server" (aka "SLES") easier to work with. You have to register with novell.com's web site and could then download the "SLES 10 SP2" DVD *.iso image. Setting up shares, DHCP, DNS, Windows Domains, etc. is very similar to what you might be used to ...

Take a look here:
[http://www.pcc-services.com/sles/](http://www.pcc-services.com/sles/)

> **4xjbh said:**
>  I am unsure as to what flavour (VMware Server, VirtualBox, QEMU, KVM, Xen) of virtualisation I would use. I figured why not try them all....  **You can't.** 

Both VirtualBox and VMware require special kernel modules (= "drivers") that might conflict with each other and most likely with the other products too. Xen requires its own patched Linux kernel so it can activate its paravirtualisation features; the other two (QEMU, KVM) too need special kernels or special kernel modules if I am not mistaken, making them incompatible with most of the other products.

If you want something that is easy to understand and to learn I'd recommend these two:

- VirtualBox
- VMware Server

Both can be downloaded for free and with both of them it's easy to get into this virtualisation business. VMware has the advantage of being a de facto "Industry Standard" when it comes to virtualisation, e.g. many people and companies use VMware, there are many pre-configured "VMware Guest Images" (= virtualised OS installations) available on various web sites that you can download and thus try out new operating systems without having to install any of them yourself.

VirtualBox too is easy. SUN which bought the German company who originally developed it is now aggressively pushing VirtualBox into the market, and more and more features will be added over time.

In my own experience VirtualBox seems to be a few ticks faster than VMware.

Cons against VirtualBox and pro VMware: Certain features such as bridged networking are far more complicated to setup in VirtualBox whereas in VMware you can enable network bridging just with a few mouse clicks.

Your mileage may vary.

> **4xjbh said:**
>  I might as well get a CPU with virtualisation support.  CPU virtualisation only offers advantages in certain scenarios, e.g. you want to run a virtual Windows under XEN. Yes, you will need CPU virtualisation for that scenario. But you won't need it e.g. if you want to run a virtual Windows inside VMware as VMware's hypervisor does "full virtualisation" whereas XEN is a "para-virtualiser". You may want to check what the differences are:

[http://en.wikipedia.org/wiki/Paravirtualization](http://en.wikipedia.org/wiki/Paravirtualization)
[http://en.wikipedia.org/wiki/VMware_Server](http://en.wikipedia.org/wiki/VMware_Server)
[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

Besides, if I am not wrong then all current "high-end" server and "high-end" desktop CPU's that are sold should now have virtualisation support. The only CPU's that might lack this new feature are the "cheapo" product lines such as Intel's "Celeron" and the cheaper laptop CPU's.

> **4xjbh said:**
>  If it realy is not going to make a big difference from a learning, experimenting, playing point of view I might as well save some dollars and stick with the quad.  From a learning point of view it should not matter much. 

Besides: According to Wikipedia a Core2Quad Q6700 should have virtualisation support:
[http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Quad](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Quad)

> "Kentsfield" (65 nm)

    * All models support: MMX, SSE, SSE2, SSE3, SSSE3, Enhanced Intel SpeedStep Technology (EIST), Intel 64 (Intel's x86-64 implementation), XD bit (an NX bit implementation), iAMT2 (Intel Active Management), **Virtualization Technology,** Trusted Execution Technology ... 

> **4xjbh said:**
>  Base Spec so far is Quad Core, 8GB RAM  I'd reserve 1 - ~1.5 GB of RAM for the OS itself. So this leaves us with around 6 GB RAM for virtual machines. With VMware you could then easily run 6-7 virtual machines with 1 GB RAM each; or 10+ virtual machines if you keep their RAM sizes low, 512 MB RAM or even less per virtual machine if possible (many BSD's and Linux distros will easily run with 256 MB and even less if you don't use any GUI).

As I said .... you should be quite happy with that setup ;)

---

### Post by fjgaude on 2008-08-18
Scorp123, Opteron-based servers are being replaced by AMD Phenom ones.These are much slower than the Intel quads, the Duo Quad Extremes. Check it out.

---

### Post by scorp123 on 2008-08-18
> **fjgaude said:**
>  Scorp123, Opteron-based servers are being replaced by AMD Phenom ones. Sources???  Phenom's are desktop CPU's, not server CPU's. You may want to read what the differences are, e.g. here:

[http://forums.techpowerup.com/showpost.php?p=512092&postcount=3](http://forums.techpowerup.com/showpost.php?p=512092&postcount=3)

And if AMD intended to kill the Opteron line why are they then releasing their new "Bulldozer" product line? Yes, that's the next release of Opterons:  [http://en.wikipedia.org/wiki/Opteron#Future](http://en.wikipedia.org/wiki/Opteron#Future)  ;)

My favourite "toy" right now is this one:
[http://www.sun.com/servers/x64/x4600/](http://www.sun.com/servers/x64/x4600/)

32 Opteron CPU cores in such a small box .... yummy :D

> **fjgaude said:**
>  These are much slower than the Intel quads, the Duo Quad Extremes. Check it out.  Only in your dreams ;)

Besides ... you listed gamer CPU's it seems?? Those may be faster GHz-wise and provide good performance in FPS shooters, but that doesn't mean anything in the server room. See the link above.

---

### Post by fjgaude on 2008-08-18
Okay, points made.

frank

---

### Post by Kolipoki on 2008-08-18
> **scorp123 said:**
> My favourite "toy" right now is this one:
[http://www.sun.com/servers/x64/x4600/](http://www.sun.com/servers/x64/x4600/)

32 Opteron CPU cores in such a small box .... yummy :D

:eek: Wowzers... nice little monster. Up to 32 cores and 256GB of memory O.o

---

