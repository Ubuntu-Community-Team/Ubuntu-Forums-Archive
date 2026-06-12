---
title: "Setting up LTSP server on a subnet of a larger network"
date: 2013-08-08
forum: Server Platforms
---

### Post by terabyte128 on 2013-08-08
Hello all!

I am trying to get my school to give Edubuntu a try instead of Linux, and as a transition step/small-scale step, I'd like to set up computers in one room to use Edubuntu. They are all connected to the same switch and then to the larger network.

[ATTACH=CONFIG]245191[/ATTACH]
Here is a diagram of what it currently looks like.

[ATTACH=CONFIG]245192[/ATTACH][SIZE=5][SIZE=2]
[/SIZE][SIZE=2]And here is how I'd like to configure it.
[/SIZE][SIZE=2]
Given that, for their Windows machines, the school runs a PXE ghosting server on their larger network, is it possible to configure Ubuntu such that one network interface (the one connected to the larger network, let's call it eth0) gets internet and login services from there, and that the other one (call it eth1) is acts as a gateway for the smaller subnet in the classroom? 

Eth0 would keep the classroom computers connected to the school network and allow them to login via LDAP.
Eth1 would run DHCP, DNS and an LTSP server for the computers in the classroom so that the PXE services of the LTSP server wouldn't interfere with the school's ghost server for Windows. 

Is this possible? 
[/SIZE]
[/SIZE]

---

### Post by SeijiSensei on 2013-08-09
Sure.  

First, if you really are going to run LTSP, then you shouldn't need to do any special since the clients are all running sessions on the server itself.  If the server can see the Internet, the LTSP clients will be able to as well.  You will probably want to have at least 4 GB, and preferably 8 GB, on the server to accomodate the parallel sessions.

However, let's assume you go the route of installing Linux on the workstations behind the gateway rather than using LTSP.  Then you will need to enable IP packet forwarding on the gateway machine by uncommenting "net.ipv4.ip_forward=1" in /etc/sysctl.conf.  You'll need to reboot to put this change into effect.

You'll also need an iptables rule like this:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source ip.addr.of.eth0
```

replacing "ip.addr.of.eth0" with the address assigned to that interface.

I presume the default gateway on this box points upstream to the rest of the campus network.  You'll probably be best served by assigning addresses to your workstations entirely outside your school's network subnets.

---

### Post by terabyte128 on 2013-08-09
Will enabling IP packet forwarding automatically figure out which network interfaces to forward between, or is that what the iptables rule does?

I didn't even consider that if they're using LTSP they just see what the server sees, that's perfect. Thanks. I think that's what I'll end up doing because the workstations are pretty old and slow, plus that way we don't have to erase their hard drives to do it. 

If LTSP is just a session on the server, would that mean that any sort of login services the school district uses (like LDAP) when installed on the server will allow workstation clients to log in using them too? That makes things so easy :D

Thanks!!

---

### Post by SeijiSensei on 2013-08-11
> **terabyte128 said:**
> Will enabling IP packet forwarding automatically figure out which network interfaces to forward between, or is that what the iptables rule does?

No, that's what routing does.  On a "multi-homed" machine, Linux will automatically set up routes for the subnets to which each interface is connected.  The "default" route handles packets destined for addresses outside your network; in your case they would be forwarded to the school's upstream router.

> If LTSP is just a session on the server, would that mean that any sort of login services the school district uses (like LDAP) when installed on the server will allow workstation clients to log in using them too? That makes things so easy :D

I don't know since I've never used LTSP, though it seems likely that it would.  I presume the clients are authenticated using whatever mechanism the server uses.  Just use [pam_ldap]("http://www.padl.com/OSS/pam_ldap.html") for authentication.

---

### Post by newbie-user on 2013-08-13
> **terabyte128 said:**
> If LTSP is just a session on the server, would that mean that any sort of login services the school district uses (like LDAP) when installed on the server will allow workstation clients to log in using them too?

Yes. Just make your LTSP server to pull accounts from your LDAP server. We retired our LTSP installation a while ago, but that's how it was set up. Just install libpam-ldap to the server and make sure your ldap.conf and nsswitch.conf are set up correctly.

---

