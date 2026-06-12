---
title: "Apache2 SSL Issue"
date: 2007-02-10
forum: Server Platforms
---

### Post by cltrenholm on 2007-02-10
Hello,

I find myself in a unique situation where a developer has built an application for us and part of this process was that they would build and configure the server. The following is what was installed on the system.

Apache/2.0.54 (Ubuntu) PHP/4.4.0-3 mod_ssl/2.0.54 OpenSSL/0.9.7g mod_perl/2.0.1 Perl/v5.8.7

As part of the build out they setup and installed a dummy SSL certificate, which works but of course throws errors. However I have purchased a valid cert and now want to install it. I realize that I haven't provided alot of imformation but am willing to provide whatever is necessary if I know what is required.

I am relatively new to Linux and Apache and don't know where to start. Is it a matter of copying and pasting the contents of my certificate file into another file? Any help that you can provide would be greatly appreciated.

---

### Post by jtc on 2007-02-11
Is it a possibility to have the original developer install the real certificate?

(After all, he can have setup your webbserver in quite a few different ways.)

---

### Post by MJN on 2007-02-11
Alternatively, your current Apache config (SSL portions) would be useful then we can see how it is currently configured (the SSLCertificate* directives will say where the certs are stored, however there will be other important ones too such as intermediate CAs etc so list them all).

Mathew

---

### Post by cltrenholm on 2007-02-12
> **jtc said:**
> Is it a possibility to have the original developer install the real certificate?

(After all, he can have setup your webbserver in quite a few different ways.)

Unfortunately the developer handed off the config portion to another person to whom they no longer have contact with.

---

### Post by cltrenholm on 2007-02-12
> **MJN said:**
> Alternatively, your current Apache config (SSL portions) would be useful then we can see how it is currently configured (the SSLCertificate* directives will say where the certs are stored, however there will be other important ones too such as intermediate CAs etc so list them all).

Mathew

Thanks Matthew. Again I am new to Linux/Apache so if you can guide me to the file/info that  you are reffering to I can certainly provide the info.

---

### Post by MJN on 2007-02-12
Sure - it'll likely be the config in /etc/apache2/sites-available/default. There could well be other files in sites-available - let us know if there are. Alternatively, the config could be in /etc/apache2/apache2.conf. The bits you're after are any directives starting with SSL...
 
Mathew

---

### Post by cltrenholm on 2007-02-12
> **MJN said:**
> Sure - it'll likely be the config in /etc/apache2/sites-available/default. There could well be other files in sites-available - let us know if there are. Alternatively, the config could be in /etc/apache2/apache2.conf. The bits you're after are any directives starting with SSL...
 
Mathew

Thanks Mathew.

The two files that you mentioned didn't seem to contain anything substantial in regards to what you were saying however the following file contain the following entries.

/etc/apache2/sites-enabled/ssl

NameVirtualHost *:443
<virtualhost *:443>
        ServerAdmin webmaster@localhost

        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        DocumentRoot /var/www/
        <directory />
                Options FollowSymLinks
                AllowOverride None
        </directory>

        <directory /var/www/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </directory>

        <Directory /var/www/ADMIN/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </directory>

</virtualhost>

---

### Post by MJN on 2007-02-12
Okay, that's fine - it's rather scant on the config front but there's enough!
 
The important line is **SSLCertificateFile /etc/apache2/ssl/apache.pem -** this is the path to your current (self-signed) certificate in PEM format.
 
To use your commercially-signed certificate, copy it into /etc/apache2/ssl/ and changed the config to point at it. Alternatively, backup your current apache.pem certificate and move/rename your new certificate as apache.pem then you can leave your config alone. Either way restart Apache with **sudo /etc/init.d/apache2 restart**.
 
Finger's crossed your new certifcate should be delivered to clients and they'll trust it as per the signature path.
 
However, your new certificate *might* be in DER format and hence will require converting into PEM with **openssl x509 -inform der -in originalcert.crt -out newcert.pem**
 
