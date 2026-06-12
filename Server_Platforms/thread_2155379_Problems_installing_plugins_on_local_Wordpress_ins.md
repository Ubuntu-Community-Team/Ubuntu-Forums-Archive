---
title: "Problems installing plugins on local Wordpress installation"
date: 2013-06-18
forum: Server Platforms
---

### Post by Feelkarma on 2013-06-18
Hi,
I have installed Wordpress locally in Ubuntu 13.04 following these instructions [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress).
I am now trying to install a plugin (wordpress-importer but that's no the point). I have tried direct installation or via upload, everytime I end up on the page asking me for the ftp server details. 
I have figured out so far that this is a permission issue, however I have tried everything I came across on the forums without success, i.e.:


```
sudo chown -R www-data wp-content
sudo chmod -R 755 wp-content

```

I have also added the following line to wp-config.php:


```
define('FS_METHOD', 'direct');

```

I have tried copying and pasting the plugin folder in the plugin directory but it still doesn't appear in the list of available plugins.

I feel that I've run out of options...


Thanks!

---

### Post by SeijiSensei on 2013-06-18
Are you trying to install the plugins from your WP Dashboard or some other method?  The former usually works for me.

---

### Post by Feelkarma on 2013-06-18
Ok, got it - I just had to create a symbolic link:

```
sudo ln -s /var/www/wordpress/wp-content/plugins/wordpress-importer /var/lib/wordpress/wp-content/plugins/wordpress-importer
```

Thanks

---

