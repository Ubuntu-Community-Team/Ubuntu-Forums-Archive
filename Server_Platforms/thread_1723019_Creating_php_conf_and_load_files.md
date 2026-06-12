---
title: "Creating php conf and load files"
date: 2011-04-06
forum: Server Platforms
---

### Post by cmnorton on 2011-04-06
I need to create .conf and .load files for php. PHP is installed and I've verified PHP with test.php <?php
print_r (phpinfo());
?>

Is there boilerplate available for creating the .load and .conf files? I am having trouble finding it in what's been installed.

Thanks.

---

### Post by SeijiSensei on 2011-04-06
As a *long*-time PHP user, I must admit I haven't the foggiest idea what a .conf or a .load file might be.  PHP's configuration is managed by php.ini.  Care to point to an example of what you're asking about?

---

### Post by cmnorton on 2011-04-06
I finally figured it out. 

For some reason with Ubuntu 10.04 Apache's directories got sub-divided. You used to put a load module command directly into the httpd.conf or apache2.conf. No more; you're expected to drop modules, .conf and .load into /etc/apache2/mods-available and soft links created in /etc/apache2/mods-enabled. The .conf file might contain configuration information if needed. The .load file contains the LoadModule directive.

---

### Post by SeijiSensei on 2011-04-06
> **cmnorton said:**
> For some reason with Ubuntu 10.04 Apache's directories got sub-divided.

Oh, **those** .conf and .load files.  I see them as part of Apache.

---

