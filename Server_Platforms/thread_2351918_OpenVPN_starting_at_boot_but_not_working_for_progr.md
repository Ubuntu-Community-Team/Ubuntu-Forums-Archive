---
title: "OpenVPN starting at boot but not working for programs in X"
date: 2017-02-07
forum: Server Platforms
---

### Post by kevpatts2 on 2017-02-07
So I have OpenVPN working and connecting at boot (using the /etc/default/openvpn). If I check my IP from the command line I can see that the VPN is used, but no programs that run in Kodi or via X Forwarding seem to use the VPN.

What am I doing wrong?

---

### Post by geeksmith on 2017-02-07
How are you running the programs (SSH, VNC, plain old X client/server)? Are you connecting to a system across the Internet or in your home LAN?

Your VPN IP address doesn't take over and become the default IP for all new communication on your box. Only traffic that's configured to use the VPN will forward traffic through it.

---

### Post by darkod on 2017-02-08
What are you doing with /etc/default/openvpn exactly? I have set up many openvpn connections and never needed to touch that file. It is true that I mostly setup Ubuntu Server connections but the same would apply to Ubuntu Desktop too. I simply use a .conf file in /etc/openvpn on the client side and it works.

Whether the VPN tunnel will become default GW for all traffic depends on the setup on the server side too. If you have confirmed that the tunnel is default GW after it is established, then all programs (graphical or not) should use that GW because that will be a system wide setting.

If you are connecting it differently at boot (not using the default procedure) you might be getting different results...

---

### Post by SeijiSensei on 2017-02-08
Have you tried using "ssh -X ip.addr.of.remote" to connect where "ip.addr.of.remote" is the address assigned to the remote's OpenVPN tunnel device, usually tun0?

Once you do that, you can run commands on the remote in the SSH session, and their graphical output will appear on your desktop.

---

### Post by kevpatts2 on 2017-02-08
> **darkod said:**
> What are you doing with /etc/default/openvpn exactly? I have set up many openvpn connections and never needed to touch that file. It is true that I mostly setup Ubuntu Server connections but the same would apply to Ubuntu Desktop too. I simply use a .conf file in /etc/openvpn on the client side and it works.

Whether the VPN tunnel will become default GW for all traffic depends on the setup on the server side too. If you have confirmed that the tunnel is default GW after it is established, then all programs (graphical or not) should use that GW because that will be a system wide setting.

If you are connecting it differently at boot (not using the default procedure) you might be getting different results...

Hey darkod,

I'm using that file purely for the AUTOSTART line to trigger the connection to one of the locations. My route table  after boot look like:
```
routeKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.80.10.5      128.0.0.0       UG    0      0        0 tun0
default         192.168.99.1    0.0.0.0         UG    0      0        0 eth0
10.80.10.1      10.80.10.5      255.255.255.255 UGH   0      0        0 tun0
10.80.10.5      *               255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.80.10.5      128.0.0.0       UG    0      0        0 tun0
192.40.88.11    192.168.99.1    255.255.255.255 UGH   0      0        0 eth0
192.168.99.0    *               255.255.255.0   U     0      0        0 eth0
```

The main problem is that Kodi doesn't seem to be using it, the X forwarded applications was just for information.
[COLOR=#000000]
SeijiSensei, the problem wasn't the SSH X forwarding, it was just a symptom.[/COLOR]

---

### Post by darkod on 2017-02-08
It also helps if you try checking the public IP to be sure if the default GW is through the VPN or not... You can do that with:
```
curl icanhazip.com
```

As I suggested, you can also undo what you did in /etc/default/openvpn and try with the client.conf file in /etc/openvpn. You do have one, right?

And how the openvpn client acts is also controlled from the server side so you need to be sure the server is set up to make the vpn default GW.

And last, are you sure Kodi is not using the vpn GW or it just doesn't seem like it?

---

### Post by geeksmith on 2017-02-08
Your routing table looks messed up to me. Two default gateways is generally an error in configuration, unless you're doing something with load-balancing. These two lines look suspicious, like the route was added twice, once correctly and once incorrectly:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.80.10.5      128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.80.10.5      128.0.0.0       UG    0      0        0 tun0

```

From what I see, it looks like you're simply not routing what you think you're routing. It's unclear whether these route entries were pushed by the OpenVPN connection or somehow manually added. What does your routing table look like with the VPN disconnected? Can you share any more details of the VPN configuration that might explain the odd entries in the routing table?

The VPN will only be used for destinations that are configured to use it. Right now, it looks like 128.0.0.0/7 is the only properly configured destination for the VPN. To add other destinations, e.g. if 192.168.55.0/24 were a destination inside the VPN, you could use something like this:
```

sudo ip route add 192.168.55.0/24 via 10.80.10.5

```

To solve your problem, it would help if you posted the server and client configs (sanitized of passwords and keys, of course). A description of what you're trying to do here would also help, like what subnets you're trying to connect together.

---

### Post by kevpatts2 on 2017-02-08
> **darkod said:**
> It also helps if you try checking the public IP to be sure if the default GW is through the VPN or not... You can do that with:
```
curl icanhazip.com
```

As I suggested, you can also undo what you did in /etc/default/openvpn and try with the client.conf file in /etc/openvpn. You do have one, right?

And how the openvpn client acts is also controlled from the server side so you need to be sure the server is set up to make the vpn default GW.

And last, are you sure Kodi is not using the vpn GW or it just doesn't seem like it?
Thanks man, I don't have a client.conf file.

I don't have control over the server.

I'm not 100% sure but there is no observable slowdown in connection speed when I connect to Australia, so I don't think so!

---

### Post by kevpatts2 on 2017-02-08
> **geeksmith said:**
> Your routing table looks messed up to me. Two default gateways is generally an error in configuration, unless you're doing something with load-balancing. These two lines look suspicious, like the route was added twice, once correctly and once incorrectly:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.80.10.5      128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.80.10.5      128.0.0.0       UG    0      0        0 tun0

```

From what I see, it looks like you're simply not routing what you think you're routing. It's unclear whether these route entries were pushed by the OpenVPN connection or somehow manually added. What does your routing table look like with the VPN disconnected? Can you share any more details of the VPN configuration that might explain the odd entries in the routing table?

The VPN will only be used for destinations that are configured to use it. Right now, it looks like 128.0.0.0/7 is the only properly configured destination for the VPN. To add other destinations, e.g. if 192.168.55.0/24 were a destination inside the VPN, you could use something like this:
```

sudo ip route add 192.168.55.0/24 via 10.80.10.5

```

To solve your problem, it would help if you posted the server and client configs (sanitized of passwords and keys, of course). A description of what you're trying to do here would also help, like what subnets you're trying to connect together.
I thought the same thing but if I check my external address using
```
dig +short myip.opendns.com @resolver1.opendns.com
``` and I get the VPN remote IP address.

---

### Post by darkod on 2017-02-08
The important thing on the server side is whether it is set up to force the client to use the vpn tunnel as default GW. You don't actually need control over it...

How do you connect without .conf file? You are using the Network Manager GUI?

You can still try with a .conf file, that's what I wanted to say. Even for the Desktop version that has a GUI you are not required to use GUI tools, you can still do it with the classic .conf text file.

Apart from that, I don't know what to suggest.

---

