---
title: "HOWTO: Installing Mambo"
date: 2006-02-11
forum: Server Platforms
---

### Post by atoponce on 2006-02-11
This is a brief HOWTO on setting up a [Mambo-powered]("http://www.mamboserver.com/") CMS site.  I was able to get [The Ogden Area Linux Users Group]("http://www.oalug.com/") up in less than 20 minutes. 

Before beginning, you will need your domain setup through Apache as the installation of Mambo is web-based. PHP will also need to be installed and working. Finally, you will need a working MySQL database server. 

```
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
``` 

Restart Apache:

```
sudo /etc/init.d/apache2 restart
```

1. Grab the latest stable release, [MamboV4.5.3.zip]("http://www.mamboserver.com/MamboV4.5.3.zip") and place in any directory. 

2. Unzip the package and copy to your web server directory (E.G. /var/www): 

```
unzip -d Mambo MamboV4.5.3.zip
sudo mv Mambo /var/www 
``` 
3. Make the following directories in the Mambo folder writeable using chmod: 

administrator/backups/
administrator/components/
administrator/modules/
administrator/templates/
cache/
components/
images/
images/banners/
images/stories/
language/
mambots/
mambots/content/
mambots/search/
media/
modules/
templates/ 

EG:
```
sudo chmod a+w administrator/backups/
``` 
4. Create a file called configuration.php inside the Mambo direcotry and make it writeable as well using the chmod example above. 

```
cd Mambo
touch configuration.php
chmod a+w configuration.php
``` 
5. Navigate to the installation directory using your web browser:[http://localhost/Mambo/installation]("http://localhost/Mambo/installation") 

The first page of the Web Installer will do a quick preconfiguration check to make sure everything is running and working on your system. For those checks that pass, they will be highlighted in green, for those that don't, they will be in red. Make sure everything is green before continuing. When you are ready, click the "Next" button at the top right of the page. 

The first page will be the lisence.  After reading and accepting the terms of the lisence, click on "Next". 

There are only 4 steps to installing Mambo as follows: 
Step 1:[LIST]
[*] Provide the name of your host.  Generally, localhost works just fine here.
[*] Enter your MySQL username and password and verify that password. Generally, this is not your user account on the server. Check with your server admin for this information.
[*] Enter a MySQL database name for the site. Mambo is completely database driven, so a name is required. The database name Mambo works just fine. Warning: make sure you don't type a database name that is already used.
[*] Enter a prefix for each table in the database.  By default, "mos_" is used.
[*] The 3 check boxes don't need to be changed from their default for first time installs. If installing Mambo a second time, you can drop the existing tables, and backup the old tables if needed.[/LIST]Once the data is entered, press "Next" to continue. 
Step 2:[LIST]
[*] Give your site a name.  This can be anything you want to refer to your site by.[/LIST]Press "Next" to continue. 
Step 3:[LIST]
[*] Provide the root path URL that will be accessed when users access the site.  In other words, if you want users to go to [http://www.example.com]("http://www.example.com/"), then your root path needs to be inside the Mambo folder ([http://www.example.com/Mambo]("http://www.example.com/Mambo")).
[*] Give the local directory on your server where the Mambo files reside.
[*] Provide your email address
[*] Type a password for the administrator account, or use the random password already generated.
[*] Edit file and directory permissions as needed.[/LIST]Press "Next" to continue. 
Step 4:[LIST]
[*] As mentioned, completely remove the installation directory. You will no longer need it, and it presents a security hole if it remains.[/LIST]Congratulations!  You are finished installing Mambo.

---

### Post by woland on 2006-03-27
Great guide, thanks!

There is one problem thou. I have problem with my database.
When I try to view some or all content items, I get the following error message:> DB function failed with error number 1054
Unknown column 'c.access' in 'on clause' SQL=SELECT c.*, g.name AS groupname, cc.name, u.name AS editor, f.content_id AS frontpage, s.title AS section_name, v.name AS author FROM mos_content AS c, mos_categories AS cc, mos_sections AS s LEFT JOIN mos_groups AS g ON g.id = c.access LEFT JOIN mos_users AS u ON u.id = c.checked_out LEFT JOIN mos_users AS v ON v.id = c.created_by LEFT JOIN mos_content_frontpage AS f ON f.content_id = c.id WHERE c.state >= 0 AND c.catid=cc.id AND cc.section=s.id AND s.scope='content' AND c.sectionid='4' ORDER BY cc.ordering, cc.title, c.ordering LIMIT 0,10
Another thing, probably related, in text edit from the frontend I cant choose any categories.

Using Mambo 4.5.3, MySQL 5.0.18-8.1, PHP 5 
I've tried deleting the entire database and restaring te whole site, but it wouldn't help. What else can I do?

---

### Post by Velvet Elvis on 2006-03-27
Any reason you're sticking with Mambo rather than following the codebase to Joomla?

---

### Post by woland on 2006-03-28
Never heard of it before, but I like it more, thanks.
It's seems faster and doen't have that MySQL bug.

---

### Post by Akli on 2006-03-31
Before going to step 1, you need to create a database:

sudo mysql

create database mydatabase;
GRANT ALL ON mydata.* TO username@localhost IDENTIFIED BY "password"

that's it, you've got your 

-database name : mydatabase
-your username : username
-your password : password

---

### Post by LordHunter317 on 2006-04-01
***This guide has MAJOR security issues and should not be used.***

[QUOTE=atoponce]Restart Apache:```
sudo /etc/init.d/apache2 restart
```[/quote]This is totally unnecssary at this point.

> ```
sudo chmod a+w administrator/backups/
``` ***No.  The whole world does not need write access to these directories.  This command is dangerous and a security issue.***

> 4. Create a file called configuration.php inside the Mambo direcotry and make it writeable as well using the chmod example above. The exact same thing applies above.

---

### Post by woland on 2006-04-01
I agree. 
I chown-ed these files to user **www-data** and chmod-ed to 544, exept for 744 for the listed directories.

---

### Post by mailo on 2006-07-11
> **woland said:**
> Great guide, thanks!

There is one problem thou. I have problem with my database.
When I try to view some or all content items, I get the following error message:
Another thing, probably related, in text edit from the frontend I cant choose any categories.

Using Mambo 4.5.3, MySQL 5.0.18-8.1, PHP 5 
I've tried deleting the entire database and restaring te whole site, but it wouldn't help. What else can I do?


Hi, there is a work around for that error. First auf all which DB did you use, mysql 5, then go on. 
On mysql5 the joining of tables has other rules... you can can change 2 lines for a working mambo :-)

> 
file: admin.content.php line 201
old: . "\n FROM , #__content AS c, #__categories AS cc, #__sections AS s"
new: . "\n FROM #__categories AS cc, #__sections AS s, #__content AS c "

simply move the content AS c to the end.
> 
also: Line 312 on the same file
old: . "\n FROM , #__content AS c, #__categories AS cc, #__sections AS s"
new: . "\n FROM #__categories AS cc, #__sections AS s, #__content AS c "


This is original from [forum.mamboserver]("http://forum.mamboserver.com/showthread.php?t=65497")

---

### Post by az on 2006-07-11
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by mailo on 2006-07-11
For that changing, you will not be able to login in to your mamboo administration. You must give an execute flag for all.

So chmod 555 for the Directories works fine.

Marc

---

