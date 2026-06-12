---
title: "Suspend with XEN?"
date: 2013-09-05
forum: Virtualisation
---

### Post by thenoname on 2013-09-05
Hi,

I am working with Xen on my laptop running Ubuntu 12.04. I wonder if there are any ways to suspend/hibernate while running Xen? Currently if I use pm-suspend, the machines goes to suspend as usual but cannot wake up, black screen appears. To note that my machine can suspend/hibernate normally before installing Xen.
I have searched around for this issue but nothing seemed positive.

Any help is appreciated. Thanks!

---

### Post by TheFu on 2013-09-05
You need to save each running VM first. There is a Xen command for that - **xm save {vm-name}**, I think.  

Sorry - I stopped using Xen about 2 yrs ago - KVM is working much better for our needs and we had a few reoccurring issues with Xen after almost every Xen kernel update. Sometimes it wouldn't boot with the new kernel and we'd be forced to drop back the hostOS and all paravirtual kernels to a prior version for a few weeks.

---

### Post by thenoname on 2013-09-05
> **TheFu said:**
> You need to save each running VM first. There is a Xen command for that - **xm save {vm-name}**, I think.  

Sorry - I stopped using Xen about 2 yrs ago - KVM is working much better for our needs and we had a few reoccurring issues with Xen after almost every Xen kernel update. Sometimes it wouldn't boot with the new kernel and we'd be forced to drop back the hostOS and all paravirtual kernels to a prior version for a few weeks.

Hi, thanks for the reply.

I have tried to shut off all vm, also disconnected xen via virt-manager, but the machine could not awake. Another problem I have with Xen is that I cannot use normal kernel after installing Xen. It is something like 'kernel panic', caps lock keeps blinking. Then the only option I have is xen kernel.

I am learning about libvmi - an introspection library. It supports Xen and KVM. But KVM needs some patch to work with libvmi. I am afraid I cannot apply the patch correctly so libvmi does not work. That's the reason why I stick with Xen.

I think I would give KVM a try. Going to backup the whole system and reinstall an os ;)

---

### Post by TheFu on 2013-09-05
Xen needs a completely different Kernel to work. KVM is just a kernel module.

I migrated my Xen VMs to KVM using normal backup and recovery methods. Not that big of a deal, it turned out.
For KVM, I use 
* kvm
* libvirt
* virsh - CLI vm manager - can run from the same or remote machine
* virt-manager - GUI vm manager running from the same or a remote machine
Virt-manager is a GUI like vSphere or VirtualBox or VMware Player that manages VMs on libvirt systems. The VMs can be local or remote - it uses ssh, so managing any remote VM is secured by ssh-keys.

**sudo apt-get install kvm virsh** on the VM host. Add your normal login to the libvirt group.
**sudo apt-get install virt-manager** on any remote clients you'd like to manage from.
I think that will handle dependencies for you. Setup some ssh keys, be happy.

Of course, don't expect fast GUI from any remote machines. You can try the spice guest kernel and a local spice interface, but when I've tried it, it wasn't stable.  For remote desktops when ssh just isn't enough, I use FreeNX on the server and the NoMachine NX client.

---

### Post by tgalati4 on 2013-09-05
Xen is designed for real server hardware running 24/7 serving several virtual machines.  I don't believe it has the hooks for sleep/suspend.  Running Xen on a laptop is an exercise, but you would not use it for production.  Being a module of a normal linux kernel, KVM is what you want on a laptop.

Because Xen runs a heavily-modified kernel as the Host OS, don't expect it to behave like a regular linux kernel.  Reinstall is your only choice at this point, unfortunately.

Find some old server hardware that you can allow to run 24/7 and put Xen on that.  You will then see the power of Xen.  On a laptop?  Not so much.

As many things in linux: * Just because you can doesn't mean it's a good idea.*

---

### Post by TheFu on 2013-09-05
> **tgalati4 said:**
> Find some old server hardware that you can allow to run 24/7 and put Xen on that.  You will then see the power of Xen.  On a laptop?  Not so much.

As many things in linux: * Just because you can doesn't mean it's a good idea.*

+1!   Xen can work well (most of the time) on common desktop machines ($300) with VT-x, so don't think you need a Xeon powered monster for $2500.

> Pro: Linux is extremely flexible.
Con: Linux is extremely flexible.

---

### Post by thenoname on 2013-09-05
Thanks so much guys,
I am going to reinstall :)
I hope someday I would have chances to work with real Xen server as described as you did :)

---

### Post by tgalati4 on 2013-09-05
I bought a couple of Xeon monsters for $300 each.  Servers are cheap these days.  All of that virtualization has freed up a lot of single-rack servers that are just waiting for new homes and operating systems.

---

