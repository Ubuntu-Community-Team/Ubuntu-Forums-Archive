---
title: "ErrorDocument 401 of Apache2 doesn't work"
date: 2010-08-17
forum: Server Platforms
---

### Post by gg_fish on 2010-08-17
Hi there,
   I have a problem about apache2 that has been troubling me for a day and still not solved. Here it is:
   
   For security consideration, which is also recommended by the apache2's documentation, I set basic type authorization check first on my root directory using mySQL, in the server configuration file, something like:

<Directory />
AuthMySQLEnable on
AuthMySQLDB   my_db
AuthMySQLNameField my_name_field
... ...
AuthType Basic
AuthName "password!"
</Directory>

Then, for a authorization failure, I want to use a customized page which is under /var/www/html/err/401.html. Thus I have something in my configuration file like:

ErrorDocument 401 /var/www/html/err/401.html

But because the root directory is set to check user account/password,  apache2 doesn't serve 401.html well.

So I reconfigured the configuration file and added these lines:
<Directory /var/www/html/err>
Options -Indexes FollowSymLinks
Allow from all
satisfy any
</Directory>

Then making sure I can access /var/www/html/err/401.html without authorization check by input the whole URL.


But problem comes that when authorization check fails, apache2 can't sever the error page, pop lines like :

Additionally, a 401 Authorization Required error was encountered while trying to use an ErrorDocument to handle the request.

together with the default "authorization required" page.

But if I set the ErrorDocument like
ErrorDocument 401 "boo boo"

The words "boo boo" pops on browser correctly.



So is there any idea on how to let apache2 serve the customized error page correctly? All the resource on my site has to be password protected. Thanks for any help.

---

