---
title: "apache and hula"
date: 2006-03-18
forum: Server Platforms
---

### Post by gary79 on 2006-03-18
Hi all,

I am aiming to host an apache webserver and hula mailserver on my trusty ubuntu box. I would like to be able to access both webpages and webmail (via hula's web module) over port 80. Using port 80 for both is important as some users that are inside a corporate network will only have access to port 80 requests.

Currently I have installed and configured apache and hula with each working nicely and mail is being received as it should. Now, I want to access both over port 80 but are unsure how to go about this.

I thought I could just add a virtual host entry within apache that pointed to the hula webmail index page, but it seems hula does not let you link its webpage directly. The only way I can access hula is via a request on port 8080.

I am not sure what options are available to resolve this issue so all thoughts or comments would be greatly appreciated. 

Gary.

---

### Post by bsm0f0 on 2006-03-18
You need to enable mod_proxy for apache

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

here's a clip from my virtual host ...

    <Proxy *> 
        Order deny,allow 
        Allow from all 
    </Proxy>

    <Location /> 
        ProxyPass [http://127.0.0.1:8080/](http://127.0.0.1:8080/) 
        ProxyPassReverse [http://127.0.0.1:8080/](http://127.0.0.1:8080/) 
    </Location>

---

### Post by gary79 on 2006-03-19
Cool, thanks.[LIST=1]
[/LIST]

So, how does the user hit the hula page? Do you have a virtual host named something like mail.example.com with the <Proxy> entery 'localhost:8080' in its config file?

Also, I have to ask, what are the core security steps I need to take to when using the apache proxy module to point at localhost? Just seems like something to be cautious of.

---

### Post by bsm0f0 on 2006-03-24
i use mail.domain.com for the virtual host ... as for the proxy, you need to make sure you turn off proxyrequests ... 

#
# Proxy requests are bad mmmkay.
# 
    ProxyRequests    Off

put that in your virtual host ... apache.org should have to docs on where to put it exactly :)

---

