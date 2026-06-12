---
title: "Configuring apache reverse proxy  without breaking the https tunnel"
date: 2014-07-14
forum: Server Platforms
---

### Post by Sanjeeb on 2014-07-14
I have configured apache reverse proxy. In that configuration https connection is possible between client to reverse proxy and again reverse proxy to server. But I want https connection between client to server like forward proxy. The https connection should not be broken at reverse proxy.

   [IMG]http://i57.tinypic.com/2rpzk3d.png[/IMG]

[B]If end to end https tunnel is not possible in reverse proxy then how can it be ensured that ssl proxying option is safe and even the Reverse proxy administrator(if reverse proxy got compromised) can not decrypt the tunnel or man in middle attack can't be done.

[/B]

---

### Post by SeijiSensei on 2014-07-14
The only way I know of that might work is to use a current version of [Squid with SSLBump]("http://wiki.squid-cache.org/Features/SslBump") correctly configured to spoof the identity of the remote certificate.  This makes it essentially a "man-in-the-middle."  

Are you using Apache because you want to select the proxy based on the ServerName parameter?  If not, and you are just trying to forward the connection from outside back to an HTTPS server, why not just use iptables or some other method to proxy the TCP connection directly through the machine now running Apache?   Something like:
```
/sbin/iptables -A PREROUTING -p tcp -d ip.of.apache.box --dport 443 -j DNAT --to-destination ip.of.target.box:443
```
You'll need to enable packet forwarding /etc/sysctl.conf if you haven't yet done so, and you might need to add a corresponding FORWARD rule depending on how you have iptables configured.

---

