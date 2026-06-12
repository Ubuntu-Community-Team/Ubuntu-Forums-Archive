---
title: "LAMP installation. Did I do it right?"
date: 2007-07-21
forum: Server Platforms
---

### Post by tombiz on 2007-07-21
This is the first time I tried and hopefully installed Ubuntu LAMP Server.

I already had Ubuntu 7.04 on the desktop and added LAMP to it for the ZoneMinder software that requires LAMP.

When I enter Localhost in Firefox, it takes me to a login screen from there I see the following:
apache2-default/ folder and when I clock on it it says, "It works!"

Does that mean that I have successfully installed LAMP Sever?

How do I check the PHP & MySQL version installed?

Thanks.

---

### Post by mpeters on 2007-07-21
Create a file in your web root  with your favourite text editor and call it phpinfo.php and add the following lines:

```

<?php

echo phpinfo();

?>

```

Now open the file in your browser by accessing [http://localhost/phpinfo.php](http://localhost/phpinfo.php). If you see lots of information about your install that not only confirms your installation is working but should provide the information you need.

---

### Post by tombiz on 2007-07-21
How do I get the script up to the localhost directory? Can I FTP it?

---

### Post by mpeters on 2007-07-21
> **tombiz said:**
> How do I get the script up to the localhost directory? Can I FTP it?

If you have an FTP server appropriately set up, yes, however I doubt that is the case if you've just added LAMP to a desktop setup. The default web root is probably /var/www, you can check by running:

```
sudo grep -ir documentroot /etc/apache2/
``` 

on the box where your LAMP server is installed. This should show something like:

```
/etc/apache2/sites-available/default:   DocumentRoot /var/www/
/etc/apache2/sites-enabled/000-default: DocumentRoot /var/www/
```

where the last bit, /var/www in the above example, is where your web pages live. Copy the file to that directory locally:
```
sudo cp phpinfo.php /var/www/
```

---

