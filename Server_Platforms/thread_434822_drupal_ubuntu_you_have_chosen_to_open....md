---
title: "drupal ubuntu you have chosen to open..."
date: 2007-05-06
forum: Server Platforms
---

### Post by rogue35 on 2007-05-06
Hi all, I am a total noob on webservers, I am running feisty LAMP with ubuntu-desktop, I have downloaded and extracted Drupal 5.1,  but when I go [http://localhost/drupal](http://localhost/drupal) I get the following error (this is the same for Joomla) you have chosen to open which is a PHTMLfile from [http://localhost](http://localhost) what should firefox do with this file? Open with or save to disk...

Any help would be greatly appreciated.

---

### Post by EmmEff on 2007-05-06
This would indicate that you do not have PHP5 enabled in Apache...  or perhaps you forgot to restart Apache after installing PHP.  Make sure you have libapache2-mod-php5 installed and have restarted Apache since it was installed.

---

