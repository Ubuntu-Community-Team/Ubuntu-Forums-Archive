---
title: "permissions etc"
date: 2011-01-28
forum: Server Platforms
---

### Post by Yvkaya on 2011-01-28
I'm setting up an Ubuntu server where I'd like to host several Wordpress-based sites which were originally on a temporary Windows XP based server (using xampp). Now I run into permission-troubles moving those sites to the Ubuntu server, using CoreFTP, so I hope someone can help me: 

1. Moving wordpress files from Windows to linux. I can't seem to move the entire wordpress folder from xampp/htdocs to /var/www, using CoreFTP. How to solve the permission problems so I can write to that directory without causing security issues?

2. Or, do I need to install a new wordpress-site into /var/www and import a backup I made on the windows machine? 

3. Does Linux use another encryption system when it comes to SQL passwords? I did a test and when I import a sql-database from windows with phpmyadmin (based on the ubuntu server) I can't seem to login with a test site I made. It works when exporting/importing between windows-environments. 

Thanks in advance

---

### Post by Celauran on 2011-01-28
By default, you won't have write permission to /var/www.  Copying the wordpress directories to your home directory and then 'sudo mv'-ing to /var/www is probably your best bet.

Insofar as the MySQL issues, have you set up your user in MySQL?  What errors are you getting?

---

### Post by Yvkaya on 2011-01-30
Thank you for your reply. I discovered another problem though and I can't figure out why it happened. For some reason I don't have permissions to write anything to the homedirectory. 

That's the first problem I need to solve...

About Mysql: I already had an administrator account on the windows machine. But when importing to the linux server I can't log into the site. I guess it can't read the login information because it seems to be working with another string? In other words: I can't use my old admin account and need to setup a new user in mysql when I switch the database to linux. 

I was wondering why that is, since I have all the administrator login information which worked in the windows installation. When switching between windows machines the 'problem' doesn't occur.

---

