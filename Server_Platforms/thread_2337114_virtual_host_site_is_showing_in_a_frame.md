---
title: "virtual host site is showing in a frame"
date: 2016-09-14
forum: Server Platforms
---

### Post by micahpage on 2016-09-14
I have a server with 2 sites

python-gaming.com 
metulburr.com 

We want to change metulburr.com to python-forum.io (domain only, not the path)

We pointed that domain at the IP address in namecheap
[http://imgur.com/a/O4efF](http://imgur.com/a/O4efF)

and in the server made a vhost file for both metulburr.com and python-forum.io to point back to the same directory
```
metulburr /etc/apache2/sites-enabled $ ls
metulburr.com.conf  python-forum.io.conf  python-gaming.com.conf
metulburr /etc/apache2/sites-enabled $

```

But the problem is if you login to metulburr.com and then try to login to python--forum.io, it fails only in python-forum.io. If you check the page source of python-forum.io it shows it in a frame. I dont know why this frame is here?

---

