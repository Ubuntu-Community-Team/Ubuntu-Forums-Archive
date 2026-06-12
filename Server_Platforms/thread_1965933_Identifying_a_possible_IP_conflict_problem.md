---
title: "Identifying a possible IP conflict problem"
date: 2012-04-26
forum: Server Platforms
---

### Post by azzamite on 2012-04-26
Hello forum

So Windows will pop a nice colorful message whenever there is an IP conflict, and it also save the information somewhere in its logs...

How can I tell from my GNU/linux server whether or not there is an IP conflict and if possible detect the culprit (get it's mac address, hostname or something)?

More information: I can(not) access the http and ssh services at random...

---

### Post by papibe on 2012-04-26
Hi azzamite.

If you are using dhcp, you may take a look ate the /var/log/daemon.log:
```
grep -i dhclient daemon.log
```

If you set a static address for your machine, that in itself could be the problem. I can see a couple of situations:
[LIST]
[*]Your router (or DHCP server) does not support static IPs.
[*]Your router support them, but the address you set is not in the range supported.
[/LIST]
I hope that helps, and tell us how it goes.
Regards.

---

### Post by azzamite on 2012-04-26
> **papibe said:**
> If you set a static address for your machine, that in itself could be the problem.

Yeah, the server uses an static IP... because it is the head node of a cluster we were provided with an unused external IP address for it...

AFAIK the DHPC server (which I have no access to) does NOT assign external IPs, however anyone here can just illegally use them anyway to bypass some restrictions from the switches... or something like that.

So I'm trying to figure out if linux logs somewhere the event that there is an IP conflict like other OSes does so that I can complain to someone about it randomly going offline :p

---

### Post by darkod on 2012-04-26
I wouldn't say using a public IP illegally is that easy. Unless you are connected to the correct router, you can set what ever you want on your computer/server, it will be invisible from the internet. It would be like a private IP in a way. Without correct gateway.

One thing to try is disabling the interface on your server and pinging the IP. If it returns a reply, it is configured somewhere else. But that would work only at the moment when you think you have a conflict. And if you can disable the interface.

---

### Post by SeijiSensei on 2012-04-26
Install nmap (sudo apt-get install nmap) and do a ping scan of the subnet in question:

```
nmap -sP 192.168.0.0/24
```

replacing 192.168.0.0/24 with the appropriate network address and mask.  It will try all addresses in the subnet and report back with the MAC addresses of all the machines it finds.

---

### Post by azzamite on 2012-04-26
> **SeijiSensei said:**
> ```
nmap -sP 192.168.0.0/24
```
I have been playing with that and the -A option, but it doesn't gives me enough information.

> **darkod said:**
> I wouldn't say using a public IP illegally is that easy. Unless you are connected to the correct router.
Yeah, that's the way this network is configured...

> **darkod said:**
> One thing to try is disabling the interface on your server and pinging the IP. If it returns a reply, it is configured somewhere else.
I wonder why that didn't occurred to me at all. Thanks, I just did and I'll make sure some MAC/person gets banned from the network tomorrow.

---

