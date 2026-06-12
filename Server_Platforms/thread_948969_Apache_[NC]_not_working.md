---
title: "Apache [NC] not working"
date: 2008-10-15
forum: Server Platforms
---

### Post by skunkbad on 2008-10-15
This rewritecond/rewriterule set redirects from the query-string version of /test/good_url.php to the non-query-string version. How come [NC] doesn't work? If I try to go to test/gOOd_URL.php I get a 404 error. I tried using [N,R=301] on the rewrite rule itself, but that didn't make a difference. Here's what I have:

```
RewriteCond %{THE_REQUEST} ^GET\ /good_url\.php.*\ HTTP/ [NC]
RewriteCond %{QUERY_STRING} !^$
RewriteRule ^good_url.php(.*)$ http://www.yourdomain.com/good_url.php? [R=301]
```

---

### Post by skunkbad on 2008-10-16
I hate bumping, but I'm feeling the need after 46 people viewed with no response. Please advise.

---

