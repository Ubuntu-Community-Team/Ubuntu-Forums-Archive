---
title: "The Ultimate Server - Ruby on Rails with Lighttpd, Apache2, PHP, MySQL, PostgreSQL"
date: 2006-11-20
forum: Server Platforms
---

### Post by James Wilford on 2006-11-20
Hi all,

For anyone out there struggling with getting Ruby on Rails running on Dapper Server, I've written a comprehensive howto on my blog. Using my procedure you can get Rails to coexist with your existing Apache/PHP sites, with Rails running in Lighttpd, and not have to compile anything from source!

Check it out and let me know what you think...

[http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server]("http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server")

Cheers,

James

---

### Post by Gaweph on 2006-11-20
I like your blog.

---

### Post by adamkane on 2006-11-20
Many thinks. I'll be adding this to the HOWTOs, if someone else doesn't.

---

### Post by emperon on 2006-11-21
I think you should consider rails development with mongrel, rather than lighttpd

---

### Post by James Wilford on 2006-11-21
emperon, the reason i went with lighty rather than mongrel was that the mod_proxy_balancer + mongrel_cluster solution requires Apache 2.2, and I wanted to avoid compiling from source to keep my server clean and maintainable. Ubuntu only has packages for Apache 2.0.

However, if you could give reasons why the mongrel solution is superior, I'd be interested to hear them. I certainly haven't had any problems using lighttpd.

---

### Post by adamkane on 2006-11-21
FYI

There's a HOWTO for xampp. xampp installs apache2.2.

---

### Post by emperon on 2006-11-23
Yes I know that ( and I went that way and it took 4 days of mine to build a deployable production environment) Note that however you can use mongrel as a standalone server or you can use **pen** for proxifying mongrel. I have just read rails community lean to mongrel way. Also you can use mongrel with capistrano. Just my 2 cents.

---

### Post by cantormath on 2006-11-23
This is also a good howto
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by Cazilla on 2007-06-02
HI all, Just want to let you all know that [http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server](http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server)
is down as of today. I was having issues connecting to the site last night. Today, noload.

Thank you.

---

### Post by gogo242 on 2007-06-02
> **Cazilla said:**
> HI all, Just want to let you all know that [http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server](http://blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server)
is down as of today. I was having issues connecting to the site last night. Today, noload.

Thank you.

[[COLOR="Blue"]A Google Cache of the page[/COLOR]...]("http://209.85.165.104/search?q=cache:Ocij2MUvjUcJ:blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server+blog.wilf.me.uk/articles/2006/11/20/the-ultimate-server-ruby-on-rails-with-lighttpd-apache2-with-php-mysql-postgresql-on-ubuntu-dapper-server&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

---

### Post by daybreaker on 2007-08-30
for some reason my fcgi was crashing preventing me from running lighttpd, and lighttpd was working before I tried installing fcgi...

For some reason, "ln -s /usr/bin/irb1.8 /usr/bin/irb" fixed the issue.

So, thanks forthe howto!

---

### Post by davidomundo on 2008-02-04
Usually, the default deployment people go with is MySQL, LigHTTPd, and Mongrel.

However, I totally recommend running rails with:

[LIST]
[*]PostgreSQL ([http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL"))
[*]Thin ([http://www.wikivs.com/wiki/Mongrel_vs_Thin]("http://www.wikivs.com/wiki/Mongrel_vs_Thin"))
[*]nginx ([http://www.wikivs.com/wiki/NGINX_vs_LigHTTPd]("http://www.wikivs.com/wiki/NGINX_vs_LigHTTPd"))
[/LIST]

---

