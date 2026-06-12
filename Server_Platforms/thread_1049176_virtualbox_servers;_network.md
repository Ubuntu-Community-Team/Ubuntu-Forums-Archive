---
title: "virtualbox servers; network?"
date: 2009-01-24
forum: Server Platforms
---

### Post by liniaal on 2009-01-24
Hi. i would like to hear someone's opinion on a thing called 'networking in virtualbox machines under ubuntu'. i've tried numerous solutions, wait a minute. what i want to do, is run some (sub)professional webserver as a test virtual machine on my workstation (i trust the machine to be powerful enough). i like debian as my server os. now lately i found this article: [https://wiki.ubuntu.com/VirtualBoxNetworking](https://wiki.ubuntu.com/VirtualBoxNetworking) and it seems to be one of the most recent, updated writings on the subject. sadly it doesn't seem to work.. if i have NetworkManager still running, do i need to get that out of the way first??

thx in advance

---

### Post by liniaal on 2009-01-24
do i need to substitute the POSTROUTING and/or MASQUERADE words?

---

### Post by liniaal on 2009-01-24
[http://pastebin.com/m5e2ba4ac](http://pastebin.com/m5e2ba4ac)

---

### Post by liniaal on 2009-01-24
ok, it works already. i made the ip static in the guest os and now i can suddenly ping both ways. thanks ubuntu ;) :D

---

### Post by dmdevotee on 2010-12-23
anybody knows if VM can see each other (ping between guests) this way? thanks!

---

### Post by HermanAB on 2010-12-23
Howdy,

Configure each VM ethernet as Bridged, rather than NAT, then the VMs will behave exactly like standalone machines.

---

### Post by cc48510 on 2010-12-27
> **HermanAB said:**
> Howdy,

Configure each VM ethernet as Bridged, rather than NAT, then the VMs will behave exactly like standalone machines.

Just to note, you should probably have separate NICs for each VM that needs to accept inbound connections. When I tried running 2 VMs [bridged] on the same NIC, they became inaccessible.

At home, I use 2 virtual NICs. The first (eth0) I set up as NAT so that I can access the repositories. The second, I set up bridged to a 2nd NIC, which is connected a 5-Port Linksys switch. I simply hook my laptop into the switch and use it as a client [to access the VM Server].

---

