---
title: "Need to settup DNS/Nameserver for new Ubuntu 16.04 dedicated server"
date: 2016-06-13
forum: Server Platforms
---

### Post by zack22 on 2016-06-13
Howdy,

I'm new to using ubuntu and have just setup my first dedicated server with a firewall and control panel (Server Pilot).  I am stuck on setting up the DNS and Nameservers.

I plan on building multiple WordPress sites on this server.

I would like to use the DNS from GoDaddy or Easydns, but cannot figure out how to set it up correctly.

What would the steps be to set this up correctly?

---

### Post by darkod on 2016-06-14
To set up your dns servers that you want your machine to use, you need to edit:
```
sudo nano /etc/network/interfaces
```

In there you will see a group of commands for your primary and any other interface, like:
```
auto eth0
iface eth0 inet static
   address ...
   netmask ...
   gateway ...
   dns-nameservers 8.8.8.8 8.8.4.4
```

That is an example with a static IP that most of the servers should have. In my example I used google DNS servers. Just modify the values for dns-nameservers, restart the networking service (or the whole server) and that's it.

You can double check the values in /etc/resolv.conf (but don't edit them there).

---

### Post by SeijiSensei on 2016-06-14
I think he wants to have the DNS for his domain(s) hosted externally, but routed to the server.

For that you'd need to add A records to each domain's nameservice records that point to the server's public IP address.  If the server is behind a router, you'd need use the router's public address and set up port-forwarding back to the server.

---

