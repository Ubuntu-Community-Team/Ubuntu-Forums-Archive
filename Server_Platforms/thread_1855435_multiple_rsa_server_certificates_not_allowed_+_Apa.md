---
title: "multiple rsa server certificates not allowed + Apache2"
date: 2011-10-06
forum: Server Platforms
---

### Post by chrislynch8 on 2011-10-06
Hi,

I just installed a Ubuntu10.04 on a new Server. I then followed notes on created a self signed cert for Apache2. When I configure the default-ssl site to use my new cert I get the following error message in the error log "multiple rsa server certificates not allowed"

If I comment out my lines nad restart apache and access my server using https it is receiving a cert myserver.mydomain which I didn't create or configure apache2 to use.

Can I stop Apache from using this cert and make it use my own self signed cert.

Rgds
Chris


I never commented out the default apache SSL settings in default-ssl

---

