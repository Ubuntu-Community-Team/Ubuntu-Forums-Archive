---
title: "NAT 2 NAT for VNC server"
date: 2013-12-13
forum: Server Platforms
---

### Post by mbnoimi on 2013-12-13
Hello,

Does any one know any NAT 2 NAT server?

I want to use a remote the desktop by VNC in similar way to TeamViewer because -as you know- it's impossible to access any remote desktop by VNC behind NAT router so I need to use a relay to fix this issue where Logmein and TeamViewer offer this solution for free (and commercially too) while I'm looking for an open source solution

---

### Post by volkswagner on 2013-12-13
I'm not sure about your server/client requirements.  If you have one or two locations with machines you'd like to access, [Guacamole]("http://guac-dev.org/") may be of interest.

Please offer more information about how you'd like to utilize the setup.  How many servers and clients? How many locations?  Do you want to utilize this
as a support for many vnc servers?

---

### Post by nerdtron on 2013-12-13
Does you router have public IPs? You can use port forwarding.
Do you have a public facing server on your LAN? You can create an openvpn server/client setting and then use the tunnel for point-to-point connectivity.

---

### Post by SeijiSensei on 2013-12-15
> **nerdtron said:**
> You can create an openvpn server/client setting and then use the tunnel for point-to-point connectivity.

That would be my suggestion as well.  Use a [static-key configuration]("http://openvpn.net/static.html") for simplicity.

---

### Post by mbnoimi on 2013-12-25
> Please offer more information about how you'd like to utilize the setup. How many servers and clients? 
In case I found a solution works in same way of TeamVierwer I suppose I've one server (the relay) and tens of clients (each two clients connect together one of them control the other)

> How many locations? Do you want to utilize this
as a support for many vnc servers?
The locations aren't specified and as I said above I consider there are one server works as a relay just for connecting two PCs which one of them control the other.

Now I wonder what if your suggestion ([Guacamole](http://guac-dev.org/)) may work in the architecture I mentioned above (simply I want an alternative to TeamViewer).
As I understood from [Guacamole Architecture](http://guac-dev.org/doc/gug/guacamole-architecture.html); it consider the server is the computer where all the users connect to by different protocols... does it?

So in case of using Guacamole; Does PC1 can controls (remote desktop) PC2 and vice versa (where both of them are connected to Guacamole)?

See the map I've imagined:
[img]http://img607.imageshack.us/img607/9779/8y2k.png[/img]

---

### Post by mbnoimi on 2013-12-25
>  Does you router have public IPs? You can use port forwarding.
Do you have a public facing server on your LAN?
No, both networks are behind a proxy and both of them don't have public IP

> You can create an openvpn server/client setting and then use the tunnel for point-to-point connectivity. 
OpenVPN doesn't solve my problem because this issue related to NAT to NAT.
TeamViewer and LogmeIn fix this issue because both of them offer relay server so in case any PC from NAT1 want to remote desktop its content it send the data to the relay (ex. LogMeIn server) then the relay redirect the data to the target PC on NAT2

---

### Post by mbnoimi on 2013-12-25
> **SeijiSensei said:**
> That would be my suggestion as well.  Use a [static-key configuration]("http://openvpn.net/static.html") for simplicity.

Well, I never tested OpenVPN static key, I'll try to apply it to see what if it will work or not.

---

### Post by volkswagner on 2013-12-26
As you can see from the Guacamole Architecture map... I don't think you can traverse a connection from PC1 to PC2.  You will need a Guacamole server
behind each NAT that you want to connect to.  You'll also need access to running web server at each NAT or access to open port for Guacamole.


You may want to check out [PortFusion]("http://sourceforge.net/p/portfusion/home/PortFusion/").

---

### Post by SeijiSensei on 2013-12-27
> **mbnoimi said:**
> OpenVPN doesn't solve my problem because this issue related to NAT to NAT.

OpenVPN tunnels can work through a NAT on one end, the client, but the server needs to be publicly visible.  You could use port forwarding to expose the server's port.

I run a number of tunnels that connect to my publicly-visible server sitting at Linode.  Many of the clients are behind NATs, but the server is out on the public Internet.

---

