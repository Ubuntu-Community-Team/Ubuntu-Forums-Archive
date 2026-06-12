---
title: "phpmyadmin file too big"
date: 2019-05-21
forum: Server Platforms
---

### Post by tomdf on 2019-05-21
HI guys,

i use ubuntu18.04 with mysql 

I want to import a database with 8.5 MB with phpmyadmin.
I get an error that the database is too big for import.

Can you help me how i can import the database to phpmyadmin?

thanks for your kind help.

---

### Post by spjackson on 2019-05-22
You need to edit /etc/php/7.2/apache2/php.ini. Both the upload_max_filesize and post_max_size parameters need to be sufficient. You will need to restart apache after the change.

---

### Post by tomdf on 2019-05-22
thanks so much for your help now it works ;)

---

### Post by SeijiSensei on 2019-05-22
If you have terminal access to the server, say via SSH, you might want to learn some of the basic command-line methods.  

I use Microsoft Access, connected via ODBC to my PostgreSQL server running on Linux,  for some projects because I generally like its graphical interface and ease of creating complex queries.  Still, for many tasks, I find it easier and faster to use the command-line client.  True, I've written a lot of SQL over the years, but knowing a few basics like SELECT, UPDATE, DELETE, etc., can often make your life easier than using a GUI interface like phpMyAdmin.

---

