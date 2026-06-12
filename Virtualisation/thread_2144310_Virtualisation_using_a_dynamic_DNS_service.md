---
title: "Virtualisation using a dynamic DNS service"
date: 2013-05-11
forum: Virtualisation
---

### Post by OR83 on 2013-05-11
Does Virtualisation for multiple websites still work the same if I'm using a service like DynDNS or FreeDNS? or do I have to do some other modifications?

---

### Post by heiko_s on 2013-05-12
> **OR83 said:**
> Does Virtualisation for multiple websites still work the same if I'm using a service like DynDNS or FreeDNS? or do I have to do some other modifications?

I would give it a try first before committing: [http://dyn.com/dns/dyndns-pro-free-trial/]("http://dyn.com/dns/dyndns-pro-free-trial/")

I understand from the dyn.com website that they use a client to report changes of the IP address to their DNS server. It should work as long as these requirements are met:

1. They have a client for your VM (if you run Ubuntu in the VM, they need to provide you with a Linux client);
2. The client is able to figure out your router's IP address (that is, it needs to handle NAT).

The network setup under Xen and probably other virtualisation solutions typically offer a layer 2 configuration, that is network bridging. So when you set up multiple VMs connected to a bridged network, you can give each one its own IP (I use the DHCP server on my router to assign the IPs, but you can also use static IP). BUT, if your PC is connected via a router to the Internet, these IP addresses are local IP addresses of the private network.

I would expect the client to handle this, as most people connect to the Internet via a router (if not, it's their loss).

To make a long story short, when you connect your VMs using a bridged network, each VM acts exactly like a discrete (hardware) PC, having its own (virtual) Ethernet port with its own IP. So yes, it should just work.

---

### Post by OR83 on 2013-05-12
I'm running Ubuntu on an actual Dell server and I've given a try at noip.com which is fine for $15/year but their client won't download, I've also given a try at DynDNS I subscribed and honestly I think it's over priced at $30/year, and their ddclient won't configure right, and finally I've used FreeDNS.afraid.org and they have no client and as the name suggests it's free and I all I had to do was port forward my router and it works fine as far as I know. But what I don't know is if I make a folder for each website would it and DynDNS be able to go to the right one. Like if I have example1.com and example2.com and I want to go to example2.com and instead it takes me to example1.com

---

### Post by heiko_s on 2013-05-13
You got 1 public IP address (the one assigned to the router), and want to run 2 or 3 different web sites. The problem is that with http you would use port 80 for all sites, so example1.com would be identified with public IP + port 80, but so would example2.com etc. Unless you run different services for each website, **or the dynamic DNS provider is able to translate port numbers**.

If the dynamic DNS provider is able to translate 'www.example1.com' 'port 80' to 'your public IP' + 'port 5001', and 'www.example2.com' 'port 80' to 'your public IP' + 'port 5002', then you are good to go.

To put it in different words, if your dynamic DNS provider is able to serve different websites having the same IP address, you are good to go.

For all practical purposes, your different virtual machines on one physical server are the same as if you had a different physical server for each VM/website. (I assume you intend to run each website on a different VM?)

---

### Post by mujahied on 2013-05-13
i used this on my vm and it worked that time try to see if this is what u need 
[http://www.debianadmin.com/bind-dns-server-web-interfacefrontend-or-gui-tools.html](http://www.debianadmin.com/bind-dns-server-web-interfacefrontend-or-gui-tools.html)

---

### Post by OR83 on 2013-05-16
Thanks to both I got it. I configured Apache to run a Name-based configuration instead of IP based.

---

### Post by heiko_s on 2013-05-16
Great - that sounds like a good solution.

---

