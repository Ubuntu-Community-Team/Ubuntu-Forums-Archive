---
title: "Apache2 PHP files"
date: 2009-01-20
forum: Server Platforms
---

### Post by Drezard on 2009-01-20
I have this virtualhost file (created by nagios).

```

# SAMPLE CONFIG SNIPPETS FOR APACHE WEB SERVER
# Last Modified: 11-26-2005
#
# This file contains examples of entries that need
# to be incorporated into your Apache web server
# configuration file.  Customize the paths, etc. as
# needed to fit your system.

ScriptAlias /nagios/cgi-bin "/usr/local/nagios/sbin"

<Directory "/usr/local/nagios/sbin">
#  SSLRequireSSL
   Options ExecCGI
   AllowOverride None
   Order allow,deny
   Allow from all
#  Order deny,allow
#  Deny from all
#  Allow from 127.0.0.1
   AuthName "Nagios Access"
   AuthType Basic
   AuthUserFile /usr/local/nagios/etc/htpasswd.users
   Require valid-user
</Directory>

Alias /nagios "/usr/local/nagios/share"

<Directory "/usr/local/nagios/share">
#  SSLRequireSSL
   Options None
   AllowOverride None
   Order allow,deny
   Allow from all
#  Order deny,allow
#  Deny from all
#  Allow from 127.0.0.1
   AuthName "Nagios Access"
   AuthType Basic
   AuthUserFile /usr/local/nagios/etc/htpasswd.users
   Require valid-user
</Directory>


```

Except this file wont seem to allow me to view php files. I have php installed, if I chuck a php file (with phpinfo() in it) in /var/www/ it works pefectly and displays but, when I try and put a php file into the /usr/local/nagios/share/ folder, it prompts me to download it and has no idea how to use it...

How Do I fix this?

Daniel

---

### Post by stefangr1 on 2009-01-20
You have to install BOTH php5 and php5-common.

---

### Post by Drezard on 2009-01-20
Yeap did that. Still not working.

Full reboot as well.

---

