---
title: "htaccess problem(permitting web files)"
date: 2011-08-16
forum: Server Platforms
---

### Post by coolx on 2011-08-16
Hi,
I want to specifically control my web server's file and directories. For  example a user should reach a file but another user shouldnt. For this  reason I am trying to implement ".htaccess" to ubuntu. But its not  working.

Firstly .htaccess is enable from "apache.conf" file.
-------------------------------
AccessFileName .htaccess
-------------------------------

Then I create a .htaccess file in "/var/www/" directory. I wrote the below in .htaccess file;
--------------------------------
<Files default.php>
Order allow,deny
Deny from all
</Files>
--------------------------------

But all users still reach this file. I tryed lots of combinations but  still doesnt work. I think "allowoverride" is should use somethings in  but I dont know in which file or directory?

Basically how can I do that?

Thanks.

---

### Post by Doug S on 2011-08-16
in the file /etc/apache2/sites-available/default, change this part:
```
 
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 

```
to this:
```
 
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
 

```
and then reload or restart the web server:
```
 
sudo /etc/init.d/apache2 reload

```
Note that various apache documentation recommends to not use the .htaccess file method, but rather the preferred method is via the mainserver configuration where one edits the same default file on a per directory basis. Myself, I use the .htaccess method. For completeness, below is an example of a possible edit to the default file, limiting access to my protected_1 directory (and sub-directories):
```

           <Directory "/home/doug/public_html/protected_1/">
              AllowOverride FileInfo AuthConfig Limit
              Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
              Authtype basic
              AuthName "Registered users only permitted"
              AuthUserFile /home/doug/.htpasswd
              Require valid-user
           </Directory>

```

---

### Post by coolx on 2011-08-16
Thanks you so much doug. :) I've been searching about this isse since yesterday. Now it is working. Thanks again.

---

