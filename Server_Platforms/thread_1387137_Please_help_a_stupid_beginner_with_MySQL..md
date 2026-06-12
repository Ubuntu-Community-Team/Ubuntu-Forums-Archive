---
title: "Please help a stupid beginner with MySQL."
date: 2010-01-21
forum: Server Platforms
---

### Post by sorino737 on 2010-01-21
Hello...
can some one help with the commands for:

1) Check if MySql is installed and running
2) How can I connect to create my db. (I want to do it from CLI not using an admin tool)
3) And if I have problems how can I make a clean uninstall/remove.

Thank you.

---

### Post by volkswagner on 2010-01-21
To find out if it is installed and what version.

```
mysql --version
```

For help.

```
man mysql
```

---

### Post by cdenley on 2010-01-21
To completely remove mysql server and any databases you may have created:
```

sudo apt-get --purge remove ^mysql-server.*

```

---

### Post by shred_eng on 2010-01-21
mysql -u root -p     then enter password at prompt

create database databasename;

q  to quit

if you find the man a bit confusing like i did, just google it, theres a ton of easy to understand tutorials,

---

### Post by vinan on 2010-01-21
if you are on a gui box


[COLOR=DarkRed]install webmin from synaptic and [/COLOR]

[COLOR=#38761D]Firefox Options -> Advanced -> Encryption -> View Certificates ->[/COLOR]
 [COLOR=#38761D]Server -> Add Exception

[/COLOR]https://yourname-desktop:10000/


regards
vinan

[COLOR=#38761D][/COLOR][COLOR=#38761D]



[/COLOR]

---

### Post by azagaros on 2010-01-21
find and follow LAMP instructions out there.  They give test cases and stuff to get everything working and they give starting places for the CLI.  Mysql's cli is picky about how you do things, personally I try to avoid if I can.  Write a script to create your dbase. Learning SQl is a good starting point for using mySql.

---

### Post by sorino737 on 2010-01-22
thank you all for yr time, now i'm clear.

---

