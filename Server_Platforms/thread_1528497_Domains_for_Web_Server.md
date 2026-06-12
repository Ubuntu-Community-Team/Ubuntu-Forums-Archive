---
title: "Domains for Web Server"
date: 2010-07-10
forum: Server Platforms
---

### Post by sctweb on 2010-07-10
I'm a Ubuntu Server beginner and I'm wondering if it is possible to have two web servers in one Ubuntu Server.

E.g. **example1**.mydomainname.com and **example2**.mydomainname.com

Can this be done on my Ubuntu Server 10.04? Does it involve Apache? How?!

Many thanks

---

### Post by Ryan Dwyer on 2010-07-10
Yes, these are called VirtualHosts.

Copy /etc/apache2/sites-available/default and call it something like example2. Then modify that file to change the ServerName, DocumentRoot and so on. Then run sudo a2ensite example2, then reload Apache.

---

### Post by sctweb on 2010-07-31
Thanks for the info Ryan!

Can these virtualhosts be reached onto the internet? Are there requirements that I need to get it onto the internet?

---

