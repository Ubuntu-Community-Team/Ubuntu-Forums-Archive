---
title: "Help! MySQL(Ubuntu Server) Windows clients"
date: 2007-05-02
forum: Server Platforms
---

### Post by Carlos Pena on 2007-05-02
I am trying to connect from Windows computer to an Ubuntu 6.06 Server running MySQL Server, but i can. 

First of all, i could not assign a root password with the commands:

sudo mysqladmin -u root password xxxxxxxxxxx

nor

sudo mysqladmin -p -u root -h localhost password xxxxxxxxxx

These command allways gives me an error, i don't know what i am doing wrong.

I really apreciate any help.

Carlos Pena 
Santo Domingo, Dominican Republic

---

### Post by rickyjones on 2007-05-02
Could you post the actual error message that you receive? It would help in figuring out what's going on.

Also - I fail to see how this has to do with Windows clients? It sounds like you are trying to set a password on the root MYSQL account on the server.

-Richard

---

### Post by garba on 2007-05-03
bear in mind that the mysql root account has nothing to do with the unix root account, no need to issue mysqladmin through sudo, anyway, if you provide us with some extra info we might be able to help

---

### Post by Carlos Pena on 2007-05-04
Hi.

Thank you for your help.

I have an Ubuntu 6.06 Server (default LAMP server installation). Linux server name LinuxED all other names and parameters as default.
I want to access this server MySQL database from Windows stations VB applications. In order to do than I know that need to install MySQL server on my Ubuntu 6.06 server and connect the Windows clients by using the "Windows ODBC Data Source Administrator". I downloaded and installed the MySQL ODBC 3.51.14 Driver on Windows workstations. 

I followed the instructions for installing the MySQL server on Ubuntu 6.06 Server. Please, let me know if i am doing something wrong on these steps.

sudo apt-get install mysql-server mysql-client

then

sudo netstat -tap | grep mysql

The command returns:

tcp  0   0  localhost:mysql    *:*   LISTEN   3726/mysqld

Then, when i run the mysqladmin command as shown in the documentation, the system do not accept it. For example:

sudo mysqladmin -u root  password mypass

the system returns:
mysqladmin: connect to server 'localhost' failed.
error 'Access denied for user 'root'@'localhost' (Using Password: NO)

Then, i tryed to type parameters in other way. So, i tried this:

sudo mysqladmin -uroot -pmypass

Now, the system returns a summary. I don't know if this means the command is succesfull or not. 
Assuming this is correct, i go to the next step.

sudo mysqladmin -p -u root -h localhost password mypass

The system returns: 
Error: 'Access denied for user 'root'@'localhost' (Using Password=YES)

Assuming the same parameters problem, i typed in other way:

sudo mysqladmin -p -uroot -hlocalhost --password=mypass
The system shows a summary like the other one.

At this time, I tried to connect from Windows Stations and ODBC Connector don't find the MySQL server.
Also I edited the my.cnf and insert a comment character ("#") to the "Bind-Address: 127,0,0,1" parameter and restart the MySQL. 

Please, i appreciate any help with this. 
Sorry for my english.

Carlos Pena
Santo Domingo, Dominican Republic

---

### Post by nomb on 2007-05-04
First try to get it working locally.  I had a very similar problem which turned out to be a problem with my admin password in the grant table.  

Try this:

stop mysql
start mysql with the --skip-grant-table option
login as root (mysql -u root)
then change your root password
flush the table
exit
restart mysql and try again to login.

Once you get it working locally then we'll get you going from your windows box.

---

### Post by Carlos Pena on 2007-05-04
It doesn't work!

I can stop, start the mysql, but there is no way to execute ' mysql -u root' command. It allways denies me the root @ localhost.

---

### Post by nomb on 2007-05-04
> **Carlos Pena said:**
> It doesn't work!

I can stop, start the mysql, but there is no way to execute ' mysql -u root' command. It allways denies me the root @ localhost.

After you stopped it what was the command you used to start it again?

---

### Post by Carlos Pena on 2007-05-04
I reinstalled everything from zero again. 

