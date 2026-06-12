---
title: "MySQL Port Problem"
date: 2010-09-15
forum: Server Platforms
---

### Post by arthurbuliva on 2010-09-15
Hi,

Am having trouble getting MySQL to be accessed externally to my server. At first I thought it was a firewall issue. After tinkering with it, I decided to uninstall it altogether, but still no luck. At least that rules out IPTABLES.

Now, take a look at this anomaly:

```
$ telnet localhost 3306
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
$ mysql -p -h localhost -P 3306
Enter password:
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 89
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

What's going on please?

---

### Post by Ryan Dwyer on 2010-09-15
Have you configured it to bind to your external address in /etc/mysql/my.cnf?

---

### Post by arthurbuliva on 2010-09-15
Yes, the parameter "bind-address" has been set to the IP address of the server

---

### Post by Ryan Dwyer on 2010-09-15
I'm not sure what else to suggest then. I just did it without any problems.

```

ryan@laptop:~$ sudo nano /etc/mysql/my.cnf 
[sudo] password for ryan:          
# I set bind-address = 192.168.2.199
ryan@laptop:~$ ifconfig
<snip>
          inet addr:192.168.2.199  Bcast:192.168.2.255  Mask:255.255.255.0
<snip>
# Confirmed IP address is correct
ryan@laptop:~$ sudo service mysql restart
mysql start/running, process 22165
ryan@laptop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO) # mysql is working
ryan@laptop:~$ telnet localhost 3306
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
# Same result as you
ryan@laptop:~$ ssh pc
ryan@ryan-pc:~$ mysql -h 192.168.2.199 -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'ryan-pc' (using password: YES)
# Working, but I probably have MySQL's root set to only allow logins from localhost

```

So I guess not being able to telnet is normal. What happens when you try to connect from the remote machine?

---

### Post by arthurbuliva on 2010-09-15
```
ERROR 2003 (HY000): Can't connect to MySQL server on '***.***.***.**' (111)
```

---

### Post by rubylaser on 2010-09-15
You can't set the bind-address to the server ip.  That will only allow connections from that ip.  So, any remote connection will fail. You need to comment out that line and restart mysql.  Then use iptables and the mysql user permissions to prevent unauthorized connections.

Something like this in iptables.
```

# Allows Client mysql request for backup 167.14.190.225 is remote sql host, 10.1.1.5 is mysql client
-A INPUT -p tcp -s 10.1.1.5 --sport 1024:65535 -d 167.14.190.225 --dport 3306 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p tcp -s 167.14.190.225 --sport 3306 -d 10.1.1.5 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

```

Mysql create user
```

GRANT ALL PRIVILEGES ON *.* TO 'user'@'remote_ip_address' IDENTIFIED BY '<Password>' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;

```

Hope that helps.

---

