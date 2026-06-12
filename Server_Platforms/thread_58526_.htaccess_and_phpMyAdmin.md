---
title: ".htaccess and phpMyAdmin"
date: 2005-08-20
forum: Server Platforms
---

### Post by KupernikuZ on 2005-08-20
UPDATE: Solved.

I had some problems with MySQL, that caused the problem, so it was'nt Ubuntu.

Original post:
I am running  Linux 2.6.8.1-5-686 #1 Tue Jun 14 22:55:54 UTC 2005 i686 GNU/Linux
with a Apache 2.0.50 webserver and a SQL server installed and so on. 
Im hosting 3 domains on the server so i'm using virtual hosts on my apache.

So. Now I have downloaded the latest phpmyadmin and untared it into a root on one of my domains web-root. It is in the dir called: /var/www/domain3/
I have renamed the dir from phpmyadmin-x.x.x-pl blah blah to 'pma' and did that recirsive.

Then I've made a file in that directory called .htaccess and a file called .htpasswd and a file called .htgroups

The .htaccess contains:
[PHP]AuthUserFile /var/www/domain3/pma/.htpasswd
AuthGroupFile /var/www/domain3/pma/.htgroups
AuthName "Secure Area"
AuthType Basic
require group editors
[/PHP]

The .htgroups contains:
[PHP]editors: bob dan george[/PHP]

The .htpasswd is made by ading passwords to a user. The file is made automaticly.

So....

Then i'm accessing it from the web: [www.domain3.xx/pma](www.domain3.xx/pma)
A popup is comming, asking for username and password.
Thats great... BUT!!!...
I'm typing a username, bob, and his password i gave him. Nothing happens. Then I tried just typing the username, WITHOUT typing the password, an I now see the phpMyAdmin site, but without some privileges.

Can someone help me?
Why can I login to the admin hust typing some letters in the username, without typing some existin users on the server and without typing password?

I tried this installation on a RedHat9 and there it works, but not on my Ubuntu. 

 ](*,)

---

