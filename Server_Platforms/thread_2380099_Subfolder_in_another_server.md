---
title: "Subfolder in another server"
date: 2017-12-13
forum: Server Platforms
---

### Post by fernandoch on 2017-12-13
Hello,

Is there a way to have a subfolder of a domain in another server with apache?

For example I have my domain.com in a server.

I want mydomain.com/tools to be in another server.

Can that be done with Apache?

Thanks

---

### Post by volkswagner on 2017-12-13
Are the two servers separated via Internet, or are they on the same LAN/private network, or do they share VPN access?

I'm not sure if the directory alias function can cross file systems or point to an SFTP mount point or not.

---

### Post by fernandoch on 2017-12-13
Separated via internet.

Better to use a subdomain?

---

### Post by volkswagner on 2017-12-15
If you can use a subdomain, that would be best. What exactly are you trying to accomplish? Are you serving web pages from that directory or are you serving file access for users to download? Why do you need to serve content on a different physical machine?

---

### Post by fernandoch on 2017-12-15
Planning to have a forum there, so if it gets a lot of activity I would like to move it to another server.

---

### Post by volkswagner on 2017-12-15
I would definitely use subdomain. You'll be glad you did if you was to use SSL certificate, or if you do move it ...URLs won't change, migration will be easy.

---

