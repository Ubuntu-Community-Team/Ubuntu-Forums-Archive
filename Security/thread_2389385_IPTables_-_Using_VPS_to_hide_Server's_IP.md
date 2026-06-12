---
title: "IPTables - Using VPS to hide Server's IP"
date: 2018-04-16
forum: Security
---

### Post by benn20002 on 2018-04-16
[COLOR=#242729][FONT=Arial][FONT=inherit][COLOR=#6A737C][FONT=inherit][COLOR=#242729][FONT=inherit][COLOR=#6A737C][FONT=inherit][COLOR=#242729][FONT=inherit]I have a cheap VPS with a very good protection and a very strong server which does not have that good protection against attacks. So I want to use my VPS to redirect all connections to the strong server without exposing its IP.[/FONT][/COLOR][/FONT][/COLOR][/FONT]
[/COLOR]
[FONT=Verdana][COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit]I found many solutions using IPTables, but they either did not work at all for me, or they didn't keep the clients IP (only got it working with my webserver at all)[/FONT]
[FONT=inherit]To clarify: I want to run a Server with the Port 27015 (UDP), a Webserver with the Port 443 (TCP) and a Teamspeak Server which uses [these Ports]("https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use"). 
As I already said, I've got the webserver to work but without keeping the clients IP and the other two didnt work at all.
[/FONT]
[FONT=inherit]I am very unexperienced in IPTables, so don't hate on me please.. :c
Thanks for any help! :)[/FONT]
[/FONT]
[/FONT][/COLOR]
[/FONT]
[/FONT][/COLOR][/FONT]
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2018-04-16
```

#!/bin/bash

PUBLIC_IP=10.10.10.10
SERVER_IP=192.168.1.1

/sbin/iptables -A INPUT -d $PUBLIC_IP -p tcp --dport 443 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -d $PUBLIC_IP -p tcp -m tcp --dport 443 -j DNAT --to-destination $SERVER_IP:443


```

This would set up forwarding for port 443 on the VPS's PUBLIC_IP back to port 443 on SERVER_IP.

The server needs a static IP address.

The remote needs to be able to see the server.  if the server is behind a router, that won't be true.

My general solution is to use an OpenVPN [static-key connection]("http://openvpn.net/static.html") between the two machines, then send traffic between them over the VPN tunnel.

---

### Post by benn20002 on 2018-04-17
> **SeijiSensei said:**
> ```

#!/bin/bash

PUBLIC_IP=10.10.10.10
SERVER_IP=192.168.1.1

/sbin/iptables -A INPUT -d $PUBLIC_IP -p tcp --dport 443 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -d $PUBLIC_IP -p tcp -m tcp --dport 443 -j DNAT --to-destination $SERVER_IP:443


```

This would set up forwarding for port 443 on the VPS's PUBLIC_IP back to port 443 on SERVER_IP.

The server needs a static IP address.

The remote needs to be able to see the server.  if the server is behind a router, that won't be true.

My general solution is to use an OpenVPN [static-key connection]("http://openvpn.net/static.html") between the two machines, then send traffic between them over the VPN tunnel.

First off, thanks for your help! 
But I didn't manage it to get working..
Installing openvpn did work, but after connecting the server with the vps, I couldn't reach my server at all.
So I tried using your code for IPTables, but that doesn't work either, I think it might be because the vps can't see the server.
With my PC I can ping the server, but with my VPS I can't.

---

### Post by SeijiSensei on 2018-04-17
If you really have a working OpenVPN tunnel between the machines, the VPS should be able to talk to the server's VPN address. Can you ping each end of the tunnel from the other machine?

---

### Post by benn20002 on 2018-04-17
They weren't able to ping eachother when I tried it, but I was able to fix that (there were some wrong settings with the firewall of the vps).
But the VPN connection is still not working.
Can you recommend any guide how to install openvpn properly? I might just have messed up that..

---

### Post by SeijiSensei on 2018-04-17
Here's the link from before:  [http://openvpn.net/static.html](http://openvpn.net/static.html)

On the client I have this in /etc/openvpn/client.conf

```

dev tun
remote myvpn.example.com
ifconfig 10.1.0.2 10.1.0.1
port XXXXX
secret /etc/openvpn/my.key
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

On the server I have basically the same file without the "remote" directive and with the IP addresses reversed in the "ifconfig" directive.  (Syntax is local address followed by remote address.)

The port is an arbitrary number > 1023 and < 65535 not already in use.  I often create mnemonics with a phone touch-pad, e.g, "crazy" => "27299".  That port must be open on the VPS.  It could be firewalled by default.  If you are using iptables on the VPS, and your server has a fixed public IP, I'd use an iptables rule like this:

```
/sbin/iptables -I INPUT -s your.servers.public.ip -p udp --dport 27299 -j ACCEPT
```

If that doesn't work at first, try eliminating the "-s your.servers.public.ip" and allow all comers until you get this working.

---

