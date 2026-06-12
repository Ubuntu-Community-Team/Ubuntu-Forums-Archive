---
title: "Domain Name Troubles"
date: 2006-06-25
forum: Server Platforms
---

### Post by Jayzilla on 2006-06-25
Some time ago I purchased a domain name (jaylindsey.us), and I'd like it to point at my Ubuntu box.  Now, I set my host/domain name (for the Ubuntu machine) to server1.jaylindsey.us.  Do I have to set up a DNS server or something?  And even if I do, GoDaddy wants two nameservers.  What do I do?

---

### Post by Randomskk on 2006-06-25
You do need a nameserver; BIND from the repos is good (I'd advise bind9).

On GoDaddy, you need to tell it your IP (look under remote DNS or something), and the two name servers you will need to set up in your BIND. I believe the Ubuntu server guide has info on setting up bind, if not you should be able to find something on google.
As far as two nameservers go, that's easy, you just use ns1.domain and ns2.domain, and your one server can host both.

---

