---
title: "2 Questions"
date: 2018-07-20
forum: Virtualisation
---

### Post by stardawg on 2018-07-20
1) Ive got amd ryzen 5 1600, 16gb 3200 RAM, running vmware player 14. Am i expecting too much for my guest Ubuntu 18.04 LTS to run exact the same as host performance wise? The PC seems to cope really well with multiple tasks.  I can have chrome running on w10 host with many tabs, and VMWare with VS code running on both the host and guest and it still works really fast. Everything loads fast just the animation for maximizre and minimize shows me there is a slight lag. I have tried Ubuntu mate with similar issue. I have jus going to try Mint and some windows to see if Its the same. I think I maybe expecting too much , it works really great aside from that.

2) In particular i have a scrolling down issue which I seemed to have solved by connecting mouse from host to guest. This seems much better but then my keyboard doesnt work in the guest and I cannot access the Top menu bar so I cant choose to suspend machine.


Thanks for any input.

---

### Post by wildmanne39 on 2018-07-20
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by TheFu on 2018-07-20
TL;DR:
Does Vmware Player have guest additions? Did you install those?

Longer version:
It is hard to understand the issue from the words above.  Please re-read and clarify which OS is running on the Host and which is running in the different guests and which is showing something bad as the host or the guest. Clarity helps.

> it still works really fast.
Well, if it works really fast, why post anything?

The ryzen 5 1600 is a great CPU, but vmware player and the hostOS have to take  some RAM and CPU and **graphics is always a performance issue with every virtual machine solution**, everywhere.  The solutions that provide the best performance require having  2 GPUs, with 1 dedicated to the specific guest OS using PCI passthru.  This is non-trivial and I don't think VMware Player supports it. There are other HW requirements for GPU passthru too.  

But for office productivity needs, most desktop hypervisors do well enough for non-gaming needs.
The virtualbox "guest additions" provide a fairly good trade-off between performance and easy of use.  
VMware Workstation probably does very well too, but I haven't used it in over a decade.
KVM uses the SPICE protocol with QXL video drivers.

If you had an Intel CPU/iGPU, they have been coding some direct HW access methods for guest VMs, but I get the impression they aren't ready for general use.  These work only with KVM and Xen hypervisors.

For non-GUI tasks, a single VM should provide 90-95% of native performance if the VM software is properly tuned and hardware contention is managed.  There are lots of guides for how to setup VMs for the best performance. I've written a few for virtualbox and KVM.  We stopped using VMware software in 2010 due to VMware pricing decisions. The general tuning ideas apply to all VM hypervisors.

Today, I use KVM+libvirt+virt-manager for my hypervisor and management solution.

---

### Post by stardawg on 2018-07-20
> **TheFu said:**
> TL;DR:
Does Vmware Player have guest additions? Did you install those?

Longer version:
It is hard to understand the issue from the words above.  Please re-read and clarify which OS is running on the Host and which is running in the different guests and which is showing something bad as the host or the guest. Clarity helps.


Well, if it works really fast, why post anything?

The ryzen 5 1600 is a great CPU, but vmware player and the hostOS have to take  some RAM and CPU and **graphics is always a performance issue with every virtual machine solution**, everywhere.  The solutions that provide the best performance require having  2 GPUs, with 1 dedicated to the specific guest OS using PCI passthru.  This is non-trivial and I don't think VMware Player supports it. There are other HW requirements for GPU passthru too.  

But for office productivity needs, most desktop hypervisors do well enough for non-gaming needs.
The virtualbox "guest additions" provide a fairly good trade-off between performance and easy of use.  
VMware Workstation probably does very well too, but I haven't used it in over a decade.
KVM uses the SPICE protocol with QXL video drivers.

If you had an Intel CPU/iGPU, they have been coding some direct HW access methods for guest VMs, but I get the impression they aren't ready for general use.  These work only with KVM and Xen hypervisors.

For non-GUI tasks, a single VM should provide 90-95% of native performance if the VM software is properly tuned and hardware contention is managed.  There are lots of guides for how to setup VMs for the best performance. I've written a few for virtualbox and KVM.  We stopped using VMware software in 2010 due to VMware pricing decisions. The general tuning ideas apply to all VM hypervisors.

Today, I use KVM+libvirt+virt-manager for my hypervisor and management solution.

Thanks for your detailed reply, I guess I was expecting a bit too much, anyway I tried Linux Mint and it is slightly better even. Yes I have got open-vm-tools and open-vm-tools-dekstop. The only issue I have now is the mouse one, but I will post that
 elsewhere if i cannot find a solution.

---

### Post by TheFu on 2018-07-20
Mouse integration is provided by the guest additions.

---

### Post by stardawg on 2018-07-22
> **TheFu said:**
> Mouse integration is provided by the guest additions.

I can switch between host(w10) and guest(ub64) and have keyboard and mouse working on both. If I connect my logitech mouse from host to guest thats when my scrolling issue is fixed, but then I cannot access the top toolbar of VMWare Workstation Player 14, even If i switched to full screen.

---

