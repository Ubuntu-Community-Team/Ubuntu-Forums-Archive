---
title: "PHP isn't work!"
date: 2006-09-21
forum: Server Platforms
---

### Post by nadavvin on 2006-09-21
Hello

I did some change in the installation of some packages of PHP.

Now the PHP isn't work at all.

I install the libapache2-mod-php5 but it didn't help.

I have edgy.

Thanks for your help.

Nadav.

---

### Post by nadavvin on 2006-09-22
I found that the httpd.conf file is reset to some comments:
```

$ cat /etc/apache2/httpd.conf
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so


```

What should I do in order to regenerate the file content?

Happy new year;)

---

### Post by spp on 2006-09-22
Look in /etc/apache2/mods-enabled and see if there is a php5.load file. If not, run the following command:

```
sudo update-apache2-modules --enable php5
```

SP

---

### Post by nadavvin on 2006-09-22
```


sudo update-apache2-modules --enable php5
Password:
No Such Module


```

---

### Post by spp on 2006-09-22
Ok... 

Look in /etc/apache2/mods-available and see if anything is there related to PHP

the update-apache2-modules merely symlinks those files into the mods-enabled directory.

SP

---

### Post by nadavvin on 2006-09-22
```

/etc/apache2/mods-available$ ls|grep php
php4.conf
php4.load
php5.conf
php5.load

```

```
$ cat php5.conf
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

```
nadav@nadav-desktop:/etc/apache2/mods-available$ cat php5.load
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

```
$ ls -l /usr/lib/apache2/modules/libphp5.so
-rw-r--r-- 1 root root 5162340 2006-09-15 20:09 /usr/lib/apache2/modules/libphp5.so

```

---

### Post by spp on 2006-09-22
Ok, now what is in the mods-enabled directory? Is there a symlink back to the php5.load file?

SP

---

### Post by nadavvin on 2006-09-24
Thanks

I add a symlink to php5.load and now it's work.

---

### Post by hartunnoo on 2006-10-21
nadavvin, can you elaborate more on how to symlink this files?

I have experencing with this problem.


Thank you.

---

### Post by nadavvin on 2006-11-10
```

$ locate php5.load|xargs ls -l
-rw-r--r-- 1 root root 59 2006-09-14 16:35 /etc/apache2/mods-available/php5.load
lrwxrwxrwx 1 root root 37 2006-09-24 23:44 /etc/apache2/mods-enabled/php5.load -> /etc/apache2/mods-available/php5.load

```

but there is better solution:
a2enmod will enable a module:
```

$ a2enmod
Which module would you like to enable?
Your choices are: actions asis auth_anon auth_dbm auth_digest auth_ldap cache cern_meta cgid cgi dav_fs dav deflate disk_cache expires ext_filter fastcgi file_cache headers imap include info ldap mem_cache mime_magic mod_mono mod_python modxslt perl php4 php5 proxy_connect proxy_ftp proxy_http proxy rewrite ruby speling ssl suexec unique_id userdir usertrack vhost_alias
Module name?                                        

```

and a2dismod will disable module:
```

$ a2dismod
Which module would you like to disable?
Your choices are: cgi fastcgi mod_python perl php5 ruby userdir
Module name?      

```

---

