---
title: "[SOLVED] Mod_rewrite question"
date: 2008-09-12
forum: Server Platforms
---

### Post by skunkbad on 2008-09-12
Google ended up indexing some URLs on my friends site, complete with session ID. I'm trying to redirect (using mod_rewrite) one of the URLs, but it always tacks on the session id.

RewriteRule ^catalog/accessories(.*) [http://www.thesite.com/accessories](http://www.thesite.com/accessories) [R=301]

Is there some way to tell Apache not to append the session id (?osCsid=23528750) on to the end??

Thanks for your help

---

### Post by windependence on 2008-09-13
according to google's webmaster pages, placing this in your robots.txt will stop googlebot from indexing any pages with a 
? 
in it 
User-agent: googlebot 
Disallow: /*?* 

-Tim

---

### Post by skunkbad on 2008-09-14
Awesome! I had already fixed it with the regex in the actual rewrite rules themselves, but this is good to know!

BTW, the fix was to add a ? to the end of the URL to be rewrited, like this:

RewriteRule ^catalog/accessories(.*)? [http://www.thesite.com/accessories](http://www.thesite.com/accessories) [R=301]

---