Make backups along the way as it sounds like this is a production server hence the ability to wind things back should they not work out could be important!
 
Mathew

---

### Post by cltrenholm on 2007-02-12
Still no luck. I made the config change and restarted the daemon but it won't come back up.

I thought that I may have to run the DER conversion so I did and it threw these errors.

unable to load certificate
27442:error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag:tasn_dec.c:946:
27442:error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error:tasn_dec.c:304:Type=X509

Am I missing something?

---

### Post by MJN on 2007-02-12
What's the file extension of the new certificate? It sounds like it's already in PEM format (open it with a text editor and see if it starts/ends with ----BEGIN X509 CETIFICATE---- and ----END X509 CERTIFICATE----)
 
You say you tried it 'as is' - if Apache didn't start what errors did it give? (the error logs are likely in /var/log/apache2/)
 
Mathew

---

### Post by cltrenholm on 2007-02-12
It starts with.

-----BEGIN CERTIFICATE-----

And ends with

-----END CERTIFICATE-----

Part of the error.log reads

[Mon Feb 12 11:51:03 2007] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Mon Feb 12 11:51:03 2007] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Mon Feb 12 11:51:03 2007] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Mon Feb 12 11:51:03 2007] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
[Mon Feb 12 11:57:20 2007] [warn] RSA server certificate CommonName (CN) `pulse.mapletradefinance.ca' does NOT match server name!?
[Mon Feb 12 11:57:20 2007] [warn] RSA server certificate CommonName (CN) `pulse.mapletradefinance.ca' does NOT match server name!?
[Mon Feb 12 11:57:20 2007] [notice] Apache/2.0.54 (Ubuntu) PHP/4.4.0-3 mod_ssl/2.0.54 OpenSSL/0.9.7g mod_perl/2.0.1 Perl/v5.8.7 configured -- resuming normal operations
[Mon Feb 12 11:58:45 2007] [notice] caught SIGTERM, shutting down
[Mon Feb 12 12:00:52 2007] [warn] RSA server certificate CommonName (CN) `pulse.mapletradefinance.ca' does NOT match server name!?
[Mon Feb 12 12:00:52 2007] [error] Unable to configure RSA server private key
[Mon Feb 12 12:00:52 2007] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
[Mon Feb 12 12:02:15 2007] [warn] RSA server certificate CommonName (CN) `pulse.mapletradefinance.ca' does NOT match server name!?
[Mon Feb 12 12:02:15 2007] [warn] RSA server certificate CommonName (CN) `pulse.mapletradefinance.ca' does NOT match server name!?
[Mon Feb 12 12:02:15 2007] [notice] Apache/2.0.54 (Ubuntu) PHP/4.4.0-3 mod_ssl/2.0.54 OpenSSL/0.9.7g mod_perl/2.0.1 Perl/v5.8.7 configured -- resuming normal operations

---

### Post by MJN on 2007-02-12
Okay, so the certificate is already in PEM format hence can be left as-is.

Do you have a copy of your server's private key? You likely used this to sign the request that you sent to your certificate provider. This should be referenced in the Apache config file with **SSLCertificateKeyFile /path/to/serverprivatekey**

The warning about the certifcate CN field not matching the server name is important - this will always throw an alert to visiting clients. As it implies, your Apache server name should be the same as the cert CN however it looks like you don't actually have a server name specified so add a **Servername pulse.mapletradefinance.ca** to the config file above - presumably this is the name you intend to access the site with?

Mathew

---

### Post by cltrenholm on 2007-02-12
Mathew,

It's fixed. I put in the Servername directive and found the key to match the cert. I added the lines for those as well, restarted and it came online.

Thank you again for your help; greatly appreciated.

cT

---

### Post by MJN on 2007-02-12
Great! :guitar:

(not sure when that's meant to be used but I reckon this is as good a time as any!)

Mathew

---

### Post by cltrenholm on 2007-02-12
Very appropriate actually!!!

---

