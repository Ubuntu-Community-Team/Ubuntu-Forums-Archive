---
title: "Security when running Apache/Mysql/PhpMyadmin as a local service."
date: 2016-03-18
forum: Security
---

### Post by irvine_himself2 on 2016-03-18
[LEFT][COLOR=#000000]I have recently set up a MediaWiki on localhost and, (using [this guide]("https://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu"),) I installed Apache, Mysql and PhpMyAdmin from the repos. (Note, this was not a bundled package like Bitnami or LAMP, each unit was installed separately.) As a result, I am now checking up on the basic security of the installation.[/COLOR]
 [/LEFT]
    
[LIST]
[*=left][COLOR=#000000]My UFW settings are currently  deny all incoming and allow outgoing[/COLOR] 
[*=left][COLOR=#000000]The Mysql instalation was secured[/COLOR] 
[*=left][COLOR=#000000]The mysqld.cnf sets the **bind-address 127.0.0.1** flag[/COLOR] 
[*=left][COLOR=#000000]The MediaWiki was set to private.[/COLOR] 
[/LIST]
  [LEFT][COLOR=#000000]This [Blog-post ]("https://procurity.wordpress.com/2013/07/20/restrict-apache-acess-to-localhost-only/")suggests modifying **000-default.conf** file as follows:[/COLOR]
[/LEFT]
  > 1) Change **allow from all** to *allow from 127.0.0.1*
 [LEFT]2) Add this line: *deny all*[/LEFT]
 [LEFT]3) Change *Order allow,deny* to *Order deny, allow*[/LEFT]
  [LEFT][COLOR=#000000]Since my **000-default.conf**  doesn&#8217;t even have the lines that he suggests should be changed, I could do  with a bit of advice.
[/COLOR]
[/LEFT]
  [LEFT][COLOR=#000000]For your consideration, currently the aforementioned **000-default.conf** is as follows[/COLOR][/LEFT]
  ```

<VirtualHost *:80>
# The ServerName directive sets the request scheme, hostname and port that
# the server uses to identify itself. This is used when creating
# redirection URLs. In the context of virtual hosts, the ServerName
# specifies what hostname must appear in the request's Host: header to
# match this virtual host. For the default virtual host (this file) this
# value is not decisive as it is used as a last resort host regardless.
# However, you must set it for any further virtual host explicitl
#ServerName www.example.com

ServerAdmin webmaster@localhost
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

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

``` 

[LEFT][COLOR=#000000]Similarly, checking in **/etc/apache2/conf-enabled/****security.conf**  the, possibly(?), equivalent entry has been commented out, with a warning that changing these settings could break the configuration of some Debian Web applications :[/COLOR]
[/LEFT]
 ```

# Disable access to the entire file system except for the directories that
# are explicitly allowed later.
#
# This currently breaks the configurations that come with some web application
# Debian packages.
#
[B]#<Directory />
#   AllowOverride None
#   Order Deny,Allow
#   Deny from all
#</Directory>[/B]
# Changing the following options will not really affect the security of the
# server, but might make attacks slightly more difficult in some cases.
&#8230;..
&#8230;..

```  

[LEFT][COLOR=#000000]Finally, [ this post]("https://askubuntu.com/questions/492390/making-apache-secure-on-ubuntu-14-04") suggests not loading unnecessary modules by deleting the links in **/etc/apache2/mods-enabled**, but I have no idea which modules are necessary?

[/COLOR]
[/LEFT]
  [LEFT][COLOR=#000000]Any advice on the above or further tips on securing the installation is more than welcome. [/COLOR] 
[/LEFT]
  [LEFT][COLOR=#000000]Thanks in advance, Irvine[/COLOR]
[/LEFT]

---

