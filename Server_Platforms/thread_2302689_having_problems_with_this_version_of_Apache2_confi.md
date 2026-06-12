---
title: "having problems with this version of Apache2 configs"
date: 2015-11-12
forum: Server Platforms
---

### Post by phoenixcomm on 2015-11-12
Ok I have been using Apache2 on my Sun servers for a long time...
but this new LAMPS install with a "Debian style configs are freaking killing me..

[COLOR=#333333][FONT=Trebuchet MS]Linux Mint 17.2 is based on Ubuntu 14.04. [/FONT][/COLOR]
Whirlwind sites-enabled # apache2 -verServer version: Apache/2.4.7 (Ubuntu)
Server built: Oct 14 2015 14:20:21
Whirlwind sites-enabled # 


First problem..
I have a server on my desk (internal only) called Whirlwind. its address is 192.168.1.23. This is one of several boxes that I do my development on. 
now I really only need to see these servers here at my desk so I can use localhost, but I want to put up several websites for development. 
so they could be [www.name.dev]("http://www.name.dev") [www.othername.dev]("http://www.othername.dev") which I put in my etc/hosts file.
```

127.0.0.1 localhost
127.0.0.1 localhost
127.0.1.1 Whirlwind
# The following lines are for the vhosts on localhost
127.0.0.1 [www.librarian.dev]("http://www.librarian.dev")
127.0.0.1 [www.netfashions2go.dev]("http://www.netfashions2go.dev")
# The following lines are local network hosts
192.168.1.1 Router
192.168.1.23 Whirlwind

```


and created a conf file in sites-available and ln -s them in sites-enabled.
here is one of the conf files. Now please don't tell me not to use SSI that is a conversation for another time.
```

<VirtualHost NetFashions2Go-DEV:80>
ServerName NetFashions2Go-DEV
ServerAdmin webmaster@localhost
DocumentRoot /export/home/NetFashions2go
DirectoryIndex index.html index.shtml index.pl index.py
<Directory />
Options Includes ExecCGI FollowSymLinks
AllowOverride Indexes
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
but when I do [www.netfashions2go.dev]("http://www.netfashions2go.dev") in chrome
all I get is the directory of the default splash page (ubuntu test page)

and worse yet when I restart the service this is what i get in the console
Whirlwind sites-enabled # service apache2 restart
* Restarting web server apache2 
[Thu Nov 12 11:18:45.615600 2015] [core:error] [pid 8571] (EAI 2)Name or service not known: AH00547: Could not resolve host name librarian -- ignoring!
[Thu Nov 12 11:18:45.647361 2015] [core:error] [pid 8571] (EAI 2)Name or service not known: AH00547: Could not resolve host name NetFashions2Go-DEV -- ignoring!

---

### Post by TheFu on 2015-11-12
Wrong subforum - should be "servers", not "Desktops"

Which version of ubuntu?

"Apache2" is vague. 2.0, 2.2, and 2.4 each have important differences in their configurations. For example, config files must end in .conf now.  That is new. Also some **grant** permissions might be necessary.

Was **apache2ctl configtest** run? Any helpful warnings/errors/info?


Posting configs without using code-tags makes it hard for us to read. Please edit the OP and add code-tags so things line up.

Mixing case in hostnames. In theory, it shouldn't matter, but it is one more thing to check. Lazy script creators may not force all hostnames to a single-case (lower) for comparisons. Over 20 years, I've learned to avoid mixed case in domainnames.

In theory, the /etc/hosts file should be used for name resolution, but that isn't always the situation. nsswitch.conf look ok?

---

