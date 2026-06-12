---
title: "Configuring KVM Guest as FIrewall/Router"
date: 2014-01-03
forum: Virtualisation
---

### Post by rchman on 2014-01-03
Since my motherboard does not support Vt-d, I'm having trouble setting up my KVM Guest as the router/firewall (Untangle). In Hyper-V, this was easy: set WAN ethernet X to not be shared with the host, and set the mac address.

I want traffic to be WAN -> Untangle Guest -> LAN

What do I need to do to get Untangle to get a DHCP lease from my modem? 

I've tried (and several other combinations - although I haven't tried setting the address static):

#WAN Interface
auto eth2
iface eth2 inet dhcp

auto br2
iface br2 inet manual
brige_ports eth2
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

I spent hours googling and trying different settings and restarting my modem, but to no avail. My guest was never able to get a lease from my modem. Any ideas?

As an aside, I got it working this way (which I'm not content with):

WAN->Host Machine on eth2->IP Masqueraded/forwarded to Eth1 (which is setup as a dhcp server on that port)->Untangle on br1->Lan on br0. 

Problem is that my host is not behind Untangle and I'm pretty sure this is not a very "proper" setup.

Any helpful pointers?

---

### Post by TheFu on 2014-01-05
Don't know how to do what you need, but definitely NEVER put a VM-hostOS/server directly on the internet. That is a good way to be hacked AND have all your VMs hacked.

---

### Post by rchman on 2014-01-05
That's my gut concern. However, is that true even if all traffic is being forward by the host from WAN to the firewall appliance on the LAN?

---

### Post by TheFu on 2014-01-05
If there is a physical connection ... don't trust it. That's my opinion.  My boxes have been hacked twice, but not since 2002. All these folks saying that security is easy haven't been hacked. Not being hacked doesn't mean a damn thing about how good their setups are. It just means
* nobody is interested, yet
* they have been hacked, but just haven't discovered it - this is the scary one.

There are too many reasons to list why **real security people** use single-purpose hardware for firewalls. The relatively "new idea" that virtual networks are just as good as physical networks will need ... er ... 20 more years of seasoning before they can be trusted.  This statement will tweak lots of people - especially those running at cloud providers claiming that a virtual router is just as good - after all, those routing devices run virtual routers too. Right?

In the end, it is YOUR decision to make.

I really like to see 1 CAT5e in and 1 CAT5e out - "green" and "red".  It is clear. Not too confusing. Hard to mix up and do much damage.  VM environments tend to get complex.  Under Linux, there are security issues sharing bridges between VMs. Without seeing the internal code AND understanding it, I'd want 1 physical connection per VM in a hostile environment. In a trusted environment, I'm willing to go a little further, but expect that traffic seen by 1 client can be seen by all the others on the same bridge.

I will say that in the last 12 months, I've deployed very small physical pfSense boxes [http://pcengines.ch/alix2d3.htm](http://pcengines.ch/alix2d3.htm) rather than going with a virtual machine solution at clients with minimal budgets.  **Just because you can do something, doesn't mean it is secure** or that it should be done.

Go ahead and test firewall VMs on a lab network, but never connect that to the internet.

Did you see that [VM attack]("http://arstechnica.com/security/2014/01/openssl-site-defacement-involving-hypervisor-hack-rattles-nerves/") last week?

---

