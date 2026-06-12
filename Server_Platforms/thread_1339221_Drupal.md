---
title: "Drupal"
date: 2009-11-27
forum: Server Platforms
---

### Post by seabag on 2009-11-27
I have read extensively regarding Mysql but I still cant get a running server. I go to phpMyaDmin and it has my username and password (I put no password in while installing) I click on go and get error # 1045-Access-denied for user acme@localh phpMyaDmin using password yes. I go back to phpMyaDmin delete the password and the up it comes. I type localhost in the title bar and get it works, I type 127.0.0.1 and get it works. I got to Drupal database configuration and the mysql button in highleted, database name is blank, database username is filled using acme, database password is filled in but I did not enter any password at the install. I just don't know how to do the daterbase name. I have read many how to's but they stop at the database configuration. I am using 8.04

---

### Post by KayakJim on 2009-11-27
It sounds as though you do have an operational mysql server. To verify, open a terminal and type:
```
mysql -u root mysql
```
enter the password for the root mysql user when prompted and you should see a prompt similar to:
```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1753297
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
```
If so, then you definitely have mysql server running properly. If that is the case, then ensure you have created a database and proper user account to access that database.

To create the database while still at the "mysql>" prompt enter:
```
create database [database name];
```
Then to create the acme user with all rights to the new database:
```
grant all privileges on [database name].* to 'acme'@'localhost' identified by '[acme user password]';
```
followed by:
```
flush privileges;
```
Then enter the above values for the database name, user, and password in your drupal configuration.

---

### Post by seabag on 2009-11-27
Thanks for the reply.
This is one of my problems
I enter this 
mysql -u root mysqland get this
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

So I am stopped before I start so maybe if I can get past this I will go places.

---

### Post by KayakJim on 2009-11-27
> **seabag said:**
> Thanks for the reply.
This is one of my problems
I enter this 
mysql -u root mysqland get this
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

So I am stopped before I start so maybe if I can get past this I will go places.

Okay, try:
```
mysql -u root -p mysql
```
instead.

---

### Post by seabag on 2009-11-27
> **KayakJim said:**
> Okay, try:
```
mysql -u root -p mysql
```instead.

OK and thanks again, I will have to try tomorrow now as it is 5pm here and I have to pick a person up at a distant airport. Hope I hit lucky when I try it.

---

### Post by seabag on 2009-11-28
As it happens I have been to this stage at one point but thought I was on the wrong track
 here it is

    	 	 	 	 	 	  acme@acme-laptop:~$ mysqladmin -u username -p create databasename  
 Enter password:  
 mysqladmin: CREATE DATABASE failed; error: 'Access denied for user ''@'localhost' to database 'databasename''  
 acme@acme-laptop:~$ mysqladmin -u username -p create databasename  
 Enter password:  
 mysqladmin: connect to server at 'localhost' failed  
 error: 'Access denied for user 'username'@'localhost' (using password: YES)'  
 acme@acme-laptop:~$ createuser --pwprompt --encrypted --no-adduser  
 The program 'createuser' is currently not installed.  You can install it by typing:  
 sudo apt-get install postgresql-client-common  
 bash: createuser: command not found  
 acme@acme-laptop:~$ --no-createdb username  
 bash: --no-createdb: command not found  
 acme@acme-laptop:~$ mysql -u username -p  
 Enter password:  
 Welcome to the MySQL monitor.  Commands end with ; or \g.  
 Your MySQL connection id is 9  
 Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)  
 

 Type 'help;' or '\h' for help. Type '\c' to clear the buffer.  
 

 So I did this

  mysql> mysql -u username -p   
 
acme@acme-laptop:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
acme@acme-laptop:~$ mysql -u username -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database [bero];
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '[bero]' at line 1
mysql> 

I used no password but a.s you can see I am still in trouble

---

### Post by KayakJim on 2009-11-28
At least you have confirmed your MySQL server is operational.

You used the wrong command for creating the database, which is why you received the last error. Do not enclose the database name with brackets.

I have a few questions for you so I know how to proceed next.
1. Do you know your mysql root user's password? I do not need to know it but just need to know if you do. ;)

2. What name do you want to give the database? I typically try to keep it the same as the client or project.

3. What username do you want to use to access the database?

---

### Post by seabag on 2009-11-28
I cant remember using or filling in a password for mysql root user
 I don't care what the database name is as long as it works what ever you suggest
 I would use bero username to access the database but again anything to get it working.

