---
title: "Lucid dead end for virtualization (on low end)"
date: 2010-04-22
forum: The Cafe
---

### Post by Ibidem on 2010-04-22
A little bit of a rant here, watch out. 

Getting tired of some "progress" here...
And false advertising in the repos.
KVM-doesn't work with the Atom (or plenty of other things)
Same for Xen
VMWare Player is a joke (can't create an appliance?!)
VMWare Server is a dead end, the modules need patching and support ends in just over a year
VirtualBox doesn't play nice with Lucid guests (That's the version in the repos!), and the 16-bit support is known to be crud (if you use DOS in it, it will crash somewhere, with errors abou invalid opcodes &c. that work on most real hardware)
Qemu doesn't support kqemu any more?!?!

So qemu-kvm is a joke...they lied about "Without hardware support, you can use qemu emulation instead."
Honestly, has whoever perpetrated that build EVER used plain Qemu on a system like that?
Either they do no testing before advertising, or their idea of "use" is more ridiculous than claims that Vista will "run" on 512 MB of RAM and an 800 Mhz CPU.

I THINK that's all...
Figured this shouldn't go in the Lucid forum.

---

### Post by tubezninja on 2010-04-22
Let me get this straight.... you're trying to run VMs.... on an ***atom processor...*** and blaming *ubuntu* for it not working out well?  :confused:

---

### Post by wilee-nilee on 2010-04-22
I have xp,w7,lucid,arch,salix all running on sun vb with a atom 1.6 no problems here.

---

### Post by tubezninja on 2010-04-22
Sounds painful!  but hey if it works for you, the questions remains, why not for the OP?  Since there are many variation of the atom processor, some which purport to support VT and many which don't, we'll need more info.

---

### Post by zmjjmz on 2010-04-22
> **wilee-nilee said:**
> I have xp,w7,lucid,arch,salix all running on sun vb with a atom 1.6 no problems here.

Surely not simultaneously, right?

---

### Post by Ibidem on 2010-04-22
> **scaredpoet said:**
> Let me get this straight.... you're trying to run VMs.... on an ***atom processor...*** and blaming *ubuntu* for it not working out well?  :confused:
Absolutely.
VirtualBox does run acceptably here, apart from the bugs.  
Qemu would work decently if it weren't for kqemu getting dropped; I've used it on Windows.  But on Ubuntu I tried booting a custom OpenSUSE livecd (just IceWM, nothing real bloated), and it took forever (5+ minutes).
**Overall, on Windows virtualization was decent.  So it's not the CPU**.
With kqemu performance should approximate a 1 Ghz CPU (WAG, may actually be underestimating).
The thing is, the one best emulator (QEMU) no longer has its guts (kqemu accelerator), so it has lost performance.
Perhaps the problem is that VirtualBox is too buggy.

---

### Post by Ibidem on 2010-04-22
Atom N270 (no VT)
Lucid on VirtualBox on Lucid (as a guest)  is rather buggy/reluctant to run (A2 to B1). (Alpha1 ran very well.)  
eg-A2 netboot fails to boot, ~A2-A3 the VB guest addons caused others' VMs to crash, jaxx was testing the Spri ISO in VB and it didn't boot-I suggested using Qemu, and it worked.
Also, I've participated in FreeDOS testing, and saw A LOT more "invalid instructions" and crashes in VB than Qemu; I later saw comments about "bad 16-bit emulation" in VB.
The only speed issue is when running pure Qemu.

---

### Post by wilee-nilee on 2010-04-23
> **zmjjmz said:**
> Surely not simultaneously, right?

No, I thought after posting I should have mentioned that. Of course these all run a tiny bit slower then if installed in the netbook as a OS. I understand that there are different atom setups.

---

