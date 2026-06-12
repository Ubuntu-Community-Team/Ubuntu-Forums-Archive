---
title: "Google Chrome Update&amp;Bind9 relationship for Doh protocol"
date: 2019-10-08
forum: Server Platforms
---

### Post by secooonder on 2019-10-08
Hello
i use Ubuntu 16.04 LTS Firewall+Bind9(Dns Server)+Squid on one machine in my company.200 computers in my company.
My dns server serves both inside network and outside network from 53 port.
Of course,if the query comes from outside network,recursive query disabled.

i read a news lately about DOH(Dns over https) protocol.Doh protocol works via 443 port.
A very short time ,Google Chrome will activate Doh protocol with new update.

When computers receive this update,will my Bind9 server not work ? Do i need to make a new setting on my Bind9 Server?or do i need to do something?

i know how to turn of chrome updates but how far ?

What are your suggestions ?

Thank you

---

### Post by SeijiSensei on 2019-10-08
I strongly doubt Chrome would stop using port 53 queries since millions of people's DNS resolution would break.

It might slow resolution down a bit if Chrome always tries 443 first and waits for a reply.

---

