---
title: "How do you reroute/forward dns requests?"
date: 2006-11-30
forum: Server Platforms
---

### Post by TheGreatBradley on 2006-11-30
Hey,
I'm wondering how to reroute/forward web-addresses requested on my LAN.

Heres what I want to be done: If any computer on my LAN requests a site, ex: [www.google.com](www.google.com), the server will forward them to another site such as, ex: [www.yahoo.com](www.yahoo.com), without connecting to [www.google.com](www.google.com) as if [www.google.com](www.google.com) hadn't existed.

I'm sure theres a way to do it, I've been searching around google for a while and I've had no luck:( 

Much thanks to any help!

---

### Post by tturrisi on 2006-11-30
I believe that can be done using a hosts file.

---

### Post by Kurt` on 2006-11-30
The DNS server(s) that your client machines are pointing to can set up a CNAME record to perform the redirect.

[quote=Wikipedia.org]# A CNAME record or canonical name record is an alias of one name to another. The A record that the alias is pointing to can be either local or remote - on a foreign name server. Useful when running multiple services from a single IP address, where each service has its own entry in DNS.[/quote]

Or, as tturrisi said, you could edit the /etc/hosts file on each machine. (C:\windows\system32\drivers\etc\hosts on Windows XP)

---

