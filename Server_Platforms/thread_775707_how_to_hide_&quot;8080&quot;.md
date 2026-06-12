---
title: "how to hide &quot;:8080&quot;?"
date: 2008-04-30
forum: Server Platforms
---

### Post by vitorgatti on 2008-04-30
How can I hide the ":8080" from the address bar?
My site is, for example, **mysite.com**
Then it redirects to **mysite.com:8080/opencms/opencms/**

Is there a way to keep mysite.com in the address bar?
Just for eye candy...

I'm using Apache and OpenCMS.

Thanks!

---

### Post by bluefrog on 2008-04-30
not an apache guru but I think mod_rewrite might do that
investigate that

---

### Post by cdenley on 2008-04-30
Something like this would work.

```

sudo a2enmod proxy
sudo a2enmod proxy_http

```

```

NameVirtualHost *
<VirtualHost *>
        <IfModule mod_proxy.c>
                ProxyRequests Off
                <Proxy *>
                        Order deny,allow
                        Allow from all
                </Proxy>
                ProxyVia On
        </IfModule>
        ServerName mysite.com
        ProxyPass / http://127.0.0.1:8080/opencms/opencms/
        ProxyPassReverse / http://127.0.0.1:8080/opencms/opencms/
</VirtualHost>

```

---

### Post by vitorgatti on 2008-04-30
Thanks a lot for the help
I'm going to test those stuff

:)

---

### Post by vitorgatti on 2008-04-30
> **cdenley said:**
> Something like this would work.

```

sudo a2enmod proxy
sudo a2enmod proxy_http

```

```

NameVirtualHost *
<VirtualHost *>
        <IfModule mod_proxy.c>
                ProxyRequests Off
                <Proxy *>
                        Order deny,allow
                        Allow from all
                </Proxy>
                ProxyVia On
        </IfModule>
        ServerName mysite.com
        ProxyPass / http://127.0.0.1:8080/opencms/opencms/
        ProxyPassReverse / http://127.0.0.1:8080/opencms/opencms/
</VirtualHost>

```


where do I put this code?
httpd.conf?
apache.conf?

---

### Post by cdenley on 2008-04-30
Backup your default vhost configuration...
```

cp /etc/apache2/sites-available/default ~/vhost_backup.txt

```

...then replace /etc/apache2/sites-available/default with the configuration I posted, then reload apache.
```

sudo /etc/init.d/apache2 reload

```

---

### Post by vitorgatti on 2008-04-30
this almost worked...
worked, but now the page isn't displayed correctly
like the images links weren't linked right

I wonder why...

---

### Post by cdenley on 2008-04-30
What are the URL's of the images?
```
http://mysite.com:8080/opencms/opencms/images/myimage.jpg
or
http://mysite.com:8080/opencms/images/myimage.jpg
```

How are the images referenced in your html code?
```

<img src="http://mysite.com:8080/opencms/opencms/images/myimage.jpg" />
or
<img src="/opencms/opencms/images/myimage.jpg" />
or
<img src="images/myimage.jpg" />

```

---

