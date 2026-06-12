---
title: "phpmyadmin"
date: 2006-08-16
forum: Server Platforms
---

### Post by statue on 2006-08-16
I am trying to restrict remote access to phpmyadmin via port 80. Im trying to achieve this by using these vaules in /var/www/phpmyadmin/config.inc.php :

$cfg['Servers'][$i]['AllowDeny']['order'] = 'allow,deny';
$cfg['Servers'][$i]['AllowDeny']['rules'] = array('allow % from localhost');         

supposedly this should work but I have spent hours messing with the different values and yet nothing seems to be working....please help...so tired.


UPDATE: I achieved the effect I wanted, just used the directory option in apache's config to request user/pass.

---

