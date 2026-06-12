---
title: "Can more than 1 VM share a physical NIC?"
date: 2019-06-11
forum: Virtualisation
---

### Post by webmiester on 2019-06-11
Hi everyone,

Can 2 VM's share the same NIC?

Let's say I have VM1 running linux, and VM2 runnig Windows.  Do I need separate NICs for them or can they share the same physical NIC without problems?  Thanks

---

### Post by kpatz on 2019-06-11
Your VMs can share the same NIC.  In virtualbox the default is to use NAT; another option is bridged.  There are other options as well, which I won't get into here. Other VM managers like VMWare work in a similar way.

With NAT, each VMs is put behind a virtual router and it gets a private IP from that virtual router.  You can set up port forwarding to access ports on the VMs from outside if you desire.  Another option is NAT Network, where you give the network a name and then the virtual router is shared by multiple VMs using the same NAT network so they can see each other.

With bridged, each VM connects directly to your NIC with its own MAC address, so it's like having a virtual switch connected to your NIC.  Each VM gets an IP on your network either from your network's DHCP server, or statically assigned.  In this mode it's like each VM is a separate physical machine that has an IP on your network.

You can also create virtual networks that don't use a physical NIC at all, so VMs can see each other without having any access to the real LAN.  You can also have multiple NICs per VM... one that connects to the real NIC and others that are virtual.  You could even run PFSense or iptables/ufw on a VM acting as a firewall for other VMs.  The sky's the limit, and it's handy for testing different network scenarios or to isolate VMs from each other or the network at large.

---

### Post by webmiester on 2019-06-12
Thank you so much!  This is the best answer I have ever gotten.

---

### Post by webmiester on 2019-06-12
Is there any particular reason why I would use NAT over bridged or vice versa?  Is it like just preference?

---

### Post by fragglebliss on 2019-06-12
although i might not be able to provide you with the answer you might be seeking, i always use bridged in virtualbox because nat provides me with stupid ip address allocation. whereas bridged sticks to traditional allocation patterns which integrate better with other systems on the network.

---

### Post by SeijiSensei on 2019-06-12
NAT is more secure since the VM is hidden behind the host in the same way a local network is hidden behind most routers. If you plan to run servers in the VMs, you need a bridged connection so client machines can see the server.

---

### Post by kevdog on 2019-06-12
Bridge uses Level 2 networking stack where as NAT uses Level 3?  Perhaps I'm wrong about this. NAT is a lot more tricky to set up however probably more secure in the end -- that being said NAT to me is a PITA to me likely because I don't know what I'm doing.

---

### Post by kpatz on 2019-06-12
> **kevdog said:**
> Bridge uses Level 2 networking stack where as NAT uses Level 3?  Perhaps I'm wrong about this. NAT is a lot more tricky to set up however probably more secure in the end -- that being said NAT to me is a PITA to me likely because I don't know what I'm doing.Yes, essentially.  Think of bridged is having a switch connected to your LAN that your VMs are plugged into, and NAT as having a router with the WAN port connected to your LAN and your VMs connected to the LAN ports so they're on their own network, getting IPs from the router.

(I'm referring to Virtualbox's networking modes here, VMWare and other VM managers will have similar options, maybe named differently)

Let's say your LAN has the IP range 192.168.1.0/24, your LAN's router is on 192.168.1.1 and your VM host is on 192.168.1.100.  When using bridge mode, it's like plugging directly into your LAN's router (or a switch), so your VMs will have 192.168.1.x IPs and they can see everything on your LAN, everything on your LAN can see the VMs, the VMs can get to the internet through your LAN's router, just like any other computer on your network.

So, VM 1 might have IP 192.168.1.101, VM 2 might get 192.168.1.102, etc.  Your LAN router or whatever DHCP server you're using would hand out IPs to the VMs just like a physical box.  It's like your NIC acts as a separate NIC for each VM, each with its own MAC address.

So, for VMs in bridge mode:
Host: 192.168.1.100
VM 1: 192.168.1.101
VM 2: 192.168.1.102
etc.

