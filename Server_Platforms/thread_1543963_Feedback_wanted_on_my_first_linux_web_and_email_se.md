---
title: "Feedback wanted on my first linux web and email server"
date: 2010-08-01
forum: Server Platforms
---

### Post by cvandal on 2010-08-01
Hello,

I've just finshed putting together my first linux web and email server and would like some user feedback in regards to the way it was constructed.

01. Get all available updates: sudo apt-get update
02. Get all available upgrades: sudo apt-get upgrade
03. Install dbus: sudo apt-get install dbus
04. Install the LAMP stack: sudo tasksel install lamp-server
05. Secure MySQL: sudo mysql_secure_installation
06. Set the vps account as the owner of /var/www/: sudo chown -R vps /var/www/
07. Install phpMyAdmin: sudo apt-get install phpmyadmin
08. Install the Postfix MTA and the Dovecot MDA: sudo apt-get install dovecot-postfix
09. Install vsftpd: sudo apt-get install vsftpd
10. Configure vsftpd: sudo vi /etc/vsftpd.conf and uncomment write_enable=yes
11. Restart the vsftpd service: sudo service vsftpd restart
12. Get the latest stable release of RoundCube: [http://www.roundcube.net/download](http://www.roundcube.net/download)
13. Upload RoundCube to: /var/www/roundcube
14. Browse to: [http://www.website.com/roundcube/installer](http://www.website.com/roundcube/installer) and follow the steps.

I'd say this is a very simple and straight forward way to get everything up and running quickly. No problems have encountered yet *fingers crossed*.

---

### Post by inphektion on 2010-08-01
Can you live without phpmyadmin?
I only ask cause i'm not sure what great benefit it gives (i've never used it) but i do know in all my server logs I frequently see attacks or exploits where the script kiddie is trying to hit various things off phpmyadmin.  

So if you need it lock it down like mad.  htpasswd, apparmor apache, etc.

---

### Post by cvandal on 2010-08-01
> **inphektion said:**
> Can you live without phpmyadmin?
I only ask cause i'm not sure what great benefit it gives (i've never used it) but i do know in all my server logs I frequently see attacks or exploits where the script kiddie is trying to hit various things off phpmyadmin.  

So if you need it lock it down like mad.  htpasswd, apparmor apache, etc.

I could live with out it however my command line skills are quite lacking and so phpmyadmin helps me a lot when creating and managing my databases.

---

### Post by Sporkman on 2010-08-02
> **cvandal said:**
> I could live with out it however my command line skills are quite lacking and so phpmyadmin helps me a lot when creating and managing my databases.

One thing you can do is install phpmyadmin outside of your served document root, then just place a symbolic link to it from within your document root when you want to use it.

Then, when you're done for the time being, delete the link.

---

