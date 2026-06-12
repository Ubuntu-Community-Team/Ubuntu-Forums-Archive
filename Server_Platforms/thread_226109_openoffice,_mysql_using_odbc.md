---
title: "openoffice, mysql using odbc"
date: 2006-07-30
forum: Server Platforms
---

### Post by sheberlein on 2006-07-30
I need help setting up openoffice base to connect to MySql data base. I have installed libmyodbc and unixdoc utilities.  I still can not connect to mysql.

Any help would be appreciated.

---

### Post by adamkane on 2006-07-30
It's a sad fact that OpenOffice doesn't have well developed support for Ubuntu and ODBC or JDBC. For now, you can use phpmyadmin or MySQL Query Browser.

As with most things, Ubuntu uses su (sudo) in a special way, and this causes issues with almost all major software packages. We always have to wait for the MOTUs to get the message, and to fix these sudo issues.

For the time being, they are only working on issues of consequence to the majority of Ubuntu users, and those of who use Ubuntu to maintain our databases are left waiting.

Hopefully someone will prove me wrong on the situation.

---

### Post by foxylad on 2006-07-30
Is MySQL running? More details about which machine (localhost/remote) it is on and any error messages would help.

---

### Post by sheberlein on 2006-07-30
I have mysql up and running on local host. All mysql command line commands work fine. I also have Mysql Administrator and Query browser they work just fine. I have populated a sample data base from a script file all works and I can access it with the above software. I have ubuntu 6.06 installed and all the updates applied. Open office can not connect to the data base. I am using this as a test to demo for a business to show the abilities of ubuntu linux. Currently they are looking at using a dell server with windows 2000 sql server for a data base and file server. I think some of the file links maybe incorrect and some file permissions but I am not sure. The error is [unixodbc manager] can not connect to the odbc and driver.

---

### Post by llbbl on 2006-07-31
Just use query browser to access it. You can also build a web interface. You can have them export the open office documents into cvs or something like that you can import into mysql. Connecting to mysql via openoffice is not something that is normally done.

---

### Post by sheberlein on 2006-07-31
llbbl
Thanks for the help. What would you recomend to use for a simple but easy to use interface for updating, adding and printing formated output from mysql. Keep in mind the target here is windows only office employees clerks etc. I would like to show the benefits of ubuntu or linux in general for office use.       They will need to update or add new data easily and be able to print reports with the data retrieved. I think query browser is great for me but maybe not for them.

---

### Post by sheberlein on 2006-07-31
Thanks everything is up and running now. Problems file permissions and the unixodbc did not automaticly install the utilities. I installed this and did all the configs. It works GREAT!!:p :p :p

---

### Post by adamkane on 2006-08-01
How did you install the utilities? Please elaborate.

This is so cool.

---

### Post by yurtboy on 2006-08-04
Alright this seems to work for me.
Here is what I have installed
i   libmyodbc                            - ODBC Binding for ruby1.8
i   libodbcinstq1c2                      - ODBC driver for PostgreSQL
i A odbcinst1debian1
i   unixodbc                             - ODBC tools libraries
i   unixodbc-bin       

Do you need them all?  Not sure
Then I setup the two main files as such
/etc/odbc.ini
[Marketing] <--THE NAME THAT APPEARS IN OO CONNECTOR
Description = MySQL test database
Trace       = Off
TraceFile   = stderr
Driver      = MySQL
SERVER      = 192.168.1.254
USER        = YOU USER NAME HERE
PASSWORD    =
PORT        = 3306
DATABASE    = contacts

/etc/odbcinst.ini
[MySQL]
Description = ODBC Driver for MySQL
Driver = /usr/lib/odbc/libmyodbc.so
Setup = /usr/lib/odbc/libodbcmyS.so
FileUsage = 1
CPTimeout =
CPReuse =

Alright now the server
since mine was not local host I had to change 
/etc/mysql/my.inf
Pound out this line
#socket         = /var/run/mysqld/mysqld.sock
added
bind-address            = 127.0.0.1 
#skip-networking
bind-address = 192.168.1.254 <-- the machine I connect from

Well it worked though I am sure this is a better way...

Then in phpmyadmin I made sure the db I was connecting to had user privledges that allowed my ip address to connect to the db
so user so and so with password whatever from ip 192.168.1.254
This was key as well.

Well restarted mysql and connected no prob via OO
If I notice probs as I go I will note them.
Just wanted to write this before I forgot.
Also an old pdf may help?
[http://www.unixodbc.org/doc/OOoMySQL.pdf](http://www.unixodbc.org/doc/OOoMySQL.pdf)
Maybe,
Good luck

---

