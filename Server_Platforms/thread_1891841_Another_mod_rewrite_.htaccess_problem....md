---
title: "Another mod_rewrite .htaccess problem..."
date: 2011-12-06
forum: Server Platforms
---

### Post by GB_Joe on 2011-12-06
Hi All!

It's got to the point now where I've tried pretty much everything I can think of, so I need some help!

I'm a volunteer (short on time!) in charge of a charity website at [http://www.candoweb.org]("http://www.candoweb.org"), we get free web hosting but it's command-line only over SSH, the server runs Ubuntu 10.04.3 and I can do pretty much what I like with it. I'm trying to add some PHP, both for a contact form and to consolidate some standard content with some includes. It all basically works fine, but I'm going to have to change the names of all the pages to x.php instead of x.html (unless someone knows a better way). I'm worried this will mess with Google's SEO and users' bookmarks & caches, so I want to set up redirects.

I've enabled mod_rewrite and restarted Apache, it now appears in the PHP info page. I've just started playing with changing AllowOverride to All instead of None, but I don't know exactly where to do this; there's a default file (tried this first) and a candoweb file (did this one too), three instances of AllowOverride in each... I set them all to All in the end!

My .htaccess file looks like this:
```
RewriteEngine On
RewriteRule ^contact\.php$ http://www.candoweb.org/contact.html [R=301,L]

```
Both those pages exist; ultimately I'll be wanting to redirect in the other direction, but I want to see it working before I start redirecting people to the new .php pages.

Cutting to the chase (finally): NOTHING I'VE DONE HAS MADE ANYTHING REDIRECT ANYWHERE!

Any help would be massively appreciated - let me know if more information is required, and spell it out because I really don't know what I'm doing!!!

Cheers,
Joe.

---

### Post by GB_Joe on 2011-12-06
Oh blinking flip...

I've just cleared my browser cache and it worked...

What a numpty! Time to add a self-deprecating signature and mark this one [SOLVED]...

](*,)

---

