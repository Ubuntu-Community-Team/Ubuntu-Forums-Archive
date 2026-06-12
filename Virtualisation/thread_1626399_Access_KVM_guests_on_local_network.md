---
title: "Access KVM guests on local network"
date: 2010-11-20
forum: Virtualisation
---

### Post by Neil Stoker on 2010-11-20
Hello,

I wonder if someone could help point me in the right direction with a KVM problem I'm having.

I guess it's best I describe my set up and then what I'm trying to acheive.

The computer set up is:
1. A Server (running Ubuntu 10.10 Server) - this hosts several KVM guests
2. KVM guests - OS will vary, but I'm currently focused on Ubuntu server VMs
3. A Laptop (Ubuntu 10.04 Desktop)

The server and laptop are both connected to the local network directly and are set up for static IP addresses internally on the network (i.e. I'm not trying to give them an external static IP address).  Both computers appear on the list of connected devices in my broadband router.

The KVM guests are started via Virtual Machine Manager from the laptop which I start with:
  **virt-manager -c qemu+ssh://main@192.168.0.8/system**

The server has a public bridge set up, pretty much as per here:
[http://www.linux-kvm.org/page/Networking#public_bridge](http://www.linux-kvm.org/page/Networking#public_bridge) and here: 
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

What I would like to achieve is to be able to have the guests show up on the local network so that services can be used from the laptop.  Possibly this may mean them get their IP addresses from the DHCP on the broadband router (although I don't mind about this - if a static IP is easier, it's not concern).

At the moment I can only ping the guest from the host (the server) and not from the laptop.

I believe I may need to set up a tap and then configure a route as per the latter part of the instructions on the KVM page above, but I am not sure how to set the tap up.

I've tried various things, without any luck, but if you have any sensible suggestions I'll try to give them a shot!

Incidentally in a work/Windows environment (using Virtual PC), I was able to achieve something similar and it "just worked" (in that I didn't need to configure anything once I'd said to use a shared network).  In that case, the IP address of the guest was in the same range as all the other PCs (e.g. the host was say 172.122.**0.54** and the VPC was say 172.122.**0.89**)

In Virtual Machine Manager the default was to set up the IP of the guest in a different range to the host/laptop (e.g. host/laptop are 192.168**.0.**7 and .8, whereas the guest was given something like 192.168**.122.**87) I found out how to change the range, but it can't be the same as the physical PCs (even if I tell it not to overlap with existing allocated IP addresses)

Thanks,
Neil

---

### Post by Neil Stoker on 2010-11-21
I solved my own issue - embarrassingly enough it was right under my nose and I simply needed to apply a step that was shown in here regarding existing VMs: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

At the time I read it, I didn't have any existing VMs and only produced them later (in Virtual Machine Manager), so it's not completely foolish (I hope!), but Virtual Machine Manager clearly wasn't allowing the necessary steps later to allow me to use the bridge when I assumed it would (my fault).  The step I needed to do was go into the VM's XML file under /etc/libvirt/qemu and edit the interfaces section to be of type "bridge" (in *both* places where it refers to bridge, as per the instructions in the link above), then define the VM again from the XML and restart it.  Then when I restarted the VM is showed up on my main (real) network with an IP similar to that of the laptop, visible and ping-able from the laptop and showing on my broadband router as being connected.

It's certainly not a criticism of the KVM help written up in various places and I'm very grateful, but it's a topic prone to pitfalls since there are so many scenarios people desire for their particular set ups and I get the impression the instructions often will make more sense to those writing them since they may not spot the ambiguities (e.g. "Do step X" - on the host or the VM?).  The lesson for me is to read everything **very** carefully!! (which usually try to do, but slipped up on here! :) )

---

