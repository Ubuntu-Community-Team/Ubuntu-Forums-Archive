---
title: "Apache not starting after installing SSL certificate on vhost"
date: 2013-04-19
forum: Server Platforms
---

### Post by tarmy on 2013-04-19
Hello!

I tried to install a already existing certificate from GoDaddy on a  website in ISPConfig3. I first enabled the SSL checkbox, then  copy/pasted the certificate in the SSL tab.

After I did this, apache crashed, and could not start. I'll admit I  panicked a bit, but further on I navigated to /var/www/example.com/ssl,  and deleted the certificates. I tried to restart apache, but then it  could not find the certificates, and would not start (obviously). I went  in /etc/apache2/sites-enabled/100-example.com vhost, and removed the  certificate paths from:

     Code:
     
    <IfModule mod_ssl.c> #       SSLEngine on      </IfModule> 
I then tried restarting apache, but now I'm getting this error message in apache:

[Fri Apr 19 07:57:49 2013] [error] Server should be SSL-aware but has no  certificate configured [Hint: SSLCertificateFile] ((null):0)

Any suggestions? Thanks!

---

### Post by tarmy on 2013-04-19
Deleted the vhost file from /etc/apache2/sites-enabled, restartet apache. That made it possible to re-log on ISPConfig, and fix the certificate error.

---

