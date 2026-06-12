---
title: "Ubuntu 12.04 &amp; 13.04: PHP-FPM Ignoring Memory_Limit"
date: 2013-09-03
forum: Server Platforms
---

### Post by thomas-m-beaver on 2013-09-03
Hello ):P

I am currently running Ubuntu 13.04, NGINX, PHP-FPM. I was previously running Ubuntu Server 12.04 with Apache 2.2 with FPM with the same issue. Upon upgrade the problem did not go away. I am now revisiting the problem since my site is growing larger and needs the extra memory.

I have configured my php.ini under /etc/php5/fpm/php.ini to show memory_limit = 256M instead of memory_limit = 128M. I restart PHP-FPM and then NGINX for good measure. However, when I check info.php it still shows 128M as the memory limit. suhosin memory limit is also set to 256M and the problem even occurred before suhosin was installed. So I know this is not the problem. If I remove the php.ini (I.E mv php.ini php.old) and reload PHP-FPM the info.php file says (Not Loaded) or something. When I move it back it says it's loaded from /etc/php5/fpm/php.ini which is the exact file that I changed the memory_limit to 256M in. I did a complete uninstall and purge of PHP-FPM and reinstalled. Same problem. All of my .ini's in conf.d are just to load modules and only include 
*.so configs.

I even tried to set the memory limit to 64M in php.ini just to test, the 128M in info.php remained.

After countless hours of reboots, reloads, various config changes, Google searches, etc. I am at my wits end. Has anyone else experienced this issue that has an actual solution? Reinstalling the server is not an option.

---