In default NAT mode (in Virtualbox), your VMs are each placed behind a virtual router.  So, while your host will still have 192.168.1.100, the "router" will NAT to this, and your VMs behind that will have different IPs, like 10.0.2.15.  The VMs can access your LAN (and the internet) through this router, but by default the LAN won't have access to the VMs, nor can each VM see other NATed VMs.  You can set up port forwarding to make services on the VMs accessible from the host or the LAN in general, just like on a hardware router.

So, for VMs in NAT mode:
Host: 192.168.1.100
VM 1: Virtual Router 1 -> 10.0.2.15
VM 2: Virtual Router 2 -> 10.0.2.15
(Each VM is behind a separate "router" so they may have the same IP, as each are on their own private network).

There's also a "NAT Network" mode where you give the network a name, and then any VMs using that network name will share a router.  Doing this, the VMs behind the router can see each other, but are still isolated from the LAN side.

Host: 192.168.1.100
VM 1: Virtual Router 1 -> 10.0.2.15
VM 2: Virtual Router 1 -> 10.0.2.16
etc.

NAT mode is the default in Virtualbox when you create a VM, but you can change this in the network settings for each VM.  For most VMs where I'm just playing with a distro, I just use NAT mode since it works.  If I want to run services on a VM that are accessible from the LAN or the host (like ssh or a webserver), I'll use bridged mode.

You're not limited to choosing just one network type either.  You could have a couple VMs behind NATs, a couple more bridged, some more behind a NAT network, etc.  And since each VM can have 4 virtual NICs, you can even connect one VM to more than one network.  For example, you could make a VM that has 1 NIC bridged and one connected to a NAT network (or even an isolated network).  Install pfSense in that VM, and then you have a firewall that other VMs on that isolated network can access.

---

### Post by webmiester on 2019-06-12
> **SeijiSensei said:**
> NAT is more secure since the VM is hidden behind the host in the same way a local network is hidden behind most routers. If you plan to run servers in the VMs, you need a bridged connection so client machines can see the server.

thanks. This is very helpful

---

### Post by kpatz on 2019-06-12
> **webmiester said:**
> is this advisable to use a hybrid?  Like VM1 nd VM2 will use brides while VM3 and VM4 will use NAT?Network/NIC settings are set per VM (or more specifically, per virtual NIC of which there are 4 per VM), so you can easily do this.  Is it advisable?  Depends on your use case.  You may have one VM that you want bridged so services running within are accessible over the LAN, and another VM you want to put behind a NAT for security, and another you want on an isolated virtual network, etc.

It all depends on what the particular VM is being used for and how you want its network access to be, especially visibility to other machines, whether physical or VMs.

It's no different than setting up physical machines on a network.  You can plug a few into a switch and they all see each other (bridged mode) and you might put 2 more behind a NAT router for security, or on a different subnet via a router and so forth.

As I mentioned before, when using a VM to play with a desktop distro where I'm playing in the GUI or a console I'll usually just use the default NAT, but if I want to be able to ssh into the VM from elsewhere, I'll use bridged.  It's easy enough to change on an existing VM as well, in case I change my mind.

---

### Post by webmiester on 2019-06-12
Is the MAC address physically embedded in the NIC?  If I have 3 VMs sharing a NIC on bridge mode, will the MAC addresses of each VM be different?  If yes, I presume it is the VM that generates the mac addresses for these Virtual NICs...  If so, is it possible for us to define the mac address ourselves or to replicate the mac address of a previous VMs?

---

### Post by kpatz on 2019-06-12
In Virtualbox you can set the MAC address of each virtual NIC yourself, or let Virtualbox create a random one for you (it does this automatically when you create a new VM).  If you clone a VM I don't know if it clones the MACs or not, you'd have to check, and if you need two VMs to have the same MAC address, set it yourself.  You wouldn't be able to run both VMs in bridge mode at the same time since it would cause a conflict if they share a MAC address.

A physical NIC has a fixed MAC address in the hardware but it can be overridden by the driver.  And when you use bridge mode, the NIC will send and receive packets for all the MAC addresses assigned to the VMs and pass them along to the appropriate VM.

---

