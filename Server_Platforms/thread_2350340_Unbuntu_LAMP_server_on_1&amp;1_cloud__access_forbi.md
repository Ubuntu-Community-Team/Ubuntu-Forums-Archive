---
title: "Unbuntu LAMP server on 1&amp;1 cloud : access forbiden when launching a php file in brows"
date: 2017-01-23
forum: Server Platforms
---

### Post by steph38 on 2017-01-23
Hi,

I have setup a LAMP UBUNTU server on a 1&1 cloud server.
Apache is pointing to :
```
/srv/www/
lrwxrwxrwx root www-data
```
This folder contains a symbolic link 
```
mysite
```
pointing to my home folder
```
~/www-prod/mysite
drwxrwxr-x www-data www-data
```

To be really precise : I have also a shared (mutualized) server with 1&1 and my registrar (gandi.net) is pointing to 1&1 DNS.
I had to create a subdomain pointing to the cloud servers IP, which works.

I copied an Akeeba backup archive (Joomla!) into my folder :
```
~/www-prod/mysite
```
and also the kickstart.php file (permits the recovery of the backup)

When I try to access the kickstart.php file in my browser I get the following error :
```
Forbidden
You don't have permission to access /kickstrat.php on this server.
```

The apache vhost for mysite is pointing to ```
/srv/www/
```and is defined for mysite

What am I doing wrong ? have I missed something ?

Thanks in advance for your help and advise,
please also forgive me my English as it is not my mother language.
Best regards
Stéphane from France

I had an old account here on this forum but before UBUNTU ONE, had to create an other one.

---

### Post by TheFu on 2017-01-24
kickstart.php is not the same as kickstrat.php

See the typo?  Also, if those are just typos in the post here, then what are the permissions?

---

### Post by steph38 on 2017-01-24
> **TheFu said:**
> kickstart.php is not the same as kickstrat.php

See the typo?  Also, if those are just typos in the post here, then what are the permissions?

Hi TheFu,

Sorry just a typos error in the post...
what kind of permissions do you talk about ?

I have another problem now :
Have removed apache2 and php7.0 and reinstalled them to start clean from scratch...

Got an apache error now :

```
apache2_reload: apache2: Syntax error on line 140 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/mods-enabled/php7.0.load: Cannot load /usr/lib/apache2/modules/libphp7.0.so into server: /usr/lib/apache2/modules/libphp7.0.so: cannot open shared object file: No such file or directory
```
the apache2.conf error is not really a problem, but the missing libphp7.0.so is my problem...

Any idea how I could solve this ? maybe remove again and reinstall both ?
I am convinced that my uninstall of apache 2 and php 7.0 were not really clean...

Do you know how to remove them in a clean way ?

Thanks in advance for your help and advise,
Best regards,
Stéphane

---

### Post by TheFu on 2017-01-24
Unix is a multi-user OS.  Every file and directory has permissions that need to be correct. That is the owner, group, and rwx bits along with some other permissions bits.  You'll want to be fluent in this and understanding that all processes run under different userids/owners which control file access.  "ubuntu permissions tutorial" is the search for more knowledge.

Only 1 question per thread, please.

---

### Post by steph38 on 2017-01-24
Thanks TheFu,

I could solve my problem by removing totally Apache 2 and php 7.0, and reinstalling all afterwords.

Thanks for the help,
Regards,
Stéphane

---

### Post by TheFu on 2017-01-25
Wipe and reinstall didn't really teach much like how to avoid the issue next time.
But if it solved the issue this time and you are happy, fine.

---

### Post by steph38 on 2017-01-25
You're right, but sometimes the schedule is that sort that you have no other choice. I mean it is not a question of willing... or not

---

### Post by darkod on 2017-01-25
Please mark the thread as Solved in Thread Tools above the first post. That's the correct way...

---

