---
title: "[SOLVED] multiple postfix servers for a number of subdomains"
date: 2009-01-02
forum: Server Platforms
---

### Post by zooper on 2009-01-02
Hi,

I need some help with my current postfix project.

My goal is to have 2 sub-domains and a total of 3 postfix mail servers.

The first mail server is supposed to just be a kind of routing/mail scanning server, and the 2 others is supposed to be the final destination for each subdomain.

To make things easier:
mailserver1 - All MX records for my sub-domains points to this server. (Public IP, but no mail hosting)

mailserver2 - Is on a DMZ behind mailserver1, supposed to host domain1.foo.bar.

mailserver3 - Is also on a DMZ behind mailserver1, supposed to host domain2.foo.bar


So, my question is, how can I on mailserver1, configure so that all incoming mail that belongs to domain1.foo.bar gets relayed to mailserver2. (And ofcourse, domain2.foo.bar to mailserver3)

Running postfix v 2.5.5 on Ubuntu Intrepid.

/Tomas

---

