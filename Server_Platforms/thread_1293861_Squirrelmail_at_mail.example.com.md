---
title: "Squirrelmail at mail.example.com"
date: 2009-10-17
forum: Server Platforms
---

### Post by thelethargarian on 2009-10-17
Hi,

The other day I set up an old laptop (HP/Compaq nc4000) with Ubuntu Server Edition because I had no other use for it and I like playing around with servers. I set it up as a LAMP server, plus Squirrelmail webmail client. It all works with the provided sample apache site file that comes with squirrel mail, but to visit the Squirrelmail page, it is set to use [www.example.com/squirrelmail]("http://www.example.com/squirrelmail"). This is all good and works, but I want to be able to visit mail.example.com to get there. I was wondering how this is done, as I am rather new to apache. I think I have to set up a Virtual Host file in /etc/apache2/sites-available, but I don't know how. So to recap: I want to be able to visit Squirrelmail at mail.example.com and my home page (/home/www) at [www.example.com]("http://www.example.com") (this part already works).

Thank You So Very Much!!

---

### Post by volkswagner on 2009-10-17
Yes, you will want to set up a virtual host.  Use the Apache [server docs]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") to help.

You will want to set the document root to /usr/share/squirrelmail or wherever you have squirrel mail installed, perhapss /var/www/squirrelmail.

---

### Post by thelethargarian on 2009-10-17
I have looked through everything I can find and have tried multiple ways to write the configuration file, but it just will not work. You were correct in assuming that my root directory needs to be /usr/share/squirrelmail. I just don't know why I can't get it to work. I also have another file in /etc/apache2/sites-enabled called website which makes the root directory for [www.example.com](www.example.com) /home/www (the space where my index page is).

Thanks for you help so far.

---

### Post by volkswagner on 2009-10-17
Lets get some assumptions out of the way.

Do you have a FQDN and are using [www.example.com](www.example.com) to mask your actual name in this forum?

How did you install Squirrelmail?

---

### Post by thelethargarian on 2009-10-17
Yes, I have a FQDN that I could use for this server, but I am currently planning on running the server without a domain name and accessing it via ip until it is working fully and I get around to forwarding it to my ip. I installed Squirrelmail via apt-get.

---

### Post by volkswagner on 2009-10-17
Test environments are a weak area for me.

I don't think you can use subdomains for the example.com, just [www.example.com](www.example.com) only.

I think when you use a non www subdomain, your browser will be seeking DNS globally on the net.  Do you get "page not found" or a different error?

---

### Post by thelethargarian on 2009-10-17
I get a page not found (host not found).

---

### Post by volkswagner on 2009-10-17
So yes, you cant use example.com with any other subdomain, except www.  You will need to set up your FQDN or use the subfolder setup inside example.com.

See the two attached screen shots.  I have no example.com on my LAN.  If I point my browser to [www.example.com](www.example.com) I get a page, but anything with a different subdomain returns a 404-page not found.

---

### Post by thelethargarian on 2009-10-17
Oh, sorry for the confusion. I was just using example.com to mask my domain. [www.example.com](www.example.com) is reserved as a top level reserved domain for things like the way I was using it. I should have stated that.

---

### Post by volkswagner on 2009-10-18
> **volkswagner said:**
> Lets get some assumptions out of the way.

Do you have a FQDN and are using [www.example.com](www.example.com) to mask your actual name in this forum?


> **thelethargarian said:**
> Yes, I have a FQDN that [COLOR="Red"]I could use[/COLOR] for this server, but I am currently planning on running the server without a domain name and accessing it via ip until it is working fully and I get around to forwarding it to my ip. I installed Squirrelmail via apt-get.

That is not what you stated here.

I am confused.

---

### Post by thelethargarian on 2009-10-18
> **thelethargarian said:**
> Yes, I have a FQDN that I could use for this server, but I am currently planning on running the server [COLOR=Red]without a domain name and accessing it via ip[/COLOR] until it is working fully and I get around to forwarding it to my ip. I installed Squirrelmail via apt-get.

I was planning on accessing it using it's ip address until I pointed the domain name to it. I was not planning on using example.com as the domain name, I was only using it to mask my domain name on this forum. Thank you for bearing with me on this and sorry for the confusion.

---

### Post by volkswagner on 2009-10-20
How are you handling DNS?  Do you have a static IP from your ISP?

Did you properly setup your subdomain at your registrar or dynamic host provider?

You will at least need to point your subdomain to your external IP address, at the DNS provider.


Please post output of

```
ls -alt /etc/apache2/sites-enabled
```

Please post vhost file for squirrelmail.

---

