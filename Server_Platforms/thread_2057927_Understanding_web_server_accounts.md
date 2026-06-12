---
title: "Understanding web server accounts"
date: 2012-09-14
forum: Server Platforms
---

### Post by allegrauser on 2012-09-14
I have installed ubuntu server a year ago. I have been accessing it via http by typing in my ip address and then the name of a directory in the var directory ([http://192.168.1.28/mysite/](http://192.168.1.28/mysite/)). I want to setup a ftp account as a test server for Dreamweaver. If I login via ftp and my Ubuntu user name and password it takes me to an account directory on the server (home/user_directory). However I cannot access that via http as it is not in the var directory. How do I set this up right?

---

### Post by TheFu on 2012-09-14
> **allegrauser said:**
> How do I set this up right?

I believe this is setup correctly, for certain values of "right."

Could you be more explicit with exactly what you hope to do and specifically how you want to do it?

FTP is not HTTP.
HTTP is not FTP.
SFTP is not HTTP - it is better.
ssh is not telnet, vnc, rdp, but it is better in many, perhaps even most, situations.

The way these directories behave is completely under your control as the administrator.  By default, it is not open for anyone in the world to write into the static web page directories. This is due to security concerns.

The best way manual way to move files to any web server is through **sftp** or **scp**.  A nice MS-Windows client for that is **WinSCP**.  Using **rsync over ssh **is the best practice for any sized business and allows 100% automatic updates for static web content after optimization on the different "web asset" files is performed.  Things like stripping and compressing JS, CSS, and HTML files, optimizing image files for web distribution, merging files into fewer so that download pipe-lining works better, things like that.

Anyway, I took a stab at your issue. Hopefully the information is helpful.

---

### Post by SeijiSensei on 2012-09-14
By default the DocumentRoot in Ubuntu is /var/www, but it doesn't need to be that.  You could put the site underneath /home/username as long as the www-data user that the Apache server runs under can read the files there.  For security reasons, users' home directories are set to grant permissions only to the users themselves.  You can fix this by running "sudo chmod 711 /home/username".  It would then be possible to use FTP, SFTP, etc., to transfer files as "username".

Another option is to create a user to own the web site.  I usually create a "web" user and put the site in /home/web/public, and any PHP includes in /home/web/include, again after running "sudo chmod 711 /home/web".

Take a look at the /etc/apache2/sites-available/default.  The DocumentRoot is the determining factor.  Notice there is also a <Directory> stanza that applies options to the DocumentRoot.  You would need to change that to match.

A better solution is to make a copy of /etc/apache2/sites-available/default and call it /etc/apache2/sites-available/mysite.  Add a ServerName directive that matches the computer's hostname.  Do whatever you want to the configuration in that file, then run "sudo a2ensite mysite" to make the site active.  Then restart Apache with "sudo service apache2 restart".  You should be able to navigate to [http://hostname/](http://hostname/) and see your new site appear.  

Also read [https://help.ubuntu.com/12.04/serverguide/web-servers.html](https://help.ubuntu.com/12.04/serverguide/web-servers.html)

Reading the Server Guide before asking questions here helps us all.

---

