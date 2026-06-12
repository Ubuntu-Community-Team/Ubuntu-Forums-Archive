---
title: "Apache syntax error Include conf.d/"
date: 2014-01-15
forum: Server Platforms
---

### Post by josephrushdoony on 2014-01-15
I am getting the error "apache2: Syntax error on line 516 of /etc/apache2/apache2.conf:" line 516 of apache2.conf is Include conf.d/.


I am running ubuntu 12.04.3.

---

### Post by Iowan on 2014-01-15
Could you post (copy/paste ) 3-4 lines above and including line 516? Sometimes the problem is a line or two up.
(Maybe it's just me, but that seems like a huge .conf file...)

---

### Post by josephrushdoony on 2014-01-15
Here are th lines around it:

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
#Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/
# The location and format of the access logfile (Common Logfile Format).
# If you do not define any access logfiles within a <VirtualHost>
# container, they will be logged here.  Contrariwise, if you *do*
# define per-<VirtualHost> access logfiles, transactions will be
# logged therein and *not* in this file.
#
#CustomLog logs/access_log common

---

### Post by sharadchhetri on 2014-01-20
Not sure  which is the line number, but uncomment [COLOR=#000000]#Include conf.d/ . And restart the apache  /etc/init.d/apache2 restart OR service apache2 restart

To show the line number either use vi/vim editor or you can also use cat command.

cat -n /path/of/file

With vi/vim

:set nu


[/COLOR]

---

