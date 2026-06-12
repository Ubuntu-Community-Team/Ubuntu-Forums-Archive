---
title: "Apache downloads php file instead of running it"
date: 2011-06-07
forum: Server Platforms
---

### Post by cov on 2011-06-07
Hi,

I'm trying to intall Drupal 7 on my machine, but the installation file (install.php) just gets downloaded instead of being run.

I have done this before previously, but can't see how I need to configure apache to run the file instead of downloading it.


I have followed the directions here: [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

Also installed php5-pgsql and php5-gd

---

### Post by cov on 2011-06-07
My drupal install is in /var/www/drupal.

I have set up a simple test.php in /var/www which just contains the following:

<?php
phpinfo();
?>

This runs ok and displays the php info.

This is obviously simple, but has me foxed. I've tried everything I can think of. Google is no damn good either; it just returns me this thread.

---

### Post by cov on 2011-06-07
Even more confused.

[http://localhost/drupal/testphp.php](http://localhost/drupal/testphp.php)

displays the php test info correctly.

permissions are rw-r--r--

---

### Post by ruffEdgz on 2011-06-07
Are you on the command line and trying to run install.php? If so, you still need to download the following:

```
sudo apt-get install php5-cli
```

Is that what you needed?

---

### Post by cov on 2011-06-07
Hi ruffEdgz,

No, just to run the install script through the browser.

I've got it working, but no idea why:

I had the directory drupal/ symlinked to drupal-7.2/

When I opened up [http://localhost/drupal-7.2/install.php](http://localhost/drupal-7.2/install.php), it worked fine.

But I have no idea why [http://localhost/drupal/testphp.php](http://localhost/drupal/testphp.php) worked.

It's a mystery.

---