Now i think is running fine, but locally. I can run "mysql -u root -p"  (not "mysql -u root") to enter SQL console and run some select's, show's SQL statements.

I failed to connect from a Windows computer again. 

The Windows MySQL ODBC Connector always return this error: 

[MySQL][ODBC 3.51 Driver]Unknown MySQL server host 'mysql' (11001)

I tried several server host names (on Win ODBC driver server field)  like 'mysql', 'MySQL', 'MYSQL', 'localhost'. 'ubuntu/mysql' and just blank field.

This have been very hard to me, but i think we are very close to solve the problem. 

Thank you again for your help.

Carlos Pena

---

### Post by rickyjones on 2007-05-04
The error from windows means that it can't find the server... try to put the IP adress of your MySQL server in there instead of a name.

-Richard

---

### Post by mudoch on 2007-05-04
rickyjones is correct, the problem would be that the PC name, used in the Win ODBC, on which mysql is installed is not correct or if it was then the network does not list the PC name in the DNS. One can deal with the missing dns by editing the hosts file on each windows pc.  Also make sure your odbc has the correct DB username and password.  

On the note of username and password, using mysql, I´d add a user that is granted just enough rights to manage the DB you want users to have access to, DO NOT USE the root USER of the MYSQL as that user can drop tables, dbs, grant rights, etc.....   Read up on MYSql there are a ton of books on the product.  Also since you have a LAMP try phpMyAdmin web interface I like it over the command line MYSQL admin tool.  I setup mine in a directory /var/www/phpMyAdmin and access it from multiple PCs to admin the MySQL on the Ubunto server.

---

### Post by Carlos Pena on 2007-05-05
The ODBC connector does not accept ip addresses on server name field. I tryed everything. The MySQL server is running fine, but locally on linux server.

---

### Post by mudoch on 2007-05-05
Just checked my configs, I´m using MySQL in windows for other work.....   You are correct, confused another SQL engine there. sorry...  

I found another item Ubuntu may have a firewall up and running blocking port 3306 (MySQL comm port) for external access.   Right now I´m getting the can not resolve host when trying to run ODBC or even Windows MySQL admin. Which is consistent with your findings.

OK so where do we go from here?  I´d do a check on the Windows side to be sure there is no blockage of the port 3306 there.  That being clear then we both need the assistance of others here to expose port 3306 to the local net from the Ubuntu PC.

That done, you can do either of the following : 

                       get the Ubuntu PC registered within the DNS server that your Win boxes get DNS resolved 
                       add the Ubuntu PC IP to each Win PCs %SystemRoot%\System32\Drivers\Etc\Hosts file.

---

### Post by Carlos Pena on 2007-05-08
Hi,

MySQL is working fine since yesterday. I exported two tables from MSSQL to MySQL and modify a VB6 application to work with it. It runs very well. The tables has at least 120,000 records. I experienced other problems related to connection string parameters, but I found a full explanation and examples on mysql.com.  
In other hand, I found that MySQL is slower than MSSQL Lite (MSDE running on NT). I will change Windows server anyway.  Do you know any tips to improve performance of MySQL?

I want to thanks to everybody in this forum who spend their time to help me with my problem. 

Thank you guys!

Carlos R. Pena
Santo Domingo, Dominican Republic

---

### Post by mudoch on 2007-05-08
Question what fixed the access to the MySQL, I'm getting a no response for the Ubuntu server instance, my Win MySQL instance I have no issues, thought it was a firewall port block... because locally on the Ubuntu system I have no issues accessing.... It's just one of those things very low on my list to do, Right now I'm trying to setup a website which uses MySQL.

---

### Post by Carlos Pena on 2007-05-08
Remeber to edit the /etc/mysql/my.conf file and remark (put a #) the 'bind-address = 127,0,0,1'. This allows mysql to accept non local requests.

In my case, the problem was with the user name or privileges. When i reinstall everything again i create a new user, flush privileges and EUREKA!. On Mysql console I typed this:

GRANT ALL PRIVILEGES ON *.* TO 'xxxx'@'%' IDENTIFIED BY 'password' WITH GRAND OPTION;
FLUSH PRIVILEGES;

I hope this can help you.

Carlos Pena

---

