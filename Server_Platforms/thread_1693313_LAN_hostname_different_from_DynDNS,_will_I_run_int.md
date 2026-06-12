---
title: "LAN hostname different from DynDNS, will I run into issues?"
date: 2011-02-22
forum: Server Platforms
---

### Post by csdco on 2011-02-22
I use DynDNS to give public access to a local server, but the DynDNS domain name and the machine's hostname are not the same. I cannot alter my machine's hostname without spending a lot of time rebuilding paths on projects located on other local machines.

When Apache boots it gives me the good ol' "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName". Apache still runs just fine and I haven't *yet* seen any issues, but I've spent a lot of time fine tuning this new server and wanted to see if anyone had a recommendation.

**TL;DR: Will I run into any pitfalls using a hostname that is not my public domain name in a development environment?**

---

### Post by stmiller on 2011-02-22
Yeah it will be fine to have dyndns be one thing and your host name something else. 


To give apache a server name, make this file:

```
sudo nano /etc/apache2/conf.d/fqdn
```

and put in your desired server name in that file:

```
ServerName localhost
```

or

```
ServerName mydomain.com
```

---

### Post by mclimber43 on 2011-02-23
I have a setup like this to run a LAN network and a public website with different domain names.  I haven't had any problems yet.

---

### Post by csdco on 2011-02-23
The method described by stmiller works perfectly. Thank you!

mclimber43 -- thanks for reporting the status of your server, good to know this will work happily for both setups.

---

