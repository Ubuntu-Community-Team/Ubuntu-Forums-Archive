---
title: "openssl issuer subject fqdn"
date: 2011-07-19
forum: Server Platforms
---

### Post by jose07 on 2011-07-19
Where does OpenSSL get the issuer, and subject from? I notice that it uses, server.gateway.2wire.net. I changed my hostname, and resolv.conf a while back to remove 2wire references, so I don't know where it is getting those fields from. The only other place I found that line was in the conf file for postfix(main.cf) under myhostname, and mydestination.

solved:
I thought I was using the new self-signed cert I created. Instead the Apache configuration file for default-ssl pointed to the snakeoil cert in /etc/ssl/certs, which was created when I installed Ubuntu.

---

