---
title: "Rewrite error on Apache"
date: 2008-08-21
forum: Server Platforms
---

### Post by dbourrion on 2008-08-21
Hi. On the apache server of my Ubuntu, I put this in the httpd.conf :

```
RewriteCond %{HTTP_USER_AGENT} !.*bot.*
RewriteRule ^/.*/.*/.*/.*/.*/([a-Z]+)\.([0-9]+)\.html$ \
http://mywebsite.fr/F?func=find-b&request=$2&find_code=SYS&local_base=$1
```

but each time I restart apache, i got that message :

> Syntax error on line 313 of /etc/apache2/apache2.conf:
RewriteRule: cannot compile regular expression '^/.*/.*/.*/.*/.*/([a-Z]+)\\.([0-9]+)\\.html$'

Help welcome ;-)

---

### Post by windependence on 2008-08-21
Obviously the syntax is wrong in that line. I don't even know what that is supposed to do. Can you tell us? It would be very helpful if we knew what you are trying to accomplish. Did you copy this from a tutorial?

-Tim

---

### Post by dbourrion on 2008-08-21
I took the RewriteRule directly from the doc of the developper of my ILS (I'm working in an academic library)

We're trying to expose our data from our catalog to google, via an Apache server. The rules are used to link the server to the catalog.

---

### Post by windependence on 2008-08-21
OK, well somewhere in that line there is a mistake. You may need to contact the developer and find out what it is. Also, if you typed this in manually, make sure you didn't make an error. ;)

-Tim

---

### Post by MJN on 2008-08-21
> **dbourrion said:**
> Hi. On the apache server of my Ubuntu, I put this in the httpd.conf :
 
```
RewriteCond %{HTTP_USER_AGENT} !.*bot.*
RewriteRule ^/.*/.*/.*/.*/.*/([a-Z]+)\.([0-9]+)\.html$ \
[http://mywebsite.fr/F?func=find-b&request=$2&find_code=SYS&local_base=$1](http://mywebsite.fr/F?func=find-b&request=$2&find_code=SYS&local_base=$1) 
```One immediate problem is that you've got a leading slash - remove it because URIs won't start with a slash when matched against internal rewrite rules (unlike if the code were in .htaccess, which is where this code was probably written for). Confusing, you bet.
 
Hence, it should be:
 
```
RewriteCond %{HTTP_USER_AGENT} !.*bot.*
RewriteRule ^.*/.*/.*/.*/.*/([a-Z]+)\.([0-9]+)\.html$ \
[http://mywebsite.fr/F?func=find-b&request=$2&find_code=SYS&local_base=$1](http://mywebsite.fr/F?func=find-b&request=$2&find_code=SYS&local_base=$1) 
```I don't know if that's the cause of the problem, but it won't work anyway until you fix that.
 
Also, take the rule out of httpd.conf (nothing should be in there) and put it either in the main config file or the appropriate virtualhost container. That's not the problem here, but it's the right thing to do.
 
Mathew

---

