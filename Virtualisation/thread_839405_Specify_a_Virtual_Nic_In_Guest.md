---
title: "Specify a Virtual Nic In Guest"
date: 2008-06-24
forum: Virtualisation
---

### Post by zaarch on 2008-06-24
Is is possible to create a virtual nic on the guest that is different from the physical nic on the host ?

Ex. NIC on host : Broadcom 5702
and I would like the NIC on the guest to be Realtek XX-XX

Is this possible via KVM+QEMU and using LIBVIRT to create and manage VMS?

---

### Post by igwk on 2008-06-24
The way almost all virtual machine monitors work is that they create an entire set of virtual hardware devices that the virtual machine sees.  So for that reason, if you have a Broadcom 5702 NIC on your host machine, your virtual machine will never get to access the NIC as a Broadcom 5702 directly.  The virtualized ethernet NIC that your virtual machine will see depends on what devices the virtual machine monitor supports.  I believe KVM/QEMU virtualizes a Realtek 8139 ethernet NIC.

---

### Post by seetho on 2008-06-24
Yup kvm presents Realtek 8139 NIC to all VMs.  The trouble is OpenBSD running as a VM is having trouble with this NIC.  I get kernel watchdog timeout errors appearing and the NIC stalls under load.

Is there any possibility of presenting a different NIC to VMs under kvm? e.g. PCNet or Intel NICs.

---

### Post by igwk on 2008-06-25
According to the QEMU documentation at [http://bellard.org/qemu/qemu-doc.html#SEC10](http://bellard.org/qemu/qemu-doc.html#SEC10), it supports many different virtual ethernet NICs.

> 
`-net nic[,vlan=n][,macaddr=addr][,model=type]'
    Create a new Network Interface Card and connect it to VLAN n (n = 0 is the default). The NIC is an ne2k_pci by default on the PC target. Optionally, the MAC address can be changed. If no `-net' option is specified, a single NIC is created. Qemu can emulate several different models of network card. Valid values for type are i82551, i82557b, i82559er, ne2k_pci, ne2k_isa, pcnet, rtl8139, smc91c111, lance and mcf_fec. Not all devices are supported on all targets. Use -net nic,model=? for a list of available devices for your target.


You're probably safe using the ne2k_pci model, as the NE2000 ethernet cards are pretty much the lowest common denominator as far as ethernet cards go.  Some of the other models are likely to have better performance though.

---

### Post by seetho on 2008-06-25
> **igwk said:**
> According to the QEMU documentation at [http://bellard.org/qemu/qemu-doc.html#SEC10](http://bellard.org/qemu/qemu-doc.html#SEC10), it supports many different virtual ethernet NICs.



You're probably safe using the ne2k_pci model, as the NE2000 ethernet cards are pretty much the lowest common denominator as far as ethernet cards go.  Some of the other models are likely to have better performance though.

I use virt-install to create my VMs.  It does not have any options to specify NICs to use.  How exactly do you create VMs with specific NICs then?

---

### Post by igwk on 2008-06-25
I just run kvm directly without using the virt-manager tools so I'm not sure.  When you run kvm directly you specify which NIC to use at the command-line, so you can change the ethernet NIC model each time you start the virtual machine monitor.

---

### Post by seetho on 2008-06-25
OK.  I'll give it a go and see what happens.  It'll be interesting to see what happens to existing VMs when I change the NIC.

---

### Post by zaarch on 2008-06-25
hmm..interesting..

So KVM.QEMU virtulizes with realtek instead of creating a virtual copy of my physical nic (broadcom).

well the real reason why i asked, was that my win 2k3 install was in all way perfect..except that 2k3 was unable to load drivers for my nic..

i went to the manufacturers site and found that they dont have drivers for the 2k3 ...(every other windows they support but not 2k3)...

but still that confuses me..realtek is now almost generic...i think ..2k3 would be able to load drivers for that..

guess i need to go back and redo the whole installation..

will try this out tomorrow.

thanks guys..

---

### Post by igwk on 2008-06-26
zaarch, before you redo the entire installation, try to change the NIC device on the command-line.  Win2k3 might just auto-detect the NIC and use the appropriate driver automatically and save you some time.  If that fails, you could always reinstall from scratch.

---

### Post by seetho on 2008-06-26
I checked [libvirt.org]("http://libvirt.org") for their domain xml format info.  Unfortunately there's no way to specify any NIC type.

I checked around for virt-install info and found that there's no way to specify NIC types.  The roadmap [virt-manager site]("http://virt-manager.et.redhat.com/") does not include any functionality to specify NICs in short and long term.

I tried starting my VM with kvm -net nic,model=pcnet.  It works but then I don't have network connection to my bridge anymore.  Tried setting up tap devices but could not get it to work properly.

I give up!  I don't plan to use OpenBSD for any VMs anyway so it's not a problem for me.  I think I'll stick to virt-install and Ubuntu/JEOS for my VMs.

seetho

---

