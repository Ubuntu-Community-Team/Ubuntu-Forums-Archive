---
title: "HTTP redirection to multiple servers"
date: 2007-02-11
forum: Server Platforms
---

### Post by matt_b on 2007-02-11
Hi all,

I used to have multiple static IP addresses from my ISP so that each of my 3 servers (all win 2003 web servers) had it's own address and each served a separate website. Due to a move I now only have one static IP address but would still like to host my websites on the same three servers, but cannot because I only have the one address!

I would like to have my main Ubuntu server (which has the only static address) redirect traffic to the appropriate server based on the http address people are accessing (e.g. [www.mysite1.com](www.mysite1.com) redirects to 192.168.1.1, [www.mysite2.com](www.mysite2.com) redirects to 192.168.1.2 etc.)

Is there any way I can do this with Apache, reverse web proxy or using some inbuilt linux IP tools? My Ubuntu server does not host any websites (it doesn't even have apache installed) but I am willing to put whatever tools on it I need.

Thanks for any help!
matt_b

---

### Post by jtc on 2007-02-11
How about running Apache2 with mod_proxy as a reverse proxy?

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)

---

### Post by matt_b on 2007-02-13
Hi, thanks for the input. Rather than use host-based redirection I've opted for a /site1, /site2 or /site3 redirect to each of my boxes (as per *[http://ubuntuforums.org/showpost.php?p=1852061&postcount=5)](http://ubuntuforums.org/showpost.php?p=1852061&postcount=5))*. I've installed Apache2 and enabled proxy, also have set up my /etc/apache2/sites-available/default as follows:

```

NameVirtualHost *

<VirtualHost *>
  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>

  ProxyPass /site1 http://192.168.1.1
  ProxyPassReverse /site1 http://192.168.1.1
  
</VirtualHost>

```

When I browse to this host via [http://192.168.1.254/site1](http://192.168.1.254/site1) I see the proxied web page on 192.168.1.1 as expected, but none of the images are displayed and hyperlinks don't work. 

Instead of links being [http://192.168.1.254/site1/myotherpage.htm](http://192.168.1.254/site1/myotherpage.htm) they are [http://192.168.1.254/myotherpage.htm](http://192.168.1.254/myotherpage.htm). It's as if the ProxyPassReverse isn't working at all...

Any help would be appreciated

---

### Post by Brazen on 2007-02-13
ProxyPass and ProxyPassReverse will not add in the /site1 portion.  The link on your site will need to point to /site1/myotherpage.htm.  We do this here and to make sure internal clients can use the same site, we have our internal computers also go through the proxy.

---

### Post by Brazen on 2007-02-13
Oh yeah, if you want it to add in the /site1, I believe you can use mod_rewrite.

---

### Post by matt_b on 2007-02-13
Thanks - I've decided that host-based redirection is actually better for me, and have it semi-working (I can't seem to get OWA working over HTTPS, but still have a few more things to try).

I have a question though - what's the functional difference between:

```

<VirtualHost *>
  ServerName www.mydomain1.com

  ProxyPass / http://192.168.1.1/
  ProxyPassReverse / http://192.168.1.1/

</VirtualHost>

<VirtualHost *>
  ServerName www.mydomain2.com

  ProxyPass / http://192.168.1.2/
  ProxyPassReverse / http://192.168.1.2/

</VirtualHost>

```

and 

```

<VirtualHost www.mydomain1.com>

  ProxyPass / http://192.168.1.1/
  ProxyPassReverse / http://192.168.1.1/

</VirtualHost>

<VirtualHost www.mydomain2.com>

  ProxyPass / http://192.168.1.2/
  ProxyPassReverse / http://192.168.1.2/

</VirtualHost>

```

From what I've been reading I'm not sure where to put the domain name - if I choose option 1 then apache warns that I have overlapping virtual hosts, if I choose option 2 it seems to stop working altogether (I get a standard apache "page not found" error).

Thanks
Matt

---

### Post by Brazen on 2007-02-13
> **matt_b said:**
> ...

From what I've been reading I'm not sure where to put the domain name - if I choose option 1 then apache warns that I have overlapping virtual hosts, if I choose option 2 it seems to stop working altogether (I get a standard apache "page not found" error).

Thanks
Matt

there shouldn't be any functional difference.  Do you also have the "NameVirtualHost" directive?  You'll need it.  should just be this, you can put it right above your VirtualHost sections:```
NameVirtualHost *
```

Here is my config for comparison, with just our public ip and dns name changed to protect the innocent :) :```
NameVirtualHost 999.999.999.999:80

<VirtualHost 999.999.999.999:80>
    ServerName www.server.com:80

    ProxyPass / http://192.168.2.36/
    ProxyPassReverse / http://192.168.2.36/
</VirtualHost>


<VirtualHost 999.999.999.999:80>
    ServerName ww2.server.com:80

    ProxyPass /foo/ http://192.168.2.4/
    ProxyPassReverse /foo/ http://192.168.2.4/

    ProxyPass /FOO/ http://192.168.2.4/
    ProxyPassReverse /FOO/ http://192.168.2.4/

    ProxyPass / http://192.168.2.36/
    ProxyPassReverse / http://192.168.2.36/
</VirtualHost>


<VirtualHost 999.999.999.999:80>
    ServerName owa.server.com:80

    Redirect permanent / https://888.888.888.888/exchange/
</VirtualHost>

```

Using * instead of an ip address should be just as good though.  My way just makes sure it only listens on the specified IP address in the case of having multiple IP addresses on a server.  If you use * then it will just apply to all IP addresses of all network adapters.  Same thing with the :80 just specifies port, but it should not be needed.

As for Exchange OWA, it is a known problem reverse proxying through Apache.  If you google for "OWA apache proxy" you should find some documentation on it.  I think I found that someone had figured out how to do it, but I never tried it myself.  As you can see, my solution was just to eat another public IP and have the requests directed to that.

---

### Post by matt_b on 2007-02-13
Excellent, thanks for clearing that up. I've made a few changes and now both my test sites work :)

I had "NameVirtualHost *" in my config file but forgot to include it in my post - d'oh.

There seems to be lots of resources online for reverse proxying SSL OWA, but some of them differ so wildly that I don't know which one(s) to follow. I think I'll start at the beginning at see what happens...

I assume that I first need to set up Apache to serve HTTPS as well as HTTP, before I setup the reverse proxy? If this is the case, is OpenSSL the way to go?

Thanks for your input so far
Matt

---

### Post by Brazen on 2007-02-14
Yes you will have to setup OpenSSL and mod_ssl before you can reverse proxy https websites and before you tackle the additional issues of reverse proxying OWA.  I personally have not done any https with Apache though.

---

