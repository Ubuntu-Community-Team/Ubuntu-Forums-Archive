---
title: "Recompiling Apache with mod_ssl"
date: 2013-04-15
forum: Server Platforms
---

### Post by eljaywasi on 2013-04-15
I've got an old machine running Ubuntu 12.04 32bit in my office to host our internal wiki and bugzilla sites. We're also testing our new php app with it and I'm trying to get SSL working with a self signed certificate on it so that we can test everything before we make it live on our production server (which is also running 12.04). 

I've followed these instructions:
[https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html](https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html)
[http://www.onlamp.com/2008/03/04/step-by-step-configuring-ssl-under-apache.html](http://www.onlamp.com/2008/03/04/step-by-step-configuring-ssl-under-apache.html) (old, I know) 

and enabled the ssl mod with *sudo a2enmod ssl *

My apache2.conf file includes the mods:
```

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

```


My ports.conf file reads:

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz


NameVirtualHost *:80
Listen 80


<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>


<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```



My *sites-available/* folder has two files: *default* and *default-ssl*

*default *reads:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost


        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>


        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


        ErrorLog ${APACHE_LOG_DIR}/error.log


        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn


        CustomLog ${APACHE_LOG_DIR}/access.log combined


    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


        Alias /bugzilla/ /var/www/bugzilla/
        <directory /var/www//bugzilla>
                AddHandler cgi-script .cgi .pl
                Options +Indexes +ExecCGI +FollowSymLinks
                DirectoryIndex index.cgi
                AllowOverride Limit
        </directory>


</VirtualHost>


```


and *default-ssl* reads:

```

<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin webmaster@localhost


        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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


        ErrorLog ${APACHE_LOG_DIR}/error.log


        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn


        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined


        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

#   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on


        #   A self-signed (snakeoil) certificate can be created by installing
        #   the ssl-cert package. See
        #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
        #   If both key and certificate are stored in the same file, only the
        #   SSLCertificateFile directive is needed.
#       SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
#       SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
        # Modified
        SSLCertificateFile    /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key




        #   Server Certificate Chain:
        #   Point SSLCertificateChainFile at a file containing the
        #   concatenation of PEM encoded CA certificates which form the
        #   certificate chain for the server certificate. Alternatively
        #   the referenced file can be the same as SSLCertificateFile
        #   when the CA certificates are directly appended to the server
        #   certificate for convinience.
        #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt


        #   Certificate Authority (CA):
        #   Set the CA certificate verification path where to find CA
        #   certificates for client authentication or alternatively one
        #   huge file containing all of them (file must be PEM encoded)
        #   Note: Inside SSLCACertificatePath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        #SSLCACertificatePath /etc/ssl/certs/
        #SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt

        #   Certificate Revocation Lists (CRL):
        #   Set the CA revocation path where to find CA CRLs for client
        #   authentication or alternatively one huge file containing all
        #   of them (file must be PEM encoded)
        #   Note: Inside SSLCARevocationPath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        #SSLCARevocationPath /etc/apache2/ssl.crl/
        #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl


        #   Client Authentication (Type):
        #   Client certificate verification type and depth.  Types are
        #   none, optional, require and optional_no_ca.  Depth is a
        #   number which specifies how deeply to verify the certificate
        #   issuer chain before deciding the certificate is not valid.
        #SSLVerifyClient require
        #SSLVerifyDepth  10


        #   Access Control:
        #   With SSLRequire you can do per-directory access control based
        #   on arbitrary complex boolean expressions containing server
        #   variable checks and other lookup directives.  The syntax is a
        #   mixture between C and Perl.  See the mod_ssl documentation
        #   for more details.
        #<Location />
        #SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
        #            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
        #            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
        #            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
        #            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
        #           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
        #</Location>


        #   SSL Engine Options:
        #   Set various options for the SSL engine.
        #   o FakeBasicAuth:
        #     Translate the client X.509 into a Basic Authorisation.  This means that
        #     the standard Auth/DBMAuth methods can be used for access control.  The
        #     user name is the `one line' version of the client's X.509 certificate.
        #     Note that no password is obtained from the user. Every entry in the user
        #     file needs this password: `xxj31ZMTZzkVA'.
        #   o ExportCertData:
        #     This exports two additional environment variables: SSL_CLIENT_CERT and
        #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
        #     server (always existing) and the client (only existing when client
        #     authentication is used). This can be used to import the certificates
        #     into CGI scripts.
        #   o StdEnvVars:
        #     This exports the standard SSL/TLS related `SSL_*' environment variables.
        #     Per default this exportation is switched off for performance reasons,
        #     because the extraction step is an expensive operation and is usually
        #     useless for serving static content. So one usually enables the
        #     exportation for CGI and SSI requests only.
        #   o StrictRequire:
        #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
        #     under a "Satisfy any" situation, i.e. when it applies access is denied
        #     and no other module can change it.
        #   o OptRenegotiate:
        #     This enables optimized SSL connection renegotiation handling when SSL
        #     directives are used in per-directory context.
        #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>


         #   o StdEnvVars:
        #     This exports the standard SSL/TLS related `SSL_*' environment variables.
        #     Per default this exportation is switched off for performance reasons,
        #     because the extraction step is an expensive operation and is usually
        #     useless for serving static content. So one usually enables the
        #     exportation for CGI and SSI requests only.
        #   o StrictRequire:
        #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
        #     under a "Satisfy any" situation, i.e. when it applies access is denied
        #     and no other module can change it.
        #   o OptRenegotiate:
        #     This enables optimized SSL connection renegotiation handling when SSL
        #     directives are used in per-directory context.
        #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>


       #   SSL Protocol Adjustments:
        #   The safe and default but still SSL/TLS standard compliant shutdown
        #   approach is that mod_ssl sends the close notify alert but doesn't wait for
        #   the close notify alert from client. When you need a different shutdown
        #   approach you can use one of the following variables:
        #   o ssl-unclean-shutdown:
        #     This forces an unclean shutdown when the connection is closed, i.e. no
        #     SSL close notify alert is send or allowed to received.  This violates
        #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
        #     this when you receive I/O errors because of the standard approach where
        #     mod_ssl sends the close notify alert.
        #   o ssl-accurate-shutdown:
        #     This forces an accurate shutdown when the connection is closed, i.e. a
        #     SSL close notify alert is send and mod_ssl waits for the close notify
        #     alert of the client. This is 100% SSL/TLS standard compliant, but in
        #     practice often causes hanging connections with brain-dead browsers. Use
        #     this only for browsers where you know that their SSL implementation
        #     works correctly.
        #   Notice: Most problems of broken clients are also related to the HTTP
        #   keep-alive facility, so you usually additionally want to disable
        #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
        #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
        #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
        #   "force-response-1.0" for this.
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown


</VirtualHost>
</IfModule>



```

After making all the changes I was sure to restart apache (using *service apache2 restart*, *apchectl -k restart*, *sudo /etc/init.d/apache2 restart* - I've used them all at some point, though I don't know if there is a difference).

After all this, HTTPS does not work: If I try to go to [https://fileserver](https://fileserver) with my browser (Chromium) I get an error:

```

**[SIZE=2][FONT=arial][B]SSL connection error**[/FONT][/SIZE][/B]

[COLOR=#000000][FONT=Helvetica]Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
[/FONT][/COLOR][COLOR=#777777][FONT=Helvetica]Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.[/FONT][/COLOR]

``` 

But if I try to go to my wiki, using for example [http://fileserver:443/wiki/Main_Page](http://fileserver:443/wiki/Main_Page), I do get to the main page, but it doesnt appear to be an ssl connection. If I try to access it via [https://fileserver/wiki/Main_Page]("http://fileserver:443/wiki/Main_Page") I get the same error as above. If I simply go to [http://fileserver:443](http://fileserver:443) I get a 404.

In any case, it's clear ssl is not working.

When I installed apache I used the apt-get so perhaps the problem is that the mod_ssl module was not compiled and installed? If that sounds like it may be the problem then my question is: How do I re-install or recompile apache with it? Will I have to redo all the config changes I've made?

---

### Post by eljaywasi on 2013-04-15
_**Diagnosis:**_


The result of running ```
sudo a2enmod ssl
``` is ```
Module ssl already enabled
```


```
sudo netstat -lnp | grep 443
``` gives


    ```
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1624/apache2
```



I had a look at the error.log, access.log and other_vhosts_access.log files under /var/log/apache2 but didn't see anything strange or interesting in any of those files. The only line I don't understand in the error.log is this one:


    ```
[Mon Apr 15 10:43:18 2013] [error] [client 192.168.1.128] Invalid method in request \x16\x03\x01
```


```
sudo a2ensite default-ssl
``` output:

```
Enabling site default-ssl.
To activate the new configuration, you need to run:
  service apache2 reload
```


Then I run ```
service apache2 reload
``` and get:


```
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
Syntax error on line 55 of /etc/apache2/sites-enabled/default-ssl:
SSLCertificateKeyFile: file '/etc/ssl/private/server.key' does not exist or is empty
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
```


Output of ```
ls /etc/apache2/sites-enabled
``` is ```
./  ../  000-default@  default-ssl@
```


[U][B][I]Conclusion
[/I][/B][/U]
SSL Virtual Host was not enabled, I enabled it when I entered ```
sudo a2ensite default-ssl
``` and then when I reloaded (or restarted) the service I had to have root privilege to read the server.key file stored in /etc/ssl/private, ie use ```
[COLOR=#444444][FONT=Consolas]sudo service apache2 reload[/FONT][/COLOR]
``` or ```
[COLOR=#000000][FONT=Consolas]sudo apache2ctl restart[/FONT][/COLOR]
```

---

