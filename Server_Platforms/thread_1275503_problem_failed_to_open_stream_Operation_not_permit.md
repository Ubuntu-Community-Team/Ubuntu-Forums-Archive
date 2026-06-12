---
title: "problem: failed to open stream: Operation not permitted"
date: 2009-09-25
forum: Server Platforms
---

### Post by cybershan on 2009-09-25
I just install ubuntu server 9.04 with LAMP, it works.

but when I install Drupal software, it shows below error:

####

Warning: fopen(./sites/default/settings.php) [function.fopen]: failed to open stream: Operation not permitted in /var/www/drupal614/includes/install.inc on line 236

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal614/includes/install.inc:236) in /var/www/drupal614/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /var/www/drupal614/includes/install.inc:236) in /var/www/drupal614/includes/install.inc on line 619

###

I believe it's my server setting problem,  but I have no ideas.

Anybody can help me out?

Thanks in advance. 
:confused::confused::confused:

---

### Post by cariboo on 2009-09-26
Seeing as you are little short on information, I would suggest you check the [Official Guide]("http://drupal.org/getting-started/install") to see if you have missed something.

Please don't double post on the same subject.

---

