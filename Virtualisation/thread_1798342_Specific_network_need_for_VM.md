---
title: "Specific network need for VM"
date: 2011-07-06
forum: Virtualisation
---

### Post by pieroxy on 2011-07-06
I don't have a preferred way of virtualizing (KVM, VirtualBox, VMWare...) and I want to build a couple of virtual machines so that they are accessible from my LAN (and Internet if I map the correct ports on my router) and I want the VM to be able to access the Internet. My host would be ubuntu-server and my guests ubuntu-server as well.

However, I don't want the VM to be able to access any of my LAN network (but for the gateway of course).

Is this a "standard" need that is addressed by all virtualization solution? 

I guess NAT and Bridged are out since they would allow too much access. So am I stuck with Host-only and I'd have to setup a bunch of tunnels back and forth?

Any advice is appreciated.

---

### Post by CharlesA on 2011-07-06
Just use a firewall to prevent that machine from accessing any IP except the gateway.

---

### Post by pieroxy on 2011-07-07
> **CharlesA said:**
> Just use a firewall to prevent that machine from accessing any IP except the gateway.

Ah! Thanks for the tip. A few questions then:
1. I guess I need to set up this firewall on the host (I need my users to be root on their VM). Would that limit the host's ability to access the LAN as well?
2. Can you point me to a good/usable firewall in the ubuntu repos?

---

### Post by CharlesA on 2011-07-07
You'd have to run the firewall on the VM as far as I know.

Check here: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

