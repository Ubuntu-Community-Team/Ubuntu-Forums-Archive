---
title: "Apache2 virtual hosts"
date: 2007-10-21
forum: Server Platforms
---

### Post by Santos1204 on 2007-10-21
Hi,

I've looked over the other VH posts and couldn't find anything that helped. 

I'm running Apache 2.2.3 on the latest version of Ubuntu using PHP 5.2.1.

I'm trying to setup Virtual Host so that multiple websites run from one IP.

I've added the following code into /etc/apache2/httpd.conf;

NameVirtualHost *80

<VirtualHost *:80>
ServerName [www.someAddress.co.uk](www.someAddress.co.uk)
ServerAlias *someAddress.co.uk
DocumentRoot /www/someFolder
</VirtualHost>

This is then repeated three further times. And is the only code in the httpd.conf file.

Whenever I put in any url handled by my server, I am greeted with the DocumentRoot folders level specified above.

Can anyone help?

Cheers

Santos

---

### Post by conjur3r on 2007-10-21
You made your changes to the wrong file.  Put httpd.conf back to an empty file.

For each site you want, create a file in /etc/apache2/sites-available and based on default.  The only redundant thing is that NameVirtualHost * does not need to appear in your site configs as it's already specified in default.

When you've done that, enable the site using **a2ensite SITECONF** (replace SITECONF with the name of the file(s) you created) and then restart apache.  If it was all done correctly, it should be working now.

---

### Post by Santos1204 on 2007-10-22
conjur3r,

Thanks that worked a treat!

Cheers

Chris

---

