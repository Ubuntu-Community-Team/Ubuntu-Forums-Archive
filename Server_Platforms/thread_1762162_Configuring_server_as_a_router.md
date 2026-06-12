---
title: "Configuring server as a router"
date: 2011-05-18
forum: Server Platforms
---

### Post by racheleson on 2011-05-18
Hi!
    I have a situation here. I am working with 2 networks. The server can connect to internet while the host in the network cannot. I want that the host can connect also to the internet through the server. How can I do this? What are the configuration files to be touch so that the clients or host can connect to the intenet? By the way, I am using the command line interface.
    Thank you!




weak24

---

### Post by jamesjenner on 2011-05-18
G'day,

I'm not sure what you mean by two networks. Do you have two separate subnets? Your server will need two network ports, one to the modem and one to your switch for the network. If you have two networks then you will need three network ports on your server.

Normally the server install gives you the options for what you need to allow this. I personally don't use Ubuntu server for a gateway, I use IPCop as a linux based gateway with the adv proxy plugin to give me a lot of control over white and black lists. 

I do highly recommend IPCop, it's a very painless process to setup if you wish to run a server as a gateway. Mind you, this would be a dedicated gateway.

Generally for SOHO, you'd use a dedicated hardware based gateway. Though no reason why you cannot do this via a server.

Cheers,

James.

---

### Post by Lars Noodén on 2011-05-19
> **racheleson said:**
> I want that the host can connect also to the internet through the server. 

[IPTables](https://help.ubuntu.com/community/IptablesHowTo) can make  the server into a [gateway](http://www.debian-administration.org/articles/23) for you.

---

### Post by HugoSerrano on 2011-05-19
Hi!

I see that you got other post about proxy. I don't know if you ever looked to some appliances that can help you with your job. 

What your are doing it's good for the learning process, but to manage it may not be easy.

take a look at:
- zentyal;
- pfsense;
- clearos.

There's more solutions, but this will get you on the road!

Best Regards!

---

### Post by YesWeCan on 2011-05-19
> **racheleson said:**
> Hi!
    I have a situation here. I am working with 2 networks. The server can connect to internet while the host in the network cannot. I want that the host can connect also to the internet through the server. How can I do this? What are the configuration files to be touch so that the clients or host can connect to the intenet? By the way, I am using the command line interface.
    Thank you!

It's not too hard:
1) You need to tell the kernel to allow packet forwarding. Nothing will work until you have done this.
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
(edit /etc/sysctl.conf to make this permanent)

2) You need to ensure the firewall allows forwarding.

3) You need to enable masquerading for outgoing packets.
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

4) You need to tell your client PC that the server's IP is its gateway. The server should have a static IP address.
sudo ip route add default via 192.168.0.x

5) If you want your client PC to know where to find a DNS service (converts text urls into numerical IP addresses) then you either need to tell the client the IP address(es) of the DNS server(s) (/etc/resolv.conf) or you need to set up a DHCP service on the server so the client can ask the server for the DNS info.
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)


see also: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by elico on 2011-05-19
as [YesWeCan]("http://ubuntuforums.org/member.php?u=934104")...
there is no problem using a server as a multitask server such as web+gateway+mail+proxy+antispam+sql and other services.
this is the whole idea of SMB windows server version.
you just need the proper hardware for the server.

---

### Post by SeijiSensei on 2011-05-19
> **YesWeCan said:**
> 3) You need to enable masquerading for outgoing packets.
sudo iptables -A POSTROUTING -t nat -j MASQUERADE


Generic masquerading can make it difficult to diagnose routing problems.  I generally include interface definitions in the masquerade command as well.  If eth0 points to the Internet, and eth1 connects to the internal network, I recommend using:

```
iptables -A POSTROUTING -t nat -i eth1 -o eth0 -j MASQUERADE
```

This only masquerades outbound traffic and leaves internal traffic alone.

If you use a transparent proxy like squid, you'll need to put this command after those that redirect web traffic to the proxy.

---

### Post by YesWeCan on 2011-05-19
Agree @ SeijiSensei

---

### Post by brettg on 2011-05-21
If you are still having trouble, try configuring your router using [this guide]("http://tuxnetworks.blogspot.com/2011/02/howto-configure-ubuntu-as-router.html")

Cheers

---

