---
title: "mysql database setup"
date: 2008-11-08
forum: Server Platforms
---

### Post by kami_iwinaru on 2008-11-08
So I was following this tutorial on how to set up a mail server using 7.10 found at [http://flurdy.com/docs/postfix/#install](http://flurdy.com/docs/postfix/#install). I think I'm fine all the way up to the part where I have to make the mysql Database. When I type in the code:
```
mysqladmin -u root password *password_i_choose*
```
it returns with:
```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
So I entered in
```
ls /etc/rc2.d | grep mysql
```
and in turn, it returns with
```
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
```
Then I typed
```
pgrep mysqld
```
The first time it didn't return anything, so I was told to reboot. After I did that and ran the code again, it returned with:
```
6468
6446
```
So I tried this again:
```
mysqladmin -u root password *password_i_choose*
```
it returns with:
```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
AGAIN.
And then when I enter
```
mysql -u root -p
```
it comes up with
```
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

I've tried everything that I used. Is there a way to reset it all?

And just to make sure I'm doing this right, the code is 
```
mysqladmin -u root password *password_i_choose*
```

Correct?

---

### Post by cariboo on 2008-11-09
The easiest way I have found to rest the root password for mysql is to do the following:

```
sudo dpkg-reconfigure mysql-server-5.0
```

This will allow you to set a new root password for mysql.

I usually like to set another user with full privileges by enter the following in the mysql console:

```
grant all privileges on *.* to <user>@'localhost' identified by '<password>' with grant option;
```

then

```
grant all privileges on *.* to <user>@'%' identified by '<password>' with grant option;
```

the second command allows me to remotely access mysql directly from another computer on the network.

Jim

---

### Post by MaindotC on 2008-11-09
I suggested to OP on instant message the other night to install phpmyadmin.  For some reason I don't have as many issues logging into a database or executing queries and it's a nice graphical interface that is widely used.

What really confuses me is that there are different ways of passing in the password.  For example, some people suggest using:
```

-p<password>

```
Here, the password is right next to the -p.  This invokes the prompt:
```

Enter password:

```
And when I enter the password it says "Unable to execute command <password>" because it read my previous entry for the password as the command to be executed.  Frustrating.  Some people suggest:
```

-p "<password"

```
When I use this method, I am prompted the same way and the same error.  I've never understood why this happens.  Clearly I have not read every document concerning the use of MySQL but just getting this simple command to work only works once (the first time) and never again.  I use phpmyadmin to login and I don't have any problems.

---

### Post by thmarth on 2008-11-09
To strAlan, there are generally two ways to login to mysql using either mysqladmin or mysql.

```
mysqladmin -u *user* -p
```
```
mysql -u *user* -p
```
This will make it prompt for the password, this is the safest way.

```
mysqladmin -u *user* --password=*password*
```
```
mysql -u *user* --password=*password*
```
This will make you login right away.
Note the equal sign, this tells the program that *password* is to be set as the value for the password input.

Hope this clears it up.

---

### Post by cariboo on 2008-11-09
> mysql -u user --password=password

The only problem with the above is that your password is echoed in plain text for all the shoulder surfers to see. Plus:

```
mysql -u <user> -p
```

is way less to type :)

Jim

---

### Post by MaindotC on 2008-11-11
> **thmarth said:**
> To strAlan, there are generally two ways to login to mysql using either mysqladmin or mysql.

```
mysqladmin -u *user* -p
```
```
mysql -u *user* -p
```
This will make it prompt for the password, this is the safest way.

```
mysqladmin -u *user* --password=*password*
```
```
mysql -u *user* --password=*password*
```
This will make you login right away.
Note the equal sign, this tells the program that *password* is to be set as the value for the password input.

Hope this clears it up.

the mysqladmin command doesn't really work - at least not what I expect it to do.  If you use mysql command here's the output:
```

amd64@amd64-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.51a-3ubuntu5.3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

```
Which is what I'd like to see - a prompt that is ready to accept commands.  If you use the mysqladmin here's the output:
```

amd64@amd64-desktop:~$ mysqladmin -u root -p
mysqladmin  Ver 8.41 Distrib 5.0.51a, for debian-linux-gnu on x86_64
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Administration program for the mysqld daemon.
Usage: mysqladmin [OPTIONS] command command....
  -c, --count=#       Number of iterations to make. This works with -i
                      (--sleep) only.
  -#, --debug[=name]  Output debug log. Often this is 'd:t:o,filename'.
  -f, --force         Don't ask for confirmation on drop database; with
                      multiple commands, continue even if an error occurs.
  -C, --compress      Use compression in server/client protocol.
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
                      Set the default character set.
  -?, --help          Display this help and exit.
  -h, --host=name     Connect to host.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: Providing a
                      password on command line is insecure as it is visible
                      through /proc to anyone for a short time.
  -P, --port=#        Port number to use for connection.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -r, --relative      Show difference between current and previous values when
                      used with -i. Currently works only with extended-status.
  -O, --set-variable=name 
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  -s, --silent        Silently exit if one can't connect to server.
  -S, --socket=name   Socket file to use for connection.
  -i, --sleep=#       Execute commands again and again with a sleep between.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -u, --user=name     User for login if not current user.
  -v, --verbose       Write more information.
  -V, --version       Output version information and exit.
  -E, --vertical      Print output vertically. Is similar to --relative, but
                      prints output vertically.
  -w, --wait[=#]      Wait and retry if connection is down.
  --connect_timeout=# 
  --shutdown_timeout=# 

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
count                             0
force                             FALSE
compress                          FALSE
character-sets-dir                (No default value)
default-character-set             (No default value)
host                              (No default value)
port                              3306
relative                          FALSE
socket                            /var/run/mysqld/mysqld.sock
sleep                             0
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
user                              root
verbose                           FALSE
vertical                          FALSE
connect_timeout                   43200
shutdown_timeout                  3600

Default options are read from the following files in the given order:
/etc/mysql/my.cnf ~/.my.cnf /usr/etc/my.cnf 
The following groups are read: mysqladmin client
The following options may be given as the first argument:
--print-defaults	Print the program argument list and exit
--no-defaults		Don't read default options from any options file
--defaults-file=#	Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Where command is a one or more of: (Commands may be shortened)
  create databasename	Create a new database
  debug			Instruct server to write debug information to log
  drop databasename	Delete a database and all its tables
  extended-status       Gives an extended status message from the server
  flush-hosts           Flush all cached hosts
  flush-logs            Flush all logs
  flush-status		Clear status variables
  flush-tables          Flush all tables
  flush-threads         Flush the thread cache
  flush-privileges      Reload grant tables (same as reload)
  kill id,id,...	Kill mysql threads
  password new-password Change old password to new-password, MySQL 4.1 hashing.
  old-password new-password Change old password to new-password in old format.

  ping			Check if mysqld is alive
  processlist		Show list of active threads in server
  reload		Reload grant tables
  refresh		Flush all tables and close and open logfiles
  shutdown		Take server down
  status		Gives a short status message from the server
  start-slave		Start slave
  stop-slave		Stop slave
  variables             Prints variables available
  version		Get version info from server
amd64@amd64-desktop:~$

```

Is that what is supposed to happen? Why doesn't it just prompt me for the password?

---

### Post by guitsy on 2009-07-11
hi friend.
the solution which worked for me
 
install webmin. to install webmin

Preparing Your System

You need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Download latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)

Now we have webmin_1.340_all.deb package you need to install using the following command

sudo dpkg -i webmin_1.340_all.deb

If your server complains that there is some library things does not find. Just run the following command

sudo apt- get install -f

You should now be able to login to Webmin at the URL [https://localhost:10000/](https://localhost:10000/)

go to webmin login
click on mysql
click change password option,put ur new password.....now on terminal type.

mysql -uroot  -p ..........bingoo......

---

