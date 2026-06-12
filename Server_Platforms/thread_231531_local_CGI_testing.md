---
title: "local CGI testing?"
date: 2006-08-07
forum: Server Platforms
---

### Post by &amp;)ky#)^ on 2006-08-07
I'm not running an Ubuntu server, just regular desktop Ubuntu.  I am doing CGI script development using Python, but I've got no way to test it without running a server.  I'd rather not turn my desktop system into a server.  Does anyone know of any solutions where I could run my CGI scripts locally for testing?

---

### Post by Glut on 2006-08-08
No. The best method is to install apache (or web server of choice) and limit it to localhost access. You will be able to test scripts and wont have to worry about external access.

---

