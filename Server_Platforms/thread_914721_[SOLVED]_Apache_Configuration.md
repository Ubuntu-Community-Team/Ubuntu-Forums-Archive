---
title: "[SOLVED] Apache Configuration"
date: 2008-09-09
forum: Server Platforms
---

### Post by beercz on 2008-09-09
Hello folks.

Bit of a newbie when it comes to apache here.  Running apache2 on ubuntu.

I have 2 subdomains: sub1.beercz.com and sub2.beercz.com say.

My ISP has my top level domain (beercz.com), and can forward all web requests to my server, via port mapping on my router.  That is all done.

I have set up two websites, one for each domain, the locations of each site is as follows:

/home/websites/sub1
/home/websites/sub2

What I am trying to achieve is to for a user who wants to go to [http://sub1.beercz.com](http://sub1.beercz.com) pick up the site in /home/websites/sub1, and simililary if another user wants to go to [http://sub2.beercz.com](http://sub2.beercz.com) be directed to the site in /home/websites/sub2

I think this is a configuration issue within apache2.  Can someone offer guidance as to how I can achieve this.

Thanks in advance.

---

### Post by dgoosens on 2008-09-09
hi,

you might want to check that your subdomains are correct:

here is a little tutorial:
[http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/")

---

### Post by volkswagner on 2008-09-09
What you need to do is setup virtual hosts for each sub domain.  You can read up on virtual hosting, in the meantime this will get you started.

You need to create the .conf file for each sub domain and edit it.

then disable the default, and enable the two new subdomains in sites-enabled.  If you will be running other sites, without the subdomain, ie: beercz.com, or [www.beercz.com](www.beercz.com), you will also want to create virtual hosts for them as well.

This can all be done in a terminal or webmin.

One how-to I followed also had me edit /etc/hosts and add all my subdomains listed with 127.0.0.1.  I am not sure if it is required.

[http://www.debian-administration.org/articles/412]("http://www.debian-administration.org/articles/412")

I just went trough this, post #3 has several links.

[http://ubuntuforums.org/showthread.php?t=911087&highlight=apache+virtual+host]("http://ubuntuforums.org/showthread.php?t=911087&highlight=apache+virtual+host")

---

### Post by devonps on 2008-09-09
> **volkswagner said:**
> 

One how-to I followed also had me edit /etc/hosts and add all my subdomains listed with 127.0.0.1.  I am not sure if it is required.

[http://www.debian-administration.org/articles/412]("http://www.debian-administration.org/articles/412")


I followed the same tutorial + a couple of others and didn't need to add any entries to my /etc/hosts file to get my sites up and running.

Hope this helps,
Steve.

---

### Post by beercz on 2008-09-10
All sorted now and my knowledge has increased.

Thanks guys.

---

