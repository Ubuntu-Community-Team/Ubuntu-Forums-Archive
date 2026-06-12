---
title: "mythtv and mysql help.  ERROR 1045: Access denied for user: 'root@localhost'"
date: 2005-11-07
forum: Server Platforms
---

### Post by fragmental on 2005-11-07
First off, I should say that I know very little about mythtv or mysql.  All I wanted was a working tv recorder so I could record 2 or 3 shows throughout the week.

I was trying to install mythtv, but all i really did at first was install the mythtv package and then forget about it.  I think, after that I was getting the error

```
Setting up mythtv-database (0.18.1-5) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.18.1-5); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured

```
 every time I install a package, but I can't quite remember if it was the same thing.  I'm getting the error now, anyway.

I finally went to the trouble of trying to find some directions and do it the right way, and when I tried to add a password I accidentally left off the brackets and typed 
```
UPDATE user SET Password=PASSWORD(password) WHERE user='root';
```
instead of
```
(<password>)
``` 

Now I get the error 
```
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)
```

if I type mysql -u root -p

and if I run mysql-admin I can log in using root with no password but if I click on "user administration" I get the error "Could not retrieve user privilege information."

and if I run phpmyadmin and login with root and no password it says "no privileges" under "create new database"

I don't know what's wrong.  In trying to get it to work, I was only stabbing in the dark and I can hardly remember what I did now.

I could really use someone's help, because I've already spent hours on this and it's very frustrating and depresssing.

Edit: I should also say that I had no idea which forum to put this in.  There is no "applications support" forum for Breezy, where I would have put this, probably.

---

### Post by fluffy on 2005-11-08
first of all uninstall mythtv and anything else so u get back to a clean system
then install mysql and make sure it is running and has thr right users in place
then install mythtv

try this from a command line:
 apt-get remove mythtv

now add this to your sources.list:
 deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

then do:
 apt-get update
 apt-get install mysql-server-5.0
 apt-get install mythtv

see how u get on from there
;)

---

### Post by fragmental on 2005-11-09
[QUOTE=fluffy]first of all uninstall mythtv and anything else so u get back to a clean system
then install mysql and make sure it is running and has thr right users in place
then install mythtv

try this from a command line:
 apt-get remove mythtv

now add this to your sources.list:
 deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

then do:
 apt-get update
 apt-get install mysql-server-5.0
 apt-get install mythtv

see how u get on from there
;)[/QUOTE]

I should mention that earlier I tried uninstalling mysql and mythtv and reinstalling and also running dpkg-reconfigure on the packages.

I did what you suggested and then I tried

```
stewart@StUbuntu:/var/lib/mysql$ mysql -u root mysql
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
stewart@StUbuntu:/var/lib/mysql$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 13 to server version: 5.0.15-Debian_0.dotdeb.1-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE user SET Password=PASSWORD('<password>') WHERE user='root'     -> FLUSH PRIVILEGES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FLUSH PRIVILEGES' at line 2
mysql> FLUSH PRIVILEGES;
ERROR 1227 (42000): Access denied; you need the RELOAD privilege for this operation
mysql> RELOAD PRIVILEGES;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'RELOAD PRIVILEGES' at line 1
mysql> RELOAD;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'RELOAD' at line 1
mysql> quit
Bye
stewart@StUbuntu:/var/lib/mysql$ mysql -u root -p mysql
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
stewart@StUbuntu:/var/lib/mysql$ mysql -u root -p mysql
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
stewart@StUbuntu:/var/lib/mysql$ mysql -u root mysql
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'

```

As you can see, I don't know what I'm doing, but regardless, it's not working.

Is there a way that I can completely start from scratch with mysql?  I guess I could delete the config files and the stuff in /var/lib/mysql?

Edit:  I tried resetting the password via these instructions:
```
 Alternatively, on any platform, you can set the new password using the mysql client(but this approach is less secure):

   1.

      Stop mysqld and restart it with the --skip-grant-tables --user=root options (Windows users omit the --user=root portion).
   2.

      Connect to the mysqld server with this command:

shell> mysql -u root

   3.

      Issue the following statements in the mysql client:

mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
    ->                   WHERE User='root';
mysql> FLUSH PRIVILEGES;

      Replace &#8220;newpwd&#8221; with the actual root password that you want to use.
   4.

      You should be able to connect using the new password.
```

and I got this:

```
stewart@StUbuntu:~$ mysqld -skip-grant-tables --user=root
051109 12:51:22 [ERROR] mysqld: unknown option '-k'

stewart@StUbuntu:~$ mysqld --skip-grant-tables --user=root
051109 12:51:43 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line

051109 12:51:43 [Warning] Can't create test file /var/lib/mysql/StUbuntu.lower-test
051109 12:51:43 [Warning] One can only use the --user switch if running as root

051109 12:51:43  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
```

I thought this line "051109 12:51:43 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line" was pretty interesting.  Sounds like that could be the problem, maybe?  I don't know. I just want to delete everything and start over again.  I'mnot planning on using my mysql database for anything besides mythtv, so I probably won't touch it again once it's working.

---

### Post by fluffy on 2005-11-10
ok ... i installed mysql5 with no problems at all using a simple apt-get install mysql-server-5.0 ... afaik initially there is no root password ... are u installing from the dotdeb archive or an ubuntu archive?

---

### Post by fragmental on 2005-11-10
It installed fine, it was the stuff I did after it to try to get mythtv to work, that messed it up.

---

### Post by fragmental on 2005-11-10
I deleted everything in /var/lib/mysql and ran "dpkg-reconfigure mysql-server-5.0" and after that I set the password using phpmyadmin.  Everything seems ok now except that I haven't quit gotten mythtv completely setup yet.  It's pretty complicated.

---

### Post by mcewen98 on 2005-11-10
[QUOTE=fragmental]I deleted everything in /var/lib/mysql and ran "dpkg-reconfigure mysql-server-5.0" and after that I set the password using phpmyadmin.  Everything seems ok now except that I haven't quit gotten mythtv completely setup yet.  It's pretty complicated.[/QUOTE]

You may want to try taking at look at these sites. They helped me a lot with my setup:

[http://www.abarbaccia.com/](http://www.abarbaccia.com/)
[http://www.cs.duke.edu/~reynolds/pvr150/](http://www.cs.duke.edu/~reynolds/pvr150/)

Also, it took me a while to realized that I needed to set my cable to HRC instead of standard.

---

### Post by randu on 2007-11-28
hi,
went i try to do backup of databases to Administrator. in log file apper
Cannot connect to MySQL Server. Access denied for user 'root'@'localhost' (using password: NO) (Error Number 1045)

---

