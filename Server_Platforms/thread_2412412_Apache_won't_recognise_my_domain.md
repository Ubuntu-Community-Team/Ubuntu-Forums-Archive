---
title: "Apache won't recognise my domain"
date: 2019-02-12
forum: Server Platforms
---

### Post by igf1 on 2019-02-12
I have hosting on a remote server, and I have all the DnS files set up correctly, but when I try to access my client's domain and it won't resolve? I've contacted support and they tell me it's a problem with apache? I've setup apache 1000 times and I've never had this problem. My friend says he can access it on Mobile Chrome but not on his pc and I can't either. This is a weird one guys

Richar Corsale

---

### Post by howefield on 2019-02-12
Moved to "*Server Platforms*"

---

### Post by LHammonds on 2019-02-12
Sounds like a Domain Naming Service (DNS) issue.

This is not likely an Apache issue.  Apache will direct the incoming user to the appropriate site based on the address used to reach your server and how you have the sites configured in the .conf files.

If the client device cannot resolve the domain name, it is likely your domain name is not configured to go to the correct IP which should be your externally-facing firewall/router.  The router should then direct the port 80/443 or whatever ports you want to the internal IP/port of your server.

Also keep in mind that making changes to DNS at your registrar (like GoDaddy or NetworkSolutions) may take up to 24 hours to propagate those changes worldwide to all the public DNS servers.

LHammonds

---

