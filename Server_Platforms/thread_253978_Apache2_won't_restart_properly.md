---
title: "Apache2 won't restart properly"
date: 2006-09-09
forum: Server Platforms
---

### Post by CzarAlex on 2006-09-09
When I make some changes to apache2.conf and upload them to my server via ssh, I then restart the apache2 service but get this:

czar@queeg500:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...
httpd (pid 8268) already running
   ...done.
czar@queeg500:~

Tis new for me as ive been fiddling with the .conf file for the last week. Changes have worked and i didnt get that message about the httpd process already running. If I reinstate a backup of apache2.conf (without uploading it. i just renamed it to apache2.conf_BACKUP in the same dir) it`ll restart just fine. Im not making any major changes, just redirecting a virtual host from /var/www to /var/www/site and it wont take. Suggestions?

---

### Post by mssever on 2006-09-10
Try
```
sudo apache2ctl stop
ps -ef | grep apache
# If any instances of apache still show up, kill them (x = the numerical pid of the apache process
sudo kill x
sudo apache2ctl start
```
If you still get errors, look in /var/log/apache for errors.

By the way, the canonical way to control apache is by using apache2ctl.

To restart Apache, I prefer ```
sudo apache2ctl graceful
```.

---

