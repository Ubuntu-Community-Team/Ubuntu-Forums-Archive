---
title: "PHP files get downloaded"
date: 2018-05-31
forum: Server Platforms
---

### Post by mao_dze_dun on 2018-05-31
[SOLVED] I found the fix for this here [URL="https://www.virtualmin.com/node/57240"]https://www.virtualmin.com/node/57240

[/URL]SOLUTION
  In  "/etc/apache2/mods-enabled/php*.conf" (replace php* with  your filename, depending on the php version you're using - in my case it  was php7.2.conf) comment out the following two lines:
  SetHandler application/x-httpd-php
  SetHandler application/x-httpd-php-source
  Restart the apache server via the following command:
  sudo service apache2 restart
  Now set your webstite to FCGId (Virtualmin -> Server Configuration  -> Website options -> PHP script execution mode ) and it should  work properly.


ORIGINAL POST


Hello,
I bought a VPS a from OVH a few days back and opted to install Ubuntu along with Virtualmin. I'm a complete noob to this, but using the magical power of Google I got around to settings the basic things up, pointing my domain to the server etc. However, I have one big problem. I used Virtualmin's integrated script to install Wordpress, everything seemed fine until I went to the actual domain, expecting to see the familiar Wordpress install screen. Unfortunately, my browser just asked me where to save the install.php file. I checked google for solutions and from what I can tell it's some apache related problem, but all the workarounds I've found are NOT for Ubuntu. Can anybody tell me what the solution for an Ubuntu Server would be. I feel really stupid - being stuck at the last step before being able to launch a website :).
Thanks in advance.

---

### Post by LHammonds on 2018-05-31
If Apache is wanting to send the .php file to you as a downloadable file, then that means you do not have PHP installed/associated with Apache so it simply does not know how to process .php files on the server.

On an Ubuntu Server 16.04 LTS server, I would install Apache and PHP like this:
```
sudo apt-get install apache2 php7.0 libapache2-mod-php7.0
```

On an Ubuntu Server 18.04 LTS server, I would install Apache and PHP like this:
```
sudo apt install apache2 php7.2 libapache2-mod-php7.2
```

LHammonds

---

### Post by mao_dze_dun on 2018-05-31
Guess I missed something. I'm positive php is installed, because after I posted, I managed to find the setting in Virtualmin and switched from FCGid to mod_php to and now everything works fine, now. However, I know FCGid is more convenient for Wordpress sites, so obviously this is not ideal.

---

### Post by SeijiSensei on 2018-06-01
I just use
```
sudo apt install lamp-server^
```
and get MySQL as an added bonus.

---

