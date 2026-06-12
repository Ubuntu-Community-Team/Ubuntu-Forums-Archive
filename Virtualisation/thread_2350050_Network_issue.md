---
title: "Network issue"
date: 2017-01-20
forum: Virtualisation
---

### Post by 9-mike-w on 2017-01-20
Hopping someone can give me some direction I am out of ideas.

 I have a Ubuntu Host and PFSense running in a VM on the host. WAN NIC is using PCI passthough and the LAN side is a bridge. Host can ping the internet so icmp passes but no other kind of traffic will pass any thoughts?
 I had the same setup with centos and it worked but Ubuntu don't. All firewalls are off on the host and even pfsense is set to pass all.

---

### Post by geeksmith on 2017-01-20
Operating a virtual bridge may require promiscuous mode to be enabled in the VM. The hypervisor often doesn't allow this, or requires you to intervene in the host OS to enable promiscuous mode. Since you didn't mention the hypervisor in use it's tough to say what your scenario might require.

You also said that the host can ping the Internet. You mean the Ubuntu host OS, right? If you can ping through the PFSense VM, but nothing else, then this must be related to the firewall setup. Routing and presumably DNS are in place if ICMP works, so I'm not sure what else would get in the way.

Can you give any other info? Routing tables, packet captures, interface addresses, hypervisor in use, etc?

---

### Post by 9-mike-w on 2017-01-20
You are AWESOME!! it was   [COLOR=#000000]promiscuous mode!!!   Thanks fyi I am running libvirt  Thanks again![/COLOR]

---

### Post by wildmanne39 on 2017-01-20
*Thread moved to **Virtualisation**.*

---

### Post by geeksmith on 2017-01-21
Great, glad you were able to fix it!

---

