---
title: "Setting up DNS for a small lan"
date: 2010-01-25
forum: Server Platforms
---

### Post by StueyB on 2010-01-25
Hi everyone,

I am aware there are already a few guides around on how to set up dns/bind but the issue I am hitting is that I want to just create a non internet domain setup ie t60.mysuperlan. desktop.mysuperlan. etc . Using a hosts file isn't the best as its pretty much about learning all the stuff to make it work.

I know it's doable and I have spend several hours, days almost trying to figure it.

I have looked at the docs but it doesnt do an abc on it :)

Any help appreciated.

Regards

Stu

---

### Post by BkkBonanza on 2010-01-25
Do you have a router on your LAN? Most routers can provide basic DNS for the LAN as well. For example, mine, the popular Linksys WRT54GL with DD-WRT has dsnmasq running and it gives the LAN both DHCP and DNS service. This is fine for a modest sized LAN and by far the simplest way to get it running.

Read up on your router info, maybe you just need to configure the names.

---

### Post by jarilin on 2010-01-25
This works for me fin.local etc...
[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

---

