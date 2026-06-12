---
title: "round robin help"
date: 2008-05-27
forum: Server Platforms
---

### Post by tronica on 2008-05-27
can anyone explain the basics of setting up a round robin? someone basicly told me this: in /etc/hosts you put 

> [www.domain.com](www.domain.com). IN A 66.66.66.66
IN A 66.66.66.67
IN A 66.66.66.68

and you bind your local ip to your public ip and all should work.. That seems to simple and i can't find any good guides on this subject. Could someone explain in a little more detail? Thanks

---

### Post by pdwerryhouse on 2008-05-27
Not in /etc/hosts; you'll need to do it in the DNS.

The principle is correct, however: one name, multiple IP addresses, and most resolvers will then use round-robin to access them.

After that, just give each public IP address to a different server.

---

