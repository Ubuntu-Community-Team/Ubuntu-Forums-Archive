---
title: "Can't connect to Mysql server from LAN"
date: 2010-11-19
forum: Server Platforms
---

### Post by Tilex on 2010-11-19
Hi guys,

I've looked everywhere for this (simple) problem, and I can't get this working.  

I have a mysql server on my LAN which is accessible from within the server.

I want to access the mysql server from another computer on the LAN, but it never works.

The MySQL server is started :
```
$ ps aux | grep mysql
mysql    18205  0.1  0.2 188780 31316 ?        Ssl  11:31   0:00 /usr/sbin/mysqld
```

The MySQL server binds to all interfacs in /etc/mysql/my.cnf :
```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address = 127.0.0.1
```

And the proof is :
```

$ netstat -l --numeric-ports | grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     

```

I even added a rule to make sure the port is open in the iptables :
```

sudo iptables -I INPUT -p tcp --dport 3306 -j ACCEPT

```

But still, to no avail.

Any ideas ?  Oh and yes, the user/password have been checked/reset many times so that can't be the problem ! :p

---

### Post by DaithiF on 2010-11-19
in the my.cnf snippet you posted bind-address is set to 127.0.0.1 -- this line should be commented out if you want to listen on all network interfaces as opposed to just localhost

---

### Post by Tilex on 2010-11-19
Yes, you're right, it actually was commented out but I copied/pasted the line without the # in front, my bad.

Thanks for pointed that out, though!

---

### Post by DaithiF on 2010-11-19
yes i thought that might be the case since your netstat output showed it listening on all interfaces.

anything on the client end interfering -- client firewall ?

one way to test is (on the server):
```
telnet localhost 3306

```
hit return a couple of times, you'll get a string showing mysql version #, and then it will close the connection.

try the same using the servers lan address:
```
telent x.x.x.x 3306
```

and see if you get the same ... if not then you've a problem with the server.  if that works ok but you can't do the same from the client machine(s) then you've got a problem at the client end.

---

### Post by Tilex on 2010-11-19
Yes, it works for localhost, but not for my LAN IP:
```

$ telnet 10.0.1.187 3306
Trying 10.0.1.187...
Connected to 10.0.1.187.
Escape character is '^]'.
CHost '10.0.1.187' is not allowed to connect to this MySQL serverConnection closed by foreign host.

```
Weird.

I just tried to allow ALL traffic on the LAN:
```

$ sudo ufw allow from 10.0.1.0/24

```

and still, can't connect using my LAN IP.

Any other suggestions ? :)

---

### Post by DaithiF on 2010-11-19
**'10.0.1.187' is not allowed to connect to this MySQL server**

What Host do you have set in the mysql.user table for the user you are trying to connect as?  If you have specific IP addresses (or localhost) set there rather than the wildcard '%' then that will be your problem.

by default you may have entries like this:
```
 Host        User    
 ----------  ------- 
 127.0.0.1   root    
 localhost   root    
```

but to connect from another host you would need either a wildcard entry:
 %           root    
 
or else additional entries per-IP you want to connect from

---

### Post by Tilex on 2010-11-19
Hi DaithiF, thanks for your quick reply !

I've looked at my mysql.user table, and the entries there are all encoded like :
  HOST                    User
3132372e302e302e31	726f6f74

Do you know what they're encoded into so I can add a new line with my IP+root ?

Thanks !

---

### Post by DaithiF on 2010-11-19
strange, what are you using to view those? (they're ascii codes in hex by the way -- 127.0.0.1 root)

you can issue this sql command at the mysql command prompt:
```
select Host, User from mysql.user;
```

easiest way to add a new entry is to use the create user command, and then grant privileges to whatever resources you want, e.g.:
```
create user dave@'%' identified by 'password';
grant all on somedatabase.* to dave@'%';
flush privileges;

```

---

### Post by Javier Bracero on 2012-05-21
Hi,
I've got remote access to MySql Server. Basically I've change the mysql.conf and I've added access to some of my remotes IP and users. Please have a look the following post to read all the process.

[http://javierbracero.blogspot.co.uk/2012/05/how-to-enable-remote-access-to-mysql.html](http://javierbracero.blogspot.co.uk/2012/05/how-to-enable-remote-access-to-mysql.html)
[]("http://javierbracero.blogspot.co.uk/2012/05/how-to-enable-remote-access-to-mysql.html")

---

