---
title: "phpmyadmin 403 after installing nginx"
date: 2009-07-17
forum: Server Platforms
---

### Post by Fliggerty on 2009-07-17
Hello again!

A friend recently suggested that I install nginx for use as a reverse proxy to serve all of my static content.  So I followed several different tutorials and got it up and running, and it seems to work splendidly.

I did, however, just discover an unwanted side effect.  I can't access phpmyadmin any longer; I just get a 403 Forbidden error, which is served by nginx.  I could access it just fine when I was just using Apache2.

A Google search gave me a site that suggested I make sure that phpmyadmin.conf has this in it:
```
[B]#Order Allow,Deny
  #Deny from all[/B]
  Allow from 127.0.0.1
```Well, it actually told me to comment out those first two lines.  None of that was in the file however, so I added it.  Still to no avail.

Any suggestions please?  Thanks!

--Fligg

---

