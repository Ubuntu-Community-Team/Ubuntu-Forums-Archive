---
title: "Apache2 password protect &quot;/var/www&quot; root folder"
date: 2013-04-02
forum: Server Platforms
---

### Post by ebenflood on 2013-04-02
Hello,

We're running Ubuntu Server 12.04 and Apache2 to serve out a webpage and it's running just fine.  However, the owner of the site would like to password protect the entire website including the homepage which is currently located in the /var/www folder.  I've been able to successfully password protect any "subfolder" below that root with no problem, e.g., /var/www/testfolder or /var/www/forms but I'm unable to get the root folder (/var/www) password protected using a similar setup.  

I'd read that it's best to avoid using the .htaccess file method and instead to modify the httpd.conf file in the /etc/apache2 folder to specify which folder(s) should be password protected.  So, I created a password file named "passwords" using the htpasswd utility and i stored the password file in a new folder I created that isn't located on the website (/usr/local/apache).  I edited the httpd.conf file in the /etc/apache2 folder and it now contains only the following lines -

<Directory "/var/www/testfolder">
AuthType Basic
AuthName "Restricted"
AuthBasicProvider file
AuthUserFile /usr/local/apache/passwords
Require user testuser
Allow from 192.168.1.99 [the computer at this IP doesn't need to authenticate]
Order allow,deny
Satisfy any
</Directory> 

A httpd.conf file with the above lines sucessfully password protects the "testfolder" folder. However if I change the top line of the httpd.conf config to point to the "root" /var/www then I never receive any password prompt.

I've tried a lot of variations on the <Directory "/var/www"> line to try to get it to work and after i made each of the test modification i stopped and restarted the Apache2 server.  I've tried - <Directory "/var">, <Directory "/var">, <Directory "/">, <Directory "/var/*">, <Directory "/var/www/*">, etc.  I've tried quite a few more variations than those listed above but none of them seems to work.  Once again, if I change the <Directory line back to /var/www/testfolder or some other subfolder I successfully get the password prompt every time on those subfolders.

I even tried giving up on the "var/www" folder and instead I edited the "default" file in the "sites-available" folder and changed the document root from /var/www to /var/www/testfolder but once i did that the "testfolder" lost it's password protection while once again any subfolder below this "new root" could be easily password protected.  

I haven't made any modifications to the apache2.conf file located in the /etc/apache2 folder.  Does the website root folder have its own special set of permissions or is somehow able to deny password protection or authentication overrides?

Thanks, any help will be greatly appreciated...

---

