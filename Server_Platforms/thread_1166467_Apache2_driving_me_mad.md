---
title: "Apache2 driving me mad"
date: 2009-05-21
forum: Server Platforms
---

### Post by ant284 on 2009-05-21
Hi,
 
I have tried everything for the last two days looking over the web anyways, 
I have Ubuntu that uses apache2... I had a problem with it and deleted a file apache2 in /etc/init.d 
anyways I need to re-install it, i tried download it manually and install it but i had to use httpd to start and I lost the folder /etc/apache2 (because I deleted all the old apache2) 
anyways
I would like to do ap-get install apache2, but i get this
>>Reading package lists... Done
>>Building dependency tree
>>Reading state information... Done
>>apache2 is already the newest version.
>>0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
But I have delted everything to do with apache2 I'm really Lost any help would be appreciated 
 
Thank You!!

---

### Post by BkkBonanza on 2009-05-21
Try the --reinstall option.

apt-get --reinstall install apache2

See if that fixes things up again. If not you may have to manually edit the apt-get cache settings. I've fixed this type of mess before manually by removing apt config files but it is tricky and may screw something up. Better if the above command will work.

---

### Post by ant284 on 2009-05-22
Hi,
 
I tried it before and it never worked, how would I delete manually with the apt cache?
 
thank you

---

### Post by ant284 on 2009-05-22
Hi,
 
I managed to fix the problem 
I used 
sudo aptitude remove .....  
but I had to re-install 
mpm-event
mpm-prefork
so I could uninstall
mpm-worker, then apache2.2-common then uninstall apache2 
 
then managed to install everything back

---

