---
title: "Using firewall to redirect"
date: 2014-04-10
forum: Server Platforms
---

### Post by misterpockets on 2014-04-10
I am fairly new to Ubuntu and am trying to setup a server with a few services running on it. My goal is to have everything running through :80.

Currently I have Subsonic setup as non-root and operating on :4040. I used the firewall guide here -[http://www.debian-administration.org/articles/386](http://www.debian-administration.org/articles/386) to allow Subsonic to be accessed via :80.

Is it possible to use the firewall settings to allow subdomains or pages(?) to access different internal ports?
Example:[INDENT]example.com/subsonic brings up (internal) :4040
example.com/other brings up (internal) :8080
[/INDENT]

Thank you!

Edit: I should note that I am running everything on one machine that is running Ubuntu Server 12.04.

---

### Post by SeijiSensei on 2014-04-11
I don't think so.  Iptables has no idea about the names used in URLs.  You might be able to use the [proxy features in Apache]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") for this, but you'd need to configure your sites as [name-based virtual hosts]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

I'm not entirely sure what the point of putting everything on the HTTP port is.  It isn't any more secure against automated port scanners.  They'll find the service whether it's on 80 or 4040.

---

