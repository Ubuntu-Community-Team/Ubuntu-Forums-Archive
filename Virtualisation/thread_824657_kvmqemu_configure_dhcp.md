---
title: "kvm/qemu configure dhcp"
date: 2008-06-10
forum: Virtualisation
---

### Post by ema on 2008-06-10
Hi all,

I'm successfully using kvm (Ubuntu 8.04), running WindowsXP SP2 virtual OS.
I can browse the web, and should not have any issue with TCP/IP and UDP/IP software.

The problem is that I have a default address of the class 10.*.*.*
I need to use the virtualized XP to run a remote desktop software inside it and I fear that the 10.*.*.* class is actually used in the remote network I'm trying to connect on (so the packets destined to the 'real' 10.*.*.* hosts get lost under the virtual dhcp).

Is there a way (simple maybe) to configure the DHCP kvm/qemu addresses at command line, without having to install/configure any other complex software?

I'd like to use maybe another class of addresses like
192.168.1.* or 192.168.254.* or whatever, just different from 10.*.*.*

I don't know if it's possible to bridge the main DHCP because I'm using my notebook (Asus G2S) wireless network card.
Isn't there a way to 'instruct' kvm to use another default subnetwork than 10.*.*.*?

Thanks in advance,
Ema.

---

### Post by grantek on 2008-06-11
It shouldn't matter - the 10.*.*.* network inside kvm/qemu is separate from the 10.*.*.* network from your PC to the outside network, so they won't interfere, even if it does seem a bit confusing. Ubuntu on the host PC won't really even see kvm/qemu's internal 10.*.*.* network.

The other alternative is to give the guest direct 2-way access to the outside network (giving it a "tap" interface), which will mean it won't use kvm/qemu's dhcp server, and will access any dhcp server on the outside network.

---

### Post by ema on 2008-06-12
> **grantek said:**
> It shouldn't matter - the 10.*.*.* network inside kvm/qemu is separate from the 10.*.*.* network from your PC to the outside network, so they won't interfere, even if it does seem a bit confusing. Ubuntu on the host PC won't really even see kvm/qemu's internal 10.*.*.* network.

The other alternative is to give the guest direct 2-way access to the outside network (giving it a "tap" interface), which will mean it won't use kvm/qemu's dhcp server, and will access any dhcp server on the outside network.

I think that the 10.*.*.* shouldn't be an issue because actually the VM subnet is 255.255.255.0 so actually the fake local network is 10.0.2.* (so that should not interfere with another 10.*.*.* class network).

But seems I can't make a bridge on my pc as seen as I'm using a wireless network adapter and probably I can't 'forge' NIC, so the option to use a TAP is not available.

Still can you confirm me that with kvm/qemu the only network protocols supported are TCP/IP and UDP/IP?

Cheers,
Ema.

---

### Post by grantek on 2008-06-12
> **ema said:**
> Still can you confirm me that with kvm/qemu the only network protocols supported are TCP/IP and UDP/IP?

Not quite. It's an IP network presented by qemu, so you can use anything that works over IP. In the real world, that's basically only TCP, UDP, RDP, and ICMP ("ping", etc), but if you have a more obscure protocol that uses IP addresses, it'll work.

Anything "lower" than that using raw ethernet (eg. a protocol that needs to communicate with network devices using their MAC addresses) won't work in this mode.

---

### Post by ema on 2008-06-13
> **grantek said:**
> Not quite. It's an IP network presented by qemu, so you can use anything that works over IP. In the real world, that's basically only TCP, UDP, RDP, and ICMP ("ping", etc), but if you have a more obscure protocol that uses IP addresses, it'll work.

Anything "lower" than that using raw ethernet (eg. a protocol that needs to communicate with network devices using their MAC addresses) won't work in this mode.

Acutally ping is not working...and I don't get why then.
From what I read around only the 2 main protocols based on IP are supported. Eg:

TCP/UDP (supported)
|
IP (available only through TCP, UDP)
|
(raw data) (not available)

Stil is it possible to instruct kvm/quem to use another subnetwork than the 10.0.2.*/255.255.255.0 ? Like 192.168.2.*/255.255.255.0?

Cheers,

---

### Post by ema on 2008-06-16
Update.

I still didn't manage to specify another subnet but the application I was trying to make work is now working. That thing needed SP3 installed...

Cheers,

---

### Post by grantek on 2008-06-17
> **ema said:**
> From what I read around only the 2 main protocols based on IP are supported.
Yes, I think I may have been wrong. You can't really do port translation on a protocol that doesn't use ports, so that would tie user-mode networking to TCP and UDP. I don't know how ICMP would work, I'd say it's possible to get ICMP etc. working by passing everything seen by the host to the guest, but it's probably not implemented that way because it would be a security issue.

---

