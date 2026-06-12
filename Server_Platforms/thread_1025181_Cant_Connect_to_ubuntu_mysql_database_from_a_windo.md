---
title: "Cant Connect to ubuntu mysql database from a windows machine"
date: 2008-12-29
forum: Server Platforms
---

### Post by UltraDangerLord on 2008-12-29
Hello all,

I made a mysql user granted all the privileges and I cant connect threw my windows odbc machine. I did the same exact steps on freebsd and got in no problem is there a extra step that im missing in general ? I also installed the odbc drivers for linux, did'nt seem to make a difference.


*sorry for the half *** post i g2g*

---

### Post by cariboo on 2008-12-29
Have you set up your user to allow him to connect remotely? To reconfigure the user ssh into your server and at the prompt open the mysql console:

```
mysql -u <user> -p
```

When in the console type:

```
grant all privileges on *.* to <user>@'%' identified by '<password>' with grant option;
```

of course change <user> and <password> to your mysql user and password, with the above entered your user should be able to connect to mysql remotely.

Jim

---

### Post by Thirtysixway on 2008-12-29
I thought I read somewhere that by default, mysql only listens on localhost for connections.  It may be in the configuration somewhere ontop of granting access per user.

---

### Post by lykwydchykyn on 2008-12-30
> **Thirtysixway said:**
> I thought I read somewhere that by default, mysql only listens on localhost for connections.  It may be in the configuration somewhere ontop of granting access per user.

This is correct.  By default, mysql only listens to requests from the server itself (which is what you'd want if you were doing, for instance, a LAMP server where Apache talks to MySQL on the same box).

To change that, edit /etc/mysql/my.cnf.  find the line that says:
```

bind-address = 127.0.0.1

```
and change 127.0.0.1 to the IP of your server.  Then restart mysql.

---

