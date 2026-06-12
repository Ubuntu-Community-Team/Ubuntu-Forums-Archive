---
title: "Configure Apache2 DirectoryIndex option"
date: 2008-10-10
forum: Server Platforms
---

### Post by cquick on 2008-10-10
I am attempting, in vain, to get Apache to work with the DirectoryIndex directive and redirecting root. I'm not sure what's going on or why it doesn't seem to want to behave.

I have installed OTRS 2.3 (manually because the repository installs 2.2). The system is up and working great, everything behaves. However, I want to instruct my customers to go to a location without a hard to remember URL, so my first desire is to redirect all calls to the root to my OTRS installation ([http://server/](http://server/) --> [http://server/otrs](http://server/otrs)). I have modified the apache2.conf with the Redirect permanent directive, but it gets caught in an endless loop.

Next, I want the DirectoryIndex to force the page customer.pl to load. Here's my configuration stored in /etc/apache2/conf.d/otrs.conf:

[INDENT]#
# Basic apache configuration files for OTRS
#
# agent, admin and customer frontend
#
ScriptAlias /otrs/ "/opt/otrs/bin/cgi-bin/"
Alias /otrs-web/ "/opt/otrs/var/httpd/htdocs/"
#
# Directory Settings
#
<Directory "/opt/otrs/bin/cgi-bin/">
        AllowOverride None
        Options +ExecCGI -Includes
        Order allow,deny
        Allow from all
        DirectoryIndex customer.pl index.pl
</Directory>
<Directory "/opt/otrs/var/httpd/htdocs/">
        AllowOverride None
        Order allow,deny
        Allow from all
        DirectoryIndex customer.pl index.pl
</Directory>
[/INDENT]

This is running on 8.04 LTS Server with Apache2, MySQL 5 and all necessary dependencies for OTRS.

Any tips on what I might be doing wrong? Thanks!

---

### Post by Crummy_Gummy on 2008-10-27
Alter it in 

/etc/apache2/mods-enabled/dir.conf

---

