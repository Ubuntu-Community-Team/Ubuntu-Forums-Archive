---
title: "Database server"
date: 2008-01-28
forum: Server Platforms
---

### Post by infinitezero on 2008-01-28
Does anyone have a quick and dirty way of creating a database I can serve up through apache.

Thanks,
iz

---

### Post by jpeddicord on 2008-01-28
```
sudo apt-get install apache2 phpmyadmin mysql-server
```You will be asked for a password to set as root, type one in and continue.
```
mysql -u root -p
```Put in the same password you entered in the first step.

Then visit: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

That's the quick and dirty to get it set up, if you want something more complicated you will probably have to write some PHP or Python code to connect to the database.

Jacob

---

### Post by Maxtorm on 2008-01-28
Depending on the complexity of the database, you might also want to consider SQLite. It is an optional component of php (though, if I recall correctly, it is installed by default with an apt-get install of php) that stores databases in flat files. Certainly not elegant or fast, but for small databases, it gets the job done. More on SQLite here: [http://ca3.php.net/sqlite](http://ca3.php.net/sqlite) .

---

### Post by infinitezero on 2008-01-29
Thank you, that is the info I was looking for.


iz

---

