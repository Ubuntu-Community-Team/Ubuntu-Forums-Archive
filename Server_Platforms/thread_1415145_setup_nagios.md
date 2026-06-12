---
title: "setup nagios"
date: 2010-02-24
forum: Server Platforms
---

### Post by dsexton18 on 2010-02-24
I have installed Nagios 3 on ubuntu 9.10 server. How ever I need help with getting the web interface to show up. Appache is installed and working. I setup a sym link between /etc/nagios3 and /var/www/ thinking if I setup a sym link that would work but it just errors out when I type [http://IPaddress/nagios](http://IPaddress/nagios) I assume I am missing some thing but what.

---

### Post by Iowan on 2010-02-24
Dunno if [this]("http://www.ghacks.net/2009/06/08/how-to-install-nagios-on-ubuntu-server/") article will answer any questions?
 [Another]("https://help.ubuntu.com/community/Nagios3") help page.

---

### Post by joberly on 2010-02-24
I don't mean to state the obvious, but your post indicates you are going to [http://IPaddress/nagios](http://IPaddress/nagios) when in fact the correct url would be [http://IPaddress/nagios3](http://IPaddress/nagios3).

---

### Post by kernelzilla on 2010-02-25
I'm not sure what guide is telling you to create a symbolic link between /etc/nagios3 and /var/www, but this is unnecessary.  The configuration for the /nagios3 URL is installed automatically by the package (at /etc/apache2/conf.d/nagios3.conf)

---

### Post by dsexton18 on 2010-02-25
I can't recall what guide I was using it dident work and I did not book mark it.  The resion I setup a sym link is becuse when I went to /var/www it was empty.  So I though if I setup a symlink it might work. I also thought maybe when nagios was installed  an alis would be added to httpd.conf You will have to forgive me I don't know much about Apache.   
 
And I also tried [http://ipaddress/nagios3](http://ipaddress/nagios3)

---

### Post by dsexton18 on 2010-02-26
Now it seams like I have a problem with a config file.  /etc/apache/conf.d/nagios3.conf it's contents look like this
It appears to be a sym link to /etc/nagios3/apache2.conf

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





^G Get Help               ^O WriteOut               ^R Read File              ^Y Prev Page              ^K Cut Text               ^C Cur Pos
^X Exit                   ^J Justify                ^W Where Is               ^V Next Page              ^U UnCut Text             ^T To Spell

---

### Post by dsexton18 on 2010-02-26
never mind i got it working.  Thanks for you help every one

---

