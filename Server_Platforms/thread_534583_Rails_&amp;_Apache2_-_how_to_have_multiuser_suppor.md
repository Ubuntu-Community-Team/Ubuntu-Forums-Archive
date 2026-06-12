---
title: "Rails &amp; Apache2 - how to have multiuser support?"
date: 2007-08-25
forum: Server Platforms
---

### Post by geekphreak on 2007-08-25
All, 

I have configured Apache2 with FCGI to serve my Rails applications. Since I am the admin of my server, modifying fastcgi.conf is not a problem.
However, how can I have Rails apps from all users of my server running through Apache2 FCGI?
Ideally, I'd like to have a setup  like 
```
http://someserver/~someuser1/railsapp1/
http://someserver/~someuser1/railsapp2/
http://someserver/~someuser2/railsapp1/
...

```
which would serve up those Rails apps.
Is there a way this can be done through Apache and FCGI? Or do I need to use Mongrel or lighttpd or something else?

Thanks!

---

