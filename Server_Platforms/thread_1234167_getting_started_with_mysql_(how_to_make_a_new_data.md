---
title: "getting started with mysql (how to make a new database)"
date: 2009-08-07
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-08-07
i have ubuntu desktop, with LAMP installed

i know how to use mysqul from php, 

but i need to set up the initial database to connect to.

i used xampp, and isp's before, and they have ways to add/edit/remove databases from the web browser.

all i need to do is know how to make a database that i can connect to from php, and then i can take it from there (i can add tables to the database from php).


please help.

---

### Post by Zeroangel on 2009-08-07
I would suggest you install this package
```
sudo apt-get install phpmyadmin
```

You can then work with your MySQL database by [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by OctPhil on 2009-08-07
phpmyadmin will provide you with a nice web interface to access and use your databases, but if you want to manage the database from PHP, you might find this simple shell command easier:

```
mysql -u username -p -h localhost CREATE database_name
```

This should create the database for you.  Of course, you would replace username with an appropriate mysql username (I usually use root when creating a database) and database_name would be whatever you want to name the database.

Also, I would usually log in to mysql and create a user for the database:

```
mysql -u root -p
```

Should get you to the mysql shell, then:

```
GRANT SELECT, INSERT ON database_name.* TO newuser@localhost IDENTIFIED BY 'password'
```

I usually specify the rights (SELECT, INSERT in the example - but I think ALL is an option, though I doubt it's recommended).  Again, database_name, newuser, and password would be replaced by your own values.

Using this method saves you from needing to install phpmyadmin.  I find it easier, you may like phpmyadmin more.

---

### Post by rhythmiccycle on 2009-08-07
thanks alot, both good suggestions, i'll try them out. 

i'm going to try "mysql -u username -p -h localhost CREATE database_name"

first, because all i need to do is make a database,

but if that gives me issues, or if i need to do any other admin tasks i'll install "phpmyadmin"

thanks.

---

