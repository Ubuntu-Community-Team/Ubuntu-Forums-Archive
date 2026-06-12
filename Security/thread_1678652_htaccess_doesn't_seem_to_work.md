---
title: "htaccess doesn't seem to work"
date: 2011-01-30
forum: Security
---

### Post by MSPdwalt on 2011-01-30
You web guys are probably going to laugh at me, but I can't seem to get htaccess to work.

I've created a .htpasswd file like so:

```
htpasswd -c -m .htpasswd user
```

Then it prompts me for a password for that user.  I put the password file one dir above my document root and I created a .htaccess file like this in the directory I wish to secure

```
AuthUserFile /web/.htpasswd
AuthGroupFile /dev/null
AuthName Secured Page
AuthType Basic
require valid-user
```

What kind of permissions do the .htaccess file and the .htpasswd file need to have?  Am I doing this right?

My webserver has a couple of different sites on it, we use virtual hosts to handle the redirections.  Each document root is under /web.

So for example: 

```
ls /web
site1 site2
```

Any help would be greatly appreciated,
-DW

---

### Post by bodhi.zazen on 2011-01-31
The only things I see are :

1. AuthUserFile needs to be the full path. So as long as you have a directory /web, you are OK. But is /web in /var/www ? In that event it should be /var/www/web

2. Your use of /dev/null in AuthGroupFile. You might try deleting this line, it is not necessary.

3. Linux does not like spaces, so change

AuthName Secured Page

to

AuthName "Secured Page"

I am not sure if any or all of that applies.

---

### Post by MSPdwalt on 2011-02-01
Thanks for the tips bodhi,

The paths are correct.  I removed the AuthGroupFile, and I changed the space to an underscore.  Still no go.  Any other thoughts?

My gut was saying file permissions, but I haven't found anything that says what kind of permissions the files should have.  Right now www-data is the group and owner and it has read and execute permissions.

---

### Post by bodhi.zazen on 2011-02-01
OK, second guess, .htaccess is outside the web root ?

Did you put a .htaccess file in each /web/site ?

Did you re-start apache ?

---

### Post by SeijiSensei on 2011-02-01
By default, you cannot override authentication (or anything else) in .htaccess.  Take a look at /etc/apache2/sites-enabled/000-default:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

Notice the "AllowOverride None" entries? These forbid making changes through .htaccess.  (The entry for "Directory /" applies a default to all directories.)  You can replace "None" with "All", or be more selective and choose the appropriate options [here](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride).  You need at least the "AuthConfig" option.

Also /dev/null is a perfectly acceptable option for AuthGroupFile if you're not using groups.  I've used it myself.

---

### Post by bodhi.zazen on 2011-02-01
> **SeijiSensei said:**
> By default, you cannot override authentication (or anything else) in .htaccess.  Take a look at /etc/apache2/sites-enabled/000-default:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

Notice the "AllowOverride None" entries? These forbid making changes through .htaccess.  (The entry for "Directory /" applies a default to all directories.)  You can replace "None" with "All", or be more selective and choose the appropriate options [here](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride).  You need at least the "AuthConfig" option.

Also /dev/null is a perfectly acceptable option for AuthGroupFile if you're not using groups.  I've used it myself.

Thank you for the information SeijiSensei

---

### Post by MSPdwalt on 2011-02-01
It was the AllowOverride in my vhost config.

Thanks guys,

DW

---

