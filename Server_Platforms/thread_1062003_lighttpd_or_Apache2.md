---
title: "lighttpd or Apache2?"
date: 2009-02-06
forum: Server Platforms
---

### Post by Bozmeister on 2009-02-06
Hi

Couple of queries here. I have installed Ubuntu (LAMP) on VirtualBox inside Vista premium.  Seems ok. When I login as root using sodu, and try to start the Apache server using:

 httpd -h

I get -bash: httpd: command not found

I also see at the top of the screen:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1

Also, would I be better of using Lighttpd or should I stick to Apache? I want to develop PHP on mysql db using a server. I have installed ubuntu server edition.

Hope you can help.

---

### Post by BlackHero on 2009-02-06
apache2 for ever..

---

### Post by Skyride on 2009-02-06
As much as I am for using linux, why bother with a linux VM AT ALL? Theres a windows version of Apache.

Otherwise, Apache

---

### Post by punx45 on 2009-02-06
i believe its /etc/init.d/apache2 start,stop etc.

---

### Post by Thirtysixway on 2009-02-08
I like both apache and lighttpd.  I did a very simple test and on my machine, lighttpd could handle requests faster than apache.  It also used less memory so that was nice.

I stuck with it untill I started really doing some developing/testing with things like Drupal which require .htaccess for things like cleanurls.  I switched back to apache for the .htaccess support, and a lot of scripts are written for apache.

It's up to you, really.  for a vm or low resource environment I'd suggest lighttpd.  If you need some of the modules or .htaccess support use apache.

---

