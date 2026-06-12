---
title: "Mixing sub-domain wildcard serving with userdir mod"
date: 2009-11-01
forum: Server Platforms
---

### Post by seaders on 2009-11-01
Ok, to cut a long story short, I'm one of the admins on my old college computing society, which we've recently upgraded from 1 machine to 3, while we've also been adding in new features.

The way we've worked for a good few years now (on the 1 machine) was simply with Apache's userdir wherein anyone who requested a page which matched [http://www.domainname.com/~username](http://www.domainname.com/~username) served files which were located at /home/members/username/public_html. now, the main server isn't hosting the user files, it's on a second server, called homes.domainname.com, which works in the way I described above, with Apache's userdir mod, while also having a rewrite rule in place that redirects any request on the www server with a "/~" url to go to the homes server.

That's all working fine, but I just started playing around with serving wildcard sub-domains, so that every one of our members are able to access their web folder through username.domainname.com. Now, I've set the bind server up to point [www.domainname.com](www.domainname.com) to our www server and all other *.domainname.com to the homes server.

Unfortunately, though, it doesn't work how I'd like it to, instead of serving the files directly from there, it rewrites the URL to the way userdir expects it, homes.domainname.com/~username. what I'd actually like to do is have the server directly serve the files from both URLs, username.domainname.com and homes.domainname.com/~username.

My problem is that I don't know how to expand the userdir mod so that it catches and attempts to serve all URLs that aren't that catch all subdomains that aren't "homes", as well as any URLs that match homes.domainname.com/~*.

Anybody with an idea how I can do this?

---

### Post by seaders on 2009-11-01
Realistically, just to add, what I'd mainly want to do is modify the userdir directive,
[http://httpd.apache.org/docs/2.2/mod/mod_userdir.html](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html)

Rather than just catching the "domainname.com/~([^/]*)/" part of the URL, I'd like it to catch the "([^.]*).domain.com" part.  I can do this with rewriting conditions, but that's not the way I want the server to work, I would like Apache to serve the files directly, without rewriting the URL, like it does with the userdir mod.

---

