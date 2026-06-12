---
title: "mod rewrite trailing slash"
date: 2009-02-28
forum: Server Platforms
---

### Post by obley on 2009-02-28
Hi, I know this isn't an Ubuntu specific issue, but there are a lot of bright and friendly people around here so I thought I'd throw this out there.

I'm trying to keep my root folder a little more organized so I have a subfolder with several "micro" sites, but I want to strip out the folder "micro" from the urls. I've got a rule that works perfectly, until the url is missing the trailing slash.

[PHP]RewriteRule ^5krun/?(.*)$ /micro/5krun/$1 [NC,L][/PHP]

for example: [http://foo.com/5krun/](http://foo.com/5krun/)
This loads the site perfectly. All relative links maintain the path structure and its great.

example2: [http://foo.com/5krun](http://foo.com/5krun)
This loads the index page, but the relative links are missing the /5krun/. The relative links become [http://foo.com/image1.jpg](http://foo.com/image1.jpg) instead of [http://foo.com/5krun/image1.jpg](http://foo.com/5krun/image1.jpg).

If I add a Redirect to my rule it works great, but does not strip the folder "micro" out of the url.

I've also tried to redirect ^5krun$ to 5krun/ but that returns [http://foo.com/http://foo.com/5krun](http://foo.com/http://foo.com/5krun) resulting in a 404.

Do I need a conditional rewritebase? If so, how do I do that?

Thanks for any help.

---

### Post by JeppeM on 2009-02-28
Hey :)

This is a comon problem, and it sadly can only be fixed by an external redirect ([R] flag). You can read more about it in apaches own mod rewrite guide: [http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html) - Scroll down to "Trailing Slash Problem".

I hope this helps a bit :)

---

### Post by obley on 2009-03-02
Thanks, I've gone ahead and just used two rules to fix that.

```
RewriteRule ^(mexico|5krun|morelight)$ /$1/ [r=301,L]
RewriteRule ^(mexico|5krun|morelight)/(.*)$ /micro/$1/$2 [L]
```

seems to have done the trick

thanks

---

