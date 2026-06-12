---
title: "Need some help setting server up"
date: 2011-07-20
forum: Server Platforms
---

### Post by crazyjust on 2011-07-20
I am going to set up a lamp server, and would like some advice. I want to set up lamp and ftp. I would like to create a new user that would have the home directory of /var/www so I could log in ftp with this user and create, edit, delete, chmod files. How exactly could I accomplish this? Thanks

---

### Post by wojox on 2011-07-20
It would be better to enable module userdir and set up public_html in your home folder.

---

### Post by crazyjust on 2011-07-21
Ok. If i wanted to just give a user permission to write, delete, chmod files in /var/www without creating a new dir, how could I do that? Thanks

---

### Post by schnelle02 on 2011-07-21
Do you need multiple users with access to the files?  Otherwise you could set your root password with 
```
<snip>
see RootSudo howto here:

https://help.ubuntu.com/community/RootSudo
```
 then put in your current password as well as a new one (or same one) twice.  This will allow you to log in as root and you can set permissions to read/ write for owner through your ftp client.  Before that you should get your SSH package and LAMP installed via command line if you didn't install them with the disk.  Once you have them run ```
update
``` then ```
upgrade
```.  Now you're all up to date and can start modifying your website through ftp.

---

### Post by wojox on 2011-07-22
> **crazyjust said:**
> Ok. If i wanted to just give a user permission to write, delete, chmod files in /var/www without creating a new dir, how could I do that? Thanks

```
sudo a2enmod userdir
```

```
sudo service apache2 restart
```

```
sudo nano /etc/apache2/mods-enabled/userdir.conf
```

Change these two lines:

```

AllowOverrideAll
OptionsExecCGI
```

```
sudo nano /etc/apache2/mods-enabled/php5.conf
```

Comment out:

```
#php_admin_value engine Off
```

```
sudo service apache2 restart
```


Now make your directory in $HOME:

```
mkdir public_html 
cd public_html 
nano index.php 

```

[PHP]<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-align:center;">
<?php
print Date("Y/m/d");

?>
</div>
</body>
</html>[/PHP]

Now visit your site and test it.

---

