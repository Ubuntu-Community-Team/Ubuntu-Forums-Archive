---
title: "Apache2 SSL Issues"
date: 2015-11-03
forum: Server Platforms
---

### Post by win0922 on 2015-11-03
Hi, 

I recently bought an SSL certificate for server. In order to install it to my server I edited my 000-default.conf file to include the necessary certificate files. My .conf file reads: 

```

<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	ServerName localhost


	ServerAdmin #email
	DocumentRoot /var/www/html


	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn


	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined


	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
	
</VirtualHost>
<VirtualHost *:443>
	# The ServerName directive sets the request scheme, hostname and port t$
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName localhost


        ServerAdmin admin@crablab.co.uk
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn
	        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf


        
        SSLEngine on
        SSLCertificateFile crablab-co-uk.crt
        SSLCertificateKeyFile ../../../root/crablab.key
        #SSLCertificateChainFile /path/to/DigiCertCA.crt
</VirtualHost>
# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



```

At the moment, when I run Apache I get the error: 

> [Tue Nov 03 14:43:16.357074 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOCK_DIR} is not defined[Tue Nov 03 14:43:16.357280 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_PID_FILE} is not defined
[Tue Nov 03 14:43:16.357377 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_RUN_USER} is not defined
[Tue Nov 03 14:43:16.357463 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_RUN_GROUP} is not defined
[Tue Nov 03 14:43:16.357560 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
[Tue Nov 03 14:43:16.364461 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
[Tue Nov 03 14:43:16.364742 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
[Tue Nov 03 14:43:16.364791 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
[Tue Nov 03 14:43:16.364848 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
[Tue Nov 03 14:43:16.364887 2015] [core:warn] [pid 1516] AH00111: Config variable ${APACHE_LOG_DIR} is not defined
AH00526: Syntax error on line 74 of /etc/apache2/apache2.conf:
Invalid Mutex directory in argument file:${APACHE_LOCK_DIR}




Any help would be appreciated!

---

### Post by darkod on 2015-11-03
Were you editing apache2.conf in any way? Because it seems to complain on its content.

You were editing only conf files in sites-available right?

---

### Post by win0922 on 2015-11-03
No I wasn't. 
I managed to fill the issue by running this command: ```
sudo a2enmod ssl
``` so now Apache2 runs, but no HTTPS connection.

---

### Post by darkod on 2015-11-03
What do you mean no https connection? It doesn't open https at all or it shows certificate error?

If I remember correctly in the new apache there is the default http site, and there is separate default https site. So you don't put the SSL data in the same .conf file with the default http site.

You can also try doing it that way. And you will need to enable the default https site I think. Not sure if it's enabled by default.

---

### Post by win0922 on 2015-11-04
> **darkod said:**
> What do you mean no https connection? It doesn't open https at all or it shows certificate error?

If I remember correctly in the new apache there is the default http site, and there is separate default https site. So you don't put the SSL data in the same .conf file with the default http site.

You can also try doing it that way. And you will need to enable the default https site I think. Not sure if it's enabled by default.

I can't open the connection, it redirects to http. 

I'll try redirecting the https connection to the http folder, thanks.

---

### Post by win0922 on 2015-11-04
I had a look at my config file and the document root for 80 and 443 is the same. 

How would I enable the https site?

---

### Post by darkod on 2015-11-04
First, in /etc/apache2/sites-available open the 000-default.conf and make sure there is no 443 virtual host defined in it. Only the standard 80 host should be there.

Then open default-ssl.conf and modify it with the SSL certificate file and the key. Also the root certificate path if necessary.

After that is done enable the site with something like:
```
sudo a2ensite default-ssl
```

Restart apache. That should be it.

---

