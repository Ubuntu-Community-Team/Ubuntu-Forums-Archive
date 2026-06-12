---
title: "Reverse dns?"
date: 2013-07-09
forum: Server Platforms
---

### Post by mirceabondar on 2013-07-09
Hy..
reverse address on my DNS server is required if the delegation did not?

---

### Post by SeijiSensei on 2013-07-09
I cannot tell what you are trying to ask but, in general, correct reverse DNS is a good idea for any publicly-visible server.  It is critical for mailservers these days, but a good idea for DNS servers as well.

When you speak of "delegation" do you mean [RFC2317 delegation](http://www.ietf.org/rfc/rfc2317.txt)?  That type of delegation refers to IP subnets rather than single hosts.  If you have a publicly-visible server, your ISP is the only one who can set up proper reverse DNS for you.

If you have a server on a residential connection, nearly all ISPs will ignore a request to set up reverse DNS for you.  After all, most ISPs ban servers on residential connections under their terms of service.

---

