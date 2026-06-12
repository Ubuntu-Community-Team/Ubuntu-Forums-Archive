---
title: "FYI - Ubuntu LAMP (Dapper) connection to MS SQL Server"
date: 2008-11-18
forum: Server Platforms
---

### Post by mahalie on 2008-11-18
After a lot of doc reading at PHP.net, FreeTDS and here and trying and then backing out of several attempts to get my Ubuntu Lamp on Dapper Drake LTS to connect via ODBC to a Microsoft SQL Server on our corporate network I found a step-by-step tutorial that worked for me here: [http://benlinus.blogspot.com/2007/08/ubuntu-610-building-mssql-module-in.html](http://benlinus.blogspot.com/2007/08/ubuntu-610-building-mssql-module-in.html)

Here is how I did it - already running working LAMP with PHP5. 

```
sudo apt-get install freetds-dev
sudo apt-get source php5
cd php5-5.1.2/ext/mssql
sudo apt-get install php5-dev
sudo phpize
sudo ./configure --with-mssql
sudo make
cd modules
cp mssql.so /usr/lib/php5/20051025
sudo vi /etc/php5/apache2/php.ini

```

add the following line:
```
extension = mssql.so
```

```
sudo /etc/init.d/apache2 restart
```

To confirm if MSSQL support is available, create a new php file and execute phpinfo() function. 

To test my connection tried code from PHP.net using MSSQL_CONNECT
[PHP]
<?php
// Server in the this format: <computer>\<instance name> or 
// <server>,<port> when using a non default port number

$server = 'DBSERVERNAME.corp.DOMAIN.com';

$link = mssql_connect($server, 'UserName', 'UserPassword');

if(!$link)
{
    die('Something went wrong while connecting to MSSQL');
}
?>
<h1>Test</h1>[/PHP]
If you don't have errors, it's working. If you have 'cannot open default DB' then make sure your permissions for the user is set property on the MS SQL server and that their default database is the one you are pointing at.

---

### Post by citybird on 2009-01-09
Was trying this and ran into all kinds of hell.

My solution:
Make a directory where you want to put all this crap while you work on it...

```
sudo apt-get install freetds-dev php5-dev
sudo apt-get source php5 freetds-dev
cd freetds-0.82
.configure
make
```

now you have to copy some files around so the install finds libtds.a|so because it's in a hidden dir called ~freetds-0.82/src/tds/.libs/

```
cd php5-5.x.x/ext/mssql

sudo phpize
sudo ./configure --with-mssql=../../freetds-0.82
sudo make
cd modules
cp mssql.so /usr/lib/php5/20060613
sudo vi /etc/php5/apache2/php.ini

```
and the rest you know.

---

### Post by citybird on 2009-01-09
Now it seems the only thing that will work is windows authentications on my MSSQL machine :-P

---

### Post by ethos84 on 2009-02-27
Guys having some issues with this, I getting:

sudo ./configure --with-mssql=/home/administrator/freetds-0.82

I recieve the error:
configure: error: Could not find /home/administrator/freetds-0.82/lib/libtds.a|so

Any ideas?

---

### Post by ethos84 on 2009-03-02
Bump if I may :)

---

