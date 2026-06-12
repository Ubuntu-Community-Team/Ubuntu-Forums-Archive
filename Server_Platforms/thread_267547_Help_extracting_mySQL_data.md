---
title: "Help extracting mySQL data"
date: 2006-09-28
forum: Server Platforms
---

### Post by bunnynuts on 2006-09-28
I have been given a cd which contains data from a mySQL database. I need to extract the information into any other easy to read file (spreadsheet, plain text). I have the basic 6.06 LAMP setup and am operating from command line. I've never used a SQL server before and am unsure what files to look for on the CD (there are many files and I don't know which ones I need) or what to do with them once I've found them. Any help will be greatly appreciated.

---

### Post by foxylad on 2006-09-29
It would be useful to know what files are on the CD. The usual method of dumping data from mysql involves a utility called mysqldump, which outputs the sql statements required to recreate the database. Generally there are two types of sql statements: "create table ..." which create database tables, and "insert into ..." which insert data into the tables. So open some of the files on the CD with a text editor, and see if this is what is in them.

If so, you need to first create a database - from a terminal, run mysql and type in "create database greg;". Now exit mysql, and run mysql again but with a redirection command to pipe the file contents into the database:

mysql -u xxxx -pyyyy greg < cd_file

This should create and populate the tables contained in the file. You can then query and report on the contents as you wish.

If the files do not contain sql statements, and are named things like *.myd and *myi, then you have the raw database files. Unless you have exactly the right version of mysql, you are going to have a lot of problems. Probably best to ask whoever gave you the CD to give you sql files instead.

create

---

### Post by bunnynuts on 2006-09-29
Thank you for the help. I've now identified the files I need to extract data from and unfortunately they are .myi, .myd, and .frm files. Any ideas on how to get at the data? I'm guessing that my next step will be to determine the mySQL version used and then set it up as you suggested. If there are any other ideas on how to do this easily I would greatly appreciate them.

Thanks

---

### Post by bunnynuts on 2006-10-07
Ok, I've finally gottent time to work on this once again, and have installed the mySQL server. From here I'm lost as to what to do with the .myi and .myd files. Thanks to subscriptions to books 24x7 and safari I'm sure that I'll be able to figure this out...eventually. If anyone can help me speed up the process I would greatly appreciate the help.

---

### Post by paul.maddox on 2006-10-07
Ok, the files you have are the actual database files, not the databases exported to SQL (the normal method of MySQL backup).

*.FRM: Contains the table structure
*.MYI: Contains the indexing information (I think!)
*.MYD: Contains the actual data

No worries though, they can still be imported.

Ok, firstly stop the database server

```

paul.maddox@web1:~$ sudo /etc/init.d/mysql stop

```

Now create the folder for the database (replace databasename with whatever you want the database to be called)
```

paul.maddox@web1:~$ sudo mkdir /var/lib/mysql/databasename

```

Now copy in the files you have
```

paul.maddox@web1:~$ sudo cp *myi *myd *frm /var/lib/mysql/databasename/

```

Make sure the files have the right permissions
```

paul.maddox@web1:~$ sudo chown -R mysql:mysql /var/lib/mysql/databasename
paul.maddox@web1:~$ sudo chmod -R 700 /var/lib/mysql/databasename

```

Start MySQL 
```

paul.maddox@web1:~$ sudo /etc/init.d/mysql start

```

Check the database contains valid tables (this command should output a list of tables within the database)
```

paul.maddox@web1:~$ mysql -u root databasename -e "SHOW TABLES;";

```


Hope this works for you!

---

### Post by bunnynuts on 2006-10-08
Paul,

Thank you so much for the help, I've done everything you suggested and all worked out perfectly. I imagine you have saved me countless hours. Now, I must reveal my ignorance pertaining to SQL databases...I have no idea what to do from here. What I would like as an end result is some form of a spreadsheet that contains all of the data. I'll then be transfering this information into a statistical package (SPSS). Again, any help is very much welcome/needed/appreciated.

Thanks

---

### Post by paul.maddox on 2006-10-08
Does your desktop PC run windows or linux?

If you are using Windows as a desktop I'd recommend getting a 30 day trial of Navicat ([www.navicat.com)](www.navicat.com)). You can use this to connect to the database server, view tables etc and export the data directly to CSV format which can be viewed in OpenOffice / MS Excel.

I'm sure there are linux alternatives to navicat (hell, they even have a linux version but it's not as polished as the windows one) but I can't think of any at the moment.

---

