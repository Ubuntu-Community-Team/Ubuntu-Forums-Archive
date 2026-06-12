---
title: "help with multi-domain server running on non-standard port"
date: 2009-02-22
forum: Server Platforms
---

### Post by jdcnosse on 2009-02-22
Okay, so here's my situation.  I have a Linksys router running DD-WRT.  I also have my Ubuntu 8.04 server, running at 192.168.1.2 (static IP).

I have set up an account at no-ip.com, and I have enabled the DDNS service in my router for the hostname annaandjameswedding.no-ip.org.

in /etc/apache2/sites-available I have 3 virtual hosts, annaandjameswedding, computerrepair4u, and default.

both the annaandjameswedding & the computerrepair4u one look basically like this (except this one has computerrepair4u where annaandjameswedding is):

```

<VirtualHost 24.180.***.***:10910>
ServerName annaandjameswedding.no-ip.org
ServerAlias http://annaandjameswedding.no-ip.org
ServerAdmin number1pbefan@gmail.com
DocumentRoot /home/james/www/annaandjameswedding
</VirtualHost>

```

The default one looks like this:
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/james/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /james/home/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

I have Apache listening on port 10910 because port 80 is blocked either by my ISP or my cable modem (which was issued by my ISP).

right now when I go to annaandjameswedding.no-ip.org:10910 it gives me a page that says:

> 
Forbidden

You don't have permission to access / on this server.


I thought I had everything set up so that depending on which domain name you went to ([http://annaandjameswedding.no-ip.org](http://annaandjameswedding.no-ip.org), or [http://computerrepair4u.no-ip.org](http://computerrepair4u.no-ip.org)) the server would figure out where the request was coming from and use the correct VirtualHost.

Can anybody tell me what I'm doing wrong if I am doing something wrong?

---

### Post by RealPSL on 2009-02-22
By default Ubuntu blocks access to all directories the web server can serve. In order for others to be granted access you must explicitly allow it. Try the below modification of your code stub. Ignore the IP address I just did not like the *

```

<VirtualHost 10.2.3.10:10910>
	ServerName annaandjameswedding.no-ip.org
	ServerAlias http://annaandjameswedding.no-ip.org
	ServerAdmin number1pbefan@gmail.com
	DocumentRoot /home/james/www/annaandjameswedding
        <Directory /home/james/www/annaandjameswedding>
                Options Indexes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

---

