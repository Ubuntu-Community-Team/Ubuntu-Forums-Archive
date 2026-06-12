---
title: "Setting up basic auth on Apache"
date: 2011-06-24
forum: Server Platforms
---

### Post by evilkronos on 2011-06-24
I am to create a part of my site to require a password. Upon research, I have created my .htpasswd file and modified my httpd.conf. When accessing the /admin section (the part I want to secure) no password is asked.

attached is my httpd.conf, I am not using .htaccess.
#========================================================================
<Directory />
Options Indexes Includes FollowSymLinks MultiViews
AllowOverride AuthConfig
Order allow,deny
Allow from all
</Directory>


<Directory /admin>
# Begin password protection #
AuthName "Login"
AuthBasicProvider file
Require valid-user
AuthUserFile "/home/roger/.htpasswd"
AuthType Basic
# End password protection #
</Directory>

---

### Post by elico on 2011-06-25
i would go with other settings such as:

```
                 AllowOverride All
```and in the .htaccess file of the specific directory use:
```

AuthType Basic
AuthName "Restricted Area: By Invitation Only"
AuthUserFile /home/www/1111
AuthGroupFile /dev/null

#AuthGroupFile /usr/local/apache/passwd/groups
#Require group GroupName

Require valid-user
```

---

### Post by dapperdanny77 on 2011-06-25
it's crucial that the apache process has permission to read the AuthUser file. 

your file /home/roger/.htpasswd sounds not readable by default

---

### Post by evilkronos on 2011-06-26
@elico
Changing my httpd.conf file and adding the .htaccess file you provided does nothing. I am never prompted for the user/pass, the page loads right away.

@dapperdanny77
I set the permissions for the file to 0777, did't work. I moved it to /var/www/ as well and it didnt work

---

### Post by Bachstelze on 2011-06-27
<Directory> blocks contain the full path of the directory in question in the filesystem, so you want something like /var/www/mysite and /var/www/mysite/admin.

---

### Post by dapperdanny77 on 2011-06-27
check out the <Location> directive instead of <Directory>

[http://httpd.apache.org/docs/current/mod/core.html#location](http://httpd.apache.org/docs/current/mod/core.html#location)

<Location> refers to URLs not to Directories in filesystem

---

### Post by evilkronos on 2011-06-27
> **dapperdanny77 said:**
> check out the <Location> directive instead of <Directory>

[http://httpd.apache.org/docs/current/mod/core.html#location](http://httpd.apache.org/docs/current/mod/core.html#location)

<Location> refers to URLs not to Directories in filesystem

THANK YOU! It worked,

I put a location /admin tag in the httpd.conf file and it works!

Solved

---

