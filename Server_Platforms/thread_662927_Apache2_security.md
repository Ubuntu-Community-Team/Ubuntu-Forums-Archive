---
title: "Apache2 security"
date: 2008-01-09
forum: Server Platforms
---

### Post by TorchlightJay on 2008-01-09
So this may sound like a dumb quesiton but I have to ask.

I am currently running a server with Ubuntu 7.04 server edition and MySQL, PHP, and Apache2. Now I ahve a few websites and php apps (SugarCRM, WordPress, and I hope to put on PHPMyAdmin). Now naturally I do not want people logging into the website and figuring out hwo to access the folders on my php-based apps and changing things nor do I want to have them access anything else and change it. 

I am probably opening a huge can of worms here but what would you advise is the best way to prevent that. I have heard people suggest .htacess files but I figure there must be other options in setting up users or something to that matter. Let me know if you guys have any suggestions. Thank you in advance.

---

### Post by k_grdn on 2008-01-09
Hi,

Check out: suexec,mod_security,apparmour.  If want to focus on php take a look at this article:

[http://www.securityfocus.com/infocus/1706](http://www.securityfocus.com/infocus/1706)

Good Luck,

k_grdn

---

### Post by az on 2008-01-09
> **TorchlightJay said:**
> So this may sound like a dumb quesiton but I have to ask.

I am currently running a server with Ubuntu 7.04 server edition and MySQL, PHP, and Apache2. Now I ahve a few websites and php apps (SugarCRM, WordPress, and I hope to put on PHPMyAdmin). Now naturally I do not want people logging into the website and figuring out hwo to access the folders on my php-based apps and changing things nor do I want to have them access anything else and change it. 


Start from the basic things.  Do not allow apache to be able to write to your document root.  That's why /var/www is not owned by www-data.  Apache2 runs as www-data and only root can write to /var/www.  Allow apache to write to only the specific files and folders required by your web application.  A web application that doesn't keep it's php code read-only is not smart.

Make sure your database is being accessed by a mysql user with minimum privileges.  Granting all privs to the mysql user that is used by php is not smart.  Using the mysql root user is even worse.

Other than that, don't allow anyone to ssh into your machine and pick strong passwords.

Only you will decide how much security is enough.  But if you are not hosting anything with sensitive information like credit card numbers, I think doing the above is due diligence.

Keep up-to-date with software updates.

---

### Post by TorchlightJay on 2008-01-10
> **az said:**
> Start from the basic things.  Do not allow apache to be able to write to your document root.  That's why /var/www is not owned by www-data.  Apache2 runs as www-data and only root can write to /var/www.  Allow apache to write to only the specific files and folders required by your web application.  A web application that doesn't keep it's php code read-only is not smart.

So how do I ensure that apache is not able to write? I know it's a dumb question but I am not sure where to begin looking. I know that the folder holding my web information is only accessible by root but I don't know what Apache2 is set as. How can I check and change should I need to?

> **az said:**
> Make sure your database is being accessed by a mysql user with minimum privileges.  Granting all privs to the mysql user that is used by php is not smart.  Using the mysql root user is even worse.

So I should create a user called mysql or is there one already there by default simply because i installed mysql? How do I edit privs? I am not an expert at setting up users and what not. 

If you can point me in the right direction, that would be great. Thanks in advance.

---

### Post by k_grdn on 2008-01-10
Hi,

> So how do I ensure that apache is not able to write? I know it's a dumb question but I am not sure where to begin looking. I know that the folder holding my web information is only accessible by root but I don't know what Apache2 is set as. How can I check and change should I need to?

ls -ld DocumentRoot;  (long dir listing)

chown user DocumentRoot;  (change the owner of the folder)

chmod permissions DocumentRoot;  (modify permissions; 421, rwx use -R for reclusive)

> So I should create a user called mysql or is there one already there by default simply because i installed mysql? How do I edit privs? I am not an expert at setting up users and what not.

Default mysql user is root, have you set a password?

If not: mysqladmin -u root password NEWPASSWORD

To update: mysqladmin -u root -p password 'NEWPASSWORD'

You need to create the initial database user and assign only the required permissions needed to function.

Privileges: SELECT,INSERT,UPDATE,DELETE,CREATE,DROP

mysql -u root  -p (gets you to db prompt)

>SHOW DATABASES;

>GRANT UPDATE,CREATE,DROP on database.* TO user@localhost IDENTIFIED BY 'password'; (example do not assign these to the user)

>flush privileges;

Regards,

k_grdn

---

### Post by TorchlightJay on 2008-01-10
Hey, so when I try mysqladmin, this is what I get.
-----
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
-----

I was wondering what I am suppsoed to do. Currently, to log into mysql all I do is "sudo mysql" and I am in. I have a few tables set up for some of my php programs. Any ideas of what to do?

Also, on the first step, everything is in root according to the ls -ld but I see other things like drwxr -xr -x and other things. Is there a list online or something that can help me translate it? Thanks

---

### Post by k_grdn on 2008-01-10
Hi,

Read this doc for permissions:

[http://tldp.org/LDP/intro-linux/html/sect_03_04.html]("http://tldp.org/LDP/intro-linux/html/sect_03_04.html")

Looks like you have no root password for mysql.

Which mysqladmin command gives that error initial or update?

If you can access your dbs/tables, look up user rights.

>use mysql;
>select * from user;
>select * from db;

You need to work out which web apps use what dbs/tables, Create an initial user and assign privilages or modify the existing users privilages on dbs/tables;

Regards,

k_grdn

---

### Post by TorchlightJay on 2008-01-10
sorry, it's the very first command to set the command 

mysqladmin -u root password NEWPASSWORD

and that's the response I get.

---

### Post by k_grdn on 2008-01-10
Hi,

Good, that means that you have a root password which if mysql was installed from apt and you choose too, you would of set one.

So just login to sql and GRANT permissions at will.

Regards,

k_grdn

---

