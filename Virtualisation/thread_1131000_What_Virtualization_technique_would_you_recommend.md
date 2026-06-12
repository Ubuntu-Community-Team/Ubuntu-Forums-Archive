---
title: "What Virtualization technique would you recommend?"
date: 2009-04-20
forum: Virtualisation
---

### Post by fletschge on 2009-04-20
Hi guys,

I have a Lenovo T61p Notebook which includes an Intel Core2 Duo T7300 CPU, therefore VT-enabled.
I'd like to run a Ubuntu 9.04 Jaunty on it which virtualizes a Windows XP OS as a guest system upon it. But I'm not sure what kind of virtualization technique I should use. I already tried kvm through qemu, but in my opinion is too slow compared to other solutions (for example hardware acceleration) and it somehow doesn't recognize all my hardware (i.e. network adapters).
So I thought XEN would be a good idea, but I haven't tried it out yet...

Btw.: I would like to have full-virtualization, not that paravirtualization stuff :D

Of course, I could just use VirtualBox or vmWare, but I need to run heavy 3D-applications on it (not games).

Dual-Boot is no option because I need to have access to both system at the same time.

What do you guys recommend me to do?

Thanks in advance!


Yours sincerely,

fletschge

---

### Post by ninjapirate89 on 2009-04-20
I've always used VirtualBox. I haven't had any problems from it that make me want to use anything else.

---

### Post by fletschge on 2009-04-20
AFAIK VirtualBox is just an emulator? I would like to have native-access to my hardware

---

### Post by bowens44 on 2009-04-20
> **fletschge said:**
> AFAIK VirtualBox is just an emulator? I would like to have native-access to my hardware

VirtualBox is not an emulator.

---

### Post by fletschge on 2009-04-20
> **bowens44 said:**
> VirtualBox is not an emulator.

So does that mean that I will have direct-hardware-access with VirtualBox?

---

### Post by Therion on 2009-04-20
Having ruled out Qemu and Xen your remaining options are pretty much VirtualBox or VMWare Workstation.  

I've used both VMWare and VirtualBox.  I use VirtualBox now because I'm more familiar with setting it up, but for hardcore 3D acceleration you might be better off with VMWare.

> **fletschge said:**
> So does that mean that I will have direct-hardware-access with VirtualBox?
What exactly does that mean?  You'll have access to peripheral devices, yes.  I'm not sure what you mean by "direct-hardware-access" though.

---

### Post by fletschge on 2009-04-20
> **Therion said:**
> Having ruled out Qemu and Xen

Why are they ruled out?

Thanks for the advice, I already tried VMWare, but I'm not really happy with it because it's not open source.


EDIT: Maybe I now misunderstand something, but isn't it possible to have access to the underlaying hardware so that the guest system 'sees' the same hardware specs as the host system? I.E: Qemu has it's video card shown as a 'Cirrus CLGD 5446 PCI VGA', so I don't have access to my nVidia card directly, see what I mean?

---

### Post by Therion on 2009-04-20
> **fletschge said:**
> Why are they ruled out?
Your OP said you'd tried them already and they weren't working out for you.


> **fletschge said:**
> Thanks for the advice, I already tried VMWare, but I'm not really happy with it because it's not open source.
That pretty much leaves you with VirtualBox then.

---

### Post by emnaki on 2009-04-21
> **fletschge said:**
> 
EDIT: Maybe I now misunderstand something, but isn't it possible to have access to the underlaying hardware so that the guest system 'sees' the same hardware specs as the host system? I.E: Qemu has it's video card shown as a 'Cirrus CLGD 5446 PCI VGA', so I don't have access to my nVidia card directly, see what I mean?

If your CPU is VT-enabled, then I don't see why you need to access you hardware directly. Sure, there is a slight overhead in that communication needs to pass through the Hypervisor, but since it is directly mapped to Hardware because of VT, the load to the hypervisor is minimal. 

If you are obsessed with direct hardware access then you could give VMWare ESX 4 (vSphere) a try. It has a feature called VMDirect Path which bypasses the Hypervisor. I don't know how much faster this is, but I know that the main buzz with this feature for its adopters is that VMWare will finally be able to support <<insert currently unsupported hardware >> and less to do with speed.

---

### Post by bodhi.zazen on 2009-04-21
Virtualization , by definition, does not directly use your hard ware. The cpu, the network card, the videocard, the hard drive, they are all virtual.

Since you have the hard ware and prefer open source I suggest KVM and openvz (depending on what you want to do, openvz is for servers).

If you want a few more features , go Virutlabox. Vitrtualbox has better video resolution and integration with your OS (mouse integration and copy / paste).

If you want more features, go with VMWare (Workstation and/or ESX). I believe workstation has the best video options (at the moment, although I could be wrong) and ESX is a powerful hypervisor.

I would steer you away from Xen.

---

### Post by fletschge on 2009-04-21
Hi guys

@bodhi.zazen and @emnaki:

Thank you for your introduction, I am really convinced of VirtualBox by now. I used to have it years ago, but back then it wasn't as versatile as it is now and the performance was very bad.
Do you have any idea why VirtualBox is extremely faster than KVM on my machine? I tested it with Windows XP and Ubuntu 9.04. In VirtualBox I had no problems at all, in KVM I couldn't install Windows XP after the first reboot was necessary and Ubuntu was starting up incredibly slow. Also the pointer seems to lag intolerable, maybe I missed to install or configure something?

The main application of the virtual machine (basically windows xp) will be direct3D programs I need to write for school, so I guess that video performance is a very important criteria.


By the way, why shouldn't I use xen?

Thanks guys,

- fletschge

---

