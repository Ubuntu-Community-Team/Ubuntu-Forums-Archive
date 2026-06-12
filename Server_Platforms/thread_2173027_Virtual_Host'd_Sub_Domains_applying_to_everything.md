---
title: "Virtual Host'd Sub Domains applying to everything"
date: 2013-09-07
forum: Server Platforms
---

### Post by sunny946 on 2013-09-07
Hello.
This is the code, I'm using to redirect the sub-domain to another port.
<VirtualHost *>
    ServerAdmin [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL]
    ServerName dev.mydomain.com
    ProxyPreserveHost On

    # setup the proxy
    <Proxy *>
        Order allow,deny
        Allow from all
    </Proxy>
    ProxyPass / [http://localhost:8888/](http://localhost:8888/)
    ProxyPassReverse / [http://localhost:8888/](http://localhost:8888/)
</VirtualHost>


However, [www.mydomain.com]("http://www.mydomain.com") , and any other sub domain, goes to the port as well.

---

### Post by volkswagner on 2013-09-07
I wrote a quick [how to]("http://ubuntuforums.org/showthread.php?t=1920715&highlight=proxypass") way back, but it should still apply.

You may try changing a couple settings.

Change:
```
<Proxy *>
Order allow,deny
Allow from all
</Proxy>
```


To:
```
 <location />
          allow from all
     </location>

```

If that does not help you can also substitute 127.0.0.1 for localhost in your proxy/proxyPass urls.


> However, [www.mydomain.com](www.mydomain.com) , and any other sub domain, goes to the port as well.

This could be an indication of NameVirtualHosts not working.  How many virtual host files do you have in /etc/apache2/sites-enabled?
Are they all working as expected except before setting up the reverse proxy host?

---

### Post by sunny946 on 2013-09-07
Errr, I have one file in /sites-enabled called 000-default
I tried changing it to location, same result, everything going to the new port.

---

### Post by volkswagner on 2013-09-07
Each virtual host should have it's own vhost file in /etc/apache2/site-available.  When you enable the site
using command 'a2ensite' it create the symbolic link in /etc/apache2/sites-enabled.

Please read up on the setup of Apache2 NameVirtualHosts in the [sticky on this Server Forum]("https://help.ubuntu.com/10.04/serverguide/httpd.html").

You should have a unique file/virtual host file for each domain.  This is how apache will determine which site to serve based on the request and what is
included in your config file.

---

### Post by sunny946 on 2013-09-07
Success \o/
Thanks!
Edit:
Hmmm, it now sees the incoming IP as being local, can I prevent this or will I just need to deal with it?

---

### Post by volkswagner on 2013-09-07
> **sunny946 said:**
> 
Hmmm, it now sees the incoming IP as being local, can I prevent this or will I just need to deal with it?

I assume "it"=apache2 access logs?

Where there's a will, there's a way.  I have not done this so, I won't be much help.

It seems you need to utilize "X-Forwarded-For", look for it in the [Apache2 docs]("http://httpd.apache.org/docs/trunk/mod/mod_proxy.html").

You may need to dig a bit, but it does seem possible.

---

