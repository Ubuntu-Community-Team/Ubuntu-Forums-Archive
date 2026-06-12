---
title: "2 x NATed and PROXYed VPN connections"
date: 2010-11-08
forum: Server Platforms
---

### Post by grasnal on 2010-11-08
Hi. I need some advice with VPN Server configuration. Situation is shown below.

```


                                   |--------|                                    |---------|
[ubuntu vpn server] <--> [lan port]|        |[wan port] <- internet -> [wan port]|         |[lan port] <--> [localhost#2]
                                   |  nat#1 |                                    |  nat#2, |
[localhost#1] <--------> [lan port]|        |                                    |  proxy  |
                                   |--------|                                    |---------|
  

```

Explanaion:
I need to transfer files between localhost#1 and localhost#2 like between host in the same, local subnet. Nat#2 configuration is out of my control. Nat#1 is configured to forward all traffic to UbuntuVpnServer. I'm trying to follow [**[COLOR="DarkOrange"]this[/COLOR]**]("http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html") guide. But I can't figure out if I need to use two hardware NICs on UbuntuVpnServer o just one will be fine. Any other advice or suggestion would be great.

---

### Post by NathanBC on 2010-11-19
Is the Ubuntu VPN server involved in the connectivity between the two localhosts?

Is localhost#2 the device that is NATed by the router labelled [NAT #2]?

There is not really enough detail here to say exactly what you need to do to make this work.

The simplest plan would be to have both localhosts NATed at their respective router/firewalls.  Set up appropriate rules so that only inbound connections from the other localhost are allowed.  Then use an encrypted file transfer protocol to move the files.  If localhost#1 is sending a file it would connect to the NAT (public) IP address of localhost#2.

If you need to use a VPN then you would want a site-to-site VPN controlled by something like your Ubuntu VPN server at BOTH ends.  You would then need to set up appropriate routes so that packets destined for the remote network are routed to the VPN server on the sending hosts network.

---

