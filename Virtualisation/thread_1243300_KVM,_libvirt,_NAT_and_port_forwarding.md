---
title: "KVM, libvirt, NAT and port forwarding"
date: 2009-08-18
forum: Virtualisation
---

### Post by stephanhughson on 2009-08-18
Hi,

I've been using libvirt, KVM and virt-viewer successfully for a while now with bridged networking. It works really well.

I got a new dedicated server recently (for personal use) and wanted to do the same there, but unfortunately the dedicated server company don't support bridged networking. I thought a VLAN might solve the problem but they don't offer VLANs yet.

So... To my question...

It seems that libvirt provides quite a lot of network management stuff. I can setup the virtual machines on the "default" network it provides which gives IPs starting with 192.168.1.*.

Those machines can access the Internet by default without me touching anything. I can then forward ports from the public IP addresses I have using iptables rules.

The thing is, it only works when I type in these iptables rules once the virtual machines are already up. I suspect there is a lot of stuff libvirt/kvm/something is doing in the background and I don't want to mess with it.

What's the proper way to be doing this? I want to work with libvirt/kvm, not do my own thing which might mess it all up.

I far far far prefer the bridged networking setup which was a total piece of cake, but unfortunately I need to work out this method too.

Also, if I make my normal firewall script which flushes all rules and puts its own in, it makes the rules that libvirt seems to put in go away. Where can I get those rules and maybe add to them?

Thanks for your help.

---

### Post by bodhi.zazen on 2009-08-18
It depends on what you are wanting to de exactly, there are several ways to skin the cat.

The first, and probably easiest, if you wish to use bridged networking is to simply purchase additional IP addresses.

Most hosting companies allow this and the cost is minimal, a $10 one time fee is typical.

You then assign each VM a unique IP address.

I am guessing your hosting company is thinking of some other type of hardware bridge and not virtualization.

The other way to do things is to use a single public IP and assign your internal VM a private IP (10.0.0.xx). You then use some kind of a (reverse) proxy, for example a web proxy. Depends on the service you are wanting to run.

If you go the way you are speaking, configure iptables and assign static IP to your guests.

---

### Post by stephanhughson on 2009-08-25
Hi,

Thanks for the reply. Sorry I didn't see it earlier, I didn't get the notification e-mail.

In the end I changed supplier, so I've got a dedicated server now with another company that doesn't stop me using bridged networking and it "just works" which is great.

I did have multiple IP addresses previously, but they said I couldn't use a network bridge (in software) for security reasons, as each switch port could only have one MAC address speaking on it.

So it's all good. Thanks again for the help.

---

