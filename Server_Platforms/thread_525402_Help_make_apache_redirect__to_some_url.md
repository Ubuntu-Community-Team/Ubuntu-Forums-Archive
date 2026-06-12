---
title: "Help make apache redirect / to some url"
date: 2007-08-14
forum: Server Platforms
---

### Post by dudi.dalal on 2007-08-14
Hi

I installed Mediawiki on my Ubuntu 7.04 (apt-get install . . . )
runing apache2

I configured successfuly the Mediawiki

When I access [http://my_host_name/mediawiki](http://my_host_name/mediawiki)  I'm directed to the main page of Mediawiki    that is fine ! ! !

I want to make apache server to redirect me to : 

[http://my_host_name/mediawiki](http://my_host_name/mediawiki)

when I access to: 

[http://my_host_name/](http://my_host_name/)

What Apache doing when I access [http://my_host_name/](http://my_host_name/) is howing me me to some index page with the apache2-default directory

How can I do it?

P.S
I try to place the directive at httpd.conf 

Redirect /   [http://my_host_name/mediawiki](http://my_host_name/mediawiki)

---

### Post by lavinog on 2007-08-14
Just to let you know I am pretty new at this but maybe this could help:

on my webserver:
 /etc/apache2/sites-available
has a couple of files, each one being a virtual server.
you may only have the default file
in the default file there is a line that says 
```
DocumentRoot /somepath/
```

I would say that what you should do is add mediawiki to the end
```
DocumentRoot /somepath/mediawiki/
```


I installed webmin on my server. It made setting it up much easier.

---

