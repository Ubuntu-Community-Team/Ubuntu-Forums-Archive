---
title: "How to network KVM server to LAN"
date: 2020-02-08
forum: Virtualisation
---

### Post by mn1247 on 2020-02-08
I have a question about networking in KVM/QEMU.  I'm new to this and am finding the options rather daunting.

Briefly, I'm setting up a home server (a standalone computer running Ubuntu/KVM) connected to my home LAN that will host a number of VMs for various purposes.  There are other IP devices on the LAN (computers, cameras, video displays) that need to be able to communicate (efficiently) with the VMs, and also I need to be able to manage the server using libvirt on a separate computer (not the server host).  Ideally, all IP addresses would be assigned from my home router, but I can live with having the server assign its subnet IPs as long as they are unchanging (so they are known on the wider LAN).

At present, I've got KVM and a couple of VMs running, but am currently unable to access these from the LAN.  I think I need a bridge, but am totally confused as to how best to set this up.

Any advice would be greatly appreciated.

Thanks,
Eric

---

### Post by TheFu on 2020-02-08
Which Ubuntu release?

I can provide exact directions for 16.04.

18.04 switched networking backends.  Yesterday, someone asked a similar question, I searched and found some bridge how-to guide and posted the link in these forums.  I've never tried those instructions.

Servers need static IPs.  Best NOT to trust DHCP for that. Manually set the network connection properties using the netplan methods for each VM.

What you want is to use bridge-utils to manually create a bridge for each physical NIC in the server.  Then inside each VM, select one of those bridges to be used by a VM.

There are security considerations with bridge setup and bridge assignments for VMs and the host.  I group different VMs to a bridge based on the risk profiles for each VM.  The hostOS uses a NIC port that doesn't have any bridge assigned.  Promiscuous mode used by bridges can be used by VMs to watch all the traffic on a NIC.

---

### Post by mn1247 on 2020-02-08
Thanks for the reply.  I'm using 18.04.  Desktop, not server version.

The LibVirt manager allows me to create bridges under two tabs: one for "network interfaces" and one for "virtual interfaces".  I'm not sure which one of these I should be trying to create a bridge under.  

Is there a good example somewhere?

Eric

---

### Post by TheFu on 2020-02-08
> **mn1247 said:**
> Thanks for the reply.  I'm using 18.04.  Desktop, not server version.

The LibVirt manager allows me to create bridges under two tabs: one for "network interfaces" and one for "virtual interfaces".  I'm not sure which one of these I should be trying to create a bridge under.  

Is there a good example somewhere?

Eric

The libvirt bridges have been slow for 10 yrs.  Manually create them.  There is no point-n-click method to create a fast bridge and you don't want to use any desktop GUI to setup KVM networking at the OS layer.  All you can use virt-manager for is to select the bridge you've manually created outside libvirt.   

As I said already above, yesterday I posted a link in these forums for a guide to setup bridges in 18.04.  5 seconds searching found this: [https://ubuntuforums.org/showthread.php?t=2436506&p=13930592#post13930592](https://ubuntuforums.org/showthread.php?t=2436506&p=13930592#post13930592)

---

