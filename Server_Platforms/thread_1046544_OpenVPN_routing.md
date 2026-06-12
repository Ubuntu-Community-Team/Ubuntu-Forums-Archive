---
title: "OpenVPN routing"
date: 2009-01-21
forum: Server Platforms
---

### Post by carbm1 on 2009-01-21
I am trying to setup an OpenVPN server inside our network where some of our users from home can connect and then connect to another subnet that is firewalled and requires a connection directly from our site.  

I can set the default gateway in OpenVPN server config however I don't want all our home users internet traversing our network, only traffic to the specific IP subnet. 

For example, the server is on 10.10.10.0/24, the network the VPN user needs access to is a public network 74.125.45.0/24 (completely an example!). Pretend 74.125.45.0/24 is firewalled to only allow connections from our public IP on our 10.10.10.0/24 network.  How can I get traffic destined for 74.125.45.0/24 to go through our OpenVPN without having to completely set the default gateway on the OpenVPN server?

I tried adding the following to the server.conf:
```
push "route 74.125.45.0 255.255.255.0"
```

Thanks for the help!

---

### Post by koenn on 2009-01-21
If i understand your explanation correctly, 
you'd have to configure the **clients** to send traffic for 10.10.10.0/24 and 74.125.45.0/24 through the tunnel, the rest through their default gw (towards the internet)

The openvpn server would need to know a route to 74.125.45.0/24 ; you can check and add routes with the 'route' command

If I remember correctly, you can use vpn.up scripts to do this, or add route statements to the respective conf files.
here are some notes : [http://users.telenet.be/mydotcom/howto/linux/openvpn.htm](http://users.telenet.be/mydotcom/howto/linux/openvpn.htm)

---

### Post by carbm1 on 2009-01-22
I am not familiar with routing tables.  Any idea what the command is to make sure that the OpenVPN server knows how to route 74.125.45.0/24.

Thanks,

Craig

---

### Post by koenn on 2009-01-22
> **carbm1 said:**
> I am not familiar with routing tables.  Any idea what the command is to make sure that the OpenVPN server knows how to route 74.125.45.0/24.

Thanks,

Craig
```
route add -net 74.125.45.0 netmask 255.255.255.0 gw ip.adres.of.gateway
```
gateway is the router that connects 74.125.45.0/24 with 10.10.10.0/24 
you also need this:```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

if your server is directly connected to 74.125.45.0/24, it would already have such a route added automatically. 

post the output of ```
route
```

---

### Post by carbm1 on 2009-01-22
You were correct.  That worked perfectly.  

I thought I had it all wrong at first but it helps if you relax the firewall rules also.

Thank you very much for you help.

---

### Post by koenn on 2009-01-22
> **carbm1 said:**
> You were correct.  That worked perfectly.  

I thought I had it all wrong at first but it helps if you relax the firewall rules also.

Thank you very much for you help.

note that all of that is volatile, it will disappear on reboot. To make it permanent you'll have to add it to a startup script so it's executed again when the system starts up, or include them in the vpn conf files so they're executed when the vpn is up.

yes, firewalls can complicate things and need some adjustment sometimes when your networking needs change. But don't "relax" them too much :)

glad you got it working.

---