### Post by TheFu on 2019-06-12
As others have said, yes, you can share a physical NIC, but there are security considerations when doing that for all hypervisors.  Each guest has to opportunity to see the traffic from the other users of the NIC.  If that is a concern, like it would be in a commercial hosting environment (for the clients, not the provider), then you'll want to use PCI passthru.

For the types of hypervisor use we've been discussing in other threads, you should stay away from virtualbox and non-Server stuff that VMware offers/sells.  For your needs, there are really 3 options.  KVM, Xen, or ESXi+vsphere.  If you are 100% microsoft company, then a case could be pushed that their server-Hyper-V stuff should be used.
[https://www.linux-kvm.org/page/Networking](https://www.linux-kvm.org/page/Networking)

Also, never forget that if VLAN traffic isn't filtered from the wire, then it is just a suggestion and clients can access that traffic too.  Lots of places use VLANs to run different networks over the same wires - voip + computers + admin access without realizing a nefarious computer can access all the traffic.

With that said, I use a linux bridge for my VMs tied to 1 NIC on the public network side and the hostOS uses a different NIC for the traffic it gets on the admin network, which is NOT on the public interface/network and physically separate.  If you run multiple ethernet cables to each location and plug them into the same plug in the wiring plan, it is pretty easy.  Left plug is VoIP always. Right plug is for computing devices. Of course, then you need 2x the switch ports and trunk runs (probably), so there is a price for the added security.  Worked at a place with 4 separate cable runs to each cube/office for a decade. They were serious about security.

Network security design is where all computer security begins, IMHO.

---

### Post by webmiester on 2019-06-13
> **TheFu said:**
> As others have said, yes, you can share a physical NIC, but there are security considerations when doing that for all hypervisors.  Each guest has to opportunity to see the traffic from the other users of the NIC.  If that is a concern, like it would be in a commercial hosting environment (for the clients, not the provider), then you'll want to use PCI passthru.

For the types of hypervisor use we've been discussing in other threads, you should stay away from virtualbox and non-Server stuff that VMware offers/sells.  For your needs, there are really 3 options.  KVM, Xen, or ESXi+vsphere.  If you are 100% microsoft company, then a case could be pushed that their server-Hyper-V stuff should be used.
[https://www.linux-kvm.org/page/Networking](https://www.linux-kvm.org/page/Networking)

Also, never forget that if VLAN traffic isn't filtered from the wire, then it is just a suggestion and clients can access that traffic too.  Lots of places use VLANs to run different networks over the same wires - voip + computers + admin access without realizing a nefarious computer can access all the traffic.

With that said, I use a linux bridge for my VMs tied to 1 NIC on the public network side and the hostOS uses a different NIC for the traffic it gets on the admin network, which is NOT on the public interface/network and physically separate.  If you run multiple ethernet cables to each location and plug them into the same plug in the wiring plan, it is pretty easy.  Left plug is VoIP always. Right plug is for computing devices. Of course, then you need 2x the switch ports and trunk runs (probably), so there is a price for the added security.  Worked at a place with 4 separate cable runs to each cube/office for a decade. They were serious about security.

Network security design is where all computer security begins, IMHO.

OK.  so the physical NIC is overwritten by the driver.  That is so cool.  So that's how it works.  OK, Im putting all of these concepts into my design.
You mentioned hypervisor.  Do I need this if I won't be doing baremetal VMs?  What exactly is it in my needs that you see, why I would need to stick with KVM, Xen, or ESXi+vsphere?  I was actually considering virtualbox running on top of ubuntu until you mentioned this.  I have to admit that Ive been reading posts on Virtualbox vs KVM, etc, and I was beginning to lean towards virtualbox or VMware player for ease of use and their ability to run on windows too (which means I can transfer the image to those OS's in the future).

---

### Post by 1clue on 2019-06-13
There's also SR-IOV, which stands for single-root I/O Virtualization. It's specific hardware support built into some network cards which (supposedly) handle some of the concerns about sharing a card in a virtualization environment.

---

### Post by TheFu on 2019-06-13
> **webmiester said:**
> OK.  so the physical NIC is overwritten by the driver.  That is so cool.  So that's how it works.  OK, Im putting all of these concepts into my design.
You mentioned hypervisor.  Do I need this if I won't be doing baremetal VMs?  What exactly is it in my needs that you see, why I would need to stick with KVM, Xen, or ESXi+vsphere?  I was actually considering virtualbox running on top of ubuntu until you mentioned this.  I have to admit that Ive been reading posts on Virtualbox vs KVM, etc, and I was beginning to lean towards virtualbox or VMware player for ease of use and their ability to run on windows too (which means I can transfer the image to those OS's in the future).

