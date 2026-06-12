---
title: "Internal hostname appearing in mail headers"
date: 2010-03-24
forum: Server Platforms
---

### Post by Znupi on 2010-03-24
We have an Ubuntu server running on Amazon EC2, hosting a website. We also have postfix, in order to send mail (receiving mail is done by another server which is specified in our MX records). My problem is that the internal hostname of the machine ("domU-xx-xx-xx-xx-xx-xx.compute-1.internal") appears in some "Received:" headers in the emails sent. Is that normal? It seems rather peculiar to me, and I'm thinking some e-mail systems might consider it spam because of this. GMail doesn't consider it spam, but not all systems are as smart as GMail :)

---

### Post by Znupi on 2010-03-26
Bump

---

