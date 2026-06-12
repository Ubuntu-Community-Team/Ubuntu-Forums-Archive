---
title: "Apache broken after upgrade to 8.04"
date: 2008-05-14
forum: Server Platforms
---

### Post by Jahoobie on 2008-05-14
I just finished my upgrade from 6.06 to 8.04, and the apache service keeps failing whenever I try to do a /etc/init.d/apache2 restart.

Error is:

Syntax error on line 6 of /etc/apache2/sites-enabled/ssl:
SSLOptions: Illegal option 'CompatEnvVars'         [fail]

The file follows:

NameVirtualHost *:443
<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
        SSLCertificateFile /etc/ssl/certs/www_mywebsite_org.crt
        SSLCertificateKeyFile /etc/ssl/private/sslkey.key
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>




The site associated with this has an SSL on it, and it is setup so that if someone goes to http:// it will auto redirect them to https://

Any idea what I would need to do to the ssl file to fix this?

---

### Post by freebeer on 2008-05-14
I quick google indicated that the term CompatEnvVars should be removed.  Maybe give that a try?

---

### Post by cdenley on 2008-05-14
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/179959](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/179959)

Apparently the option "CompatEnvVars" is no longer available in mod_ssl. Did you try removing it?

```

NameVirtualHost *:443
<VirtualHost *:443>
ServerAdmin webmaster@localhost
DocumentRoot /var/www
SSLEngine on
**SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire**
SSLCertificateFile /etc/ssl/certs/www_mywebsite_org.crt
SSLCertificateKeyFile /etc/ssl/private/sslkey.key
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
#RedirectMatch ^/$ /apache2-default/
</Directory>

```

---

### Post by Jahoobie on 2008-05-14
I removed the CompatEnvVars, and apache now starts, but it isn't directing to the correct site, nor is it redirecting from port 80 to 443.

I am brand spaking new to apache, and Ubuntu, so I am not sure where to go from here.  I think the httpd.conf file?

The default website should be pointing to /etc/var/www...

---

### Post by freebeer on 2008-05-14
> **Jahoobie said:**
> 
The default website should be pointing to /etc/var/www...

Do you mean /var/www (no /etc)?  Your DocumentRoot and Directory directives say /var/www.

---

### Post by Jahoobie on 2008-05-14
As I said.  Complete newbie.  Yes, I meant /var/www, not /etc/var/www.

I looked at the httpd.conf file, and apparently that is no longer used?

---

### Post by freebeer on 2008-05-14
That's ok... I was just trying to confirm that you weren't pointing to a wrong folder.  So yeah, /var/www/ is the normal folder for apache2 on Ubuntu.

And yes, httpd.conf isn't (to my knowledge) normally used on ubuntu installs (might be used on other distros).  The config file I have is /etc/apache2/apache2.conf.

---

### Post by cdtech on 2008-05-15
Bug #179959 posted  [[COLOR="DarkRed"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/179959").

I think there was a patch, not really sure (didn't read it all).

Hope this helps.

---

### Post by Jahoobie on 2008-05-15
Ok, the patch listed in that thread shows:

=== modified file 'generic/server/C/web-servers.xml'
--- generic/server/C/web-servers.xml	2007-09-12 14:52:32 +0000
+++ generic/server/C/web-servers.xml	2008-01-03 15:11:45 +0000
@@ -666,7 +666,7 @@
 <programlisting>
 SSLEngine on
 
-SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
+SSLOptions +StrictRequire
 
 SSLCertificateFile /etc/ssl/certs/server.crt
 SSLCertificateKeyFile /etc/ssl/private/server.key


Maybe I am just not looking at it correctly, but this is what my file looked like with the exception of the cert file names?

---

