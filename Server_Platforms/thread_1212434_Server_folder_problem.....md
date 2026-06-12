---
title: "Server folder problem...."
date: 2009-07-13
forum: Server Platforms
---

### Post by greenwom on 2009-07-13
I have an odd problem.
My host updated servers... 
Links to my images folder no longer work.

I.E.

All images in this /images/ folder are being properly displayed on the root page as well as other pages that are not in the site's root directory.

So the problem looks like this.

```
www.domain.com/images/border/border.html
```
This comes back with a 404 error. 
but the following works.
```
ip_address/~user/images/border/border.html
```

When I go to ```
www.domain.com/images/
``` I'm seeing the server's root directory (there just happens to also be a /images/ folder there.

besides rewriting everything to a new folder name (which should work) what am I missing. 

The unix server is running apache, I have shell access as well as cpanel.

Hope someone can help (I've tried going to server specific IRC rooms but I always seem to get answers from my fellow Ubuntu users... :)

thanks in advance

---

### Post by greenwom on 2009-07-14
Well I did figure out a work around... Not Ideal...

I created a redirect with wildcards.  

```
www.domian.com/images/ to http://ip.address/~user/images/ 
```

This works but it shouldn't be this way....


	:-({|=

---

