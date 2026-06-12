---
title: "default httpd.conf"
date: 2010-11-25
forum: Server Platforms
---

### Post by Innigo on 2010-11-25
Hi Folks, 

I've been editing stuff in /etc/apache2/sites-available  and starting and stoping apache2 ok for a while. Now I'm getting a recursion error on restart pointing to line# 208 of httpd.conf

Include /etc/apache2/httpd.conf     #Obviously a bit self-referential!

I don't think I edited the httpd.conf but ... :-( How can I get the official default httpd.conf back again? 

PS. I've already tried reinstalling apache2 but that must just do the binaries.

PPS. For starters I'd like the to just get the "It works" index page in /var/www to come up. Doco mentions uncommenting the RedirectMatch directive in httpd.conf to achieve this but seaching httpd.conf for this( in read only mode, I thought) gave a not found error.

---

### Post by James78 on 2010-11-25
You can find the default configuration files in apache2.2-common. Here's a link to the package page. You can download the deb from there, and just extract the deb using your favorite tool, then extract the data.tar.gz file, and get the files you want.

The link assumes you're using Lucid, but you can click on any other release in the top right hand corner of the page.
[http://packages.ubuntu.com/lucid/apache2.2-common](http://packages.ubuntu.com/lucid/apache2.2-common)

---

### Post by CharlesA on 2010-11-25
The default httpd.conf file is empty.

---

### Post by James78 on 2010-11-25
> **CharlesA said:**
> The default httpd.conf file is empty.
Ha, I didn't catch that. ](*,)

---

### Post by CharlesA on 2010-11-25
> **James78 said:**
> Ha, I didn't catch that. ](*,)

Happens to everyone. I only know because I've had to mess around with it a few times today to my local web server serving a page from my home directory instead of /var/www. :p

---

### Post by Innigo on 2010-11-25
Ah, thanks guys, that was in the olden days I guess. It is of course nowadays in apache2.conf where including httpd.conf would not be recursive.

---

