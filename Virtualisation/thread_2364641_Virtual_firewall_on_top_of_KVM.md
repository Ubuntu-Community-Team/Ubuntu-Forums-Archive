---
title: "Virtual firewall on top of KVM"
date: 2017-06-26
forum: Virtualisation
---

### Post by jefkebazaar2 on 2017-06-26
Hello,      

I plan on running a dedicated firewall distro, but I want to run it in a KVM VM.   


I have a machine with 2 NIC's, which I intend to assign to WAN and LAN. However, both NIC's do not support VT-d, so PCI-passthrough is a big no-go.
  Therefore, I had the setup in mind of using a macvtap in private mode for the WAN-interface and a standard bridge for the LAN-interface.  

I was just wondering: what do I do with that WAN-interface? Let's say it's called eth0 and there's a macvtap in private mode linked to it, which gets the firewall WAN interface assigned.  
How do you configure the eth0-interface itself in the linux host? Do you set it to manual mode, thereby not assigning it an IP? 
Do you give it an IP, static or DHCP? 
Do you protect it also with IPTABLE rules?  

I'm just wondering, how do you implement this type of setup securely that protects both the host and the virtual firewall guest from the WAN-side?   


Any advice you can give is appreciated!

---

### Post by KillerKelvUK on 2017-06-26
Hey, last time I tried this I believe I set the host net interface to manual and then configured the rest on the guest i.e. all IP config in the guest only.  Regards whether this is statically or DHCP assigned this is entirely your choice and dependant upon the circumstances however I would suggest that based on your use case you'd want the WAN interface of your router/firewall vm to be static so that you can apply rules to it specifically.  However this will depend on whats on the other side of that WAN interface i.e. will the interface connect the router/firewall guest to an internet gateway i.e. a modem or home router or does your internet provider give you an ethernet connection (RJ45)?

As for applying IPTABLE rules to it specifically...I'll dodge this one for someone better informed to answer however I will offer that I suspect this is the purpose of the router/firewall VM to configure i.e. provide you an interface to setup rules ergo directly configuring IPTABLES I suspect is not a requirement but then I'm often wrong.

---

### Post by TheFu on 2017-06-29
> **jefkebazaar2 said:**
>  I'm just wondering, how do you implement this type of setup securely that protects both the host and the virtual firewall guest from the WAN-side?   

Someone has to say it. Guess it will be me.

I don't believe there is any method secure enough to place a WAN-facing firewall inside a VM. The idea is flawed, IMHO.  VMs are neato, but not necessarily secure.  VM breakout techniques are learned all-the-time.  There must be 100 that haven't be published, at least 100, probably more.  If you want to use a VM as a firewall, the only secure method I know is to never connect it directly to the internet.

I do use a VM-based router/firewall on our internal LAN to segment servers, guests, kids, and my office. It is just easier and faster to deploy, but I'd never trust any VM to be secure enough for WAN protection.  It doesn't pass my *smell* test. It just smells bad - like when people think putting passwords into a web-based password manager is a good idea - doesn't that *smell bad* too? 

Considering that a $150 device can provide a great, strong, maintainable, patched, router with the best security we know, why risk it?  There are cheaper ($50-$90), solutions that have 10/100 ports, while retaining the same great, strong, maintainable, patched, router deployment.  Ebay has some Firebox Core-e: X550e, X750e devices for cheap.

Hopefully, this post isn't offensive. Really just felt the statement was needed.

---

### Post by Michael_McKenney on 2017-06-29
I played with Barracuda's virtual firewall solution.   The only way I could really secure a virtual firewall was to use very complex ACLs on the network switches and set it in VLAN 40 and isolating the VLAN to two virtual NICs.   One ingress and egress.   I was still able to hack my way around it.    

You could install it on its own physical server with VMware 6.0 hypervisor running on it.  You can install it for free.   You use two NICs for ingress and egress.  The issue is can you get around it through hacking the hypervisor.   I ended up with a Fortinet physical firewall.   I have a 800D in my data center and a 60E at home.  60E has 10 routing ports and same firewall software for $1500.

---

