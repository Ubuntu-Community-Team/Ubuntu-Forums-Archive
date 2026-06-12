---
title: "MySQL 5.5 Client with SSL Seg Fault or &quot;ASN: bad other signature confirmation&quot;"
date: 2013-05-20
forum: Server Platforms
---

### Post by marcusone on 2013-05-20
I'm running the latest LTS 12.04.2, fully apt-get update'ed

I'm trying to get the mysql client to connect to a remote MySQL with SSL enabled.  I either get a seg fault or "ERROR 2026 (HY000): SSL connection error: ASN: bad other signature confirmation"

I've tried using just a CA certificate (that works just fine on my CentOS 6 platforms), a generated certificate on Ubuntu, as well as generating and specifiying all 3 options (ssl-ca, ssl-key, ssl-cert in .my.cnf, or the command line).

Bet I can tell from google searches is that MySQL and OpenSSL versions on Ubuntu don't play nice... is there an easy way to downgrade the OpenSSL (ssllib) to 0.9.8? (Current is 1.0.1 on my system).

Or is there some other solution?

Thanks,

---

