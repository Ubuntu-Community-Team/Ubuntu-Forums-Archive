---
title: "Want GuestOS to be Network Visible"
date: 2012-06-10
forum: Virtualisation
---

### Post by Rhemat on 2012-06-10
Heya All,

I am running VirtualBox 3.2.8_OSE r64453 on Lubuntu 10.10, running an Ubuntu Server 12.04 install, and wish to allow communication from host to guest, as well as guest to network.  However, while the guest can communicate with the host, that is as far as communications go.  I have the guest set up with two adapters; one NAT, and one Bridged (tried Host-Only as well), but to no avail.  I only get that the packets are filtered when I try pinging any address of the guest.  The network set up is as follows:

Host      eth0  192.168.0.64
NAT-Gate        10.0.2.2
NAT-Guest eth0  10.0.2.15
BRI-Guest eth1  192.168.56.72

I can understand difficulty with different subnets, but it seems that some communication is possible with the NAT, as it registers filtered packets.

I have also opened port 7 in UFW on the Ubuntu Server, which is the ICMP reply port, but that does not work.

Is there any way I can fix this?  Do I need GNS3, or IPCop?

Just in case, as to why I want to do this; I want to run game servers on my machine, but in a virtualized environment.  This way, I can keep back-ups of those machines readily available, and if anyone attempts to take-over my box, they will only be able to access the virtual machine.

Thanks in advance.

---

### Post by CharlesA on 2012-06-10
Change networking to bridged instead of NAT.

The VM will then be on the same network as the host.

---

### Post by Rhemat on 2012-06-11
Thanks CharlesA, that did work.  It did change the IP addresses on the guest, but I think was to make them subnet appropriate.

---

### Post by CharlesA on 2012-06-11
> **Rhemat said:**
> Thanks CharlesA, that did work.  It did change the IP addresses on the guest, but I think was to make them subnet appropriate.
Yep. It will use whatever address scheme you use on the host's network.

NAT defaults to 10.x.x.x. :)

---

