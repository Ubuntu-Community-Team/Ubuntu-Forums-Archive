---
title: "[Apache] Redirect to domain B when domain A requested"
date: 2009-02-24
forum: Server Platforms
---

### Post by ju2wheels on 2009-02-24
Hi everyone, I was wondering if theres a way to get Apache to redirect to another domain before it even starts the processing of whatever was requested. I know this could be done through PHP, but Id rather find a solution I can add to the Apache config.

If domain A (site.location.com) is requested I want Apache to redirect to a whole new domain B ([www.newsite.com](www.newsite.com)). Is this possible to do in the Apache config? 

Thanks,

---

### Post by CrucifiedEgo on 2009-02-24
You can do this using mod_rewrite.  Here's an example that matches olddomain.com and [www.olddomain.com](www.olddomain.com), and redirects it to [www.newdomain.com](www.newdomain.com), including any file requested (the $1 part).  So if i request olddomain.com/page.html -- i get [www.newdomain.com/page.html](www.newdomain.com/page.html).  Check it out:
```
RewriteEngine on
RewriteCond %{HTTP_HOST} ^OldDomain.com$ [OR]
RewriteCond %{HTTP_HOST} ^www.OldDomain.com$
RewriteRule ^(.*)$ http://www.NewDomain.com/$1 [R=301,L]
```

---

### Post by freerkkalsbeek on 2009-02-24
Rewriting will do the trick.

Make sure mod_rewrite is available/loaded in apache.
The code mentioned below can be put in a file called .htaccess in your old websites rootdir.

Freerk

---

### Post by ju2wheels on 2009-02-24
It worked, thanks.

---

