---
title: "Virtual Host Access Control by host (single IP)"
date: 2008-09-26
forum: Server Platforms
---

### Post by modulok on 2008-09-26
I am new at apache security, but I think I understand how access controls work.

I am trying to restrict access to a virtual host to only computers with specific IP addresses. The application is Surftrackr, I have setup its own virtual host (surftrackr.domain.com), below are the default files for the virtual host and .htaccess.

```
SURFTRACKR.CONF

<VirtualHost *:*>
ServerAdmin admin@domain.com
DocumentRoot /data/surftrackr
ServerName surftrackr.domain.com

ErrorLog /var/log/apache2/surftrackr-error_log
CustomLog /var/log/apache2/surftrackr-access_log common

<Directory "/data/surftrackr">
AllowOverride All
Options None
Order allow,deny
Allow from all
</Directory>

<Directory "/data/surftrackr/media">
Options -Indexes
</Directory>
</VirtualHost>
```

```
.HTACCESS FILE

SetHandler python-program
PythonHandler django.core.handlers.modpython
SetEnv DJANGO_SETTINGS_MODULE surftrackr.settings
PythonDebug On
PythonPath "['/data'] + sys.path"
Order deny,allow
Allow from all
```

This would allow any host access the site surftrackr.domain.com, which is not what I want. From what I read the 'AllowOverride All' tells apache to read the .htaccess access controls, I changed the .htaccess to the following.

```
Order deny,allow
Deny from all
Allow from 10.2.2.229 
```

Doing the above denies me from any client, even 10.2.2.229. The way the network is setup here is that 10.2.0.0/255.255.0.0. What I am wondering is if apache is thinking the IP 10.2.2.229 is a class A, therefore its still blocking the specified IP address.

Please help!!!

Thanks in advance!!!

---

### Post by skunkbad on 2008-09-26
Where you put that code can make a difference. You haven't shown the container that it's in. Yes, you put it in an .htaccess file, but is that all you put in there?

---

### Post by modulok on 2008-09-28
/etc/apache2/sites-enabled/surftrackr.conf
/data/surftrackr/.htaccess

Does this help figure out what's going on here?

---

### Post by andrey.p on 2008-10-16
Hi!
Can anybody share Surftrackr.tar.gz with me.
Project site Surftrackr.net inaccessible for a long time.

Thanks in advance!

---

### Post by lykwydchykyn on 2008-10-16
It's worth noting, you don't *have* to use a .htaccess file for this kind of thing, in fact I believe nowadays the recommended way is not to use one.  You can just put your security directives inside the site's conf file anywhere between the <Directory></Directory> tags.

---

