---
title: "Virtualizing a gateway"
date: 2009-01-22
forum: Virtualisation
---

### Post by Arukas on 2009-01-22
I have been trying to learn how to setup a gateway/router/firewall as a learning experience.  And my setup doesn't make thing very easy.  I had a thought, if could do the initial setup virtual, it would help greatly.  

So my question is can I do this?  Can I get a virtualization setup like that and run?

---

### Post by veloce on 2009-01-22
> **Arukas said:**
> I have been trying to learn how to setup a gateway/router/firewall as a learning experience.  And my setup doesn't make thing very easy.  I had a thought, if could do the initial setup virtual, it would help greatly.  

So my question is can I do this?  Can I get a virtualization setup like that and run?

As a learning exercise, virtualisation is perfect for this.  For example, when I was playing with vms initially, I set up a virtual firewall between my vms and the rest of the work network.

I did this by having all my vms connected only to the "host only" virtual network except for the firewall which had two connections: "host only" and "bridged". 

You could even set up two (or more) "host only" networks to mimic two parts of a network that you want to connect via a gateway.

The only trap I ran into was turning off vmware's dhcp server.

---

### Post by Arukas on 2009-01-22
Does VMware do a good job or this?  From my understanding networking is the big difference between the VMs.

---

### Post by veloce on 2009-01-22
> **Arukas said:**
> Does VMware do a good job or this?  From my understanding networking is the big difference between the VMs.

Yes vmware is good for this - it's virtual networking capabilities are powerful.  However, I don't have any experience with any others so can't say whether they are better or worse.

---

### Post by Dedoimedo on 2009-01-23
Hello,
Excellent idea. Definitely go virtual.
VMware network stack is solid, it makes for an excellent test case.
Dedoimedo

---

### Post by Arukas on 2009-01-23
What is it I have to configure to make the virtulize OS have its own IP.  I'd like to be able to talk to other real computers.

---

### Post by dcstar on 2009-01-25
> **Arukas said:**
> What is it I have to configure to make the virtulize OS have its own IP.  I'd like to be able to talk to other real computers.

In VMWare Server you just use Bridged networking for the VM, then the IP is whatever you set it to in the VM (just like any "real" machine).

---

### Post by Dedoimedo on 2009-01-25
Hello,
You don't have to use bridge. You can also use NAT. But then you have to configure the host to forward requests and setup firewall rules, if any, for forwarding between different network adapters.
Dedoimedo

---

### Post by Arukas on 2009-01-25
The problem I have been having is I have been setting up with a bridge, but for some reason, I can't even access the internet, and even sharing the host ip don't work.  

I've had it working before a long time ago, but I'm upgraded my computer since then and reinstalled everything, and its become annoying.

---

### Post by veloce on 2009-01-25
> **Arukas said:**
> The problem I have been having is I have been setting up with a bridge, but for some reason, I can't even access the internet, and even sharing the host ip don't work.  

I've had it working before a long time ago, but I'm upgraded my computer since then and reinstalled everything, and its become annoying.

Okay, network troubleshooting 101:

1. Find the ip address of your vm (run ifconfig in terminal)

Does it have one?


2. Find the ip address of your host

Are the host and vm in the same address space?  If not, how did the vm get it's ip address?  You should be able to use the same dhcp server that supplied the host - is that working?

3. attempt to ping host from vm and vice versa

Does it work both ways?

Let us know how you get on.

---

### Post by Arukas on 2009-01-25
I just realized something, I've been networking on 8.10 has been an issue so far, and I was using 8.04, I may have to change version, if I don't get things working the way I want them to work. 

I'll let you know.

---

### Post by dcstar on 2009-01-25
> **Arukas said:**
> The problem I have been having is I have been setting up with a bridge, but for some reason, I can't even access the internet, and even sharing the host ip don't work.  

I've had it working before a long time ago, but I'm upgraded my computer since then and reinstalled everything, and its become annoying.

Run the vmware-config.pl again and **double check** that the network settings are not defaulting to eth0 when in fact it should be eth1 (or whatever your "real" interface is).

---

### Post by Arukas on 2009-01-26
I've fix the network on my computer, however, the network still isn't working.

I can't ping each vm or host either way, and its on the right network cards.  I know when I first installed this, there was nothing to it.

---

### Post by veloce on 2009-01-27
> **Arukas said:**
> I've fix the network on my computer, however, the network still isn't working.

I can't ping each vm or host either way, and its on the right network cards.  I know when I first installed this, there was nothing to it.

What are the IP addresses?

---

### Post by Arukas on 2009-01-27
the VM has a 198.162.112.1 address

---

### Post by veloce on 2009-01-27
> **Arukas said:**
> the VM has a 198.162.112.1 address

And the host?

Are they getting addresses from a dhcp server?

It might save time if you post the output of ifconfig / "ipconfig /all" on each machine.

---

### Post by Arukas on 2009-01-27
My host computer is fine, its on a network and working fine.  I'll post the ifconfig if you'll thing that'll help.

My host computer is assigned a static ip address.  I think the VM is dhcp, because the third octet isn't the same as the static IP

---

### Post by veloce on 2009-01-28
> **Arukas said:**
> My host computer is fine, its on a network and working fine.  I'll post the ifconfig if you'll thing that'll help.

My host computer is assigned a static ip address.  I think the VM is dhcp, because the third octet isn't the same as the static IP

If the third octet is different then they are on different subnets - which will be at least part of the problem.  Check that the vm's virtual ethernet card is connected to the "bridged" subnet.  If it is, then you have a rogue dhcp server somewhere on that network giving bogus addresses.

You could try setting the vm's ip address manually, so long as you know an address on the same subnet as the host that is not in use.

---

### Post by Arukas on 2009-01-28
That sheds some light, and i'll see what I can do with it.

---

