---
title: "64 bit guest OS in virtualbox"
date: 2009-10-16
forum: Virtualisation
---

### Post by blazemore on 2009-10-16
I am running Ubuntu Karmic 64 bit.
I am trying to install Windows 7 RTM (Which I get through MSDN as a computer science student) inside a virtual machine using Virtualbox.

However, the Windows disk won't load, saying I need a 64 bit CPU.
My Ubuntu is 64 bit.

Any ideas?

---

### Post by cariboo on 2009-10-16
Which version Virtualbox are you using? I use the puel version available [here]("http://www.virtualbox.org/wiki/Downloads"). I have Vista 64 and Windows 7 running with zero problems.

---

### Post by Hallvor on 2009-10-16
> **blazemore said:**
> I am running Ubuntu Karmic 64 bit.
I am trying to install Windows 7 RTM (Which I get through MSDN as a computer science student) inside a virtual machine using Virtualbox.

However, the Windows disk won't load, saying I need a 64 bit CPU.
My Ubuntu is 64 bit.

Any ideas?

I tested Virtualbox a month ago, and it would only run 32 bit guest OS, despite that my main system is 64 bit.

---

### Post by undecim on 2009-10-16
My VB is running 64-Bit Arch Linux just fine, with full AMD-V and all those other little hardware extensions. Did you make sure to choose the "Windows 7 (64-bit)" option as opposed to just "Windows 7" when creating the VM?

---

### Post by blazemore on 2009-10-16
There wasn't an option for that. However I installed it via the ppa, whereas now I just installed the 64 bit version from their website, where I may have better luck. I'll report back.

---

### Post by disophisis on 2009-10-16
> **cariboo907 said:**
> Which version Virtualbox are you using? I use the puel version available [here]("http://www.virtualbox.org/wiki/Downloads"). I have Vista 64 and Windows 7 running with zero problems.

I, too, have windows 7 64 running.

I have ubuntu 9.04 running fine too.

in other words, this.

---

### Post by blazemore on 2009-10-16
There still isn't an option for 64 bit.

---

### Post by bodhi.zazen on 2009-10-16
> **blazemore said:**
> There still isn't an option for 64 bit.

As has been mentioned on this thread, not all 64 bit host CPU support 64 bit guests on Virtualbox.

It sounds as if your CPU does not support 64 bit guests (I have teh same problem on one of my 64 bit machines as well).

As far as I now , your CPU has to support VT.

---

### Post by blazemore on 2009-10-16
Right well I have a Core 2 duo E7400, a really mainstream CPU.
What sort of BIOS options should I look for, as I fear it may be disabled there.

---

### Post by bodhi.zazen on 2009-10-16
> **blazemore said:**
> Right well I have a Core 2 duo E7400, a really mainstream CPU.
What sort of BIOS options should I look for, as I fear it may be disabled there.

It varies by BIOS. Somewhere there may be an option ot enable VT (Virtualilzation) technology.

I have seen it under various locations in the BIOS, you need to look through your menu.

---

### Post by paxmark1 on 2009-10-16
In 9.04 I can run guest linux and guest Windows 7 in VirtualBox in 32 bit mode.  

I have a CPU (Intel dual core E2200) that does support 64 bits nicely.

Not only does the CPU have to support the VT threadings, but the motherboard bios must support the VT threadings and the bios must be set to be "on" for VT threadings.  

I would upgrade to a VT capable cpu in a heart beat, but my mobo ASUS P5KPL-VM does not have an option to enable VT.  For some mobos, it might be possible to flash upgrade the bios and it might be enabled then.  However my understanding is that is the exception and not the hnormal state of events.  I flashed on the slim chance and had no reward, but no problems.  

If I ever buy a nice laptop, that will be a crucial decision factor for me, to ensure that I can run VirtualBox (and/or KVM) in 64 bit mode.  

I never did figure out how to get the Vbox window size to increase. Other than finding that the RC of Windows 7 is not a total piece of crap and checking out Crunch Bang linux (a very swift Ubuntu derivative) in 32 bit mode, I have done aptitude purge virtualbox. 

Sun is doing some very nice things with VirtualBox and someday all decent computers will virtualize easily, but not this motherboard. 

peace, mark r.

---

### Post by tromoly on 2009-10-16
Having the same issue here on an Acer Aspire 6920, unfortunately the BIOS are very sparse and under Settings->System->Aceleration the VT-x/AMD-V option is greyed out, that's the way the cookie crumbles sometimes I guess :(

Side question, is VT-x/AMD-V needed for all 64bit virtualization nomater what program it is (virtualbox, vmware, etc)?

---

### Post by bodhi.zazen on 2009-10-16
> **tromoly said:**
> Having the same issue here on an Acer Aspire 6920, unfortunately the BIOS are very sparse and under Settings->System->Aceleration the VT-x/AMD-V option is greyed out, that's the way the cookie crumbles sometimes I guess :(

Side question, is VT-x/AMD-V needed for all 64bit virtualization nomater what program it is (virtualbox, vmware, etc)?

It is needed for KVM and Virtualbox, I am not sure about VMWare or qemu.

---

