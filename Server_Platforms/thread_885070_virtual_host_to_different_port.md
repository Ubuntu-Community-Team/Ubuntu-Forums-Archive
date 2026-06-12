---
title: "virtual host to different port"
date: 2008-08-09
forum: Server Platforms
---

### Post by gazz1982 on 2008-08-09
I am trying to get another web address point to a different docroot

I want [www.example.co.uk:81](www.example.co.uk:81) to access www/example/index.php

I have another site which points to [www.another-example.co.uk:80](www.another-example.co.uk:80) and accesses www/another-example/index.php

I've tried to find the listen:80 but I cant remember which file this is in

Thanks for your help

---

### Post by Michael Daly on 2008-08-09
This should be in /etc/apache2/ports.conf for a typical setup.

---

### Post by gazz1982 on 2008-08-09
that file contains:

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

for web address [www.example1.co.uk](www.example1.co.uk) i want it to listen for [http://address:80/index.php](http://address:80/index.php)

and [www.example2.co.uk](www.example2.co.uk) to listen for
[http://address:81/index.php](http://address:81/index.php)

I've also seen virtual hosts which allow the use of the same port but different docroots 

I'm getting very confused

which is right?

I have 2 website urls I want one to point to one docroot and the other to point to a different docroot

---

### Post by chickpea on 2008-08-10
if "different ports to different hosts" isn't necessary, name-based virtual hosts would be your option. besides, i don't think you can point port 81 to your virtual host because this number is in the range of well-known port(0-1023).

---

### Post by Dedoimedo on 2008-08-10
Hello,

In the /etc/httpd/conf/httpd.conf file, you have the Listen directive listed, most likely:

```
Listen 80
```

Just add another for your desired, second port. Be aware that if you use privileged ports, you'll have to be root to start the server.

See if this helps.

Cheers,
Dedoimedo

---

### Post by Michael Daly on 2008-08-10
> **gazz1982 said:**
> 
I've also seen virtual hosts which allow the use of the same port but different docroots 

I'm getting very confused

which is right?

Rather than use two ports, you can use one port with two domain names.

For example, if you use port 80, you can then set (in http.conf):
```

# myserver.org is the name of your server; different than the virtual
# host names.

ServerName myserver.org:80

# This sets the use of virtual hosts by name rather than IP.
NameVirtualHost *:80

```
Then create files in sites-available, one for each virtual domain.  For example, the first domain:

File: domain1.com.conf
Contains:
```

<VirtualHost *:80>
ServerName    domain1.com
ServerAlias *.domain1.com

DocumentRoot /var/www/domain1
#other domain specific directory parameters
</VirtualHost>

```
Similarly, for domain2.com:

File: domain2.com.conf
Contains:
```

<VirtualHost *:80>
ServerName    domain2.com
ServerAlias *.domain2.com

DocumentRoot /var/www/domain2
#other domain specific directory parameters
</VirtualHost>

```
You can do this for as many domains as you wish.

If you *need* to use port 81, then add port 81 to the ports.conf file and then 
add:

NameVirtualHost *:81

to http.conf and use:
```

<VirtualHost *:**81**>
...

```
instead of 80.

Once you've created the files in sites-available, you can enable the sites with:

sudo a2ensite domain1.com.conf
sudo a2ensite domain2.com.conf
...

for each domain

---

