---
title: "After Doing the actions to specify DocumentRoot Getting the 403 Error"
date: 2011-07-12
forum: Server Platforms
---

### Post by varunaub on 2011-07-12
[LEFT]I carried out the actions under Virtual Hosts described [https://help.ubuntu.com/community/ApacheMySQLPHP ]("https://help.ubuntu.com/community/ApacheMySQLPHP")

After that when I try to accesses localhost which is /home/user/public_html/ I am getting the message
> **Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80I want to learn PHP.The Default var/www/ always needs root access to do exercises, that's, why I changed DocumentRoot to /home/user/public_html/ But now I am getting the above mentioned error 

How Will I be able to overcome this?:confused:
[/LEFT]

---

### Post by lisati on 2011-07-12
*Thread moved to **Server Platforms**.*

It sounds like a permissions problem at the file end.

---

### Post by ruffEdgz on 2011-07-12
Like stated from **lisati**, sounds like a permission issue but I was curious about the DocumentRoot location. So you have a location called '/home/user/public_html' or did you change it to something like this '/home/<username>/public'?
```

ls -ld /home/user/public_html

```
Well either case, can are following the document, can you open up /etc/apache2/sites-available/mysite, find <Directory /home/user/public_html/> and paste that information onto this post.

Cheers!

---

### Post by kgatan on 2011-07-12
Apache uses the user called www-data to read and write to files.
That means that where ever you have the document root www-data needs at least read permissions to access it.

if your user name is "albert" you can add "www-data" to the group "albert". Then www-data will have read access to your home folder.

---

### Post by varunaub on 2011-07-12
> **kgatan said:**
> Apache uses the user called www-data to read and write to files.
That means that where ever you have the document root www-data needs at least read permissions to access it.

if your user name is "albert" you can add "www-data" to the group "albert". Then www-data will have read access to your home folder.

How do I add www-data to the group "albert" (to the group of that my user name belongs):confused:

---

### Post by varunaub on 2011-07-12
> **ruffEdgz said:**
> Like stated from **lisati**, sounds like a permission issue but I was curious about the DocumentRoot location. So you have a location called '/home/user/public_html' or did you change it to something like this '/home/<username>/public'?
```

ls -ld /home/user/public_html

```Well either case, can are following the document, can you open up /etc/apache2/sites-available/mysite, find <Directory /home/user/public_html/> and paste that information onto this post.

Cheers!

to path  /home/user/public_html/ I added my user name where the term "user" is used:KS
**By pasting what you are asking for am I not giving my user name and compromising my security andthe same technique of security that Ubuntu is intends to provide:confused:**

---

### Post by kgatan on 2011-07-12
You add a user to a group with the "adduser" command,

```
adduser www-data albert
```

---

### Post by ruffEdgz on 2011-07-13
> **varunaub said:**
> to path  /home/user/public_html/ I added my user name where the term "user" is used:KS
**By pasting what you are asking for am I not giving my user name and compromising my security andthe same technique of security that Ubuntu is intends to provide:confused:**

Asking who owns a file will not compromise your security since I never asked for your server information/IP/DNS entry/etc... so its kind of hard to compromise your system without knowing the destination but whatever.

I was trying to see if that directory had the correct permissions for user,group.other and the content in it would also be important to know who owns it since the user 'www-data' (as explained by kgatan) needs to be able to view that data.

Make sure that the group permissions on the directory and files inside of that directory will allow www-data to be able to read and/or execute (depending on the content you are trying to display) will probably solve this issue.

Best with your apache configuration and security.

---

### Post by varunaub on 2011-07-13
> **ruffEdgz said:**
> Asking who owns a file will not compromise your security since I never asked for your server information/IP/DNS entry/etc... so its kind of hard to compromise your system without knowing the destination but whatever.

I was trying to see if that directory had the correct permissions for user,group.other and the content in it would also be important to know who owns it since the user 'www-data' (as explained by kgatan) needs to be able to view that data.

Make sure that the group permissions on the directory and files inside of that directory will allow www-data to be able to read and/or execute (depending on the content you are trying to display) will probably solve this issue.

Best with your apache configuration and security.

I never intended to offend you and I am sorry if I did, I was only referring to what I read about Ubuntu adopting "sudo" to allow a User to have root privileges.

I did the following

> adduser www-data <User Name> After that When I execute the following the result is as follows
> ls -l /home/<User Name>/public_html
-rw-r--r-- 1 <User Name> <User Name> 29 2011-07-12 23:52 index.html
-rw-r--r-- 1 <User Name> <User Name>  0 2011-07-14 06:08 test.php


I have created two files inside public_html

But still through Firefox when I try to access localhost the following is what I get

> **Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80The following is the complete /etc/apache2/sites-enabled/mysite contents

> 
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/<User Name>/public_html/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/<User Name>/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
Still The problem exists:confused:

Hope you can help!


When the DocementRoot and Directory is changed to /var/www it works
Pls Note: I have changed the "listen" Directive to 127:0.0.1:80
Now the mysite file looks this

> <VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>**The latest I have discovered is described below.I think the problem is in access permissions of the <User Name> Directory**

When I start the terminal l  am at <User Name>@<User   Name>-desktop:~$ Then  I typed ```
cd /home 
```Then the  prompt  looked like>  <User Name>@<User  Name>-desktop:/home$  then when given the command```
  ls
``` the result is  > <User Name> after that to  see the access  permissions of the <User Name> Directory I  typed```
 ls  -l 
```the result is ```
drwxrw---- 53 <User  Name> <User  Name> 16384 2011-07-14 14:59 <User  Name>
```I described above in order to convey the access  permissions of <User  Name> Directory in which is the folder  public_html. I  am not able to access the  public_html directory through apache2, I get  a 403 error.The reason I  think is because the folder bearing my user  name which is the home  folder of public_html(/home/<User  Name>/public_html/), has not  allowed access to to apache2 or  user-data.I have added user-data to the  <User Name> group by  issuing adduser command


How can I change the access permissions of the <User Name> Directory?:confused:

---

### Post by ruffEdgz on 2011-07-14
Now seeing the information about the /home/<User Name>/ directory, this part does seem to be the problem mostly because of the 'other' permissions are set to 0 (which doesn't allow anyone to few the files.
```

drwxrw-**---** 53 <User  Name> <User  Name> 16384 2011-07-14 14:59 <User  Name>
        ^
        |
   This is bolded

```
As a test (you don't need to keep it this way) but lets make that 'other' permission accessible for people to at least read and execute (both permissions will allow others to at least look and go into that directory which should be needed for displaying html content):
```

sudo chmod 775 /home/<User Name>

```
This will only change the directory /home/<User Name> directory. You might want to check your public_html directory permissions and make sure that is also set to let others read and execute for the directory:
```

sudo chmod 775 /home/<User Name>/public_html/

```
Again, this will only change the permissions for the directory only. Now that this has been changed, make sure you have 'mysite' config in the sites-enabled directory in apache and restart the service.

If it does or doesn't work and you want to revert back to your previous settings, use the following command to do so:
```

sudo chmod 770 /home/<User Name> /home/<User Name>/public_html

```
That will set it back to only allow the user and group owners to view those directories.

You might also want to look into the apache module called 'userdir_mod' that can be found in the directory /etc/apache/mods-available/ called 'userdir'. This approach might still need you to allow access to your home dir but its might be a little easier: [http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)

Cheers!

---

