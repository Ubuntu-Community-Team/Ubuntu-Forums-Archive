---
title: "Problem creating virtual hosts"
date: 2005-09-16
forum: Server Platforms
---

### Post by philpot on 2005-09-16
Hello

I have installed Webmin to aid with configuring virtual hosts, howver, when I create a virtual host, it doesn't appear in the Webmin list of virtual hosts, all that shows in the "Default Server". Anyone help?

---

### Post by KingBahamut on 2005-09-16
[QUOTE=philpot]Hello

I have installed Webmin to aid with configuring virtual hosts, howver, when I create a virtual host, it doesn't appear in the Webmin list of virtual hosts, all that shows in the "Default Server". Anyone help?[/QUOTE]
 Ive always edited the file manually, I wouldnt depend on something like webmin to edit it for me. That would be , in my opinion, more beneficial than using an outside editor , module, or program to do it.

---

### Post by TheDanMan on 2005-09-16
Have you added a virtualhost directive in httpd.conf for the virtual host?  Have you added NameVirtualHost directive in httpd.conf?

In apache 1.3 and apache 2 your NameVirtualHost directive would look like this:

NameVirtualHost x.x.x.x:80

Where x.x.x.x is your IP address.

In apache 1.3 it your virtual host directive would look something like this:
<VirtualHost x.x.x.x:80>
ServerName domain.tld
ServerAlias [www.domain.tld](www.domain.tld)
DocumentRoot /documentpath
ErrorLog /errorpath
CustomLog /customlogpath
ScriptAlias /cgi-bin/ /customcgipath/cgi-bin/
<Directory /publicdocumentpath>
Options Indexes IncludesNOEXEC FollowSymLinks
allow from all
</Directory>
</VirtualHost>

---

### Post by TheDanMan on 2005-09-16
You may want to install virtualmin to help you.  You can get it at the webmin site.  Or you can apt-get install webmin-virtualmin.

I recommend you install the module from the virtualmin site though.

---

### Post by philpot on 2005-09-17
Thanks all. It was a missing NameVirtualHost directive.

---

