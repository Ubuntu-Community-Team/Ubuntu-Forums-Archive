---
title: "Apache2 port 443 to 4444"
date: 2020-06-25
forum: Server Platforms
---

### Post by s4b1n on 2020-06-25
how do i change port 443 to 4444 in apache2. (ubuntu 18 server)
I tried changing the listening port in ports.conf and default-ssl.conf, and restarting apache, but it doesn't work.

lsof -i |grep apache2


apache2   493            root    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   493            root    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)
apache2   522        www-data    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   522        www-data    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)
apache2   523        www-data    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   523        www-data    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)
apache2   524        www-data    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   524        www-data    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)
apache2   525        www-data    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   525        www-data    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)
apache2   526        www-data    4u  IPv6  19362      0t0  TCP *:http (LISTEN)
apache2   526        www-data    6u  IPv6  19366      0t0  TCP *:4444 (LISTEN)



He is apparently listening on 4444, 
port 80 works normally

---

### Post by TheFu on 2020-06-25
The only problem I see above is that only IPv6 is listening. None of them are on 443, so it appears the change made already worked.  If the goal is to actually use SSL, then some certs will need to be installed. Either commercial/paid or from a free place like Let's Encrypt. I don't use apache enough to help with that. We terminate all our SSL connections on nginx.

So, either ask a question or please mark this thread as "SOLVED" using the Thread Tools button at the top of the page.

---

