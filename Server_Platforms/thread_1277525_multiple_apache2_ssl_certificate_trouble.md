---
title: "multiple apache2 ssl certificate trouble"
date: 2009-09-28
forum: Server Platforms
---

### Post by artheus on 2009-09-28
Hi there!

I've got a server, and I've gotten two valid signed certificates now. And want to install them both for different sub-domains on my server.

- 1 -
mail.mydomain.com
- 2 -
[www.mydomain.com](www.mydomain.com)
mydomain.com

is supposed to get two different ssl certificates.

So I copy these certificates to the correct folders, and add settings in a new sites-available conf file. And I get "- 1 -" to work, the one for mail.mydomain.com. But when I then try to add one more site which is the [www.mydomain.com](www.mydomain.com) and mydomain.com the browser still gets the mail.mydomain.com certificate.
So my question is, Is it possible to use multiple certificate files for my apache server?

my /etc/apache2/sites-available/ssl file :

```

NameVirtualHost *:443
<virtualhost *:443>
        ServerName mail.mydomain.com
        ServerAlias mail.mydomain.com
        ServerAdmin webmaster@localhost

       SSLEngine On
        SSLProtocol all -SSLv2
        SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM

       SSLCertificateFile    /etc/apache2/ssl/ssl.crt
       SSLCertificateKeyFile /etc/apache2/ssl/ssl.key

        SSLCertificateChainFile /etc/apache2/conf/sub.class1.server.ca.pem
        SSLCACertificateFile /etc/apache2/conf/ca.pem
        SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
        CustomLog /var/log/apache2/ssl_request_log \
        "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"

       DocumentRoot /mnt/sdb1/roundcubemail
       <directory />
               Options FollowSymLinks
               AllowOverride None
       </directory>

       <directory /mnt/sdb1/roundcubemail>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               allow from all
               # This directive allows us to have apache2's default start page
               # in /apache2-default/, but still have / go to the right place
               # Commented out for Ubuntu
               #RedirectMatch ^/$ /apache2-default/
       </directory>

       ErrorLog /var/log/apache2/error.log

       # Possible values include: debug, info, notice, warn, error, crit,
       # alert, emerg.
       LogLevel warn
</virtualhost>

<virtualhost *:443>
        ServerName mydomain.com
        ServerAlias mydomain.com www.mydomain.com
        ServerAdmin webmaster@localhost

       SSLEngine On
        SSLProtocol all -SSLv2
        SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM

       SSLCertificateFile    /etc/apache2/ssl/mydomain.com/ssl.crt
       SSLCertificateKeyFile /etc/apache2/ssl/mydomain.com/ssl.key

        SSLCertificateChainFile /etc/apache2/conf/sub.class1.server.ca.pem
        SSLCACertificateFile /etc/apache2/conf/ca.pem
        SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
        CustomLog /var/log/apache2/ssl_request_log \
        "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"

       DocumentRoot /mnt/sdb1/www/mydomain
       <directory />
               Options FollowSymLinks
               AllowOverride None
       </directory>

       <directory /mnt/sdb1/www/mydomain>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               allow from all
               # This directive allows us to have apache2's default start page
               # in /apache2-default/, but still have / go to the right place
               # Commented out for Ubuntu
               #RedirectMatch ^/$ /apache2-default/
       </directory>

       ErrorLog /var/log/apache2/error.log

       # Possible values include: debug, info, notice, warn, error, crit,
       # alert, emerg.
       LogLevel warn
</virtualhost>

```

What am I doing wrong?

Cheers,
Artheus

---

### Post by gali98 on 2009-09-28
You can only have one ssl virtual host per port.
This is by design and there isn't really anyway to get it to work.
The easiest way to fix this is to run the second virtualhost on another port, or to get another static IP.
Kory

---

### Post by artheus on 2009-09-28
I've tried now to put it on other ports.. but it still gives me errors..

