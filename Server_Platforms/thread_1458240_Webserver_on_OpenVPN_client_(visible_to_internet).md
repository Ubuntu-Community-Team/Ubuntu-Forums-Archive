---
title: "Webserver on OpenVPN client (visible to internet)"
date: 2010-04-19
forum: Server Platforms
---

### Post by IvanTerkin on 2010-04-19
Hey all,

I'm trying to run Web server (nginx, does not really matter) "behind" VPN tunnel (i.e., on VPN client - the idea is that Web server is available at VPN endpoint IP on VPN server).

Stock Ubuntu 9.10 Server with stock openvpn 2.1. No network changes done, only ufw is enabled and IPv6 is switched off.

I need this box to be available at main IP address, no default route for VPN tunnel.

Tunnel itself works nicely, no problems at all. Hand-made static routes work via tunnel just fine.

Problem is in-going traffic - I can see that it at least comes via tunnel (via OpenVPN debug), but is blocked (or dropped) by firewall or kernel.

As far as I know, specific VPN server does not filter anything and is used for running Web servers on other IPs.

I think I might need to set up some sort of IP forwarding for tap0 device to localhost - but don't really know where to start.

Tried disabling firewall, making Web server listen on all IPs (from localhost to VPN tunnel) - no luck.

The box is in another country and KVM will be time and money, so I really don't feel like experimenting. :)

openvpn.conf (IPs are obscured, non-relevant options removed, based on recommended config for that server):
```
# Setup
dev tap

remote 1.2.3.4
port 5091

route-gateway 1.2.3.1

# Route **** via VPN
route 1.2.3.4 255.255.255.0 vpn_gateway

float 1.2.3.4

# My new IP
ifconfig 1.2.3.4 255.255.255.128
comp-lzo

persist-tun
persist-key
persist-local-ip
persist-remote-ip

verb 5
mlock

user nobody
group nobody

```

Any help will be much appreciated!

---

### Post by spynappels on 2010-04-20
Is there a specific reason you are running a tap adaptor rather than a tun adaptor?

In this exact same situation, I put a rule into the firewall to allow all traffic on the tun0 (or tap0 in your case) interface. No IP forwarding is required unless you want to hop on to another machine after.

In our remote servers, the tun adaptor acts exactly as any other (eth) adaptor and the same firewall rules and routing rules can be applied to it.

Edit: Forgot to add that ufw may not be specific enough to differentiate between adaptors when creating firewall rules, you may need to use IPTables. I cheat and use the Firewall module of Webmin to control remote firewalls.

---

### Post by IvanTerkin on 2010-04-20
> **spynappels said:**
> Is there a specific reason you are running a tap adaptor rather than a tun adaptor?

In this exact same situation, I put a rule into the firewall to allow all traffic on the tun0 (or tap0 in your case) interface. No IP forwarding is required unless you want to hop on to another machine after.

In our remote servers, the tun adaptor acts exactly as any other (eth) adaptor and the same firewall rules and routing rules can be applied to it.

Edit: Forgot to add that ufw may not be specific enough to differentiate between adaptors when creating firewall rules, you may need to use IPTables. I cheat and use the Firewall module of Webmin to control remote firewalls.

VPN server is configured for bridging mode, no way to change it.

I've tried your advice, does not seem to help. Even tried overdoing - changed INPUT policy to ACCEPT, etc - nothing seems to work.

Still I have a suspicion that this is something to do with IP forwarding, as the interface is bridged, maybe there is someone with relevant experience?

---

### Post by spynappels on 2010-04-20
Ok, I'm sorry, I was not thinking about a bridged connection.

then you may need to enable IP forwarding.

this thread helped me when I was doing this on my server.

[http://ubuntuforums.org/showpost.php?p=9035195&postcount=7](http://ubuntuforums.org/showpost.php?p=9035195&postcount=7)

Hope that sorts it for you.

---

### Post by IvanTerkin on 2010-04-20
> **spynappels said:**
> Ok, I'm sorry, I was not thinking about a bridged connection.

then you may need to enable IP forwarding.

this thread helped me when I was doing this on my server.

[http://ubuntuforums.org/showpost.php?p=9035195&postcount=7](http://ubuntuforums.org/showpost.php?p=9035195&postcount=7)

Hope that sorts it for you.

Thanks for the reply!

I've played with forwarding in sysctl before, disabled UFW, added explicit ACCEPT rules to all chains - no luck. :(

Even configuring Web server to bind to tap0 IP address did not help.

---

### Post by spynappels on 2010-04-20
Do you have change access to the server.conf file?

Are you trying to access the server from another client or from the server itself? If you are trying to access from another client, you need to uncomment the following line in the server.conf file

```
#client-to-client
```

This allows clients to talk to each other as well as to the server.

If this is not the case, I'm not sure what else to try. Let us know if you can ping the client IP address from the server and from another client.

---

