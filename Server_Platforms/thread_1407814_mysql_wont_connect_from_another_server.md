---
title: "mysql wont connect from another server"
date: 2010-02-15
forum: Server Platforms
---

### Post by torres87 on 2010-02-15
I've got my website hosted on a linux shared hosting account, at ip address 123.123.123.123 (I'll refer to this as the web server, example ip obviously).

I've just installed mysql server on a cloud hosted server running ubuntu (ip 456.456.456.456) where I'm hosting the mysql database for the website.

I believe I've configured mysql server correctly to allow for remote connections from both my home pc (using mysql query browser) and from the web server, by adding 2 entries to both the 'user' and 'db' tables in the mysql database. The 'host' column in both tables I set to the ip address of my home connection, and the other row to the shared ip of the web server (123.123.123.123).

The problem is I can connect from my home pc with no problems, and also from the cloud hosted ubuntu server (via localhost connection) but any page in which I use php to connect from the linux web server I get the following error:

```
Can't connect to MySQL server on '456.456.456.456' (4)
```

Here's the php code I'm using to connect, which works fine connecting to a database on localhost, but not to the remote database:


```
$db= array(

"hostname" => "456.456.456.456:3306",
"username" => "root",
"password" => "password",
"database" => "app"
);

//connect to database
$link = mysql_connect($db["hostname"], $db["username"], $db["password"]);

if (!$link) {
	die(mysql_error());
}
```


The cloud hosted server I'm running is Ubuntu server which I'm not hugely experienced in managing. Currently I'm doing everything through a SSH connection.

Can anyone help?

---

### Post by cdenley on 2010-02-15
By default, mysql only listens on 127.0.0.1 to prevent remote connections.
```

grep bind-address /etc/mysql/my.cnf
sudo netstat -tlnp

```

---

### Post by torres87 on 2010-02-15
I've added the new bind-address line and restarted everything, but it still won't connect:
```
#bind-address           = 127.0.0.1
bind-address            = 456.456.456.456
```

The netstat -tlnp command gives the following:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 456.456.456.456:3306     0.0.0.0:*               LISTEN      3863/mysqld
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      27773/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2502/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      3304/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      2502/sshd
```

---

### Post by noway2 on 2010-02-16
You aren't getting a network connection to MySQL.  Is 456.456.456.456 a LAN address (behind a NAT router)?  Yes, I know it is a hosted site, but that doesn't necessarilly mean you aren't behind some form of address converter.  Perform ifconfig on the server to be sure what its IP address is.  For debug purposes either remove the bind-address directive or set it to 0.0.0.0 (note your netstat output - this is how apache is listening too).

---

### Post by cdenley on 2010-02-16
You should just comment that line out since mysql will listen on all interfaces if "bind-address" is not specified. Since it is listening, you should be able to establish a TCP connection.
```

nc -z -v 456.456.456.456 3306

```
If not, then you have some kind of networking or firewall issue.

---

### Post by mbehamin on 2010-02-18
when you connect to the mysql check your permission of the user you authenticate. 
for example 
**CREATE USER 'test'@'localhost' IDENTIFIED BY 'test_password';**

this assign test can login the server only from localhost address.

---

