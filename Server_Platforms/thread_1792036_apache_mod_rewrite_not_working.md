---
title: "apache mod_rewrite not working"
date: 2011-06-27
forum: Server Platforms
---

### Post by whyiturn on 2011-06-27
I can't for the life of me figure out what's going wrong here.

I have mod_rewrite and mod_proxy loaded properly for the apache2 package in 11.04.

I added the following to the bottom of my apache2.conf:

RewriteEngine: On
RewriteRule: ^/$ /test [L]

The server restarts fine, but / is not getting rewritten in the slightest.  And when I added the RewriteLog directive, the log file had absolutely nothing in it.  What might be the issue here?

---

### Post by lisati on 2011-06-27
*Thread moved to **Server Platforms**.*

---

### Post by drhiii on 2011-07-02
Same here.  For the life of me cannot figure this out.  Have followed a slew of examples.  

Did you find a solution?



> **whyiturn said:**
> I can't for the life of me figure out what's going wrong here.

I have mod_rewrite and mod_proxy loaded properly for the apache2 package in 11.04.

I added the following to the bottom of my apache2.conf:

RewriteEngine: On
RewriteRule: ^/$ /test [L]

The server restarts fine, but / is not getting rewritten in the slightest.  And when I added the RewriteLog directive, the log file had absolutely nothing in it.  What might be the issue here?

---

### Post by SeijiSensei on 2011-07-02
You need to put these directives in the <VirtualHost> container for the site in question.  Rewrite commands are not global; they apply to specific virtual hosts.

---

