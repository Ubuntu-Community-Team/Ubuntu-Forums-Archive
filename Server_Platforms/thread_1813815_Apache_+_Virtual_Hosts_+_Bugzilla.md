---
title: "Apache + Virtual Hosts + Bugzilla"
date: 2011-07-28
forum: Server Platforms
---

### Post by wesg on 2011-07-28
Previously I tried installing Trac, but that didn't work so well, so now i'm trying Bugzilla, but I seem to have run into the same problem.

I'm running the software on a VPS host, in a subdomain, but I can't seem to serve up .cgi or .pl files. I get a 500 error on the domain. The apache2.conf file has virtual host entries for the different subdomains, along with directory entries, which I've matched to the Bugzilla installation guide. 

```
<Directory /var/www/bugs.website.ca>
        AddHandler cgi-script .cgi .pl
        Options +Indexes +ExecCGI
        DirectoryIndex index.cgi
        AllowOverride Limit FileInfo Indexes
</Directory>
```

This is my Directory entry. How can Bugzilla and subdomains work together?

---

