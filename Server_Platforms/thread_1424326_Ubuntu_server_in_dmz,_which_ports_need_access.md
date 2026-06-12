---
title: "Ubuntu server in dmz, which ports need access?"
date: 2010-03-07
forum: Server Platforms
---

### Post by Jan82 on 2010-03-07
Just dns and the hosts in the apt sources or are there any other hosts on the net Ubuntu server needs access to?

Jan

---

### Post by tgalati4 on 2010-03-07
It's not a good idea to put a server in the dmz.  That's reserved for special purposes.  Put the server behind the router firewall using one of the normal ports.  Set port 80 to forward to your internal IP address (say 192.168.1.125), so that you can access your webserver.  Open other ports as you need them.

---

