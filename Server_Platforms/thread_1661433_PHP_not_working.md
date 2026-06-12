---
title: "PHP not working?"
date: 2011-01-06
forum: Server Platforms
---

### Post by themarker0 on 2011-01-06
So i got my server up, installed FTP and all those goodies. And then i got some fun. Index.HTML shows perfectly. But when i place an Index.PHP, i get nothing at all.

I get this error actually


Server error.

The website encountered an error while retrieving [http://192.168.1.102/](http://192.168.1.102/). It may be down for maintenance or configured incorrectly.

Here are some suggestions:
Reload this web page later.
  More information on this error


? Where did i screw up?

---

### Post by James78 on 2011-01-06
Need more information. These types of errors are usually logged in the Apache error log, so... Check /var/log/apache2/error.log. If you have a custom VirtualHost with an ErrorLog directive, use the log file it's poiting at instead.

---

### Post by themarker0 on 2011-01-06
> [Wed Jan 05 23:23:44 2011] [error] [client 192.168.1.103] File does not exist: /var/www/favicon.ico
[Wed Jan 05 23:24:01 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Wed Jan 05 23:24:01 2011] [error] [client 192.168.1.103] PHP Fatal error:  Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Wed Jan 05 23:25:28 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Wed Jan 05 23:25:28 2011] [error] [client 192.168.1.103] PHP Fatal error:  Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Wed Jan 05 23:25:28 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Wed Jan 05 23:25:28 2011] [error] [client 192.168.1.103] PHP Fatal error:  Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] PHP Fatal error:  Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] PHP Fatal error:  Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] File does not exist: /var/www/favicon.ico
[Wed Jan 05 23:25:29 2011] [error] [client 192.168.1.103] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
                                                                                                                                           1,1           Top





That is what i have.

---

### Post by James78 on 2011-01-06
It looks like your problem is permissions related. Please execute this command and list the output.
```
ls -l /var/www/
```
In general however, you need to make sure that apache has access to your file. It needs to be owned by www-data and be at very least 644 permissions.```
cd /var/www
sudo chmod 644 index.php
sudo chown www-data. index.php
```

---

### Post by themarker0 on 2011-01-06
```
-rw------- 1 mark mark  2905 2011-01-05 23:23 CHANGELOG
drwx------ 8 mark mark  4096 2011-01-05 23:23 cms
drwx------ 2 mark mark  4096 2011-01-05 23:23 files
-rw------- 1 mark mark  5134 2011-01-05 23:23 index.php
-rw------- 1 mark mark   878 2011-01-05 23:23 INSTALL
drwx------ 2 mark mark  4096 2011-01-05 23:23 js
-rw------- 1 mark mark 32472 2011-01-05 23:23 LICENSE
drwx------ 3 mark mark  4096 2011-01-05 23:23 media
lrwxrwxrwx 1 root root    22 2011-01-05 21:42 phpmyadmin -> /usr//share/phpmyadmin
-rw------- 1 mark mark   255 2011-01-05 23:23 README
drwx------ 5 mark mark  4096 2011-01-05 23:23 templates

```

is what i get, i ran the chmods you asked, and nothing showed.

---

### Post by James78 on 2011-01-06
That's because you have more than 1 file in /var/www. :) We'll just recursively apply the required permissions.
```
find /var/www -type d | sudo xargs chmod 755
find /var/www -type f | sudo xargs chmod 644
sudo chown -R www-data. /var/www
```
In the future, make sure all files and directories have these permissions and ownerships.

Directories: 755
Files: 644
ALL: owned by www-data

---

### Post by smo0th on 2011-01-06
sudo chown -R +r /var/www

---

### Post by CharlesA on 2011-01-06
If this is just a test/dev server, I would suggest creating a virtualhost and pointing the DocumentRoot to a folder in your home directory. That way you don't have to worry about permission problems (that is unless your home directory is unencrypted, and if that was the case, you can just point it elsewhere.

```

charles@lucid:~$ cat /etc/apache2/httpd.conf
<VirtualHost *:80>
DocumentRoot /home/charles/site/
</VirtualHost>

```

Also, be careful when using -R with chown and chmod. It can cause more headaches then not.

---

