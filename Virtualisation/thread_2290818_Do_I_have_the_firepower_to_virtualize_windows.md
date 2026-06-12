---
title: "Do I have the firepower to virtualize windows?"
date: 2015-08-15
forum: Virtualisation
---

### Post by AbleTassie on 2015-08-15
Hi, 

I just got a new machine. My old machine only had 1.25 GB of RAM -- too little to run Windows XP virtually. So I had to dual boot. My new machine has 3.072 GB of RAM, Processor 2x Intel (R) Core (TM) 2 duo CPU T5550 @ 1.83 GHz. I mostly use Linux (presently Lubuntu 14.04.3 LTS), but some times I need to use Windows. Do you need any other info?

Is this enough RAM to run Windows virtually? 

Any other comments would be welcomed.

Thanks,

A.

---

### Post by jimmy-frydkaer on 2015-08-15
I sure would like to know the name of that motherboard: 3000+ GB RAM sounds a bit in the woods.

But yes, if you are overly patient it is possible but I would not advice it, your system would be as fast as a dead fish in the water.

---

### Post by QIII on 2015-08-15
Hello!

Unfortunately, [your CPU]("http://ark.intel.com/products/32427/Intel-Core2-Duo-Processor-T5550-2M-Cache-1_83-GHz-667-MHz-FSB") does not support VT-x, so it will not be able to run a virtual machine.

---

### Post by AbleTassie on 2015-08-15
> **jimmy-frydkaer said:**
> I sure would like to know the name of that motherboard: 3000+ GB RAM sounds a bit in the woods.

But yes, if you are overly patient it is possible but I would not advice it, your system would be as fast as a dead fish in the water.

No 3.0 GB RAM, not 3000+ GB of RAM, thanks A.

---

### Post by AbleTassie on 2015-08-15
> **QIII said:**
> Hello!

Unfortunately, [your CPU]("http://ark.intel.com/products/32427/Intel-Core2-Duo-Processor-T5550-2M-Cache-1_83-GHz-667-MHz-FSB") does not support VT-x, so it will not be able to run a virtual machine.

Thank you, would some kind of software virtualization still be possible even though VT-x is not supported?

A.

---

### Post by howefield on 2015-08-16
Something rings a bell about that CPU, I think you may get a 32 bit virtual guest going, but not a 64 bit guest.

Quite trivial to test and try it though :)

---

### Post by kurt18947 on 2015-08-16
I don't recall details any more but I had a 1.5Ghz. Core2duo laptop w/ 3 GB. RAM. It would install and run 32 bit Virtualbox but performance was slow & rocky. That trial didn't last long, I sold the Core2duo machine and bought a 2011 vintage core i5 machine with 4 GB. RAM. That machine works pretty well with Virtualbox and the upgrade cost me $50 U.S so not a budget buster. Aside from a CPU that support virtualization, I'd say 4 GB. RAM is a practical minimum.  Ubuntu-Gnome 14.04 host, VirtualBox and Win10 preview guest was using 3.5 GB., no swap.

---

### Post by AbleTassie on 2015-08-16
> **howefield said:**
> Something rings a bell about that CPU, I think you may get a 32 bit virtual guest going, but not a 64 bit guest.

Quite trivial to test and try it though :)

Thanks Howefield. How would I test it?

A.

---

### Post by aldo-tanca on 2015-08-16
If I can add my 2 cents, your mileage might vary considerably dependently on what you plan to run on XP.
I have an acer 1810tz, with a processor I think a bit slower than yours and 4 gb memory.
For nearly a year, I ran XP on virtual box over ubuntu with unity and then with KDE plasma and a few virtual desktops.
Ubuntu would run ok but XP was quite slow, and I was just running a customized browser and Office on the occasion.
As suggested, you would need to test.
Create the virtual machine, install xp and give it a go with what you would typically use. Dependently on what you need to run, win7 in dual boot might be the better option.

---

### Post by CharlesA on 2015-08-16
> **howefield said:**
> Something rings a bell about that CPU, I think you may get a 32 bit virtual guest going, but not a 64 bit guest.

Quite trivial to test and try it though :)

Agreed. If I remember right, I ran into hell trying to virtualize a 64-bit machine on a 64-bit install on Windows when the BIOS did not support hardware virtualization. That was on a windows 7 box using VirtualBox. I don't know if KVM would behave the same way or not, but you should be able to run a 32-bit machine on a 64-bit OS without hardware virtualization but it'll probably run slower than normal since it's running completely thru software.

> **AbleTassie said:**
> Thanks Howefield. How would I test it?

A.

Install XP and see if it will launch, or even install a 32-bit version of Ubuntu in virtualbox and see if it will actually boot or not.

I'm going to bump this over to the virtualzation area, too.

---

### Post by pqwoerituytrueiwoq on 2015-08-16
> **howefield said:**
> Something rings a bell about that CPU, I think you may get a 32 bit virtual guest going, but not a 64 bit guest.

Quite trivial to test and try it though :)

iv tried doing that before, it worked,but the guest was very unstable (Intel B970)

---

### Post by TheFu on 2015-08-18
VirtualBox doesn't require VT-x support - at least on Windows it doesn't.  I do not know about vbox on Linux, but [https://www.virtualbox.org/manual/ch10.html#hwvirt](https://www.virtualbox.org/manual/ch10.html#hwvirt) says it is not required.

KVM definitely requires VT-x support.
QEMU doesn't, but it is very manual to setup. [https://wiki.gentoo.org/wiki/QEMU](https://wiki.gentoo.org/wiki/QEMU)

I don't know about current versions of Xen, but older versions could run paravirtual guests without VT-x support. I did this back in 2008. Windows cannot be run in this mode.

3G of RAM is a limiting factor. Plus on many systems some of that RAM (256M-1G) is stolen for use by the GPU.  The RAM allocated to a VM isn't all that is needed - there is overhead depending on the connected devices and overhead for the hostOS to manage VMs.

---

### Post by AbleTassie on 2015-08-31
I am going to mark this thread as SOLVED, I got Virtualbox installed and ran Windows XP within it and it seems to work well, 
see [http://ubuntuforums.org/showthread.php?t=2291250](http://ubuntuforums.org/showthread.php?t=2291250) .

Thanks to everybody,

Able

---

