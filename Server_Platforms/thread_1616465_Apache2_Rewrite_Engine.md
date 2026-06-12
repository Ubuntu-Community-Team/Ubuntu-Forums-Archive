---
title: "Apache2 Rewrite Engine"
date: 2010-11-08
forum: Server Platforms
---

### Post by P222PJP on 2010-11-08
I am trying to use a LAMP server to develop a CMS system and i'm wanting to perfrom the below rewrite for a server generated css file.

I would like the link /css/1/mobile.css to redirect to /css.php?website=1&client=mobile

I have written the below rule and it passes the /css/1/mobile.css to the css.php page but doesn't add the query string values

RewriteRule ^css/(.*)/(.*)\.css?$ /css.php?website=$1&client=$2 [L]

---

