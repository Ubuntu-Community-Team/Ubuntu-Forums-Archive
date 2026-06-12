---
title: "simple mysql question"
date: 2010-02-24
forum: Server Platforms
---

### Post by SSamiK on 2010-02-24
OK.. i've got one simple question.. when running a mysq query throught ssh, how do i know if it all went well? 

The reason I'm asking is I have a 700MB backup witch I try to restore..

After running 
```
mysql -u root -p >sqlfile.sql
```
I get a blank line, and I'm unsure if it's finished, working or what...

---

### Post by howlingmadhowie on 2010-02-24
> **SSamiK said:**
> OK.. i've got one simple question.. when running a mysq query throught ssh, how do i know if it all went well? 

The reason I'm asking is I have a 700MB backup witch I try to restore..

After running 
```
mysql -u root -p >sqlfile.sql
```
I get a blank line, and I'm unsure if it's finished, working or what...

to pass commands in a text file to mysql, as far as i know you have to enter the following: 
```

mysql -u USERNAME -p < NAME_OF_THE_FILE

```
and then the mysql-password for USERNAME. In your code the arrow is pointing the wrong way.

One thing you can always do is open a shell connection to the server. You can do this by just entering the following:
```

mysql -u USERNAME -p DATABASE_NAME

```
and then the mysql-password for USERNAME.  Then you can look around the data in the database using standard mysql commands (e.g. 'SELECT * FROM table;')

I hope this helps :)

---

### Post by brian.m on 2010-02-24
howlingmadhowie, you are correct. Here is a link that covers this:  [MySQL backup and restore commands]("http://www.brianm.name/backup-and-restore-mysql-databases-from-the-command-line/") (from the shell).

---

### Post by SSamiK on 2010-02-24
OK.. thanks you guys! I've got it going now, just have to wait. Guess it will take some time processing 700MB of database backup. :)

---

