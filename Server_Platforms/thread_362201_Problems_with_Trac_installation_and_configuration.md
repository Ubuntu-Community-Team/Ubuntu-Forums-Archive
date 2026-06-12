---
title: "Problems with Trac installation and configuration"
date: 2007-02-15
forum: Server Platforms
---

### Post by thiago_moreira on 2007-02-15
Hello, members of the forum,

I'm currently installing and maintaining a server which will host some e-learning platforms (like [Moodle]("http://www.moodle.org"), for example). Services like the Apache Web Server, PostgreSQL, MySQL, Tomcat 5.5, PHP, Wordpress, phpBB, Subversion are already installed and are running perfectly **on the same machine**. But the [Trac]("http://trac.edgewall.org") installation process isn't being an easy one so far. I installed this service, using the [tutorial available]("http://trac.edgewall.org/wiki/TracOnUbuntu") at the Trac website, but it doesn't work properly when I try to use both virtual hosts (the *default*, created by Apache itself, an the *trac* one), created on the Trac installation). When I try to access the trac page, using the URL: [http://localhost/trac.cgi](http://localhost/trac.cgi), the system shows the following error message:

**[SIZE="4"]Forbidden[/SIZE]**

You don't have permission to access /trac.cgi on this server.

*Apache/2.0.55 (Ubuntu) DAV/2 SVN/1.3.2 mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 mod_ssl/2.0.55 OpenSSL/0.9.8b Server at 172.17.33.221 Port 80 *

But when I disable the default virtual host, the Trac page loads normally. I need for both hosts enabled, because the e-learning platforms depends on the default virtual host to work.

Is there any other installation method than the one provided on the site? Every other tutorial shows exactly the same approach. :confused: 

Any provided solution will be very appreciated. Thanks a lot!

---

