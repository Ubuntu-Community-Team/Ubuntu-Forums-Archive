---
title: "Apache Problem"
date: 2009-06-27
forum: Server Platforms
---

### Post by Vegan on 2009-06-27
* Restarting web server apache2
Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'NamedVirtualHosts', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
invoke-rc.d: initscript apache2, action "restart" failed.

Ideas?

I only have that 1 line in my httpd.conf file

---

### Post by Vegan on 2009-06-27
OK I added some more stuff......

NameVirtualHost *

<VirtualHost *>
ServerName contract-developer.dyndns.biz
DocumentRoot /var/www/developer
</VirtualHost>

<VirtualHost *>
ServerName econ.dyndns.biz
DocumentRoot /var/www/econ
</VirtualHost>

<VirtualHost *>
ServerName computer-chess.dyndns.biz
DocumentRoot /var/www/chess
</VirtualHost>

<VirtualHost *>
ServerName vegan.dyndns.biz
DocumentRoot /var/www/vegan
</VirtualHost>


And the result is........

 * Restarting web server apache2
[Sat Jun 27 16:33:49 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first has precedence,
 perhaps you need a NameVirtualHost directive
[Sat Jun 27 16:33:49 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first has precedence,
 perhaps you need a NameVirtualHost directive
[Sat Jun 27 16:33:49 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first has precedence,
 perhaps you need a NameVirtualHost directive
 ... waiting .[Sat Jun 27 16:33:52 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first h
as precedence, perhaps you need a NameVirtualHost directive
[Sat Jun 27 16:33:52 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first has precedence,
 perhaps you need a NameVirtualHost directive
[Sat Jun 27 16:33:52 2009] [warn] VirtualHost 192.168.7.106:80 overlaps with VirtualHost 192.168.7.106:80, the first has precedence,
 perhaps you need a NameVirtualHost directive
   ...done.

---

### Post by R.Bucky on 2009-06-27
It looks like you are trying to do Name Based Virtual Hosting? The httpd.conf file does not seem to be used that often anymore. Try just making separate .conf files in /etc/apache2/sites-available/ for your sub-domains.

I have not configured a sub-domain for a while. Anyone else chime in?

---

