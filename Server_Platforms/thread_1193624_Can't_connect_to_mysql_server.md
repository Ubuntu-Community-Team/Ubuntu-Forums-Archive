---
title: "Can't connect to mysql server"
date: 2009-06-21
forum: Server Platforms
---

### Post by Jonasu on 2009-06-21
Hello all :D

Okay, first of all, i don't know if this is the correct forum to ask this.
Anyways..

This problem is kind of hard to explain, but I'll try the best i can.
So what I have done is to allow remote connections to mysql, what I did was just to edit "bind-address" to 192.168.1.20 witch is my servers ip address in "my.cnf", after that I opened the mysql port 3306
```

sudo /sbin/iptables -A INPUT -i eth0 -s 192.168.1.0/24 -p tcp --dastination-port 3306 -j ACCEPT

```Then I allowed my "not server-machine" in mysql commandline. 
```

update db set Host='192.168.1.42' where Db='webdb';
update user set Host='192.168.1.42' where user='webadmin';

```So now I have done everything to connect to my Db from my "not server-machine", and I tried to connect with an application on windows called SQLyog, and it worked!

But the problem came when I tried to connect with php:
```

    $sql_username="*******";
    $sql_password="******";
    
    $sql_server='192.168.1.20';
    
    $sql_usrtb="usr_db";

    $con=mysql_connect($sql_server,$sql_username,$sql_password);
    if ($con)
    {
        echo "Connection pwnd!!!";
    }
    else
    {
        echo mysql_error();
    }

```This did not work..
The error message I'm getting is:
```

Warning: mysql_connect() [function.mysql-connect]: Host '192.168.1.20' is not allowed to connect to this MySQL server in /hdd/web/desktop/www/info.php on line 10
Host '192.168.1.20' is not allowed to connect to this MySQL server

```Why won't it work!? Whats wrong!? Why isn't the server itself allowed to connect to the mysql server, why did it work with sqlyog and not php!? Is there something with the php setup? Pleas help!
Thanks in advance!

---

### Post by Kareeser on 2009-06-21
I like your choice in "connection succesful" messages :)

I looks as though in your attempt to allow your remote server to connect to MySQL, you inadvertantly blocked localhost from connecting to it.

Please humour me: The initial value for "bind-address" was 127.0.0.1, yes? And now you've changed it to 192.168.1.20?

---

### Post by Jonasu on 2009-06-22
> **Kareeser said:**
> I like your choice in "connection succesful" messages :)

I looks as though in your attempt to allow your remote server to connect to MySQL, you inadvertantly blocked localhost from connecting to it.

Please humour me: The initial value for "bind-address" was 127.0.0.1, yes? And now you've changed it to 192.168.1.20?

Yes. I just followed a tutorial witch allowed remote connections to mysql db. Maybe it is wrong, but I don't know. Pleas help if you got any suggestions. :D

---

### Post by JeppeM on 2009-06-22
See what happens if you take out the bind-address? If i remember right, it will then bind to all interfaces of the server, and then you should be able to connect to it from both localhost and remote...

In your config file, you can add a # infront of the bind-address line, which will comment it out... then you just need to restart mysqld :)

---

### Post by Jonasu on 2009-06-22
> **JeppeM said:**
> See what happens if you take out the bind-address? If i remember right, it will then bind to all interfaces of the server, and then you should be able to connect to it from both localhost and remote...

In your config file, you can add a # infront of the bind-address line, which will comment it out... then you just need to restart mysqld :)

Wow, thanks. But it seems like I manage to fix it another way. 
The problem was that i needed to open up ports for 192.168.1.20 (my server-machine) and 192.168.1.42 (my "not server-machine"). Then add privileges for the specified mysql user for each ip address.
To get phpmyadmin to work again I had to edit "/etc/phpmyadmin/conf.inc.php" and change localhost to 192.168.1.20 (Witch is my server-machine) and remove the coments in this line:
```

$cfg['Servers'][$i]['host'] = '192.168.1.20';

```

Anyway, thanks for helping me!
This thread is now solved!

---

