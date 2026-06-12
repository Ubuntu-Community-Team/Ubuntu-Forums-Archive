---
title: "vsftpd config"
date: 2008-08-30
forum: Server Platforms
---

### Post by gjj391 on 2008-08-30
I am successfully running vsftp and users can ftp into the home directory only.

How would I set up a user to access /var/www/ and not just home folders.

---

### Post by windependence on 2008-08-31
You should set your /var/www directory permissions to 755 and it should be UID root and GID root, i.e.:

```
drwxr-xr-x  2  root  root    4096    <date>   www
```

Next, fix the permissions that Apache applies in /etc/apache2conf. There should a section in there that begins <Directory>, you should fix it to look maybe like this:

```
<Directory />
  AllowOverride none
  Order Deny,Allow
  Deny from all
</Directory>
```

Then you can adjust the directory permissions individually like this (some of this should already be in the config file):

```
<Directory "/var/www/html">
  Options Indexes FollowSymLinks -MultiViews
  AllowOverrides None
  Order allow,deny
  Allow from all
</Directory>
```

You don't want your doc root files owned by the Apache user because then if someone comprromises that user they can change your content. You do, however want others to have read access and execute access (to be able to enter the directory).

Really, the best way is not to have ftp acces at all and acces your web files via ssh and scp with something like WinSCP.

-Tim

---

### Post by inphektion on 2008-08-31
> **gjj391 said:**
> I am successfully running vsftp and users can ftp into the home directory only.

How would I set up a user to access /var/www/ and not just home folders.

For the vsftpd config you can set a user_config_dir = /var/vsftp_users and in there put username file for any overrides from your default config.  So if the user you want chrooted to /var/www is "bill" then in your defined user_config_dir have a file called bill and have local_root = /var/www

check the man page for more details and other changes you can make
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

---

### Post by not28 on 2008-08-31
Would it be better to keep the virtual user's root directory in /home and then make a symbolic link to somewhere in /var/www? I'm still trying to figure this out as a noob.

---

### Post by inphektion on 2008-09-01
if you want him to just have a normal home dir and then be able to cd to the www then yes the symbolic link would work.

---

