---
title: "I am thinking of moving my website..."
date: 2011-09-10
forum: The Cafe
---

### Post by waloshin on 2011-09-10
From Waloshin.com/blog to Waloshin.com. 

Now would this hurt my search terms, and search traffic?

---

### Post by Mmmbopdowedop on 2011-09-10
Would a:
```

RewriteEngine On
RewriteRule ^([^/\.]+)/?$ /blog [L]

```
in a file named .htaccess in the server's root folder work out for you?
I'm not sure if that will actually work, with relative links ect.

But you won't have to change anything, just with that file, anything aimed at yourdomain.com would be showing yourdomain.com/blog with no changes at all to your search terms, as yourdomain.com/blog would still be intact and unchanged.

*shrug
*not an .htaccess guru, it's just what mine does.

Looking at it, it probably doesn't do what I/you expected, but hopefully it will be a guide for you to look into something more meaningful.

---

### Post by nmaster on 2011-09-10
it could hurt your search results. web crawlers (like the ones used by Bing and Google) would take some time to find the new site location. check out the google webmaster tools if your interested: [https://www.google.com/webmasters/tools](https://www.google.com/webmasters/tools)

i would recommend moving the website to the desired location, but put a redirect (via php for example) on the old location. the main page is probably the most important.  I recently restructured a website drastically.  the main site stayed the same but many of the subpages changed names.  after a little while, the google bots figured it out.

---

### Post by waloshin on 2011-09-10
The site is a self hosted Wordpress blog if that helps anyone.

---

