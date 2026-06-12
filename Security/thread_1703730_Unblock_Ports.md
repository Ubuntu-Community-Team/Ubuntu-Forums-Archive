---
title: "Unblock Ports?"
date: 2011-03-09
forum: Security
---

### Post by Cooldude170 on 2011-03-09
Hi, I am running a dedicated server that has Ubuntu 32-bit installed on it.
I did the iptable thing, but it still doesn't unblock the ports.
I also checked the rules, they're allowed in there.
The only way ports are able to be unblocked is if a corresponding application is apt-get'd.
I need ports 6112 - 6114 opened for inbound and outbound.
Could someone help me?

---

### Post by The Cog on 2011-03-09
Please explain what you are trying to do.
Why do you think the ports are blocked?
> The only way ports are able to be unblocked is if a corresponding application is apt-get'd.
I need ports 6112 - 6114 opened for inbound and outbound.
By default, iptables allows incoming and outgoing - doesn't block anything. So unless you have installed a firewall or configured iptables to block things, iptables is not blocking anything. But the port will remain closed until an application opens them by listening for incoming calls. Ports are always closed until an application opens them. So until you install and run an application that opens them, they will stay closed, and that's nothing to do with firewalling - closed means not accepting connections.

If you can post the output of these two commands, we can see what the state of the server ports is:
```
netstat -lntu
sudo iptables -nvL
```

---

### Post by Cooldude170 on 2011-03-09
Netstat:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:6697            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:843             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6667            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1337            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6112            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6113            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6114            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8067            0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:25                  :::*                    LISTEN
udp        0      0 0.0.0.0:68              0.0.0.0:*

sudo iptables:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist-local, it will be ignored in a future release.
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by The Cog on 2011-03-10
Well, I have no idea what that warning is all about. 

But apart from that, netstat shows that you are listening on ports 6112 - 6114, and you are also running a mail and web server along with others I dont' immediately recognise. The iptables output says that iptables isn't blocking anything. So I would expect that the server is all ready to accept connections. 

Again, what makes you think the ports are being blocked?

---

### Post by cariboo on 2011-03-10
If you are behind a router, you have to forward the ports you want others to access from the internet.

---

