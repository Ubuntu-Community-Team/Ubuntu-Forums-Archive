---
title: "Ubuntu 13.10, Virtual Hosts, and Apache"
date: 2013-11-05
forum: Server Platforms
---

### Post by dannymichel on 2013-11-05
I added my site and configured my virtual host with what you see here. problem is nothing shows up when i visit the address. [http://pastie.org/8458722](http://pastie.org/8458722) no mater what kind of file i put in the public_html directory
[http://pastie.org/8458728](http://pastie.org/8458728)
[http://pastie.org/8458726](http://pastie.org/8458726)

---

### Post by dannymichel on 2013-11-06
the fix was
> Options Indexes FollowSymLinks
		AllowOverride All
		Require all granted

---

