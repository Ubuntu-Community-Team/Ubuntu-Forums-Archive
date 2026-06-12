---
title: "Apache2 VirtualHost question (mod_ssl)"
date: 2006-03-25
forum: Server Platforms
---

### Post by Kurt` on 2006-03-25
Hi,

I've been doing alot of website work lately, and my latest project is an ecommerce site. My first time working with SSL, so it's pretty exciting.

I'm familiar with how the VirtualHost directive works, as I have 2 domains pointing to my home network (local BIND9 installation for the win). However, I have a question about how to do the following...

I want to set up a VirtualHost for a website (a subdomain) where any page you visit can be sent over SSL. For example, if a user is at [http://site.com/page1.html](http://site.com/page1.html), they can simply add "s" and visit [https://site.com/page1.html](https://site.com/page1.html) to view it over SSL.

I've read over the VirtualHost documentation, and I don't quite understand how to have a VirtualHost that works on both port 80 and 443 at the same time. Perhaps one of you can give me a small example?

Also, what is the NameVirtualHost directive usually set at? The IP that apache is bound to listen on?

Thanks in advance

---

### Post by kmi on 2006-03-25
For a self signed certificate  :
```
sudo a2enmod ssl
sudo apache2-ssl-certificate -days 3650
```
(3650 is for a 10 years certificate...)

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
sudo ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl
```
```
sudo gedit /etc/apache2/sites-enabled/ssl
```
So that it looks like this
```
NameVirtualHost *:443
<VirtualHost *:443>
```
```
sudo gedit /etc/apache2/sites-available/default
```
So that it looks like this
```
NameVirtualHost *:80
<VirtualHost *:80>
```
```
sudo gedit /etc/apache2/ports.conf
```
add
```
Listen 443
```
```
sudo gedit /etc/apache2/sites-available/ssl
```
an add 
```
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
```
```
sudo /etc/init.d/apache2 restart
```

I hope it helps ?!

---

### Post by LordHunter317 on 2006-03-25
That's totally wrong, unfortunately.

You cannot do name-based virtualhosting over SSL (There's a single case exception, you don't want/need to know about it).

To serve the same site over SSL is simple: simply use the same IP and DocumentRoot.  In essence, your port 443 VirtualHost will be identical to your port 80, with the SSL configuration added.

Do not try to add more than one Vhost to port 443.  It will not work.  You will be sorry.

---

### Post by kmi on 2006-03-25
Hi LordHunter317
I don't know what's totally wrong in the lines of post 2 - apparently everything - but I have used this method to set my https and it REALLY seems to work (login or subscription get 'httpsed'...).
Maybe a little more explanations (or links) would help me to understand ? May I ask you to give me info please ? :)

---

### Post by LordHunter317 on 2006-03-25
Well, I exaggerated a bit.  It's not totally wrong, but the 'NameVirtualHost :443' is totally wrong.  It won't work, it shouldn't be enabled.

I wouldn't put the entries in seperate files either.  They should go together, each site's http and https in a single file.  Add the stuff to default, copying what's already there adn adding SSL configuration as needed.

---

### Post by Kurt` on 2006-03-25
I had already generated my cert, so I'm all set with that.

[QUOTE=LordHunter317]You cannot do name-based virtualhosting over SSL[/QUOTE]
Then how would a company like GoDaddy offer SSL certificates for shared hosting plans? :confused:

> To serve the same site over SSL is simple: simply use the same IP and DocumentRoot. In essence, your port 443 VirtualHost will be identical to your port 80, with the SSL configuration added.
So should the NameVirtualHost be set to *:80 and *:443 respectively? I've seen websites that say to use your external (ISP-assigned) IP instead of the wildcard character. Any reason to do/not do that?

Edit:
My ISP blocks port 80, but not port 443. I want to be able to break up my hosted site into various subdomains (one for forums, one for the wiki, etc.), but not have to specify the port on the URL. So my next guess was to serve all the "sites" over SSL... would I be looking at the "you don't want/need to know about it" case mentioned in the 2nd reply?

---

### Post by LordHunter317 on 2006-03-25
[QUOTE=Kurt`]Then how would a company like GoDaddy offer SSL certificates for shared hosting plans? :confused:[/quote]Either by stuffing multiple IPs on your server, or using that one exception as I said and doing wildcard SSL certificates and a fixed hostname.

> So should the NameVirtualHost be set to *:80 and *:443 respectively?Really, for you, it should be set to neither.  Doing name-based hosting on one port of a site that's accessible over HTTP and HTTPS is a bad idea, IME.   Too many things to screw up.

> I've seen websites that say to use your external (ISP-assigned) IP instead of the wildcard character. Any reason to do/not do that?Only if you want it to be heard only on that address.

---

### Post by Kurt` on 2006-03-25
Thanks for the help guys.

I do need SSL over 2 domains on this machine, so I will investigate the wildcard SSL stuff.

---

### Post by LordHunter317 on 2006-03-25
It won't work if they're different second-level domains.

You can't get *.com.  You can get *.example.com, but that's it. 

You need to get 2 IPs and use them, hosting each site on it's own dedicated IP.

---

### Post by Kurt` on 2006-03-25
Ok, thanks alot for clearing that up!

---

