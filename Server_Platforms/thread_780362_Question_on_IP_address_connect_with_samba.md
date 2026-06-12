---
title: "Question on IP address connect with samba"
date: 2008-05-03
forum: Server Platforms
---

### Post by cpthk on 2008-05-03
Here is my network environment:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68613&stc=1&d=1209834356[/IMG]

I need to make those PC-xx computers able to connect to samba. I tried whenever I make those computers 192.168.1.x, they works. If 192.168.2.x, they don't work anymore. But due to insufficient IP numbers, I really have to make them 192.168.2.x . Right now, they all are contact by netbios name, my samba server is named SAMBA_PDC now.

---

### Post by ghostknife on 2008-05-03
What is your subnet masks?

The problem is that SAMBA uses broadcasts for many of it's features, like netbios names.

You either need to make them all be on the same ethernet network (no routers in between) and have their subnet masks be something that covers both, like 255.255.0.0. Then give them all the same broadcast address as well, like 192.168.1.255 (even the 192.168.2.0/24 subnet machines).

If you really want/need a router in between them, make the router a bridge instead. Routers don't reroute broadcasts, which is why you need a bridge.

The easiest is to obviously make a bigger subnet, as you only need to put them on the same ethernet network (same switches).

---

### Post by cpthk on 2008-05-03
> **ghostknife said:**
> What is your subnet masks?

The problem is that SAMBA uses broadcasts for many of it's features, like netbios names.

You either need to make them all be on the same ethernet network (no routers in between) and have their subnet masks be something that covers both, like 255.255.0.0. Then give them all the same broadcast address as well, like 192.168.1.255 (even the 192.168.2.0/24 subnet machines).

If you really want/need a router in between them, make the router a bridge instead. Routers don't reroute broadcasts, which is why you need a bridge.

The easiest is to obviously make a bigger subnet, as you only need to put them on the same ethernet network (same switches).

How do I give them all the same broadcast address?
You said make the router a bridge, but bridge don't have DHCP, isn't it? The bridge does not give IP 192.168.2.x.

---

### Post by VSpike on 2008-05-04
First, can the computers on the 192.168.2.x subnet ping the Samba server?

If they can't, you have a networking problem not a Samba problem!

If they can, next try this from one of the 192.168.2.x machines:

```
smbclient -L //192.168.1.99
```

(replacing 192.168.1.99 with the actual IP address of the PDC).

If that works, you should see a list of shares.  If so, this means your problem is down to name resolution.  You need to enable WINS on the Samba server (consult the docs on how to do it) and then tell the clients where to find the WINS server.  The best way to do this is to configure your DHCP server to hand out the WINS server address, if you can.  If not, you will have to manually specify it on each one.

---

### Post by cpthk on 2008-05-04
> **VSpike said:**
> First, can the computers on the 192.168.2.x subnet ping the Samba server?

If they can't, you have a networking problem not a Samba problem!

If they can, next try this from one of the 192.168.2.x machines:

```
smbclient -L //192.168.1.99
```

(replacing 192.168.1.99 with the actual IP address of the PDC).

If that works, you should see a list of shares.  If so, this means your problem is down to name resolution.  You need to enable WINS on the Samba server (consult the docs on how to do it) and then tell the clients where to find the WINS server.  The best way to do this is to configure your DHCP server to hand out the WINS server address, if you can.  If not, you will have to manually specify it on each one.

I tried to ping, it didn't work. How do I fix this?

---

### Post by ghostknife on 2008-05-04
That means your routing isn't working correctly, or you are filtering ICMP packets on your router.

What VSpike mentioned will work with routing. WINS servers eliminate the need for a bridge, but you will have to setup the WINS on all machines. When you use DHCP then then DHCP can setup the WINS for you. Maybe this will be an easier option.

So setup the router and make sure it's all working fine first. Then setup a WINS server (you can have SAMBA be your WINS server). Setup DHCP to install the WINS server options on all the clients. You can do this by adding the following option in your DHCPD configuration file (replace the IP with the IP your your WINS/SAMBA server):
```

  option netbios-name-servers 192.168.1.2;
```

To help with the routing, do the following commands on the router and paste the output. 
```

sudo iptables -nL 
sudo iptables -t nat -nL
sysctl net.ipv4
```

---

### Post by cpthk on 2008-05-04
I'm sorry. All my PCs are windows. Only the samba server is linux. My router is a actual basic router, too. Not the linux router. I don't think it can take commands.

---

