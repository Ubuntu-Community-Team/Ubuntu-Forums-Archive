---
title: "Issues with Virtual Hosts under Apache."
date: 2014-09-04
forum: Server Platforms
---

### Post by captangrypants2 on 2014-09-04
14.04 Server with a number of domains assigned to it.

All the domains were working fine a day or few a ago, tonight I found a few of the domains not working.  2 of the 3 it was a listing in .htaccess that was breaking them but the last one I am lost on.

I am getting error 404.
[B]
"Not Found[/B]
The requested URL /domainname.com/captangrypants/domainname.com/index.php was not found on this server."

If I go through the process of using a2dissite to remove the virtual host, I am greeted with this error.

**"Not Found**
 The requested URL /domainname.com/index.php was not found on this server."

Now if I a2dissite any of the other virtual hosts and attempt to hit the domain names, I am greeted with the file that is at /var/www/html/index.php
But this one will not default back to the root www directory.

I am at a lost at what would be still forcing this to go the /domainname.com/ directory even after it has been removed from configuration.

Any help would be wonderful.

---

### Post by volkswagner on 2014-09-05
> **captangrypants2 said:**
> 14.04 Server with a number of domains assigned to it.

Now if I a2dissite any of the other virtual hosts and attempt to hit the domain names, I am greeted with the file that is at /var/www/html/index.php
But this one will not default back to the root www directory.

I am at a lost at what would be still forcing this to go the /domainname.com/ directory even after it has been removed from configuration.

Any help would be wonderful.

Server 14.04 has some changes to Apache2.  The default directory is now " /var/www/html" not " /var/www".
A second change to 14.04, Apache2 expects vhost files to have .conf extension.

---

### Post by captangrypants2 on 2014-09-05
Thank you for the response.  I have check and redone both of these steps.  And yes all my domains and files are living under the /var/www/html directory and an all of the config files have .conf on them.  

But the issues remains.  Even when I a2dissite the .conf file for this domain and then delete the file completely.  When I go to the domain, I am not defaulted to the /var/www/html directory and its associated test index.html file.  I still receive a 404 error with "The requested URL /domainname.com/index.php was not found on this server."  It is like some config is persisting after the a2dissite and deleting of the file.

In the error logs I have found this
 /var/www/html/captangrypants/directory/domainname.com/.htaccess: Invalid command 'ddType', perhaps misspelled or defined by a module not included in the server configuration

This makes me thing there was something the .htaccess file that has left info behind.  But there is not any .htaccess files in any of the directories in the path to this domain now.

I have now removed all the domains and other files from /var/www/html, I have used a2dissite to remove the .conf files, I have deleted all the .conf files but the default, I have looked in the default and nothing referenced this domain, I have restarted apache many times, and I have restarted the server too.  All of these have not solved the issues.  I figure there is a config file or cache or similar somewhere that is holding onto the config.  But I have not enough experience to know the solution nor to know the correct terms to google for the solution.

---

### Post by volkswagner on 2014-09-06
I'm sorry, but I'm have a hard time determining the exact symptom.

Please post output of the following:

```
ls -al /etc/apache2/sites-available
ls -al /etc/apache2/sites-enabled
ls -al /var/www
ls -al /var/www/html
```

Additionally it will be helpful if you post the contents of your vhost files.

---

