---
title: "can't execute php files after changing LAMP DocumentRoot"
date: 2014-10-17
forum: Server Platforms
---

### Post by Linh_V_Nguyen on 2014-10-17
I'm new to LAMP and running into some troubles trying to install it on Ubuntu 14.04. I changed the DocumentRoot in 000-default.conf to a new folder instead of var/wwwand now it can't execute .php files. I'd appreciate your help.

Below is my /etc/apache2/sites-enabled/000-default.conf file:

[COLOR=#800000]<VirtualHost[/COLOR] *:80[COLOR=#800000]>[/COLOR]
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName [www.example.com]("http://www.example.com")

    ServerAdmin webmaster@localhost
    DocumentRoot "full path to folder"

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
[COLOR=#800000]</VirtualHost>[/COLOR]

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

---

