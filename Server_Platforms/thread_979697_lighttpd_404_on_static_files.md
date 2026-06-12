---
title: "lighttpd 404 on static files"
date: 2008-11-12
forum: Server Platforms
---

### Post by kristian_nissen on 2008-11-12
My lighttpd is giving me a 404 on images but I'm unable to figure out why.

docroot:
server.document-root = "/home/kristian/workspace/"

site:
$HTTP["host"] =~ "example.local" {
	server.document-root = "/home/kristian/workspace/example"
}

"which lighttpd" says:
/usr/sbin/lighttpd

file permissions on the graphics and css
drwxrwxrwx 19 www-data kristian      4096 2008-11-12 09:21 example

I've tried www-data as group as well but doesn't work.

What to do?

---

