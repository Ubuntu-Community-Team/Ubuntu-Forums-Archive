---
title: "Reverse propagation"
date: 2013-12-12
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-12-12
I set up reverse dns after two days. I took a test propagation [www.whatsmydns.net](www.whatsmydns.net) and still not propagated to all servers. I did something wrong in my configuration or even so much longer?.

---

### Post by nerdtron on 2013-12-12
Did you updated the serial number from your zone file?
Did you tried to query your domain and reverse domain from your local lan?
Not all servers can readily receive your update, I say 3 days minimum up to 1 week depending on your zone TTL settings.

---

### Post by Bondar_Mircea on 2013-12-12
I updated serial now but output for nslookup 82.78.235.77 is 

server can't find 77.235.78.82.in-addr.arpa.: NXDOMAIN


In windows

Name:    mail.beestudio.ro
Address:  82.78.235.77
Aliases:  77.235.78.82.in-addr.arpa

---