### Post by thenoname on 2013-09-09
I successfully installed KVM. Tho I failed to run a KVM VM with Windows 8. I configured the vm's cpu with vt-x already but after a windows logo, black screen appeared and cpu runs like hell. I am still struggling with the problem. I used to able to run Windows 8 vm under Xen. 
Life is not easy :(

---

### Post by TheFu on 2013-09-10
> **thenoname said:**
> I successfully installed KVM. Tho I failed to run a KVM VM with Windows 8. I configured the vm's cpu with vt-x already but after a windows logo, black screen appeared and cpu runs like hell. I am still struggling with the problem. I used to able to run Windows 8 vm under Xen. 
Life is not easy :(

I said:
> Of course, don't expect fast GUI from any remote machines. You can try the spice guest kernel and a local spice interface, but when I've tried it, it wasn't stable. 

Whoa!  This is the first time you mentioned Windows.  Running a desktop OS brings completely different requirements into play.  Xen and KVM are primarily designed to run server OSes, not desktops/GUIs.

Can you explain the "configured VM CPU with vt-x?"  That doesn't make sense to me.  Inside a client VM, vt-x should not be seen/possible. It is needed on the physical server, but not inside each guest. I'm probably just misunderstanding.  I don't believe it is possible to enable VT-x for anything except an entire physical server.  Please teach me.

Did you try the spice video to connect to the VM?  How are you connecting to Win8?  I use RDP to Win7 and it works fine for normal desktop apps, but not for video or audio. Avoid using VNC (the built-in desktop connection method).  RDP feels about 5x faster than the built-in VNC that virt-manager provides.  Also, did you follow normal VM setup "best practices" for CPU, RAM, network and disk devices?

If you want to run a desktop inside a VM and access it for desktop-like needs, especially if it is Windows, most people are better off using **VirtualBox**. The graphics in virtualbox are good enough for video and lite-gaming.  I run Win7 inside a KVM VM - it records TV for the house.  It cannot be used to watch the recorded or live TV - other devices are used for that. That same KVM host runs 6 other VMs too - all Linux servers.  Linux virtualizes much better than Windows, IME.

Linux desktops can work well inside a KVM VM, with a good remote desktop setup. I use FreeNX.  My daily use "desktop" is a Linux install running inside a private cloud ... KVM + freenx on the server. Again, video and audio don't work well. If that is a requirement, you'll **need** Spice+KVM or just install VirtualBox.

VirtualBox includes trade-offs too. If you intend to run 1 VM and it is a desktop running on a desktop, you won't care, but if you want concurrent server VMs running and need fantastic stability, then KVM is a better choice.

---

### Post by tgalati4 on 2013-09-10
I don't understand the use case that the OP is trying to solve.  Dual-boot might be a better choice.  We went from trying to put Xen to sleep to running Win8 and Linux at the same time.

---

### Post by TheFu on 2013-09-10
> **tgalati4 said:**
> I don't understand the use case that the OP is trying to solve.  Dual-boot might be a better choice.  We went from trying to put Xen to sleep to running Win8 and Linux at the same time.

I agree.  Either he wants to learn about Enterprise-class virtualization for servers .... or he wants to run a desktop.  Very different use cases with very different tools.  It is possible to cheat, just a little, on either side, server or desktop, provided the user understands the limitations of each.

If virtualizing desktops and running local is what he wants, then Xen, KVM, QEMU, LXC, UML, ESXi, OpenVZ, and all the commercial versions of those are not what he needs.

---

### Post by thenoname on 2013-10-10
> **TheFu said:**
> I said:


Whoa!  This is the first time you mentioned Windows.  Running a desktop OS brings completely different requirements into play.  Xen and KVM are primarily designed to run server OSes, not desktops/GUIs.

Can you explain the "configured VM CPU with vt-x?"  That doesn't make sense to me.  Inside a client VM, vt-x should not be seen/possible. It is needed on the physical server, but not inside each guest. I'm probably just misunderstanding.  I don't believe it is possible to enable VT-x for anything except an entire physical server.  Please teach me.

Did you try the spice video to connect to the VM?  How are you connecting to Win8?  I use RDP to Win7 and it works fine for normal desktop apps, but not for video or audio. Avoid using VNC (the built-in desktop connection method).  RDP feels about 5x faster than the built-in VNC that virt-manager provides.  Also, did you follow normal VM setup "best practices" for CPU, RAM, network and disk devices?

If you want to run a desktop inside a VM and access it for desktop-like needs, especially if it is Windows, most people are better off using **VirtualBox**. The graphics in virtualbox are good enough for video and lite-gaming.  I run Win7 inside a KVM VM - it records TV for the house.  It cannot be used to watch the recorded or live TV - other devices are used for that. That same KVM host runs 6 other VMs too - all Linux servers.  Linux virtualizes much better than Windows, IME.

Linux desktops can work well inside a KVM VM, with a good remote desktop setup. I use FreeNX.  My daily use "desktop" is a Linux install running inside a private cloud ... KVM + freenx on the server. Again, video and audio don't work well. If that is a requirement, you'll **need** Spice+KVM or just install VirtualBox.

VirtualBox includes trade-offs too. If you intend to run 1 VM and it is a desktop running on a desktop, you won't care, but if you want concurrent server VMs running and need fantastic stability, then KVM is a better choice.

There is way to copy all flags of the cpu to your VM's cpu. I use virt-manager, open the VM, in "show virtual hardware detail"/Processor/Configuration then Copy host CPU configuration. Now i can have every cpu feature in the VM.

---

### Post by tgalati4 on 2013-10-10
Some computers require setting VT-x features in BIOS--presumably to get the motherboard to play nice when serving several virtual machines.  Setting VT-x as part of the VM's CPU configuration doesn't make sense.  I'm pretty sure that it is ignored in the VM.  The host kernel would need to support VT-x to get the performance benefits, but I'm not sure how VT-x is interpretted in the VM.  

Has anyone run Windows8 using VirtualBox?  What is the performance like?

---

