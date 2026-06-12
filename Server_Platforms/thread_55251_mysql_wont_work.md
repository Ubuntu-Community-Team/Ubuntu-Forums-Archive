---
title: "mysql wont work"
date: 2005-08-08
forum: Server Platforms
---

### Post by mrweirdo on 2005-08-08
I can not for the life of me get mysql working on my hoary ubuntu system. I tried following the guide at [Ubuntuguide.org](http://ubuntuguide.org/#installmysqldatabaseserver)  to no avail. 
I used apt-get install mysql-server-4.1
then try to issue 
mysqladmin -u root password db_user_password and of corse it will not work
allways geting the following error:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

One thing I have noticed is that within phpmyadmin or mysql-admin I can access the server using the username mysql without a password but I have no permisons to make any changes at all. Anyone have any ideas?

---

### Post by dave9191 on 2005-08-08
Try your user name and your password instead of root. 

Dave

---

### Post by mrweirdo on 2005-08-08
still no luck ive tried issuing the comand 
mysqladmin -u myusername password mypassword
in both shells being loged in with my regular user or root I get the same on both:
mysqladmin: unable to change password; error: 'Access denied for user ''@'localhost' to database 'mysql''

---

### Post by mrweirdo on 2005-08-08
good news I managed to get it working by uninstalling mysql-server 4.1 and removing files that that package left behind. The in installed 4.0 and ran the mysql-admin again and it worked :). Now I need to figure out how to make a new user specificaly for phpmyadmin allowing them the ability to create and delete their own databases so Im not using the root  mysql account and they cant  access the mysql or test table. btw I have the Mysql-admin and mysqlcc GUI installed for adminstration. Any ideas on how this could be done?

---

### Post by dave9191 on 2005-08-09
You need to create a new user for mysql in the mysql user table. And give them only the access rights that you want them to have. Then set phpmyadmin to get users to log in with their mysql details. 

Dave

---

### Post by Loop0nBlue on 2005-08-09
If you just followed blindly [http://www.ubuntuguide.org]("http://www.ubuntuguide.org"), as I did, then maybe the solution is to do :
 ```
mysql -u root -p
Enter password:
``` 
and your password should be [b]db_user_password
[/b]
If it doesn't work, rejoice, it means you may have been smarter than me :)

---

