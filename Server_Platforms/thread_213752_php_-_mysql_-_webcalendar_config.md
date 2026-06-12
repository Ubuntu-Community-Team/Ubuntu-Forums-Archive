---
title: "php - mysql - webcalendar config"
date: 2006-07-11
forum: Server Platforms
---

### Post by jackdaw on 2006-07-11
I am in the process of installing Webcalendar on Dapper server. I first tried a simple apt-get install webcalendar, but had a lot of issues with mysql during the webcalendar setup phase. As it turned out, although it appeared that apt-get installed mysql-server and mysql-client, there was no daemon running after the install and indeed, no evidence of either package. So I apt-got mysql-server and client, that solved the inability to connect to mysql.sock issue. 
	Also during the setup it puked when I gave it the requested database admin password. Solved that one by creating the database first and adding the appropriate user/password. My current problem is that when I go to launch Webcalendar by going to the appropriate ip address/install/index.php, the “test database” reports no errors, but when I hit “Launch Webcalendar” I get “Could not find db_type defined in your /etc/webcalendar/settings.php file.” In fact there was no settings.php in /etc/webcalendar. So for grins I tried copying the only two settings.php I could find, but no surprise, neither worked (one was a template and the other actually contained the appropriate settings). 
	This is my first foray into the LAMP world. ( I also tried doing a LAMP install, but that installs php5, and according to what I've read, webcalendar does not work with php5.)  
	I use webcalendar every day for my business and really like it, so I'd like to be able offer it to my clients (that and I like the challenge!). Any suggestions welcome!

---

### Post by az on 2006-07-11
I find that most of the web applications in the repositories are too old.

The latest version of webcalendar runs on php5

[http://webcalendar.cvs.sourceforge.net/*checkout*/webcalendar/webcalendar/docs/WebCalendar-SysAdmin.html#requirements](http://webcalendar.cvs.sourceforge.net/*checkout*/webcalendar/webcalendar/docs/WebCalendar-SysAdmin.html#requirements)

You probably will have more success installing LAMP in Dapper and then getting the latest version of webcalendar directly from the site.

---

### Post by jackdaw on 2006-07-12
man...one more dapper lamp install, a little config and it's up and running! thanks!

---

