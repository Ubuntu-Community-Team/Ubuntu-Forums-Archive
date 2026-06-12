---
title: "Mysql database issue with XAMPP"
date: 2010-04-10
forum: Server Platforms
---

### Post by damnated on 2010-04-10
I'm an absolute beginner in this, so this question may be completely obvious.

I'm not entirely sure where MySql is looking for database files. I have put my database in ```
/opt/lampp/var/mysql
``` and when I go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I can see my database in the left side panel, however, it's only the name of the database (the name of the folder the files were in) but the database is empty when I access it, the actual files are missing. 

The files are inside the folder, and they have no issues what so ever, it works on my sister PC with the same XAMP (she uses Windows though). 

Could it be some platform crossing issue, or am I using a wrong place for the files. I'm guessing the later. Please advise!

---

### Post by Ryan Dwyer on 2010-04-10
You shouldn't need to worry about the files themselves. You can make tables inside your database using phpMyAdmin.

Also, I recommend just installing Apache, PHP, MySQL and phpMyAdmin from the repos. If you downloaded XAMP from somewhere and extracted it /opt/ then the update system probably doesn't know it exists. If anything on your system tries to install Apache or MySQL in the future it would run into problems because the ports are already in use.

---

### Post by s_ø on 2010-04-10
The mysql database files are croos-platform, so that is not the issue.
You can change the directory mysql uses for databases in the config file **my.cnf**
Look for line simmilar to this.
```
datadir         = /var/lib/mysql
``````

```

I dont really know where this will be when you install xampp, and I dont really understand why anyone would use xampp on ubuntu. There is a LAMP package, and a phpmyadmin package.
To find the my.cnf file use** locate my.cnf** in terminal.

---

### Post by damnated on 2010-04-10
> **s_ø said:**
> 
You can change the directory mysql uses for databases in the config file **my.cnf**
Look for line simmilar to this.
```
datadir         = /var/lib/mysql
```I dont really know where this will be when you install xampp

Yes, that is the folder where I put my folder containing the database files. MySql is running and recognizes the name of the database, yet can't do anything with the files.

---

### Post by Ryan Dwyer on 2010-04-10
Wait, you pasted the files there? Then you'll need to set the user and group on them. They should all be mysql:mysql.

---

### Post by damnated on 2010-04-10
> **Ryan Dwyer said:**
> Wait, you pasted the files there? Then you'll need to set the user and group on them. They should all be mysql:mysql.

How/where do I do this?

---

### Post by s_ø on 2010-04-10
open a terminal and use chown. (the -R is for recursive
**sudo chown mysql\: /var/lib/mysql -R**
And im pretty sure they need to change permissions as well.
**sudo chmod 700 /var/lib/mysql -R**

---

### Post by damnated on 2010-04-10
> **s_ø said:**
> 
**sudo chown mysql\: /var/lib/mysql -R**

I get an ```
chown: invalid spec: `mysql:'
```after this.

---

### Post by s_ø on 2010-04-10
Edit:
Try using 
**sudo chown mysql:mysql ****/var/lib/mysql -R**
-

It looks like you dont have a mysql user.
You can run this command to check if the mysql user exists. It will print any matches it finds.
**sudo grep -i 'mysql' /etc/shadow**

If there is no special reason for you to use xampp I would suggest you remove it completely and installo the LAMP stack and phpmyadmin from the repos.

To install LAMP (**L**inux**A**pache**M**ySQL**P**hp)
[B]sudo tasksel install lamp-server

[/B] To install phpmyadmin
**sudo apt-get install phpmyadmin**

---

### Post by damnated on 2010-04-10
> **s_ø said:**
> 
If there is no special reason for you to use xampp I would suggest you remove it completely and installo the LAMP stack and phpmyadmin from the repos.

To install LAMP (**L**inux**A**pache**M**ySQL**P**hp)
[B]sudo tasksel install lamp-server

[/B] To install phpmyadmin
**sudo apt-get install phpmyadmin**
Okay, I have removed XAMPP completely, and installed LAMP with phpmyadmin. 

I've put my database folder in the default, /var/lib/mysql data directory, and I have the same problem as originally: I can see the name of the databse in phpmyadmin, but it says "No tables found in database."

LATER EDIT: and after entering ```
sudo chown mysql\: /var/lib/mysql -R
``` everything works. Thanks a bunch :)

---

