---
title: "I dont get it, I follow the MySQL installation instructions and it doesnt work"
date: 2006-10-30
forum: Server Platforms
---

### Post by Danyael X on 2006-10-30
Hi!


I've installed a LAMP server on an old computer I have it was running Dapper, but I upgraded it to Edgy with apt-get dist-upgrade, before the upgrade I had not done anything to it, it was a fresh install. 

After upgrading, I decided to follow the instructions for MySQL Configuration found [here]("https://help.ubuntu.com/ubuntu/serverguide/C/databases.html")

The first step when with out any problem 
[INDENT]sudo mysqladmin -u root password newrootsqlpassword[/INDENT]

but the second step give me an error message and refuses to work
[INDENT]sudo mysqladmin -u root -h localhost password newrootsqlpassword[/INDENT]
I've tired it with the same pasword that I used in the first step and with a completly new password and all I get is the same error messages
[INDENT]Access denied for user 'root'@'localhost' (using password: YES)[/INDENT]
or
[INDENT]Access denied for user 'root'@'localhost' (using password: NO)[/INDENT]

I've done a search on this problem on the forum but I didnt get any help from it. I am a complete MySQL newbie =) and I do apologize if this is a case of RTFM.

Thank you for you help on this matter 

Chris D. Vighagen

---

### Post by Danyael X on 2006-10-30
Okay I found this after some more searching 
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

But I dont quite see how this can help me since there is one root password that is okay.

If some one could explain what the second step of the MySQL configuration does maybe I can find a solution on my own?

Again I give thanks for any help on this subject !

Chris ](*,)

---

### Post by laceiba on 2006-11-02
Any luck? I am in the same boat as you. I followed the same directions and now I cannot do anything.

---

### Post by laceiba on 2006-11-02
I may have an answer. Try:

```
mysql -u root -p
```

You should get prompted for your password and you should be able to get in and create databases, users, change passwords, etc...

---

### Post by clarkth on 2006-11-02
Try this site.  I had the same problem and had to log into mySQL root without a password and manually update the user table.

