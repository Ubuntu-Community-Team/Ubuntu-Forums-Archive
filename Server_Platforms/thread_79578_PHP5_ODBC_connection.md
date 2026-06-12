---
title: "PHP5 ODBC connection"
date: 2005-10-20
forum: Server Platforms
---

### Post by i_am_socket on 2005-10-20
Hey all,

I've got 5.10 installed at work to run our intranet (clean install, not an upgrade).  I've installed Apache2 ,PHP5, Perl5.8.7 all off Synaptic and all working.  The problem I'm having is that I'm trying to use PHP to connect to our SQL server (SQL Server 2000) and its just not working.  I've installed unixODBC and all and configured the NDS to connect to it using the FreeTDS driver (all from Synaptic).

I can connect to the database using isql from the command line, but its not working through PHP.  I'm testing it using a basic script:
```
<?php

$sqlconnect = odbc_connect("SQL", "user", "pass");

if ($sqlconnect > 0) {
     print ("<html><h1>Hooray! It works!</h1></html>");
     odbc_close($sqlconnect);
     }

?>
```

Here's the exact error message that this produces:
> Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][FreeTDS][SQL Server]Unable to connect to data source, SQL state S1000 in SQLConnect in /var/www/odbctest.php on line 3

I got the same error from isql when I was using the wrong user and password, but I've double(triple, quadruple) checked everything and it should be right.  Anybody have any ideas?

---

### Post by i_am_socket on 2005-10-21
*bump*

Ok, no luck on reconfiguring this one, sooo... since there is a lack of a php_mssql package in synaptic, how do I configure the php_odbc package to point to the freetds driver?

Or alternately, how do I recompile the current installation so that I can manually add in --with-mssql="/etc/freetds"

---

### Post by i_am_socket on 2005-10-23
*bump*

Just in case anybody wants to know, I ended up removing both the FreeTDS and PHP5 packages via Synaptic, downloaded the source packages and compiled them manually.

I basically end up with the same problem, but at least the error message has changed (probably due to the fact that I'm trying to use a SQL Server driver instead of through ODBC).  I just have to figure out which driver file to compile PHP with now since the last one I tried was close but not quite.

---

### Post by i_am_socket on 2005-10-24
To further complicate everything, I come in to work this morning and test the server to make sure it's still giving me the same error; well lo and behold, I get asked if I want to download odbctest.php.

Apparently the power went off over the weekend and something somewhere got a little screwy.  I had the php embedded in html, which worked fine on Friday, but not anymore; only straight php will run properly.

So, I changed everything around, deleted, reinstalled everything back to not-quite-working like it was Friday, and now we're back to trying the ODBC thing again.  I changed the driver in gODBCConfig (unixODBC) to the other file and now I can connect via command line to the SQL Server using tsql, but not isql.  (isql worked previously, but not anymore)

So now, going through php to connect once again, here's the brand spanking new error message:
> Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][Driver Manager]Driver's SQLAllocHandle on SQL_HANDLE_HENV failed, SQL state IM004 in SQLConnect
After looking it up via Google, I find a bug report on php.org.  Apparently its a FreeTDS problem, not a php problem.  Which to me makes no sense because I can still connect via command line.

I figure its pretty hopeless to ask seeing how much help I've gotten so far, but does anyone happen to have any ideas?  At all?

---

### Post by araz on 2006-02-24
I have the same problem :cry:  and the same no ideas :rolleyes: 
I've installed php5,apache2 and postgresql8.0.

my error msg is:
Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][Driver Manager]Data source name not found, and no default driver specified, SQL state IM002 in SQLConnect in /var/www/index.php on line 2

can anyone help me.

Thanks in advance.

---

### Post by araz on 2006-02-24
Searching for possible errors i foun that my /etc/odbcinst.ini
 and /etc/odb.ini are empty files...Is this normal?

---

### Post by araz on 2006-02-24
EUREKA!!!!

the solution for my problem was solved by:
  1.install godbcconfig
  2. run sudo ODBCConfig

based on [http://ubuntuforums.org/showthread.php?t=30149&highlight=odbc](http://ubuntuforums.org/showthread.php?t=30149&highlight=odbc)

and that was all :D

---

### Post by gymsmoke on 2006-06-15
I've got a similar problem but with mysql

I have installed the odbc and mysql drivers, made sure that the port is open on the server, made sure the user has rights, and all i get is "Cannot connect" ...

I tried it on another server that uses proxies, and that one worked... which I though was odd...

---

### Post by solowookie on 2007-08-20
I do now know if the solution has been found, but if not I have found the solution for this (I had the same problem).

even though you can run odbcinst-j to get the enviroment variables for location of odbc.ini / odbcinst.ini they are still 'unable' to be located.

export ODBCINI=/etc/odbc.ini

I put this second line from the bottom in /etc/profiles.  not sure if that is the best place for it, but it works there!  :lolflag:

---

### Post by BlackLava on 2008-01-29
Hi

I got quite the same issue with FREETDS, sql server, php and linux too...

Here is what I have : 

Error message : 
Warning: odbc_connect() [function.odbc-connect]: SQL error: [FreeTDS][SQL Server]Read from SQL server failed., SQL state 08S01 in SQLConnect in...

DSN  in odbc.conf :
[MSSQL]
Driver = /usr/local/freetds/lib/libtdsodbc.so
Description = MSSQL
Trace = No
Server = 208.99.194.130
Database = ProWagSys 
Port = 1433

Php code :
putenv('ODBCINI=/....Path..../odbc.conf');
$username="xxxx";
$password="xxxxxxxxxxxx";
$sqlconnect=odbc_connect("MSSQL",$username,$password);


The path to odbc.conf is right, username & password too, no problem there.

Please help me, starting to make me crazy :)

Guy

---

### Post by BlackLava on 2008-01-29
*Bump* sorry don't want to abuse but I've tried all day long and still can't fix that... I don't even know if the issue come from the sql server or from my linux server setup (both servers are mine btw, can change things on both sides)

---

