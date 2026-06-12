---
title: "[SOLVED] log access attempts on squid"
date: 2007-09-27
forum: Server Platforms
---

### Post by xyrer on 2007-09-27
Hi, I have managed to get squid working with authentication and I'm very happy of how my ubuntu server is working, the only problem I have is certain vpn software that only runs in windows, there is no way we can change that and I have to find a workaround.

I tried this:

```
acl noauth src 192.168.1.9/255.255.255.255
acl nivel1 proxy_auth REQUIRED
acl all src 192.168.0.0/255.255.0.0

http_access allow noauth
http_access allow nivel1
```

in the squid.conf, but it doesn't allow that ip to connect without authenticating, so I heard that if I know the identifier that the vpn soft uses to connect, I  could allow that identifier to connect freely.

now the real question: how do I get that identifier? where and how can I capture that info?
and if there is a way I could allow the whole ip to get thru the proxy without authentication, it would be greatly welcome.

Thanks.

---

### Post by xyrer on 2007-10-22
I forwarded the ip requests by iptables, solved the issue, but I still would like to know how to get the info of the connection attempts.

---

