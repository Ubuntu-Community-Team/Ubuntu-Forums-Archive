---
title: "Ubuntu 16.04 Vps ip hide - change 5 min."
date: 2020-10-21
forum: Server Platforms
---

### Post by toadelite on 2020-10-21
My virtual private server help please.       Hello everyone. I would  like to ask whether ubuntu exists vps - onto a server solution like  that,with which if I download a file from an other server every day once  then from what I download it server let ip be mésik always instead of  ip?
A kind of hyde ip I thought of a thing so pl let 5 minutes or 5 clocks modify it the ip-t. Free program please. Thanks.

---

### Post by QIII on 2020-10-21
It might be helpful for us to understand the purpose of this.

---

### Post by TheFu on 2020-10-21
You can script anything, but random IPs cannot be used without coordination with the network administrator.  

Public IPs can't ever be randomly assigned in the IPv4 public address space.
On a private LAN, changing the IP is of little use.

IPv6 supports changing the IP with each different connection. That is built into the protocol.

---

### Post by toadelite on 2020-10-22
[https://www.comparitech.com/blog/vpn-privacy/hide-ip-address-free/](https://www.comparitech.com/blog/vpn-privacy/hide-ip-address-free/)

Onto this would be needed for the server only. If for example cron a command runs then change ip

---

### Post by TheFu on 2020-10-22
> **toadelite said:**
> [https://www.comparitech.com/blog/vpn-privacy/hide-ip-address-free/](https://www.comparitech.com/blog/vpn-privacy/hide-ip-address-free/)

Onto this would be needed for the server only. If for example cron a command runs then change ip

Be very careful using free/cheap services for a VPN or SOCKS proxies. Almost always (always?), the free versions are tied to less than great organizations. A quick check is whether a VPN works in China or Russia or not.  The only reason a VPN is allowed to work in China is because the govt has access to the encryption keys or very weak encryption is used, thus access to all traffic. Same for Russia.  TLS v1.3 encryption VPNs are not allowed in China for a reason.  You should look for that type of encryption in a VPN.

The only reputable, free, service that I know is TOR, but it only works with specific browsers. It is not a whole-system method of protection and wouldn't be suitable for a server. TOR is good for privacy, but that privacy can be completely unmasked by re-using accounts that have already been used without TOR or by writing text that can clearly be tied to you through writing analysis.
If you want to setup a service that anyone in the world can access, but only over the TOR network, look into setting up a .onion domain. These are TLDs that TOR uses for hidden services and locations that cannot be traced without extensive efforts, unless the system gets hacked or the users of the service make mistakes and give away themselves. For people who use TOR in a read-only way, they should be fairly private.

BTW, deploying anything new on 16.04 is a bad idea. Support for that OS ends in a few months. Today, new installations should deploy using 20.04.  VPNs, SOCKS proxies and TOR all work on 20.04, plus it has support until into 2025.

---

