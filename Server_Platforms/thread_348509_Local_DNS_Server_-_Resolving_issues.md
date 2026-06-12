---
title: "Local DNS Server - Resolving issues"
date: 2007-01-28
forum: Server Platforms
---

### Post by maclaxguy on 2007-01-28
Hey all, I could use some help if anyone can...

In my local network, I've got an Ubuntu box at 192.168.1.105 setup as a DNS server.
I setup my router (192.168.1.1) to have the DNS as 192.168.1.105

The computers on the network take forever to resolve addresses.  Dig reveales that I'm getting the error
> ;; reply from unexpected source: 192.168.1.105#53, expected 192.168.1.1#53

I understand that I can put "nameserver 192.168.1.105" in /etc/resolv.conf to fix this problem, but I'd like another solution, as setting up each client like this is not optimal.

Is there some way to overcome this?  To have the DNS server route it's result back through the router instead of directly to the other computers?

I'd really appreciate any insight anybody could give me about this.


Thanks!

---

### Post by Stephen Howard on 2007-01-28
It sounds like your router hasn't been told that it (or rather, your ISP) isn't supposed to provide the dns service.  Log in to the router and see if there's a dns option setup wrongly.

Additionally, if its a small lan, maybe you turn off the local dns server and rely on Zeroconf for the .local domain?  Then you could setup nsswitch.conf so that zeroconf resolves names for .local, while the router does dns for the internet.

---

### Post by Stephen Howard on 2007-01-28
PS:  just for diagnosis, have you confirmed that specifying the nameserver in resolv.conf does actually fix the problem?

PPS:  Can you be more specific as to why using resolv.conf isn't acceptable in your configuration?

---

### Post by maclaxguy on 2007-01-28
> **Stephen Howard said:**
> PS:  just for diagnosis, have you confirmed that specifying the nameserver in resolv.conf does actually fix the problem?

PPS:  Can you be more specific as to why using resolv.conf isn't acceptable in your configuration?

I have verified that specifying the nameserver in resolv.conf fixes the problem.

It's not that it's unacceptable to do this, but I'd rather not have to deal with configuring all the computers.  I was hoping there was a more transparent way to get this to work.

RE your other post, I the primary DNS is set to 192.168.1.105 on my router config page.


Thanks

---

### Post by Stephen Howard on 2007-01-29
> It's not that it's unacceptable to do this, but I'd rather not have to deal with configuring all the computers. I was hoping there was a more transparent way to get this to work.

The router's dhcp section might  have options that let you assign a lan-wide hostname and IP-address to each MAC on the lan.

Alternatively, you could change the dhcp.conf file on your local nameserver so that it supersedes the router's one.  Can you provide a cat of /etc/dhcp.conf?

---

