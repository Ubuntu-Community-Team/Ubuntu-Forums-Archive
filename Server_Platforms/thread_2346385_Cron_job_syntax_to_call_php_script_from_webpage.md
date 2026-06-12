---
title: "Cron job syntax to call php script from webpage"
date: 2016-12-14
forum: Server Platforms
---

### Post by grcm59 on 2016-12-14
Hi,

On one of my wordpress websites I have a plugin that needs 3 cronjobs periodically.
The plugin developer has a page on how to do this but using this results in an error that the script could not be opened.
The cli I use is wget -O /dev/null [http://domainname/wp-content/plugins/pluginname/auto.php](http://domainname/wp-content/plugins/pluginname/auto.php)
below is the error I get when the job fails:
--2016-12-14 14:40:27-- [http://domainname/wp-content/plugins/pluginname/auto.php](http://domainname/wp-content/plugins/pluginname/auto.php)
HTTP-request send; waiting for reply... 403 Forbidden
2016-12-14 14:40:27 Error 403: Forbidden.

I changed the cli to, that is how other cronjobs are setup and working

/usr/bin/php /var/www/vhosts/domainname/wp-content/plugins/pluginname/auto.php

Now the error is 

Could not open input file: /var/www/vhosts/domainname/wp-content/plugins/pluginname/auto.php

My cron user is root.

How can I solve this so I can run my cronjobs and use the plugin?


Regards,

Gerhard

---

### Post by Irihapeti on 2016-12-14
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-12-14
When you get the "Forbidden," do you see a corresponding entry in the site's logs that gives more details?

In the second case I presume the script actually resides at the location specified?  That's clearly the correct location if the plugin was installed according to WP's standards.  What are the permissions on the script and all directories above it?  Does it work if you run the command 
```
/usr/bin/php /var/www/vhosts/domainname/wp-content/plugins/pluginname/auto.php
```
from the prompt?

---

### Post by grcm59 on 2016-12-14
Hi,

Thanks for the response. For some unknown reason SSH is not allowing connections. Maybe has to do with some security upgrade. They did have an upgrade couple of weeks back.
I asked my provider to check on that and when it is fixed I will check on the command line.
Plugin is installed via the installer within this WP installation, I am using the latest version of Wordpress.
Server runs more than 1 website and for at least 1 other web application cron jobs work fine.
This is a VPS and I have full control over the server.

---

### Post by grcm59 on 2016-12-16
I have some more information on the errors generated. Managed to get my SSH access back up again.

**Using the original command**
wget -O /dev/null [http://domain/wp-content/plugins/plugin/auto.php](http://domain/wp-content/plugins/plugin/auto.php)

**Results in**
                                   Forbidden
   You do not have permission to access this document.
   __________________________________________________________________
   Web Server at domain
   
[B]
Using the following command[/B]

/usr/bin/php /var/www/vhosts/domain/httpdocs/wp-content/plugins/plugin/auto.php

**This is the result**
PHP Warning:  require(../../../wp-blog-header.php): failed to open stream: No such file or directory in /var/www/vhosts/domain/httpdocs/wp-content/plugins/plugin/auto.php on line 3
PHP Warning:  require(../../../wp-blog-header.php): failed to open stream: No such file or directory in /var/www/vhosts/domain/httpdocs/wp-content/plugins/plugin/auto.php on line 3
PHP Fatal error:  require(): Failed opening required '../../../wp-blog-header.php' (include_path='.:') in /var/www/vhosts/domain/httpdocs/wp-content/plugins/plugin/auto.php on line 3

The file required is present in the installation

---

### Post by SeijiSensei on 2016-12-16
But maybe the relative directory path is not correct?  What if you edit auto.php manually and specify an absolute directory path to wp-blog-header.php?

---

### Post by Graham_Willis on 2016-12-16
It's also interesting if this file exists at all. @grcm59: check that.

---

