---
title: "PPTP VPN server firewall issue"
date: 2012-08-25
forum: Server Platforms
---

### Post by azharahs on 2012-08-25
Hello.

I have 2 Ubuntu servers, one is acting as a firewall/proxy/pptp server, with 3 network interfaces.  One WAN and 2 LAN interfaces.

The other server acts primarily as a SAMBA server.

I have the PPTP server configured on the firewall, and I can connect and browse the internet without issue.  However, I am unable to access any resources on the SAMBA server.

I have iptables rules configured on the server to allow only one of the local subnets to access the fileserver, and the PPTP server assigns IPs from within that subnet.  However, when I attempt to access the samba server, i am unable to connect.  The iptables logfile on the fileserver shows a denied connection attempt from the actual IP of the VPN client, rather than the IP assigned by the VPN.

example:  I connect to my pptp server with a client at IP 10.0.0.1.  The VPN assigns 192.168.1.200, and I can successfully connect to the internet via this IP.  When I attempt to access the samba server, I see a deny entry in the iptables log for source ip 10.0.0.1.

I have the samba server configured to only allow connections from the 192.168.1.0/24 subnet.

What am I doing wrong?  I can post config files as needed.  Any help is appreciated.

---

### Post by SeijiSensei on 2012-08-25
Does the routing table on the client have a route to the entire 192.168.1.0/24 network or just to the VPN router?  (What do you see with "route -n"?)  It sounds like you're using masquerading on the router if you can connect to the Internet.  Is the masquerading rule restricted only to traffic bound for the Internet-facing interface like this:

```
iptables -t nat -A POSTROUTING **-i eth1 -o eth0** -j MASQUERADE
```

This will only masquerade traffic that arrives on eth1 and is routed out the eth0 interface.  All other traffic is routed with the actual source addresses left intact.

IP masquerading is a wonderful thing, but sometimes it can lead to obscure problems if the wrong types of traffic have their addresses rewritten.

---

### Post by azharahs on 2012-08-27
Thanks for the reply.

The only masquerading I have configured on the firewall/pptp server is for traffic going out my WAN interface.

```

iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE
```

My PPTP client DOES have a route to the remote subnet, via the ppp interface.


Since my original post I've solved the issue.

My pptpd.conf file had the following entries:

```

localip 192.168.1.1
remoteip 192.168.1.201-205

```


After some reading, I tried commenting out the localip line, and restarting the pptpd daemon. After this change, I was able to successfully access my internal resources.


I'll mark this thread as solved.  Thank you for your help.

---

