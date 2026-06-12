---
title: "Apache Quick Question"
date: 2010-05-31
forum: Server Platforms
---

### Post by stepstools on 2010-05-31
I am planning on installing an Apache server today.  I know how to get it to point to addresses like "localhost" or my outside ip, but how do I get it to point to a URL like [www.mysite.com?](www.mysite.com?) (That's just an example URL)

---

### Post by lisati on 2010-05-31
Moved to "Server Platforms"

You might want to check out free services like [dyndns]("http://www.dyndns.com/") and [noip]("http://www.no-ip.com/") that let you sign up for a free domain name.

---

### Post by stepstools on 2010-05-31
Thanks for moving it, I wasn't sure where to put it.  I'm looking for a real domain, not a sub domain, I have a us.pn subdomain.

---

### Post by markbahnman on 2010-05-31
What I did was register a domain name and get it to forward the domain name to your server's IP address. Then on your side you set up the apache configurations for virtual hosting, a good guide for which is in the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html").

---

### Post by stepstools on 2010-05-31
Thanks for the info, I will try it.

---