```

NameVirtualHost 192.168.1.64:8008
<virtualhost 192.168.1.64:8008>
        ServerName mail.mydomain.com
        ServerAlias mail.mydomain.com
        ServerAdmin webmaster@localhost

       SSLEngine On
        SSLProtocol all -SSLv2
        SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM

       SSLCertificateFile    /etc/apache2/ssl/ssl.crt
       SSLCertificateKeyFile /etc/apache2/ssl/ssl.key

        SSLCertificateChainFile /etc/apache2/conf/sub.class1.server.ca.pem
        SSLCACertificateFile /etc/apache2/conf/ca.pem
        SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
        CustomLog /var/log/apache2/ssl_request_log \
        "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"

       DocumentRoot /mnt/sdb1/roundcubemail
       <directory />
               Options FollowSymLinks
               AllowOverride None
       </directory>

       <directory /mnt/sdb1/roundcubemail>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               allow from all
               # This directive allows us to have apache2's default start page
               # in /apache2-default/, but still have / go to the right place
               # Commented out for Ubuntu
               #RedirectMatch ^/$ /apache2-default/
       </directory>

       ErrorLog /var/log/apache2/error.log

       # Possible values include: debug, info, notice, warn, error, crit,
       # alert, emerg.
       LogLevel warn
</virtualhost>
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName mail.mydomain.com
        ServerAlias mail.mydomain.com webmail.mydomain.com
        Redirect / https://mail.mydomain.com:8008
</VirtualHost>

```

That's the way it looks now.. And there are two of these files.. But it can still only take one of the certificates..
Help?

---

### Post by artheus on 2009-09-28
Oh.. Sorry about that... Just a fail by me there.. I hadn't forwarded the port 8008 properly.. So it works fine now!
Thanks alot! :)

Cheers,
Artheus

---

### Post by i.r.id10t on 2009-09-28
A second IP to bind to would also work, or you could play wtih using SNI - [http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI](http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI)

---

### Post by artheus on 2009-09-29
I've been searching about SNI, and mod_ssl. And I haven't gotten that to work.. From what I can read, SNI should make it possible for me to have different certificates on the same port, but chosen by the NameVirtualServer?
I can't find a proper guide on how to do this anywhere. And the one you sent
[http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI](http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI)
I don't get..

Hope for some help!

Cheers

---

### Post by gali98 on 2009-09-29
Oh wow... After so much research I never found that. :(
I think a problem you're going to run into is I don't think that apache on ubuntu is compiled with SNI...
I'm going to test it now and report back with what I find...
Kory

---

### Post by gali98 on 2009-09-29
Sigh... It's not... So I'm going to see how much trouble it is to compile it with SNI... 
I'll report back.. But don't expect anything great...
Kory

---

### Post by gali98 on 2009-09-29
Well so far I haven't gotten it to work.
But there is good news! Karmic will come with SNI precompiled into apache.
If you want to cut your teeth, you can try following this post:
[http://ubuntuforums.org/showpost.php?p=7790181&postcount=3](http://ubuntuforums.org/showpost.php?p=7790181&postcount=3)
You can skip the part about openssl, and skip down to the apache part. (tls is in since Intrepid.)
I tried it, but it seems it is not working.
I'll tinker a bit more, but I'll probably just wait for Karmic.
Cheers,
Kory

---

### Post by artheus on 2009-10-02
Hmm ok... Thanks... But when Karmic comes.. Should it work just upgrading to karmic via aptitude?

Cheers,
artheus

---

### Post by gali98 on 2009-10-02
I would guess so... Upgrading to Karmic should also upgrade apache to the Karmic version.
I actually downloaded karmic beta yesterday and plan to install it over the weekend. I'll test SNI then..
Kory

---

### Post by gali98 on 2009-10-04
I am writing from ubuntu karmic beta. I just confirmed that SNI is indeed working.
:)
Kory

---

### Post by artheus on 2009-10-07
Fantastic! :D

I'm really looking forward to upgrading to the final stable release of Karmic Koala at 29th of October! :D

Cheers, and Thanks again!
Artheus

---

### Post by gali98 on 2009-10-07
Roger that! If you have any trouble getting SNI set up, shoot me a pm and I'll see what I can do to help :) Peace.
Kory

---

