---
title: "Ubuntu client with DHCP IP cannot resolve names from DNS server"
date: 2017-05-18
forum: Server Platforms
---

### Post by bo-guo on 2017-05-18
I have setup primary and secondary DNS servers for network mostly consisted of Ubuntu servers and desktops. The servers are on static IP and they can resolve internal serve names without issues.  

However, the Ubuntu desktops, which are set to DHCP, would not resolve from the DNS servers.  Here is the /etc/network/interfaces file on the desktops

```
# The loopback network interfaceauto lo
iface lo inet loopback


# The primary network interface
auto eth1
iface eth1 inet dhcpc
        dns-nameservers 192.168.0.29 192.168.0.26 8.8.8.8
        dns-search example.com

```

I could not find what I am missing.  Thanks!

---

### Post by darkod on 2017-05-18
I don't think the option dns-nameservers is valid when using dhcp. In this case the dhcp server should issue dns nameservers and the search domain to the clients as part of the dhcp lease.
On the clients if they are ubuntu you can check actual nameservers with:
cat /etc/resolv.conf

That will show you if your options are accepted or not and which nameservers are actually used by the client.

---

