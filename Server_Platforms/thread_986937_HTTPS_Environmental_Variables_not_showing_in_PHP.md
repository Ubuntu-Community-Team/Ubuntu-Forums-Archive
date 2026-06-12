---
title: "HTTPS Environmental Variables not showing in PHP"
date: 2008-11-19
forum: Server Platforms
---

### Post by markcorbyn on 2008-11-19
Hi All,

I am attempting to set up https on my local server and seem to have it working except for a couple of problems:
* The Apache Environmental Variables aren't showing up in PHP
* PHP shows $_SERVER['SERVER_PORT'] as 80 rather than 443

When installing ssl I followed the tutorial at [https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration](https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration)
I am using Ubuntu 7.10.

When I browse localhost I can now access both http:// and https://
When I access https:// in Firefox 2 the address bar turns yellow with the padlock and I can view the certificate details of the certificate I created.

The problem is that PHP does not seem to recognise I'm in https as the $_SERVER['SERVER_PORT'] is 80 and there is no existence of $_SERVER['HTTPS']

Curiously if I add the following command to htaccess:

RewriteCond %{HTTPS} !=on
RewriteRule .* [https://www.someotherdomain.com](https://www.someotherdomain.com) [R,L]

I do get redirected to [https://www.someotherdomain.com](https://www.someotherdomain.com) when I access [http://mylocaldomain/](http://mylocaldomain/) but not when I access [https://mylocaldomain/](https://mylocaldomain/) which suggests Apache is aware of https mode but the information isn't being passed to PHP.
When I specifically type in [https://mylocaldomain:443/](https://mylocaldomain:443/) then the SERVER_PORT is recognised in PHP as 443.

Any suggestions?

Thanks,
Mark


PS:  If you would like to see any config settings let me know which files/sections and I'll post them.

---

### Post by Philio on 2008-11-19
In Ubuntu 7.10 do you have the file:

/etc/apache2/sites-available/default-ssl

If so you can simply do:

a2enmod ssl
a2ensite default-ssl
/etc/init.d/apache2 reload

SSL should then work and allow you to connect via HTTPS.

I'm guessing the default-ssl file doesn't exist in 7.10 based on the instructions, but I don't have a 7.10 computer available to check it.

The instructions given should work though, have you checked every procedure twice and do you get any error messages?

---

### Post by markcorbyn on 2008-11-19
Hi Philio,

Thanks for the reply.  I have checked the guide and am certain I followed each step as instructed.  I didn't encounter any errors during the process.

With regards the sites-available/default-ssl, this file doesn't exist on my install.  The one which does is sites-available/default which is where I added the additional <VirtualHost *:443> directive below the <VirtualHost *:80> directive.

Thanks,
Mark

---

### Post by markcorbyn on 2008-11-19
I also have the additional <VirtualHost *:443 > set up in sites-enabled/htdocs which specifies the ServerName, ServerAlias and DocumentRoot

---

### Post by markcorbyn on 2008-11-19
Wow in explaining my configuration to you I figured out the problem.

The <VirtualHost *:443> in sites-available/default contained all of the SSLEngine on etc. details

I was assuming that the <VirtualHost *:443> in my sites-enabled/htdocs was inheriting those properties from sites-available/default but since adding these lines also to my additional VirtualHost everything is now working.

Thanks for the help,
Mark

---

