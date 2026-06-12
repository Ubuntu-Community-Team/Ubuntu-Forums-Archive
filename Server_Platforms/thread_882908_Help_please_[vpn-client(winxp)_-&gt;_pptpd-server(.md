---
title: "Help please [vpn-client(winxp) -&gt; pptpd-server(ubuntu) -&gt; http-proxy -&gt; internet]?"
date: 2008-08-07
forum: Server Platforms
---

### Post by alisakebi on 2008-08-07
Hi

I have an Ubuntu server that can connect to internet through http proxy and a laptop (win-xp) that is in another lan and can not connect to internet but it can connect to the Ubuntu server!

I want to connect to internet from my laptop through Ubuntu server(1), and I'm trying to do it using vpn.

I have installed pptpd on my Ubuntu server, I can connect to it from my laptop(win-xp) as vpn client, but I can not connect to internet from my laptop. It may be because pptpd can't go through proxy(2)!

Is there any other way to do (1)?
How can I verify (2) and how can I configure pptpd to work with proxy if it was the problem?

Thanks in Advance,
Ali

---

### Post by meftahi on 2008-09-27
1)Set ip forwarding by uncommenting this in /etc/sysctl.conf:
```
net.ipv4.ip_forward = 1
```
These changes will take effect with the next reboot. if you want them to take effect right now, use these commands
```
sudo sysctl -w net.ipv4.ip_forward=1
```

2)Adjust the netmask of the ubuntu server and proxy so that both be in same network, also the vpn connection most be in that network.

thanks

---

### Post by alisakebi on 2010-06-13
Thanks for reply, I have done it using ssh port forward:

ssh -L <localport>:<proxyadd>:<proxyport> <username>@<middleserver>

Then I set my local computer to connect to localhost:<localport> as proxy.

---

