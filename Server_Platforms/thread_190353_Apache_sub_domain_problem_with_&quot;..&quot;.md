---
title: "Apache sub domain problem with &quot;..&quot;"
date: 2006-06-06
forum: Server Platforms
---

### Post by hagen00 on 2006-06-06
Hi 

I have the following problem. When I access my site using [www.domain.com/newsite/](www.domain.com/newsite/) then everything works fine. 

However, I now put in a subdomain i.e. [http://sub.domain.com/](http://sub.domain.com/) pointing to the newsite folder and now all the paths that i've included using ".." won't work. 

For example, i reference to my images using "../images/image1.jpg" etc. But that doesn't work anymore. The error log now says ""/var/www/oldsite/newsite/images/image1.jpg" doesn't exist, but it should point to "/var/www/oldsite/images/image1.jpg". So it's not going up a folder and seems like it's basically ignoring all ".." references in my HTML. 

Any ideas?

Thanks

Hagen

---

### Post by MJN on 2006-06-06
You've changed the hierarchy of the root (by dropping a level) which in turn has thrown the relative URLs out. /newsite is now the new root and so it can't go any higher than that (hence why it appears to be ignoring the ../) - your images directory is presumably at the same level as the newsite directory?
 
Solution is the to use absolute URL references (i.e. [http://full.domain/and/path/to/destination]("http://full.domain/and/path/to/destination")) or remove the redundant ../ in each.
 
Mathew

---

### Post by hagen00 on 2006-06-06
Thanks Mathew. Some of my images are actually in the "oldsite" dir, so I would have to go up a level using "..". I fixed the problem by using absolute references...something I wanted to avoid since it's not ideal at all and much less flexible. Oh well...Thanks for the reply.

---

