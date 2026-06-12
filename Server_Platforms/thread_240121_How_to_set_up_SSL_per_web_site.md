---
title: "How to set up SSL per web site"
date: 2006-08-20
forum: Server Platforms
---

### Post by acolic on 2006-08-20
Hi,

is there a config file somewhere for apache2 that says per web site to run via ssl or without.

I have a web site that I only want to accept connections via SSL and I can't seem to find the file that specifies this. I have set up openSSL and generated the approperiate configuration. I have also set up webmin and I see that it only allows connections via SSL. I just want to do the same for another site.

Thanks

Alex

---

### Post by Glut on 2006-08-20
In the sites config file (/etc/apache2/sites-available/whatever) At the top you should have a line such as:
```
NameVirtualHost www.example.com
<VirtualHost www.example.com>

``` Or it may have asterix in place of the host name, no matter.
You want to add a port specifier to this as so:
```

NameVirtualHost www.example.com:443
<VirtualHost www.example.com:443>

```
And bob's your uncle: you will only listen to https:// requests. Redirecting from http:// to https:// is more difficult.
In addition to the Virtual host listening on 443 above, you will need one listening on 80, with basically the same setup, but with mod_rewrite you can add the following to redirect requests to https://
```

<Directory />
[color=blue]Stuff here[/color]
RewriteEngine On
RewriteBase /
RewriteCond %{SERVER_PORT} !443$
RewriteRulte ^(.*) https://www.example.com/%1 [R=301.L]
</Directory>

```

---

### Post by acolic on 2006-08-21
Thanks,

perfect just what I needed.

Alex

---

### Post by LordHunter317 on 2006-08-21
Unfortunately, this guide is totally wrong.  For starters, you can't NameVirtualHost SSL sites unless you're using wildcard SSL certs.  People using wildcard SSL certs don't need help with Apache configuration. You missed several steps too, like actually enabling SSL and configuring what certs and keys to serve.

[list=1][*]Enable ssl support via:```
sudo a2enmod ssl
```[*]Create and generate the SSL certificate and private key.  How to do this is outside this set of instructions, since there are a bunch of ways[*]Copy the certificate and key to /etc/apache2/ssl.  I normally name them <site>.crt and <site>.key, and create a root-only subdirective private/ and place the private keys there.[*]Create a new file in /etc/apache2/sites-available named <site> (from above) for this new virtual host and define the VirtualHost entry:```
<VirtualHost ssl.example.com:443>
# These directives are mandatory, even for sites not using named-based virtual hosting.
ServerName ssl.example.com
ServerAdmin root@example.com

# Turn on SSL access
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/<site>.crt
SSLCertificateKeyFile /etc/apache2/ssl/private/<site>.key

# This particular directive ought to be the same for all sites,
# and could be stuffed somewhere global if desired.
SSLCACertificatePath /etc/ssl/certs

# Directory / is needed here to enforce SSL for the entire vhost,
# including global aliases.  This prevents accidental access to 
# global aliases without SSL.
<Directory />
    Options FollowSymLinks
    SSLRequireSSL On
</Directory> 

DocumentRoot /var/www/ssl.example.com
<Directory /var/www/ssl.example.com>
    Options Indexes FollowSymLinks
    AllowOverride none
    Order allow,deny
    Allow from all
</Directory>

# The ErrorLog directive is optional, but it's good practice 
# to log each vhost to it's own set of logs anyway.
ErrorLog /var/log/apache2/ssl.example.com.error.log
CustomLog /var/log/apache2/ssl.example.com.access.log combined
</VirtualHost>
```[*]Enable the site with:```
sudo a2ensite <site>
```[/list]

---

### Post by acolic on 2006-08-21
Thanks,

just a clarification. If I have don't have domain name right now but am using an IP address provided by my ISP, would I just add that in the directive?

To access my site right now the IP address is somthing like:

[http://50.150.40.40/mysite](http://50.150.40.40/mysite)

Would I change the Dirctive to something like:

<VirtualHost 50.150.40.40:443/mysite>

---

### Post by LordHunter317 on 2006-08-21
You would use the IP address and port instead, yes.

You can't secure "just a folder" to be SSL.  You have to host the entire website (i.e., everything at IP and port) as an SSL enabled site.

However, what you can do is define the VirtualHost for SSL to only serve that directory, and then use a Rewrite like above in the regular VirtualHost to force SSL access.

But VirtualHosts only apply to IPs/ports.

---

### Post by acolic on 2006-08-21
Hi,

one thing I don't understand. I have webmin installed and it only runs via HTTPS. I went through your steps above and went through all the files you mentioned and I don't see any reference to webadmin.

Do you know how that website is running if the there is no configuration to specify that that site is to run via HTTPS?

Am I missing a config file somewhere?

Thanks

Alex

---

### Post by Joespower on 2006-08-21
Its been some time since I've used Webmin, but I do recall reading that Webmin does not run on apache but on its own integrated webserver.  Check into your bootup services and see if you can find it...

---

### Post by kernelpanicked on 2006-08-21
You are correct, Webmin doesn't run on apache. It has it's own internal server. If you want to see the configuration for it, it should be /etc/webmin/miniserv.conf.

Note* may be a different location on Debian/Ubuntu boxes. I've never run it on these, but the config file would still be miniserv.conf.

---

### Post by ChrisDerson on 2006-08-31
I could be wrong, but I suspect that acolic may be talking about *courier-webadmin* - which requires SSL for non local access.  I'm toying with this right now, and I'll post an update if i can get this working.

---