Hypervisor is a generic term.  KVM, Xen, Virtualbox, VMware Player, Workstation, ESXi ... are all hypervisors. The hypervisors I listed in the other post are stable, server, hypervisors.  The others are for desktop-on-desktop VMs.  They are also slower on modern hardware.

 **virt-manager** is a GUI to manage KVM, Xen, and other hypervisors. It looks like the virtualbox GUI or the VMware Workstation GUI or the VMware player GUI, but it provides more capabilities.  Most of those capabilities aren't needed, but when you do need them, they are there, on a different tab.  I haven't used anything except virt-manager to create and install guestOSs in at least 8 yrs.  I have needed to tweak some advanced storage needs, like sheepdog, through virsh edit, but when doing n+1 replication, no GUI will handle that cleanly.  

Should also point out that virt-manager works remotely to manage multiple hypervisors.  A minimal Ubuntu Server install with just the stuff needed to run that, remotely support it (ssh), secure it and back everything is fairly lite.  virt-manager from a desktop connects via ssh to the libvirt stuff on the hypervisor for management, setup, tear down.  No need to install any GUI **on** the hypervisor physical hardware.

Years ago, there were claims being made that type-1 and type 2 hypervisors mattered for all sorts of reasons. There were great reasons behind these claims, but it turned out for most common workloads, the performance didn't care. For some workloads, virtualbox's non-HW accelerated software-only solution was faster than using the VT-x or AMD-v stuff.  

Look at the ESXi compatible hardware list.  It might be limiting for some people.  On my 5 physical systems, only 1 would work with ESXi.  If you have expensive Dell/HP/IBM servers, current generation, then you are probably fine.  Be certain to get the approved network cards and HBAs too.  OTOH, KVM is part of the Linux kernel.  It works on any linux compatible hardware, provided VT-x or AMD-v is supported - there are other factors, but, in general, those are it.  If you don't have VT-x or AMD-v, you are out of the VM game already, except using qemu in software only mode.  I don't think vbox x64 will run on hardware without it.  I do believe that vbox x32 will, but that is crazy limiting for a VM host at this point.  Spend the $100 and get a better computer.

MS-Windows runs great under KVM, better than virtualbox if you aren't doing GPU intensive stuff.

Did I mention F/LOSS?

---

### Post by TheFu on 2019-06-13
One thing needs to be clear.  Only install 1 hypervisor on a physical computer at a time.  They will conflict almost always.  

But you should try each one out for at least a day before deciding anything.  Gather some facts. Use a stopwatch for workload comparisons. See for yourself, which performs better with your current level of skill.

Then after you pick 2, try those for a week. Run them like you would in production. See which is stable, fast, doesn't cause issues.  If you can, try a version upgrade with those 2 hypervisors. See which is less pain. Does the upgrade break things?  What hassles, if any, are there?

You don't need to commit to 1 most of the time - except VMware's paid solutions. Once you drop $2-$5K for licenses, you are sorta stuck.

---

### Post by 1clue on 2019-06-13
The theory behind a hypervisor is that it's a minimalist implementation of virtualization software, and nothing else. It's the fewest features your virtual machines need from a host. There is an OS of sorts, but it's strictly for virtualization. It's a benefit for disk space, complication, ease of maintenance and security.

KVM is built into the Linux kernel, and so you could run KVM on a full desktop system and it would be a sort of "thick" hypervisor. I like to use jelly and toast as an analogy, where the toast is your physical hardware and the jelly is the amount of stuff you have installed on your hypervisor. A strict hypervisor (VMware, etc) is a thin layer of jelly on the toast, but still enough to taste it. KVM lets you spread the amount of jelly you want, according to your taste. My 3 year old would put the whole jar of jelly on one piece of toast, and this would be a typical full-function desktop using KVM/QEMU.

---

