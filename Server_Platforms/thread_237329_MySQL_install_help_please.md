---
title: "MySQL install help please"
date: 2006-08-16
forum: Server Platforms
---

### Post by Katje on 2006-08-16
I am trying to learn LAMP right now and am having issues setting up my MySQL database.  I have been following the "How to install MYSQL Database Server" instructions off of the Unoffical Ubuntu Starter Guide.  Everything was working great until I tried to do this comand:

> mysqladmin -h root@local-machine-name -u root password your-new-password

And I get this error:

> mysqladmin: connect to server at 'root@COMPUTER' failed
error: 'Unknown MySQL server host 'root@COMPUTER' (1)'
Check that mysqld is running on root@COMPUTER and that the port is 3306.
You can check this by doing 'telnet root@COMPUTER 3306'


So I tried to check to see if mysqld was on my computer and I got this message:

> telnet: could not resolve root@COMPUTER/3306: Name or service not known


If anyone could please tell me what I'm doing wrong I would really appreciate it.  I am really looking forward to learning LAMP and can't wait to start.

---

### Post by LordHunter317 on 2006-08-16
Don't provdie the -h switch or argument, it's totally unnecessary.

---

### Post by statue on 2006-08-16
I had the exact same problem and spent a good deal of time trying to figure out what the hell I was doing wrong. Turns out that the guide is wrong when it comes to this step. Leave out the "@" and it should work.

---

### Post by az on 2006-08-16
> **LordHunter317 said:**
> Don't provdie the -h switch or argument, it's totally unnecessary.

Is that because it does not listen to the network by default?  Is that unique to Dapper or Ubuntu?

In some mysql docs, it reccommends to set two root passwords, one for the localhost and one for the network.  Is that correct?

---

### Post by LordHunter317 on 2006-08-16
> **azz said:**
> Is that because it does not listen to the network by default?No, it's just cause the guide is wrong, period.

> In some mysql docs, it reccommends to set two root passwords, one for the localhost and one for the network.  Is that correct?No, it's plain lunacy.  The fact that MySQL treats the same username coming from a different host as a different security prinicipal is also lunacy.  

Never, ever treat foo@host1 and foo@host2 differently.  You will be very sorry if you do.  Make sure you curse MySQL AB every time you run a GRANT/REVOKE for not understanding how to properly do authentication.

---

### Post by Katje on 2006-08-16
Thank you everyone for the quick response and your suggestions.

I have tried what LordHunter317 and statue suggested.  By leaving the @ out like statue suggested I got the same error as before.  When I left the -h out like LordHunter317 suggested I recived this message:
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


---

### Post by LordHunter317 on 2006-08-16
That implies to me a password was already set.

If you do: 'mysql -u root -p' and enter whatever you set teh password to, can you connect?

---

### Post by Katje on 2006-08-16
No I can't.  I got this message when I tried that command:
> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


---

### Post by LordHunter317 on 2006-08-16
Try -h 127.0.0.1, but it shouldn't matter.

---

### Post by Freddd on 2006-08-23
I have the same problem as the author of this thread. How to solve it?

---

### Post by anindya_m on 2006-08-23
Are you sure mysqld is running. Try ```
ps aux | grep mysql
```

---

### Post by Freddd on 2006-08-23
ERROR 1045 (28000): Access denied for user 'joel'@'localhost' (using password: NO)

---

### Post by Freddd on 2006-08-23
> **anindya_m said:**
> Are you sure mysqld is running. Try ```
ps aux | grep mysql
```root      4860  0.0  0.1   2656  1328 ?        S    Aug23   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4924  0.0  1.6 126400 17060 ?        Sl   Aug23   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4925  0.0  0.0   1548   500 ?        S    Aug23   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
joel      6680  0.2  1.4  42104 15520 ?        S    Aug23   0:07 /usr/bin/mysql-admin
joel      8061  0.0  0.0   2888   812 pts/0    R+   00:38   0:00 grep mysql

---

### Post by anindya_m on 2006-08-23
Ok so mysqld is running. We will try to reset the root password and try afresh. Can you try the followng (as root):

First stop the mysqld daemon.

Next start it manually with the command ```
mysqld --skip-grant-tables
```(The above command runs mysql in unrestricted mode, meaning anyone can log in).

