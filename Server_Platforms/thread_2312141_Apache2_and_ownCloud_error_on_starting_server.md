---
title: "Apache2 and ownCloud error on starting server"
date: 2016-02-02
forum: Server Platforms
---

### Post by felipe27 on 2016-02-02
Hi everyone,

I've recently tried to install owncloud on my server and everything went fine... but then when I tried to update the installation, it stopped working. I then tried to uninstall and reinstall all the packages, but now I'm getting the following error message: 

Internal Server Error

The server encountered an internal error and was unable to complete your request.
Please contact the server administrator if this error reappears multiple times, please include the technical details below in your report.
More details can be found in the server log.

The error log for the Apache2
> [Tue Feb 02 08:44:59.158764 2016] [mpm_prefork:notice] [pid 53248] AH00171: Graceful restart requested, doing restart
[Tue Feb 02 08:44:59.208014 2016] [ssl:warn] [pid 53248] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Feb 02 08:44:59.208230 2016] [mpm_prefork:notice] [pid 53248] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.14 OpenSSL/1.0.1f configured -- re$
[Tue Feb 02 08:44:59.208239 2016] [core:notice] [pid 53248] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 02 08:45:04.465789 2016] [mpm_prefork:notice] [pid 53248] AH00169: caught SIGTERM, shutting down
[Tue Feb 02 08:45:05.533822 2016] [ssl:warn] [pid 56766] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Feb 02 08:45:05.571828 2016] [ssl:warn] [pid 56767] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Feb 02 08:45:05.574934 2016] [mpm_prefork:notice] [pid 56767] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.14 OpenSSL/1.0.1f configured -- re$
[Tue Feb 02 08:45:05.574956 2016] [core:notice] [pid 56767] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 02 08:45:11.774212 2016] [mpm_prefork:notice] [pid 56767] AH00171: Graceful restart requested, doing restart
[Tue Feb 02 08:45:11.821754 2016] [ssl:warn] [pid 56767] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Feb 02 08:45:11.821964 2016] [mpm_prefork:notice] [pid 56767] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.14 OpenSSL/1.0.1f configured -- re$
[Tue Feb 02 08:45:11.821974 2016] [core:notice] [pid 56767] AH00094: Command line: '/usr/sbin/apache2'

The owncloud.conf and owncloud-ssl.conf files are the following:
> 
<VirtualHost *:80>
     ServerAdmin webmaster@localhost
     ServerName cloud.broadsword.cbmeg.unicamp.br
       # I add permanent redirect in the next line - choice is up to you #
     Redirect permanent / [https://cloud.broadsword.unicamp.br/](https://cloud.broadsword.unicamp.br/)
     DocumentRoot /var/www/owncloud

     <Directory />
                Options FollowSymLinks
                AllowOverride All
    </Directory>


     ErrorLog ${APACHE_LOG_DIR}/owncloud-HTTP-error.log
     CustomLog ${APACHE_LOG_DIR}/owncloud-HTTP-access.log combined
</VirtualHost>



> <IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin webmaster@localgost
                ServerName cloud.broadsword.cbmeg.unicamp.br
                # I add Header info base on doc.owncloud.org v8.1 admin guide #
                Header always add Strict-Transport-Security "max-age=15768000; preload"
                DocumentRoot /var/www/owncloud
                <Directory />
                        Options FollowSymLinks
                        AllowOverride All
                </Directory>

                <Directory /var/www/owncloud>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                </Directory>

                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

                SSLEngine on
                SSLCertificateFile /etc/apache2/ssl/owncloud/server.crt
                SSLCertificateKeyFile /etc/apache2/ssl/owncloud/server.key

                #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt
                #SSLCACertificatePath /etc/ssl/certs/
                #SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt
                #SSLCARevocationPath /etc/apache2/ssl.crl/
                #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl
                #SSLVerifyClient require
                #SSLVerifyDepth  10

                #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>

                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                # MSIE 7 and newer should be able to use keepalive
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

        </VirtualHost>
</IfModule>

I've already tried to reinstall my Apache2 instalation, purge, update and etc... but nothing seems to work. I'm new to this type of server setup, so I'm kind of lost. How can I fix this error?

Thanks for the help!

---

### Post by felipe27 on 2016-02-02
Solved it... It was a matter of erasing the files in /etc/apache2 and /etc/php5 folders created by the previous installations. I'll leave this topic here in case someone has the same error.

---

### Post by ajgreeny on 2016-02-02
Well done!
Please mark the thread as SOLVED from the Thread Tools menu at the top.

---

