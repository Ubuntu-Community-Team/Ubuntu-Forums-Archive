---
title: "Troubleshooting Ubuntu Server WAN connection problems."
date: 2010-09-14
forum: Server Platforms
---

### Post by crayonfingers on 2010-09-14
Hi there

I've just installed Ubuntu on a virtual machine with the LAMP package, but am unable to make any connection to the outside world.

When I try pinging a domain name, the IP is resolved, however it always returns 'host unreachable'.

The server receives its connection from a router, but has a static IP address. Every other system on the network is Windows based, and there are 3 separate domains.

I am unsure whether it is a DNS error, router problem or something else and would appreciate some pointers as to how a Linux newbie might be able to  diagnose this problem.

Thanks for any help.

Simon

---

### Post by CharlesA on 2010-09-14
Post the output of these commands please:

```
cat /etc/network/interfaces
```

```
ifconfig
```

```
route
```

---

### Post by crayonfingers on 2010-09-14
[IMG]http://www.c1systems.co.uk/stuff/1.PNG[/IMG]
[IMG]http://www.c1systems.co.uk/stuff/1.PNG[/IMG]

[IMG]http://www.c1systems.co.uk/stuff/3.PNG[/IMG]

---

### Post by CharlesA on 2010-09-14
Is this a machine on the internet or on a private network?

Private IP addresses for class C are 192.168.x.y with a subnet of 255.255.255.0.

It shouldn't have a 192.1.1.x address for a machine not on the internet.

Can you do an ifconfig /all from a windows machine and post the output?

---

### Post by crayonfingers on 2010-09-14
Hi Charles

Yes, I thought you'd comment on that. The IT Manager for our parent company for some reason set the IP address range from 192.1.1.1.

It's ridiculous, but it's apparently been like that for years and he won't change it to a private address range.

I operate a different domain within the network, but have to use the same IP range for each of my servers and desktops as we use some of the parent company's resources ( the router itself, which is 192.1.1.5 and also the ERP server).

192.1.1.22 is the W2008 DNS/AD server that controls my domain. I thought originally that it may be a problem with the DNS server and active directory authentication (didn't think it needed it if it wasn't joining the domain), so I tried changing the Ubuntu server to use the ISPs DNS like the other systems on the network, however this gave the same results. Here's one of my windows systems, and the routers config.

[IMG]http://www.c1systems.co.uk/stuff/4.PNG[/IMG]


[IMG]http://www.c1systems.co.uk/stuff/5.PNG[/IMG]

---

### Post by CharlesA on 2010-09-14
Ugh. It should be ok, but I wonder if the addressing scheme is screwing it up.

Try running traceroute to google.com and see what it says.

tracert from a windows box as well.

---

### Post by crayonfingers on 2010-09-15
Hi there, after much huffing and puffing, I eventually managed to get it to work.

The issue, strangely, was having /etc/network/interfaces eth1 set to auto instead of manual. Changing this resolved the issue.

---

### Post by CharlesA on 2010-09-15
> **crayonfingers said:**
> Hi there, after much huffing and puffing, I eventually managed to get it to work.

The issue, strangely, was having /etc/network/interfaces eth1 set to auto instead of manual. Changing this resolved the issue.

Interesting. So it's using DHCP now, instead of having a static IP set?

Glad it's working now, that's pretty strange. I'm guessing it's due to the way the network is setup.

Don't forget to mark the thread as solved. :)

---