---

### Post by KayakJim on 2009-11-28
That makes it tougher but we should be able to work through it.

Login to the mysql console as you did before, i.e. "mysql -u [mysql username] -p mysql"

I will just use the following in my examples but you can change them to what you want:
db_name will be the name of the database
bero will be the database username
bero_password is the password for the bero database user

Once you have the mysql> prompt enter the following:
```
create database db_name;
grant all privileges on db_name.* to 'user'@'localhost' identified by 'bero_password';
flush privileges;
```

---

### Post by seabag on 2009-11-28
Sorry to be a pain but still problems, if i did a password it would have been bhw12345.
acme@acme-laptop:~$  mysql -u username -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database connect;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'connect'
mysql> grant all privileges on db_name.* to 'user'@'localhost' identified by 'bero_password';
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'db_name'
mysql> grant all privileges on connect .* to 'user'@'localhost' identified by 'bero_password';
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'connect'
mysql> flush privileges;
ERROR 1227 (42000): Access denied; you need the RELOAD privilege for this operation
mysql>

---

### Post by KayakJim on 2009-11-28
Please edit your post to remove the actual password for your security. ;)

Try mysql -u root -p mysql and provide that password when prompted. If you get the mysql console then we are in business and you can follow the steps I provided above starting with the "create database" statement.

---

### Post by seabag on 2009-11-28
Its getting worse I cant figure out how to  			 		   		 		 		Please edit your post to remove the actual password for your security.

---

### Post by KayakJim on 2009-11-28
> **seabag said:**
> Its getting worse I cant figure out how to  			 		   		 		 		Please edit your post to remove the actual password for your security.

In the lower-right corner of the post box you should find an Edit button.

---

### Post by seabag on 2009-11-29
Its no good I just don't understand what I am being told, my business is exporting containers of used  goods throughout West Africa in which I do all the paper work buy the goods etc. I can do this but this server setup is proving to be a big challenge to me.  I have a few computers working on Ubuntu and Knoppix Adriane with XP as guest in Virtual box in case of incompatible software. I built myself a website just to let my customers know what I have and to keep the cost down I was hoping to have my own server as it would not matter if it was not on all the time and they more or less on the same time as me greenwich.
 I will have to read more to understand more for example I don't have a clue how to edit as you have advised me to do and think I am wasting your time. I think I will re-install and be very carefull and take more notice of what I am doing plus the fact I have gained some knowledge that I don't want to forget about. Mysql seems have given me most problems. Thank you so much for your time and help.

---

### Post by ktmom on 2009-11-30
seabag --

> **KayakJim said:**
> In the lower-right corner of the post box you should find an Edit button.

What is meant is to remove the information about what you would have used as a password on the forum here.  In a previous post you made;

> **seabag said:**
> Sorry to be a pain but still problems, if i did a password it would have been [COLOR="Red"]**********[/COLOR].
acme@acme-laptop:~$  mysql -u username -p 


Where I used asterisks, you used a password.  It is being suggested by KayakJim that you go back to your post (last one on the first page of this thread, post #10) and then click the edit button located in the lower right of that post and edit out the actual password. 

All that said, please don't use that password for anything now.  Once it's published on the Internet, you lose control of the information.

---

### Post by ktmom on 2009-11-30
> **seabag said:**
>  I think I will re-install and be very carefull and take more notice of what I am doing plus the fact I have gained some knowledge that I don't want to forget about. Mysql seems have given me most problems. Thank you so much for your time and help.

As you ponder how to move forward, I wonder if Drupal might be a bit of a big bite for a database novice.  Have you considered other CMS applications?  Drupal is very flexible, but expects a level of familiarity that might be more than you meant to take on.

I also wonder how you did the install of your server software (Apache, MySQL, PHP ?)  Did you use the Synaptic package manager?  You should have been prompted to provide a password for root during the install process.  It would have come up as a dialog box before the install finished.  I think you indicated that you did not provide a password then, but maybe you did? 

If you really want to go with Drupal, there is also a Synaptic package manager installation of Drupal 5 or 6 (best to go with 6 as it will be supported longer).  That process will setup the database for the Drupal install.

Also, make sure you install phpMyAdmin as it will make administering databases *much* easier.

Here are a couple of links to community documentation pages that may help you:
[LAMP install (Linux-Apache-MySQL-PHP)]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[Drupal install]("https://help.ubuntu.com/community/Drupal")

---

