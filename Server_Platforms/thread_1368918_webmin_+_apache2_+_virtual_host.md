---
title: "webmin + apache2 + virtual host"
date: 2009-12-31
forum: Server Platforms
---

### Post by ragit on 2009-12-31
[SIZE=2]Hey everybody I would like to learn a trick.

I have been looking on the internet for some time (read 5 days) and can not figure it out. I have done a lot of how-to;s and no result :(

Here is my setup

ubuntu 9.10
webmin 1.500
apache  2.2.12
php, mysql, phpmyadmin proftpd etc.

static ip 145.x.x.13
domain haarik.nl (redirected to 145.x.x.13 by hostcompany)

webmin virtual server 
andles the name-based server  on address *.
[/SIZE]  [SIZE=2]**Address** Any
**Port** 80[/SIZE]  [SIZE=2]**Server Name** Automatic
**Document Root** /var/www/[/SIZE] [SIZE=2]
Handles the name-based server  on all addresses
[/SIZE]  [SIZE=2]**Address** Any
**Port** 443[/SIZE]  [SIZE=2]**Server Name** Automatic
**Document Root** /var/www[/SIZE] [SIZE=2]Handles the name-based server haarik.nl on all addresses
[/SIZE]  [SIZE=2]**Address** Any
**Port** 80[/SIZE]  [SIZE=2]**Server Name** haarik.nl
**Document Root** /var/www/haarik.nl/[/SIZE] [SIZE=2]
when i try to acces haarik.nl on the web i can see my website but the source is different. 
[/SIZE]<HTML>
<HEAD>
<TITLE>haarik.nl</TITLE>
</HEAD>
<FRAMESET ROWS="*,0">
<FRAME SRC="http://145.x.x.13/haarik.nl" NORESIZE>
<NOFRAMES>
Your browser does not support frames.
</NOFRAMES>
</FRAMESET>
</HTML>
[SIZE=2]I would like to add this site to google but first need to verify that this is mine. So google will search for a document googlexxxxxxx.html as in [www.haarik.nl/googlexxxxxx.html]("http://www.haarik.nl/googlexxxxxx.html") but then i get the error 404 not found.


How can i add my site (and more sites) to google using webmin or config files?

thank you very much


[/SIZE]

---

### Post by noway2 on 2009-12-31
You don't really add your site to google.  You can notify google that your site exists (I forget how, but just about any web design book has the information).  Even when you do this, there is no guarantee as to what sort of ranking you will get.  It will undoubtedly be low at first, meaning you won't be very visible, even by google.

---

### Post by ragit on 2009-12-31
I know that i will appear low in ranking, the problem is not adding the site to google but make is accessible for google. At this moment I can access my website but if i look @ the source it is a redirection. So when i try to access for instance the file img34.jpg in the root directory [www.haarik.nl/img34.jpg](www.haarik.nl/img34.jpg) it will say 404 file not found.

---

### Post by BkkBonanza on 2009-12-31
Why do you have a redirect configured? You should just have your DNS settings point your domain to your IP address. Is there something about your hosting situation you have not explained? When I try your site I get a DNS error.

---

### Post by ragit on 2009-12-31
I have a range of ip adresses from my provider

and have the server on 145.99.241.13

I have registered my domain @ hostnet.nl and they have forwarded (dns type A) straight to my ip.

try [www.haarenik.nl](www.haarenik.nl) (this now works because i have made this the standard virtual host)

now i would like to add my site edi-factuur.nl with the same options but this dont works.

---

### Post by ragit on 2009-12-31
or should I make my own nameserver on my server? still have some ip adresses unused

---

### Post by cdenley on 2009-12-31
haarenik.nl resolves to 145.99.241.13
edi-factuur.nl resolves to 91.184.0.95

The web server at 91.184.0.95 gives a reply with a simple page which places your real site ([http://145.99.241.13/haarenik.nl](http://145.99.241.13/haarenik.nl)) in a frame. I'm guessing you probably don't have access to the server which that domain resolves to since it is probably a redirection service. You don't want a redirection service. What you want is to configure edi-factuur.nl to also resolve to 145.99.241.13, then create a new vhost/site (not a subdirectory) for that domain.

---

### Post by ragit on 2009-12-31
I will ask hostnet to forward everything to my ip.

Hopefully we know more tomorrow.

thankyou

---

### Post by BkkBonanza on 2009-12-31
You don't need to run your own name server but you do need access to configuring your domain at hostnet.nl. You need to add another A record for edi-factuur.nl pointing to your IP (as cdenley indicates). Once that name resolves to your server then you can configure a new site on your server for that name. 

If you are not familiar with the VirtualHost directive in Apache (I assume your web server) then you will need to read up on that. It allows you to run multiple sites on the same IP address. 

If you want to use a different address in your range then you can set your A record to that instead, but you still need to configure Apache to listen and serve on that IP as well.

---

### Post by ragit on 2010-01-03
OK now i have both the domains pointed to my ip
[www.edi-factuur.nl](www.edi-factuur.nl)
[www.haarenik.nl](www.haarenik.nl)

[www.haarenik.nl](www.haarenik.nl) load good 
but edi-factuur.nl points to /var/www/

this is my httpd.conf
NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.haarenik.nl](www.haarenik.nl)
ServerAlias haarenik.nl *.haarenik.nl
DocumentRoot /var/www/haarenik.nl
</VirtualHost>

<VirtualHost *:80>
ServerName [www.edi-factuur.nl](www.edi-factuur.nl)
ServerAlias edi-factuur.nl *.edifactuur.nl
DocumentRoot /var/www/edi-factuur.nl
</VirtualHost>


and i have 000-default and default-ssl in /etc/apache2/sites-available

what is it that i`m missing?

---

### Post by BkkBonanza on 2010-01-03
I tried your sites just now and they appear to be working and have different content. Did you already solve this problem? Your config looks like it's ok.

---

### Post by ragit on 2010-01-04
problem solved.
thanks for the help

There is just one more thing, could the adres stay on [www.haarenik.nl](www.haarenik.nl) even if i navigate trough the site?

---

### Post by BkkBonanza on 2010-01-04
It depends on what you mean. You can do that with a frame redirect that can be set up on some DNS services. Look there for "frame redirect" or sometimes they make up some other weird name. Also it can be done manually on your site using a frame or sometimes using .htaccess redirection in Apache. How to best do this depends somewhat on the way your site content is structured.

Usually people use a frame redirect when they want to hide the real address of the site in the address bar and the hassle is that it won't follow the page structure correctly.

---

