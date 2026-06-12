---
title: "apache2 virtual includes don't work"
date: 2007-03-26
forum: Server Platforms
---

### Post by Azzuron on 2007-03-26
Hi there. We have a Fedora server thats pretty old. We use it for our webserver here, and it works really well for what we do. I setup a ubuntu server here, and configured the DNS and all that crazy stuff. So, in general the server works. the HTTPd sends pages out to the users who wish to view the site in development. My problem is that the server doesnt work with the includes used in shtml files. They seem to be ignored. I have looked in the config file for the server and cannot find anything odd. 

```
# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>
```

is in my config file. It looks like what should be needed to handle .shtml files but like i said nothing happens. this is an example include from one of my .shtml files.

```
<!--#include virtual="/includes/menu.html" -->
```

any suggestions? Thanks a bunch.
  --Dave

---

### Post by davro on 2008-06-25
Hi,

As root or sudo try running to enable the apache module include 

```
a2enmod include
```

and then 

```
/etc/init.d/apache2 force-reload
```

hope helped 

davro.

---

