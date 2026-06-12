---
title: "problem with site permissions"
date: 2015-10-16
forum: Server Platforms
---

### Post by Rui_Pimenta on 2015-10-16
Hi! I'am having a problem with one site. when i tried do fill a form and do something next gives me the error in browser: 
[h=1]Internal Server Error[/h] The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator at   webmaster@localhost to inform them of the time this error occurred,  and the actions you performed just before this error.
 More information about this error may be available in the server error log.
 [HR][/HR] Apache/2.4.10 (Ubuntu) Server at localhost Port 80

In the apache log says:

[Fri Oct 16 11:36:48.721673 2015] [core:notice] [pid 9221] AH00094: Command line: '/usr/sbin/apache2'
[Fri Oct 16 11:36:55.722297 2015] [cgi:error] [pid 9225] [client 127.0.0.1:55768] AH01215: (13)Permission denied: exec of '/var/www/cdesp/cgi-bin/registo_mailing_list.cgi' failed, referer: [http://localhost/cdesp/registo.shtml](http://localhost/cdesp/registo.shtml)
[Fri Oct 16 11:36:55.723689 2015] [cgi:error] [pid 9225] [client 127.0.0.1:55768] End of script output before headers: registo_mailing_list.cgi, referer: [http://localhost/cdesp/registo.shtml](http://localhost/cdesp/registo.shtml)

check permissions and everything seems ok.on /var/www/cdesp

-rwxr-xr-x  1 www-data www-data 22192 Ago 10 09:55 registo_mailing_list.cgi
-rwxr-xr-x  1 www-data www-data  7958 Ago 12 19:19 registo.shtml

on /var/www/cdesp/cgi-bin

-rwxr-xr-x  1 www-data www-data 22191 Out 15 17:54 registo_mailing_list.cgi

my file on /etc/apache2/sites-available

<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName [www.example.com](www.example.com)

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www

    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    <Directory /var/www/cdesp/cgi-bin>
        Options Indexes FollowSymLinks MultiViews Includes ExecCGI
        AllowOverride None
        Order allow,deny
        Allow from all
        AddType text/html .html
        AddOutputFilter INCLUDES .html
    </Directory>
    

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
    Include conf-available/serve-cgi-bin.conf


</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

I also verify selinux:

SELinux is disabled

I don't know what i can do more. If anyone have any idea i will appreciate.
Thanks in advance.

---

### Post by volkswagner on 2015-10-19
I have never used cgi, so I can't comment from experience. I do recall seeing cgi specifics listed in old default configs though.

I believe you need specific directives set for your cgi directories, plus you may need to enable Apache2 "mod-cgi".

These two links may help.
[http://ubuntuforums.org/showthread.php?t=1789980](http://ubuntuforums.org/showthread.php?t=1789980)
[http://askubuntu.com/questions/403067/cgi-bin-not-working](http://askubuntu.com/questions/403067/cgi-bin-not-working)

---

