---
title: "Apache2 accepting both HTTP and HTTPS"
date: 2011-07-06
forum: Server Platforms
---

### Post by Cyked on 2011-07-06
Anyone successfully set this up with Ubuntu?  I've gotten both to work individually with no issues, but not at the same time.

depending on how I configure my sites-available/default file I either get an error restarting apache that says there is an error in apache2.conf file on the line for I*nclude /etc/apache2/sites-enabled* and in the apache logs this error would show up: *[warn] Init: (localhost:443) You configured HTTP(80) on the standard HTTPS(443) port!*

Or in the error logs for apache I get *Invalid method in request \x16\x03\x01.*  In FF I get *Error code: ssl_error_rx_record_too_long*

I'm not sure what should be put where between the default file and default-ssl file in sites-available, and what should be in either the apache2.conf and httpd.conf files in /etc/apache2

---

### Post by ruffEdgz on 2011-07-06
Can you post your site config or the file you edited/changed on your apache server please? 

Its hard to say why its doing it but I have been able to make both an http and https site (but most of the time, I have my port 80 traffic redirect to port 443).

Cheers!

---

### Post by Cyked on 2011-07-07
here are some of the pertinent lines from apache2.conf
```

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf


# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerSignature Off
ServerTokens Prod

```

httpd.conf (mostly... everything else in the file are all directory directives)
```
ServerName localhost
SSLProtocol all
SSLCipherSuite HIGH:MEDIUM

#LoadModule h264_streaming_module
#/usr/lib/apache2/modules/mod_h264_streaming.so

#module stuff for streaming h264
LoadModule h264_streaming_module /usr/lib/apache2/modules/mod_h264_streaming.so

#module for music streaming
LoadModule musicindex_module /usr/lib/apache2/modules/mod_musicindex.so

AddHandler h264-streaming.extensions .mp4

```


default file in sites-available
```
<VirtualHost *:80>
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks Indexes
                AllowOverride All
        </Directory>


```

default-ssl
```
<IfModule mod_gnutls.c>
<VirtualHost _default_:443>
#<VirtualHost *:443>

        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/https
        <Directory />
                Options FollowSymLinks
                AllowOverride None
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

        CustomLog /var/log/apache2/ssl_access.log combined

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
        SSLCertificateFile /etc/apache2/ssl/apache.pem
        #SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

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


I thought I just needed to add in the default file a new VirtualHost for SSl and give it a new name (instead of *:80 and documentroot of /var/www/http use the _default_:443 and documentroot of /var/www/https for example).

Apparently it is not that simple, or I am do something wrong.

---

### Post by kgatan on 2011-07-07
It should be no problem. I set up a new installation yesterday and it worked right away with default sites.
 
Maybe a stupid question,
Do you have </VirtualHost> in you site file? Guess you didnt post all of the content but might be worth mentioning :)

---

### Post by Cyked on 2011-07-07
Are you talking about the default file?  Yes, at the end of that file there is a </VirtualHost> to close it.

---

### Post by kgatan on 2011-07-07
Have you done any changes to ports.conf?

---

### Post by Cyked on 2011-07-08
I have it working now.

I think initially the issue was I didn't enable the additional site (a2ensite), along with I honestly wasn't sure what I was doing with the config file.  Since I was only EITHER running HTTP or HTTPS prior to all of this, and I had edited the default file to be the file for apache to use I didn't have to enable any additional sites.  Now that the default file is used for HTTP (controls /var/www/http) and the default-ssl file is used for HTTPS (controls /var/www/https).  

I enabled the path needed for the HTTPS side of my apache server, and its working (after figuring out how to properly config default and default-ssl files).

---

