---
title: "Fedora TortoiseSVN error"
date: 2011-10-24
forum: Server Platforms
---

### Post by balagosa on 2011-10-24
So pardon if i posted this as Fedora. Everything linux related problems i get, this forum is the first one i go to.

So we have a current setup of SVN and an Apache server.

The problem was while I was tweaking something from the apache server, the SVN server got affected. Now whenever I try to contact the SVN server, it replies 

```

SSL Error: Unknown Protocol

```

The apache server tweaks were subdomain tweaks. I changed their redirection pages.

---

### Post by balagosa on 2011-10-24
need help. Any form of help will do

---

### Post by balagosa on 2011-10-25
Just an update.

The svn on same site over port 80(http) works just fine. But when using port 443(https), this is where the problem occurs.

---

### Post by balagosa on 2011-10-25
SOLVED

I forgot to mention that webmin is also available to the server. Webmin made this problem solved easily.

The problem happened because I deleted the apache virtual server of https which is my svn access. So I had to remake the apache virtual server

I did the above but access was still not possible until I changed **Client SSL certificate** to **Not Required** via webmin.

---