Next run ```
mysql -u root
```This should give a prompt. Run ```
UPDATE user SET Password=PASSWORD('new password'') where USER='root';
FLUSH PRIVILEGES;
```

Stop the deamon with ```
killall mysqld
```and start it normally. Next run ```
mysql -u root -p
```Are you able to connect?

---

### Post by qopax on 2006-08-27
I'm basically having the same problem. I'm able to connect when I ```
mysql -u root -p
```

But I still cannot get ```
mysqladmin -h root@boom-server -u root password mypass
``` to work. 

If I do it without the -h argument I get ```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

If I do it with or without '@boom-server' I get ```
mysqladmin: connect to server at 'root@boom-server' failed
error: 'Unknown MySQL server host 'root@boom-server' (4)'
Check that mysqld is running on root@boom-server and that the port is 3306.
You can check this by doing 'telnet root@boom-server 3306'

```

Any other suggestions?

---

### Post by capitalistpiglet on 2006-09-06
Im having exactly the same problem, does anyone know a solution for this?

---

### Post by rastilin on 2006-09-08
Well I've only ever needed to type "sudo mysqladmin -u root password 'passwd'" and it's always worked. I suspect that mysqladmin MUST be run as root before it will accept a password for an account and I haven't had any luck making it accept a password for anything other than the root account.

---

### Post by davrobnz on 2006-09-10
Had a similar problem recently with a WAMP server.
You could try this:

SET PASSWORD FOR 'some_user'@'some_host' = OLD_PASSWORD('newpwd');

This relates to MySQL 5 using a password hashing algorithm that is incompatible with older clients.

See [http://dev.mysql.com/doc/refman/5.0/en/old-client.html]("http://dev.mysql.com/doc/refman/5.0/en/old-client.html")
for further info.

Hope this helps
David

---

### Post by BoneKracker on 2006-09-11
```
[COLOR="Red"]sudo[/COLOR] mysql -u root password foobar
```

then once it's set up it's just

```
mysql -u root -p
```

or whatever username you are using


setting a user like root twice (once for local and once for other) is actually not a bad idea if you want to limit privileges while remote for security reasons, but a preferable option would be to make root localhost ONLY and create a less-privileged admin account that has access from other hosts.

---

### Post by az on 2006-09-11
> **BoneKracker said:**
> ```
[COLOR="Red"]sudo[/COLOR] mysql -u root password foobar
```

There is absolutely no need to run sudo here.


> **BoneKracker said:**
> 
setting a user like root twice (once for local and once for other) is actually not a bad idea if you want to limit privileges while remote for security reasons, but a preferable option would be to make root localhost ONLY and create a less-privileged admin account that has access from other hosts.

Well, that's the question, isn't it.  By default, mysql in Ubuntu does not listen for connections from the network, so you will not be able to connect as any user unless you enable that.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150](https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150)

But If I set the mysql root password from localhost, and do not set it with -h, what happens if I listen for connections from the network and try to use the root user remotely?

---

### Post by BoneKracker on 2006-09-11
sorry - you're right.

I guess I corrected some other error and tried sudo at the same time (bad "fault isolation").  That's what worked and I jotted down.  Figured it was only required for initial setup as some sort of measure of protection for the unpassword-protected accounts, since it worked without it later.

At any rate - somebody should correct whatever guide is being referred to.

I went by the documentation from MySQL (which is unfortunately somewhat Redhat-family biased).  Still useful, though.

[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

---

### Post by nserdinsky on 2006-09-16
Just an FYI. I believe the How-to that is being referenced here is:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

The sequence of commands that are:

1) Install all packages (I used Synaptic): MySQL, MySQP-admain, phpmsql, phpmyadmin, etc
2) mysqladmin -u root password mynewpassword
3) mysqladmin -h localhost -u root -p password mynewpassword
4) sudo /etc/init.d/mysql restart
5) point browswer to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by bluevoodoo1 on 2006-09-20
> **nserdinsky said:**
> Just an FYI. I believe the How-to that is being referenced here is:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

The sequence of commands that are:

1) Install all packages (I used Synaptic): MySQL, MySQP-admain, phpmsql, phpmyadmin, etc
2) mysqladmin -u root password mynewpassword
3) mysqladmin -h localhost -u root -p password mynewpassword
4) sudo /etc/init.d/mysql restart
5) point browswer to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Awesome. Thanks! Works like a charm!

---

