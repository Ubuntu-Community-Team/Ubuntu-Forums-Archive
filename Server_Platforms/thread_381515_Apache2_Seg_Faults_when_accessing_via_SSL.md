---
title: "Apache2 Seg Faults when accessing via SSL"
date: 2007-03-11
forum: Server Platforms
---

### Post by bremedios on 2007-03-11
I'm hoping that someone out there has had the same problem before.

My exact problem, is that when someone tries to access a web page over SSL, the apache process will seg fault.  Accessing the content without going through SSL still works.

My log shows the following:

[Sat Mar 10 21:28:12 2007] [notice] child pid 27923 exit signal Segmentation fault (11)

I have created my own SSL Certificates with the command apache2-ssl-certificate -days 365, and have enable ssl via a2enmod ssl.

I also copied my default config as ssl and added 3 lines before the </VirtualHost>

        SSLEngine               on
        SSLCertificateFile      /etc/apache2/ssl/apache.pem
        SSLProtocol             all
        SSLCipherSuite          HIGH:MEDIUM

And added :443 onto the end of the * after NameVirtualHost and <VirtualHost *:443>

Does anyone know what else can be done, or what else I can look for?  I'd rather keep with the standard packages to make upgrading easier rather than compiling and installing it from source.

Thanks

---

### Post by arvindkst on 2007-03-14
try recreating the certificate

# openssl genrsa -des3 -out ca.key 2048
# openssl req -new -x509 -days 3650 -key ca.key -out ca.crt

Looks like you are missing something in you ssl conf

can you attach you apache conf and ssl conf here

---

### Post by bremedios on 2007-03-14
Here is my conf file, the virtual hosting does work too.  I'll recreate the ssl certs manually instead of using the tool that comes with Ubuntu and see if that helps.

One thing that I don't want, is I don't want to have to enter a passphrase on the startup of apache.

Thanks for your help.

NameVirtualHost *:443
<VirtualHost *:433>
        ServerAdmin [email]webmaster@domain.ca[/email]
        ServerName ssl-site.domain.ca

        DocumentRoot /var/www/ssl-site
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/ssl-site>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
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

        SSLEngine               on
        SSLCertificateFile      /etc/apache2/ssl/apache.pem
        SSLProtocol             all
        SSLCipherSuite          HIGH:MEDIUM
</VirtualHost>

---

### Post by bremedios on 2007-03-14
I ran the commands that you listed above and changed the bottom of the file to be the following:

        SSLEngine               on
        SSLCertificateFile      /etc/apache2/ssl/ca.crt
        SSLCertificateKeyFile   /etc/apache2/ssl/ca.key
        SSLProtocol             all
        SSLCipherSuite          HIGH:MEDIUM

All that has changed is that loading apache now causes it to ask me for my passphrase.

---

### Post by MJN on 2007-03-15
You can strip the passphrase (i.e. remove the triple DES encryption) with [B]openssl rsa -in ca.key -out ca-new.key

[/B]Remember to make sure it's not readable by anyone other than root!

As for the segmentation faults I really don't know - I've been searching high and low to see if I can find anything but no joy... So don't take the lack of responses as lack of interest - there're probably many of us scratching our heads but with nothing beneficial to add!

Mathew

---

### Post by rachel.greenham on 2007-11-26
You can get past this by including the directive

SSLVerifyClient none

in your /etc/apache2/mods-enabled/ssl.conf

Although should you need client cert verification you might be stuck. It appears to be related to this bug:

[http://issues.apache.org/bugzilla/show_bug.cgi?id=34846]("http://issues.apache.org/bugzilla/show_bug.cgi?id=34846")

There the final outcome appears to be to lay blame upon a "bad patch" in that SuSE distribution. Looks like mayby Ubuntu's been doing the same thing.

---

### Post by MJN on 2007-11-26
Unfortunately that won't have any effect in this case - SSLVerifyClient is 'none' by default so as the OP has not changed this setting there is no need to explicitly set it.
 
Mathew

---

