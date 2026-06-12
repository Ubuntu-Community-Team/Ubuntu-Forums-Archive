---
title: "Apache and MySQL servers on separate networks"
date: 2011-08-29
forum: Server Platforms
---

### Post by lodp on 2011-08-29
A PHP+MySQL website I run has outgrown the ubuntu LAMP server it's on. There's no more optimizing to do, and I can't upgrade the existing machine with new hardware. So I was thinking about moving the MySQL server to its own dedicated box with a lot more RAM. 

Here's my predicament: The existing server has 6 months left on its lease, but the hosting company doesn't have any good offers for the kind of additional server I'd like to get. So I was wondering if it would be at all possible to leave PHP, Apache and all the rest on the existing server, and move the MySQL server to a different host. Is that a completely outlandish idea?

The existing host is located in Germany, the new host would be in France. I can ping between the two with a latency of ~12ms.

What would be the downsides of such a setup? I'm mainly interested in whether it would impact site performance a lot, since that's the main reason I'd like to get an additional server in the first place. Site speed as reported by google is awful right now (~8sec load time per page)

Thanks so much for your advice!

---

### Post by SeijiSensei on 2011-08-30
I suggest running an OpenVPN tunnel between the two machines using a simple [static-key setup]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  Then you can firewall off the MySQL server and bind the mysqld daemon to the tunnel IP.

---

### Post by lodp on 2011-08-30
SeijiSensei, that's strictly for security reasons though, right? Is an open database port a big risk? I was planning to only allow connections to 3306 from the webserver IP with a firewall rule.

So you guys agree that, given my situation, the advantage of having a dedicated DB server probably outweighs the disadvantage of the servers being on different networks, at least in terms of site performance?

---

