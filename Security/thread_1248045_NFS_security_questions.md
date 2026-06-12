---
title: "NFS/ security questions"
date: 2009-08-23
forum: Security
---

### Post by methodtwo on 2009-08-23
Hi there
I've just set up NFS and i exported my home directory.In /etc/exports(on the server of course) i used this config
```
/home/me  192.168.1.0/24(rw)
```
Note that i used a range of I.P addresses because when i tried to set up a static I.P on the client it didn't work!
Could this be a security hole?.I mean could someone somehow find out my router's config and spoof that there packets came from an address in this range?.Is this possible?.If not are there any other security risks with my configuration of NFS?.Would it be safer with a static I.P address for the client?.Thankyou for your time

---

### Post by Rob_H on 2009-08-23
192.168.x.y addresses are not routable on the Internet. So no one can spoof such an address to gain access to your LAN.

---

### Post by methodtwo on 2009-08-23
So how do people gain access to a LAN with no open ports on the router and no sniffer with buffer overflow vulnerabilities?.Sorry for the dumb questions I'm a security n00b who got hacked recently!

---

### Post by methodtwo on 2009-08-23
Also i thought that they would just have to make the router think that the malicious packets were coming from an internal machine. Thus routable packets could seem like they were coming from another machine inside the LAN

---

### Post by Rob_H on 2009-08-23
> **methodtwo said:**
> So how do people gain access to a LAN with no open ports on the router and no sniffer with buffer overflow vulnerabilities?.Sorry for the dumb questions I'm a security n00b who got hacked recently!

A buffer overflow vulnerability is a different animal. It's an attack in which someone is able to run malicious code on your computer by exploiting a bug in a program you're using such as a web browser or PDF reader. Usually it involves you downloading some specially-crafted data from the Internet, which then gets processed by the vulnerable application. But if you are diligent about applying security updates when they're made available and you stick to visiting reputable web sites, you generally don't need to worry about these kinds of attacks.

If your computer is compromised through a buffer overflow attack, the attacker can then gain access to the LAN, naturally. But the success or failure of the attack has nothing to do with how your network is configured. The main problem is that your computer gets taken over.

---

### Post by Rob_H on 2009-08-23
> **methodtwo said:**
> Also i thought that they would just have to make the router think that the malicious packets were coming from an internal machine. Thus routable packets could seem like they were coming from another machine inside the LAN

No, it doesn't work that way. Most consumer routers have an external (WAN) port and several internal (LAN) ports. Since the router also acts as a firewall, unsolicited traffic from the WAN side gets blocked no matter what IP address it's coming from (spoofed or not). But even if the spoofed traffic were to somehow make it onto your LAN, a two-way connection would not be established because the target machine on your LAN would try to send a packet back to the spoofed address, but your router would see that it's destined for an internal address and wouldn't route it to the Internet.

---

### Post by Jack Waugh on 2011-03-19
I like to provide free Internet service to my neighbors via WIFI but don't want them to be able to mount my nfs shares.  What's the easiest security setup?

---

### Post by cariboo on 2011-03-19
Only allow specific ip addresses to connect, it probably means you need to setup static ip address for your internal network, and only allow those address to mount your nfs shares.

---

### Post by Jack Waugh on 2011-03-20
But I want the router to serve DHCP for the neighbors.  Can a typical router do that and still reserve certain numbers for my computers?

---

### Post by The Cog on 2011-03-20
Most DHCP routers allow you to specify a fixed reservation for a given MAC (hardware) address. I use this to fix the IP addresses of some of our computers. 

Even if not, you can (for instance) tell the DHCP server to issue numbers in the range 192.168.1.1-192.168.1.99 and then assign static IPs outside that range to your own computers.

---

### Post by SeijiSensei on 2011-03-20
> **Jack Waugh said:**
> But I want the router to serve DHCP for the neighbors.  Can a typical router do that and still reserve certain numbers for my computers?

You're going to be much happier if you use another router to serve your neighbors offering a different IP address space.  Another option is to add a second NIC card to the NFS server and put your machines behind it.  Add an iptables rule or alter the entry in /etc/exports so connections from those IP addresses are blocked.

If you must use only one router, then yes, you can usually specify a range of addresses that it will offer via DHCP.  For the machines that can connect to the NFS server, have the router give you static IPs based on MAC addresses.  Reconfigure /etc/exports to grant access only to machines with these pre-specified addresses.

If this all seems too complicated, you probably shouldn't be offering service to your neighbors unless you can trust them.  You might also consider whether any of them might download materials that run afoul of copyright or, worse, content laws.  You don't want the police showing up at your doorstep because one of your neighbors downloaded an image that might be construed as child pornography.

---

