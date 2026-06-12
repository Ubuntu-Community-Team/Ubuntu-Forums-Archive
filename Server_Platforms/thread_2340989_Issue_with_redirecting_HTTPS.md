---
title: "Issue with redirecting HTTPS"
date: 2016-10-24
forum: Server Platforms
---

### Post by odettefraile on 2016-10-24
I am trying to redirect HTTP to HTTPS using Apache 2.x with Ubuntu Server 14. I'm using mod_rewrite to accomplish this thing. 

This is my ../apache2/../default file:
> 
[SUP] <VirtualHost *:80>[/SUP]
[SUP]        RewriteEngine On[/SUP]
[SUP]        RewriteCond %{SERVER_PORT} !^443$[/SUP]
[SUP]        RewriteRule ^/(.*) https://militarybases.co/$1 [NC,R,L][/SUP]
[SUP]    </VirtualHost>[/SUP]


My HTTPS host is in the default-ssl is located in the same location. If you see the local IP, it does work perfectly. But, when I try to access using FQDN, the website is available at port 4334. I have mapped it to 443 on the firewall. Working without mapping is not the issue here. Problem is I can't use the port 443 of the firewall without mapping. It look like, another server has the same IP.

For now the valid ports and IPs are:
> 
https:// militarybases.co:4334
https:// 172.191.23.53:443
It works correctly, if the combination is 
> 172.191.23.53:80 

But, it is showing 400 error. If the redirect is directly being accessed using:
    > https:// militarybases.co:4334

*Error says that server does not understand the request. HTTP on SSL-enabled server port is not good. You have to use HTTPS protocol to access the url. *

**Solutions tried so-far:**
[B]
#1[/B]
I have rewritten the module with mod_rewrite and enabled in the following way:
    > .
    .
    RewriteCond %{HTTPS} off
    .
    .
[B]
#2[/B]
I know that there is an issue, with the initial request. And server does not understand the request on the 443 port. And for default settings, the http is 80 and https is 443.That's the reason, the redirecting is working locally. As a solution, I need a server, which understands HTTP and HTTPS requests on a single port. In other, have to buy a new server.
[B]
#3[/B]
Creating a dedicated hosting  also does not work. I have created configuration files as .conf file as /../httpd/.../dedicated.conf. And ovirtual.conf entry for dedicated.conf.

This is required for only inner directory pages. Rest of the site can worked using http. Also, if I try to access using an android phone, the address section is same for each site and it is taking it from [http://militarybases.co/directory/nas-key-west-navy-base-in-key-west/](http://militarybases.co/directory/nas-key-west-navy-base-in-key-west/). As the main page is not properly redirecting, it is using the address from the address mentioned on the main page of the site. I'm not able to configure, why it is only happening in android? And rest is working fine

Looking forward for some answers!
Thanks

---

### Post by TheFu on 2016-10-24
Setup a separate virtualhost for http ..

```
<VirtualHost *:80>
   ServerName militarybases.co
   ServerAdmin [email]root@militarybases.co[/email]

   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}$1 [R=301,L]
   RewriteCond %{SERVER_NAME} =militarybases.co
   RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,QSA,R=permanent]
</VirtualHost>
```

Setup a separate, standard virtualhost for https ... in a different file.

Done and done.  The DNS internal/external need to point to the WAN public IP.
If the firewall is running on a different machine, the initial 4334 redirection might be an issue, since it know about the hostname on the machine it is already on.

---

### Post by SeijiSensei on 2016-10-25
I'd follow TheFu's advice but use the Redirect directive instead.

```

<VirtualHost *:80>
ServerName militarybases.co
ServerAlias www.militarybases.co 
Redirect / https://militarybases.co/
</VirtualHost>

```

Then have a separate SSL host definition for the https site.

---

### Post by TheFu on 2016-10-25
"Redirect" appears to be a better solution. Thanks!  I'll test it soon for my situation.  Much cleaner and the apache docs recommend it for this purpose.

---

### Post by Vegan on 2016-10-25
add this to any web site header and it will reload the https version immediately

```
<script type="text/javascript">if (window.location.protocol != "https:") window.location.href = "https:" + window.location.href.substring(window.location.protocol.length); </script>
```

---

### Post by TheFu on 2016-10-25
> **Vegan said:**
> add this to any web site header and it will reload the https version immediately

```
<script type="text/javascript">if (window.location.protocol != "https:") window.location.href = "https:" + window.location.href.substring(window.location.protocol.length); </script>
```

Actually that doesn't work always.  Try it with **lynx** or **dillo** browsers - BTW, the web gets really fast that way.  That doesn't mean using javascript isn't an alternative if you can assure everyone uses javascript. I don't usually and there are many others who don't as well.  
[https://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/](https://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/)

---

### Post by Vegan on 2016-10-26
> **TheFu said:**
> Actually that doesn't work always.  Try it with **lynx** or **dillo** browsers - BTW, the web gets really fast that way.  That doesn't mean using javascript isn't an alternative if you can assure everyone uses javascript. I don't usually and there are many others who don't as well.  
[https://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/](https://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/)

I use WordPress which will not render without JavaScript and PHP along with a database

```
<noscript>This site requires JavaScript to render</noscript>
```

---

### Post by TheFu on 2016-10-26
Wordpress **does** work without javascript.  Probably a theme selection thing, but idunno.

But if control over the web server settings isn't possible and still want this to work, JS is an option.

---

