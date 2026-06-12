---
title: "diagnosing errors with mod_auth_mysql"
date: 2013-08-08
forum: Server Platforms
---

### Post by yawnmoth on 2013-08-08
So I installed mod_auth_mysql via the following:

```
sudo apt-get install libapache2-mod-auth-mysql 
sudo a2enmod auth_mysql 
sudo /etc/init.d/apache2 restart
```
I updated my .htaccess file to make it connect to the DB as well but it's not working. Here's what I'm getting in the error logs:

```
[Wed Aug 07 16:35:23 2013] [error] [client xxx.xxx.xxx.xxx] user username not found: /admin/, referer: https://www.domain.tld/
```

The username very definitely does exist. If I do SELECT * FROM userTable WHERE userName = 'username' it comes up. So I'm at a bit of a loss.

Is there a way I could see the SQL mod_auth_mysql is generating?

From my .htaccess file...

```
AuthBasicAuthoritative Off
AuthUserFile /dev/null
Auth_MYSQL On
Auth_MySQL_Host localhost
Auth_MySQL_User username
Auth_MySQL_Password password
Auth_MySQL_Authoritative On
Auth_MySQL_DB "dbname"
Auth_MySQL_Password_Table "apache_auth"
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field password
Auth_MySQL_Group_Field group
Auth_MySQL_Encryption_Types Plaintext
```
Any ideas?

---

### Post by SeijiSensei on 2013-08-09
Did you enable .htaccess in /etc/apache2/sites-enabled/default?  It is disabled by default via the "AllowOverride None" directive in that file.

In general, if you have full control over the server, you should avoid using .htaccess and place the directives that would appear there into the appropriate <Directory> stanza in the site's configuration file.  The .htaccess file is a kludge that enables ISPs to let their customers set parameters for hosted web sites.

---

