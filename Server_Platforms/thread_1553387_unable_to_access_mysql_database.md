---
title: "unable to access mysql database"
date: 2010-08-15
forum: Server Platforms
---

### Post by cvah on 2010-08-15
We started our project (it's a website "employee performance appraisal  system") in windows by starting with some html forms and then slowly  added php ,javascript and other stuff in windows we had no issues of  insertion and retrieval of data from the database.Now,we decided to  shift the entire stuff to drupal the html forms along with those php  files but we had 2 issues with this

1. the first one was ..we created "page" for each html form and  copied the html code into "page" but we didn't find where our pages are  getting stored (do they get stored in mysql database that we create for  drupal site? or do they remain as html pages somwhere?) 

2.second problem was ...for admin in drupal I gave the username  "root" and a password ..similarly for mysql also I gave a password.
now  I used phpmyadmin and created another database called "appraisal" which  is supposed to hold the data of our website.when I try to insert data  into one of the tables of this database (attendance table) ,the  following error occured "Attempt to connect failed access denied for  user 'root'@'localhost'(using password:NO) cannot run querry insert into  attendance values('x','y')" Access denied for user 'root'@'localhost'  (using password:NO)

Also I'm unable to access mysql as a normal user only super user can  access and can we unset the password that's required to reach mysql  prompt?

Thanks.

---

### Post by longvnit on 2010-08-17
**root **account is full permission on mysql server.
That error is report username or password incorrect , you check info again or using phpmyadmin create new account on mysql.

---

### Post by cvah on 2010-09-10
thanks a lot .find it silly :(

---

