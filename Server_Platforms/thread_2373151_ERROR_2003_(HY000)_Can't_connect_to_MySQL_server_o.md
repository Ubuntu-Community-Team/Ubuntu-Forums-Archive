---
title: "ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.x.x' (111 &quot;Connection"
date: 2017-10-03
forum: Server Platforms
---

### Post by sanzo on 2017-10-03
Hi,
I've read so much 3d about that and I have
[LIST]
[*]binded mysqld to 0.0.0.0
[*]disabled my firewall
[*]granted all privileges to user root for all ip (%)
[*]flushed priviliges
[*]restarted mysqld service
[/LIST]

I cannot say what other to do, but if I try to mysql -h 192.168.x.x -u root -p I receive always the error in the title.

I need to connect to mysql remotely because I use a data integration tool to extract data from it.

Using a different DB Tool I'm able to connect if I use an SSH Tunnel and then if I use localhost as connection host, but I can't do this in my data integration tool.

Can you help me?

Another strange thing is that if I do
root@myhost:/etc/mysql# lsof -Pni :3306
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mysqld  1364 mysql   19u  IPv4  17221      0t0  TCP 127.0.0.1:3306 (LISTEN)

It seems to ignore my binding to 0.0.0.0

Thanks

---

### Post by darkod on 2017-10-03
Well, first confim it is really binded to 0.0.0.0.
```
sudo netstat -plunt | grep mysql
```

Then, I think you are not aware that connecting remotely you are connecting from user@ip or user@hostname or user@fqdn format. Depending on your case, you need to grant the correct permissions for the correct connection format. Mysql is very picky about that. You should be able to see the exact format of the connection by running on the mysql server:
```
sudo tail -f /var/log/syslog
```

Then try to connect remotely and it should show the error and connection format.

But first make sure the binding above is correct, otherwise it won't work remotely anyway. Maybe that's the part that is not working for you.

It is very simple, you just need to uncomment the bind command, save the file, and restart mysql.

---

### Post by sanzo on 2017-10-03
Hi and thanks,
First of all the binding seems correct, I'll show the output
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      1360/mysqld

When I try to connect while tail is tailing :) I can read
ct  3 16:01:38 WEBSRV01 mysqld: 171003 16:01:38 [Warning] IP address '192.168.y.y' could not be resolved: Name or service not known

Where '192.168.y.y'  is the ip of the pc that is trying to connect.

---

### Post by sanzo on 2017-10-03
I don't know what is changed, but now it's working :eek: thanks

---

