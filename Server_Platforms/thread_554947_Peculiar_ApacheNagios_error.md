---
title: "Peculiar Apache/Nagios error"
date: 2007-09-19
forum: Server Platforms
---

### Post by jane21 on 2007-09-19
Hi folks:

I just finished installing Nagios on a Ubuntu server VM.  However, I am getting an odd "page not found" error when I try to view any of the monitoring pages:

> The requested URL /nagios.cgi-bin/tac.cgi was not found on this server.

This happens for all pages except the documentation pages.

I noticed the weird dot in between nagios and cgi-bin, and I figure that that's where the problem is (i.e. that dot should be a slash).  However, I can't find where that typeo lives.  My httpd.conf file is correct, as you can see:

> # This is here for backwards compatibility reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
ScriptAlias /nagios/cgi-bin /etc/nagios/sbin

<Directory "/etc/nagios/sbin">
Options ExecCGI
AllowOverride None
Order allow,deny
Allow from all
AuthName "Nagios Access"
AuthType Basic
AuthUserFile /etc/nagios/etc/htpasswd.users
Require valid-user
</Directory>

Alias /nagios /etc/nagios/share

<Directory "/etc/nagios/share">
Options None
AllowOverride None
Order allow,deny
Allow from all
AuthName "Nagios Access"
AuthType Basic
AuthUserFile /etc/nagios/etc/htpasswd.users
Require valid-user
</Directory>


Both apache and nagios are running, and I've confirmed that the cgi files do exist in /etc/nagios/sbin.  I'm using the default cgi.cfg file.

I'm not very familiar with Apache, so I'm sure there's some little picky line in some little picky file somewhere that just needs to be changed, but I have no idea where to look.  Any tips would be much appreciated!

---

### Post by compiledkernel on 2007-09-19
Did you build nagios from source, or did you install it from the repos? 

It sounds like it didnt compile properly.

---

### Post by jane21 on 2007-09-19
I installed from source.  Is there a package in the repositories?  I don't even remember if I checked.  I was using [this tutorial]("http://ubuntuforums.org/showthread.php?t=223498") to guide me.

If it didn't compile correctly, how do I fix that with the minimum amount of pain and suffering?

---