[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

---

### Post by DannyG on 2006-11-03
In console, type ```
hostname
``` and ```
hostname -f
``` Assuming both results are the same, then do ```
sudo mysqladmin -u root -h YOURHOSTNAME password newrootsqlpassword
``` which will create a MySQL username and password for MySQL connections that are NOT on localhost. The first command you did created the username and password for localhost connections.

If this still doesnt work, try ```
mysql -u root -p
``` using the password you created on the first command, this will log you into MySQL. The from here, try ```
-u root -h YOURHOSTNAME password newrootsqlpassword
``` again.

Daniel.

---

### Post by Abhi Kalyan on 2006-11-04
> **DannyG said:**
> In console, type ```
hostname
``` and ```
hostname -f
``` Assuming both results are the same, then do ```
sudo mysqladmin -u root -h YOURHOSTNAME password newrootsqlpassword
``` which will create a MySQL username and password for MySQL connections that are NOT on localhost. The first command you did created the username and password for localhost connections.

If this still doesnt work, try ```
mysql -u root -p
``` using the password you created on the first command, this will log you into MySQL. The from here, try ```
-u root -h YOURHOSTNAME password newrootsqlpassword
``` again.

Daniel.

Folowing in on the foot steps mate!!!!

---

### Post by druhboruch on 2006-11-12
I am still unable to get it to work.  There are multiple threads about this / or similar problems.

I can login to my server using mysql -u root -p

I am unable to login from the network or by using my hostname.

MySql-Admin crashes in User Administration section.

Should I file a bug?

Could anyone help?

Update:

I am running Edgy now.  Mysql works fine on dapper

---

### Post by elst on 2006-11-12
MySQL typically has *two* root accounts: root@localhost for local connections, and root@% for remote access. As these accounts are totally separate they may have different passwords. If local access with root works and remote access fails then most of the time it's because the root@% has a different password.

I would login however you can and select * from mysql.users to look at the user accounts to figure out what's going on.

Abhi Kalyan has explained how to reset the accounts, if you need to.

Hope that helps

---

### Post by druhboruch on 2006-11-12
Thank you for replying.
mysql> select host, user, password from mysql.user
    -> ;
+-----------+------------------+------------------+
| host      | user             | password         |
+-----------+------------------+------------------+
| localhost | root             | 7d31776f03964108 | 
| eft       | root             | 7d31776f03964108 | 
| localhost | debian-sys-maint | 6fd3994377bcf249 | 
+-----------+------------------+------------------+
4 rows in set (0.00 sec)

It looks all good to me...

user@eft:~$ sudo mysqladmin -u root -h localhost password mypass
Password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Please, some suggestions

---

### Post by elst on 2006-11-12
Perhaps try this:

Enter the mysql client with:

mysql -u root -p

Enter your root@localhost password when prompted.

Run these commands:

USE mysql;
UPDATE user SET password = PASSWORD('yourpassword') WHERE user LIKE 'root';
FLUSH PRIVILEGES;
EXIT;

Obviously, this resets all of the "root" accounts to the same password.

Remember to flush the client history file after setting passwords:

echo > .mysql_history

Hope that helps - IMO, this is the most confusing aspect of MySQL.

---

### Post by druhboruch on 2006-11-12
I have done what you suggested but it still does not work:

Update returned:

Query OK, 0 rows affected (0.00 sec)
Rows matched: 2  Changed: 0  Warnings: 0

Is there anything else I could try?

Am I the only one with this problem?

EDIT:

I fixed the problem by following the howto forge guide:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

It is necessary to configure host and hostname files before mysql installation.

---

### Post by Abhi Kalyan on 2006-11-13
> **druhboruch said:**
> I have done what you suggested but it still does not work:

Update returned:

Query OK, 0 rows affected (0.00 sec)
Rows matched: 2  Changed: 0  Warnings: 0

Is there anything else I could try?

Am I the only one with this problem?

EDIT:

I fixed the problem by following the howto forge guide:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

It is necessary to configure host and hostname files before mysql installation.

Dear druhboruch,
I did have similar problems with MYSQL, but now its up and running. Seen below is the illistraion of how i installed mysql and the other necessary wares to get it alltogether.

case A: Installing MYsql.
MYsql installation seems to remain common for all distros.
getting the package.
instead of using apt-get i had it installed using synaptic.
Step 1: search for 'mysql-server-5.0' in synaptic, mark for installation. This should also mark the client and you would in all probability have mysql-common already installed. if not mark it too.
wait for the installation to completye.
Step 2: after the installation is over close synaptic, this is only to remove all doubts.
step 3: open a terminal and type the following [the following procedure is to set a password for the root]
SYNTAX:
mysqladmin -u root password newpassword
Ex: My systems name is "viki" and my user name is "zen, hence the prompt that i get is
zen@viki:~$
at this prompt i type
zen@viki:~$sudo mysqladmin -u root password ss1947#%$^

Where "ss1947#%$^" is the password.
Hit enter after typing the same
The system shuld ask you the following
Enter password: Here type in your sudo password (that is the password for the logged in user)
Dont expect to have any relys. the system just returns to a prompt if all went well (i.e)
zen@viki:~$
.
Now you have mysql installed and running with a root user and password in place.Summary
1. Install pysql server and client with common,
2. setting the root password.

What you could do next is use phpmyadmin to administer mysql over a GUI. for this you need 
1. phpmyadmin installed.
This cannot be directly installed as a prerequisite you need the following installed and running.
1. Apache2  - web server
2. PHP5 -
3. MYSql5 server adn client + common
4. php5-mysql support for apache2 
plus all the other dependencies.

Only after the above are up and running can 
phpmyadmin be installed.
once you install phpmyadmin
please go to
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)
you should get a nice login page where:
login name: root
password: your password for sql entered in SYNTAX.

Cheers , all the best please do post in if you succeded. Never let go,
Sincerely
Abhi Kalyan

---

