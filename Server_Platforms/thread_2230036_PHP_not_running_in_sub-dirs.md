---
title: "PHP not running in sub-dirs"
date: 2014-06-16
forum: Server Platforms
---

### Post by mervyn511 on 2014-06-16
Hi, I'm having a problem where only php files in the top apache directory (/var/www/html) are being processed properly and php files in, for example, "/var/www/html/~*user*" are being printed as plain-text. The only other directory that seems to be able to process php is the PHPMyAdmin directory.

I'm using the LAMP stack with PHP5 & Apache2, all being kept up to date. Distro is Ubuntu Server 14.04.

[SIZE=2][SUB]Sorry if this is a simple problem, it's 3 a.m. here and I'm about to head to bed.[/SUB][/SIZE]

---

### Post by Doug S on 2014-06-17
Hi and welcome to Ubuntu forums.

Have a look at this file: /etc/apache2/mods-available/php5.conf
and have a look at this area of that file:```
# Running PHP scripts in user directories is disabled by default
#
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```

---

### Post by SeijiSensei on 2014-06-17
Look carefully at the code Doug provided.  Notice that Apache expects to find user websites in /home/username/public_html, not /var/www/html/~user.  When the [Userdir]("http://httpd.apache.org/docs/2.4/howto/public_html.html") option is enabled, users' websites will appear as [http://host/~user/](http://host/~user/).  

Now since the <Directory> container in the Apache code is for /home/*/public_html, changing the php_admin_flag setting for those directories probably won't help with /var/www/html/~user.  I recommend you move the user websites to their default directories.  It also makes it possible for the users' to edit those sites without any additional permissions.  Ordinary users have no rights to create or edit files under /var/www.

---

### Post by mervyn511 on 2014-06-17
> **Doug S said:**
> Hi and welcome to Ubuntu forums.

Have a look at this file: /etc/apache2/mods-available/php5.conf
and have a look at this area of that file:```
# Running PHP scripts in user directories is disabled by default
#
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```

Thanks, it's working now, I'd forgotten that I'd enabled mod_userdir. I'd originally done that through symlinks :rolleyes:
Changed "Off" to "On" and reset Apache :3

Thanks [SIZE=2]too[/SIZE], [COLOR=#000000]SeijiSensei. I understand how the mod works because it's what we use in college and I'd read the manual before enabling it but I'm the only person who uses the server that much anymore.

Can a mod mark as "[solved]"?[/COLOR]

---

### Post by lisati on 2014-06-17
> **mervyn511 said:**
> Can a mod mark as "[solved]"?
You should be able to do that with the "Thread tools" menu while viewing a thread.

---

### Post by mervyn511 on 2014-06-17
> **lisati said:**
> You should be able to do that with the "Thread tools" menu while viewing a thread.
Haha, thanks, I don't use forums often :oops:

---

### Post by Bigmek on 2014-06-19
> **mervyn511 said:**
> Thanks, it's working now, I'd forgotten that I'd enabled mod_userdir.


THX I apparently did the exact same thing. Finaly the past 2h of frustration are over...

---

