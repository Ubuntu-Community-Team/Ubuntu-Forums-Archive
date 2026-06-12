---
title: "Use both vmware anf QEMU KVM virt-manager"
date: 2023-10-01
forum: Virtualisation
---

### Post by ubname on 2023-10-01
Hi,
I wonder if there is any problem rumnning both vmvare player and vitmanagert(QEMU + KVM) on ubuntu host, found several info stating they cannot work together but they are working, do I have to expect some sudden crash or data corruption using them both together?

---

### Post by TheFu on 2023-10-01
> **ubname said:**
> Hi,
I wonder if there is any problem rumnning both vmvare player and vitmanagert(QEMU + KVM) on ubuntu host, found several info stating they cannot work together but they are working, do I have to expect some sudden crash or data corruption using them both together?

virt-manager is a libvirt client. It doesn't require that qemu or kvm be running on the same system.  

KVM uses hardware extensions to enable a number of I/O and CPU fast-context-switching facilities.  To my knowledge, only 1 "driver" can have exclusive use of those hardware extensions at a time.  

I've never used VMware Player, but could it be running in a software only virtualization mode?

```
$ lsmod |grep kvm
kvm_amd               155648  0
kvm                  1015808  1 kvm_amd
ccp                   102400  1 kvm_amd
```

Shows that I have the KVM driver loaded into the kernel here.

There is a thing called "nested virtualization".  Could you be running that?  Sort of like running VMs inside VMs inside VMs.
There is also the possibility that virt-manger is handling Linux Containers. Those are 100% software and don't require any specific CPU capabilities. Basically, any Linux kernel since 2.6 can run a Linux Container, since around that time is when the features for containers were added to the kernel.

Lots of things are possible.  That doesn't make using them a good idea or they are only a good idea under very specific situations.  The trick is to recognize it.

Generally, it is not recommended to have to hypervisor solutions installed at the same time on a single physical machine, but it is definitely possible by carefully managing which hypervisor loads a VM driver into the kernel.  modprobe/lsmod/rmmod.

---

### Post by ubname on 2023-10-01
```
lsmod | grep vm

vmnet                  69632  13
vmw_vsock_vmci_transport    45056  0
vsock                  57344  1 vmw_vsock_vmci_transport
vmw_vmci              106496  1 vmw_vsock_vmci_transport
vmmon                 163840  0
kvm_intel             503808  0
kvm                  1347584  1 kvm_intel
irqbypass              16384  1 kvm
```

I understand there are vmmon (vmware) and kvm_intel (KVM) in my machine, wonder if it is ok.

---

### Post by MAFoElffen on 2023-10-02
I can confirm, It does fine, with no conflicts.

The question from me is why would you want to? I used to have all, plus XCP-ng, ad VirtualBox, because I was supporting Users of all those. Nut later, now, just have KVM...

That is my preferred Virtualization host system these days. It is flexible and adaptable for so much, including hosting VM's of different ARCH platforms and various virtualized hardware, In my test suite, I can recreate what I need to, to support users with their issues that they need help with.

---

### Post by ubname on 2023-10-04
> **MAFoElffen said:**
> 

The question from me is why would you want to?

I use two monitors, not able with virt-manager, works with vmware player.

---

### Post by TheFu on 2023-10-04
> **ubname said:**
> I use two monitors, not able with virt-manager, works with vmware player.

Sure it works.  What does virt-manager have to do with 2 monitors?  You aren't actually using it to show the desktops are you?  
Virt-manager is an admin tool, not a daily user tool.  Use virt-viewer for that, if you insist on having a full desktop at all.  I don't, but you do you.

I run GUI programs and terminals across many different computers here. Some are physical, some are VMs, some are containers.  The window that gets displayed on the workstation I'm currently using doesn't care about virt-manager or virt-viewer setup. All windows, regardless of which system the program is actually running, are 1st-class programs on my workstation desktop, so they can be in any workspace or any monitor.

---

### Post by ubname on 2023-10-07
> **TheFu said:**
> Sure it works.  What does virt-manager have to do with 2 monitors?  You aren't actually using it to show the desktops are you?  
If you refer to virt-manager I said "I am not not able" not that it does not work

 > **TheFu said:**
>  if you insist on having a full desktop at all.  I don't, but you do you.
I don't "insist" I need to use tools with GUI in "Microsoft Windows" they do not exists for Ubuntu 


> **TheFu said:**
> 
I run GUI programs and terminals across many different computers here.

I do not have many different computers, I use a desktop, I need two monitors for my windows virt machine; I was able to setup vmware to use both desktop monitors and not able with "virt-manager"

If you have the time to guide me on how to setup qemu/kvm virt-manager to work with both monitor and same performance as vmware player for GUI in windows 10 I'll be glad to use only virt manager.

Thanks.

---

### Post by TheFu on 2023-10-07
Use virt-viewer, not virt-manager.  Install the Spice QXL video drivers into any guest.  [https://www.spice-space.org/multiple-monitors.html](https://www.spice-space.org/multiple-monitors.html)
Hopefully those instructions are sufficient.  I don't know about other display drivers.  Also, virt-manager might work. IDK.  I have installed QXL drivers into Windows, but it was a long time ago.

---

### Post by ubname on 2023-10-07
> **TheFu said:**
> Install the Spice QXL video drivers into any guest.  [https://www.spice-space.org/multiple-monitors.html](https://www.spice-space.org/multiple-monitors.html)
 

Thanks for the interesting info, it wont work for windows, a dedicated video card for each display seems to be needed
from the link:

> ... whereas the Windows QXL driver only supports a single display for each video device.

---

### Post by TheFu on 2023-10-07
> whereas the Windows QXL driver only supports a single display for each video device. So to enable 4 monitors, a Linux guest would need only a single QXL device, while a Windows guest would need to be configured with 4 separate QXL devices.

So add another QXL video device to the VM if you want 2 monitors supported.  I can't test this now - I don't use 2 screens with VMs, but maybe tomorrow. I do have a Windows7 VM with QXL and a 2nd monitor, but today is football day (my team is highly ranked this year!).

---

### Post by ubname on 2023-10-08
It seem QXL does not accept 3D acceleration, I use Virtio in my host "virt-manager" and it supports 3D video accelleration, don't "waste" time in this if not for your own interest.

---

### Post by MAFoElffen on 2023-10-08
Just a drive by. 

Look at this (KVM, 3D acceleration & multiple displays): [https://superuser.com/questions/1804067/how-do-i-get-a-multi-display-virgl-3d-accelerated-qemu-vm-on-a-nvidia-card-in-vi](https://superuser.com/questions/1804067/how-do-i-get-a-multi-display-virgl-3d-accelerated-qemu-vm-on-a-nvidia-card-in-vi)

---

### Post by ubname on 2023-10-11
new question will open new tread if needed.

---

