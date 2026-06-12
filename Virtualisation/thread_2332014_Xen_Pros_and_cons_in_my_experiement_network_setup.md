---
title: "Xen: Pros and cons in my experiement network setup"
date: 2016-07-27
forum: Virtualisation
---

### Post by Marius_Hov_Lauritz on 2016-07-27
Hi everyone!

I have started experimenting with various virtualisation-solutions for Ubuntu server 16.04 lately. Have tried VMWare, KVM and Xen. I find Xen most interesting, and have got it up and running, and everything is fine.

But I'm experimenting with a solution with Xen where I got only one physical Linux-box loaded with Ubuntu 16.04 and Xen. This machine got 2 NICs.

Today this server is running with no virtual guests, and my plan is to sepparate the webserver, the mailserver, fileserver and so on to virtual installations. This is practical for security when upgrading so I don't crash the whole server, you all know what I mean...

What I'm curious about is pros and cons of a network setup like the one described below, and please feel free to give me some alternative solutions:

Old Physical network connections:
--------------------------------------
NIC1 (gives external IP) <- Fibre-modem in bridged mode
NIC2 <- Connected to Gigabit Cisco-switch and acts as router, DHCP-server and so on

Now my wish is to keep most in virtual machines, that includes the firewall/router. Have read a few documents about different solutions regarding this, and I think it has to be something like this in my setup:

NIC1 connected to fibre modem which gives external IP:
---------------------------------------------------------------
xenbridge0 -> eth0 in Guest1 Firewall/router and DHCP-server 192.168.0.10

NIC2 connected to fibre modem which gives external IP:
---------------------------------------------------------------
xenbridge1 -> eth0 in Guest2 Webserver 192.168.0.11
xenbridge1 -> eth0 in Guest3 Fileserver  192.168.0.12


I'm thinking about routing the needed ports back to the other virtual machines from the firewall/router-guest, for example port 80 to 192.168.0.11

Of course I could keep this simple and configure dom0 as the router/firewall, but I don't want that. I want dom0 to be kept as clean as possible, and simple to install if a move to a new physical server is needed. Of course, I need to be able to reach dom0 via SSH or something, but I guess that would be possible one way or another. But I think it's best to not expose it directly to the internet.

I hope you understand what I'm trying to do here, it's not that easy to explain...

Would it be a clear advantage to give each virtual machine it's own physical nic instead of this?

---

### Post by MAFoElffen on 2016-07-28
I think what you do is personal preference and technique... For example, comments on this are going to follow that.

My example on how mine is setup... I down-sized my foot print (or that was the original intent).

My servers are on their on subnet, so that traffic on it does not affect my main network. My first 2 kvm servers are also providing services of DNS and dhcp (primary and secondary). I could have put them into VM's, but thought that they provide services for more than just one VM host server and I didn't want all my eggs in the same basket.

Then there is my 2 Xen Servers-- One on LVM. Next on ZFS. Then there is my ESXi Servers. (I'll skip the netwroking on them...)

For networking sake (host & guests), KVM and Xen are the same. One my main, I use 3 NIC's. One is just host services. The other two are bonded as one device, and that one device is my bridge. The other 3 are just using 2 NIC's to do the same.

EDIT-- Ended the above as my Cisco class was starting... continuing:
I think what I think of, is what is the topology I want to create, and what I want VM Guests to have access to or "not"...

If you think of a virtual netwoork as just an extension to your existing network... that is basically what it is.

Do some guest need to be on the same network as your host? (host and internet) 
Do they need access to the internet, not on the same NID as your host? 
Do they just need to talk to other VM's?
Do you want to try to separate your broadcast domains to cut down traffic?

If you have a small private local network that the outside never sees, then putting everything onto your local netork via a bridge, would be OK. Some hobbiest never scale up enough to need anything beyond that.

If you also do online gaming and might be affected by any additional traffic on your local net... then you might want to look at what affects what and how to keep your bandwidth.
You know you can setup a virtual appliance (another guest) to act a a router and gateway to your host network.

---

