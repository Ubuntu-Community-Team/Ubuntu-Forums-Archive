---
title: "Gensoft Moneyworks with Wine - firebird server in wine"
date: 2011-02-19
forum: Wine
---

### Post by krisberck on 2011-02-19
Hi i want to run this ERP warehouse software under wine on Ubuntu 10.10. [http://gensoft.bg/Downloads/MW%20Install.exe]("http://gensoft.bg/Downloads/MW%20Install.exe")
Installation run smoothly but the problem is firebird server that is needed for connection with database. I found a guide in internet and installed native firebird server in linux. I connected the database with flamerobin. But Moneyworks installed in wine cannot see the server. 
Can you help me please?

Also if you know another native linux software that i can use in my PC Shop for supply managment and sales management i will try it even if i loose 2 years history from the database.:confused:

Sorry for my bad english and thanks! :)

---

### Post by mariuz on 2011-02-23
What error do you have , maybe you need to use the localhost: prefix to the database path /var/lib/firebird/2.1/data 

Also is a good idea to unpack the firebird client dll in the same dir with the app

---

### Post by sonaris on 2011-04-09
for DB use /db/sklad.gdb must be sure that the database is the property of the firebird user and accordingly with the correct rights.

Company Gensoft using firebird 2.0.3 or 2.5 now implements. In the config file does not need to change anything cpuaffinitymask only if you have dual core or greater processor.

In Sklad.ini write the correct path to the database or use aliases.conf
```
DataBase=<Hostname:Path\Database>
```
```
DataBase=magmaserv:/db/Sklad.GDB
```important: small and large letters are important

using aliases.conf in file wright
 ```
Sklad.GDB = /db/Sklad.GDB
```
in Sklad.ini 
 ```
DataBase=magmaserv:Sklad.GDB
```
this works to and is more secure

It is important if you plan to create a new blank database. I recommend the database to be created in windows then copied to linux and it works. GenSoft MoneyWorks program is not designed to create a database on Linux.

for more info call the [offce 07001 9393 Bulgaria]("http://http://www.gensoft.bg/forums/viewtopic.php?f=1&t=368&p=6958&hilit=Linux#p6958")

---

