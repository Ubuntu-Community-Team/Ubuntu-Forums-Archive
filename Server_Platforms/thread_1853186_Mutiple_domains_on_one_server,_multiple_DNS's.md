---
title: "Mutiple domains on one server, multiple DNS's?"
date: 2011-10-01
forum: Server Platforms
---

### Post by rs2k on 2011-10-01
I'm setting up a server that will host several domains.

What should I do when setting up the name servers? I hope this makes sense.


dns1.domain1.com ip:111.111.111.111
dns2.domain1.com ip:111.111.111.111
  is DNS for domain1.com ip:111.111.111.111

dns1.domain1.com ip:111.111.111.111
dns2.domain1.com ip:111.111.111.111
  is DNS for domain2.com ip:222.222.222.222


 - or -

dns1.domain1.com ip:111.111.111.111
dns2.domain1.com ip:111.111.111.111
  is DNS for domain1.com ip:111.111.111.111

dns1.domain2.com ip:222.222.222.222
dns2.domain2.com ip:222.222.222.222
  is DNS for domain2.com ip:222.222.222.222

---

### Post by SeijiSensei on 2011-10-01
Have you ever set up a name server with BIND9 before?  You declare the zones in /etc/named.conf and create a separate zone file for each of them.

Of course, your registrar will have to be informed that your server is now the primary for these domains.  You need to have a secondary server on the Internet as well to conform the RFC requirements for running a name server.  

If you've never done any of this before, and your registrar will hosts the domains for you, you definitely want to go that route.  Setting up DNS is not a task for the faint-of-heart.

---

### Post by rs2k on 2011-10-03
Thanks, I have setup a DNS before but I did it using a single machine and following tutorials. After reading quite it bit about it I decided to switch my DNS back to the registrar. It's free, easy and provides redundancy.

---

