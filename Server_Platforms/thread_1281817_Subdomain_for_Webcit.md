---
title: "Subdomain for Webcit?"
date: 2009-10-03
forum: Server Platforms
---

### Post by jaychamp on 2009-10-03
I'm sure this is possible but my search has come up short.  Right now I access webcit using mysite.com:8989 but would like to use webcit.mysite.com.  

The only thing I found that may be on the right track is this:

```

<VirtualHost *:80>
    ServerName webcit.mysite.com
    ProxyPass / http://127.0.0.1:8989/
    ProxyPassReverse / http://127.0.0.1:8989/
</VirtualHost>

```I tried adding that to my virtual host file, and when that didn't work I tried httpd.conf.  I also enabled all proxy mods.  I got an error stating "You don't have permission to access /".    I'm sure there's something else I have to configure?  Maybe something in one of those proxy mods?

PS - I've already set up a webcit.mysite.com alias with my registrar

---

### Post by jaychamp on 2009-10-04
Any ideas?

---

