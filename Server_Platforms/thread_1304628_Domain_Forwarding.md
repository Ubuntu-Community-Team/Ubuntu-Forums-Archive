---
title: "Domain Forwarding"
date: 2009-10-29
forum: Server Platforms
---

### Post by JordanCook on 2009-10-29
I Run two internal servers the main one is Ubuntu 8.10 and the Other on is Windows XP. Currently all http requests go to the Ubuntu box. How can i forward certain domains/subdomains to the Windows Box.

---

### Post by Adina on 2009-10-30
maybe try ip-based virtual host.

---

### Post by elvinatom on 2009-10-30
yoursite.com => ubuntubox
subdomain.yoursite.com => windows xp

you do that with a DNS server (bind9)

---

