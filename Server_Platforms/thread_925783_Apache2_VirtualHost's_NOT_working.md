---
title: "Apache2 VirtualHost's NOT working"
date: 2008-09-21
forum: Server Platforms
---

### Post by randomblink on 2008-09-21
Alrighty...
I'll try to be as specific as I can.

I have a server at home.
It has a single IP address.
I have setup an account at [www.dyndns.com](www.dyndns.com)

I have named my server myservername
I have setup myservername.dyndns.com as a Host service.

Then I created two WebHop services through them.
WebHop #1) subdomain1.dyndns.com
WebHop #2) subdomain2.dyndns.net

My goal is so that when you follow: subdomain1.dyndns.com
You visit my "/var/www" folder.

When you visit: subdomain2.dynsdns.net
You visit my "/home/username/path"

SO...
( *sidenote: I had to set my router to listen on port 8080 because my ISP blocks port 80. So... that's already configured and running on my router as well.* )


I setup the following:

/etc/apache2/ports.conf
```

Listen 8080

NameVirtualHost *:8080

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

/etc/apache2/httpd.conf
```

ServerName myservername:8080

```

/etc/apache2/sites-available/default
```

<VirtualHost *:8080>
        ServerAdmin     somename@somedomain.com
        DocumentRoot    "/var/www/"
        DirectoryIndex  index.html index.htm index.php

        <Directory "/var/www/">
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

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

/etc/apache2/sites-available/subdomain2.dyndns.com
```

<VirtualHost *:8080>
        ServerAdmin     somename@somedomain.com
        ServerName      subdomain2.dyndns.net
        ServerAlias     subdomain2.dyndns.net

        DirectoryIndex  index.php
        DocumentRoot    /home/username/path
 
        <Directory /home/username/path>
                AllowOverride All
                Allow from All
        </Directory>

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

</VirtualHost>

```

It doesn't work.
I am confused.

I have successfully:
Command Line Interface
```

a2ensite subdomain2.dyndns.com

```

At DynDns I setup the accounts as follows:

1) First Services
Hostname : myservername.dynsdns.com
Wildcard : Create wildcard alias for "*.host.domain.tld" ( YES )
Service Type : Host with IP Address
IP Address : IP Address was AUTO DETECTED

2) Second Service
Hostname : subdomain1.dyndns.com
Wildcard : Not Checked
Service Type : WebHop Redirect
WebHop Settings : Redirect URL : X.X.X.X:8080
Cloak This Page : Checked
Cloaked Title : myservername

3) Third Service
Hostname : subdomain2.dyndns.net
Wildcard : Not Checked
Service Type : WebHop Redirect
WebHop Settings : Redirect URL : X.X.X.X:8080
Cloack This Page : Checked
Cloaked Title : subdomain2

So far.
What works is when I visit subdomain1.dyndns.com
Visiting subdomain2.dyndns.net ALSO visits the same page.
And... visiting myservername.dyndns.com gets nothing.

Can someone help me out?!

---

### Post by fmartinez on 2008-09-21
I don't know if this the correct way but take a look the file in /etc/apach2/apasites-enabled/000-default
this has the default configuration in it. All if did was add both virtual hosts in that file and restarted apache and both sites came up for me.

---

### Post by mbeach on 2008-09-21
take the servername out of httpd.conf and put it in the virtual host file default.

httpd.conf should really be empty.

after making changes don't forget to 
sudo /etc/init.d/apache2 reload

to reload the configurations.

---

