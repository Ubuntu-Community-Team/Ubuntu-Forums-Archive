---
title: "mysql - connection from an other computer"
date: 2010-09-04
forum: Server Platforms
---

### Post by borobudur on 2010-09-04
Hi, I would like to connect to my mysql server which is running on a server in the house (192.168.1.10).
I would like to connect to the mysql server from an other machine (192.168.1.93). 

I tried to configure this in the my.cnf file with the bind-address = 192.168.1.93 
If I add this then I can't restart the server anymore.

In the log file I find this:
```
mysql bind-address Can't start server: Bind on TCP/IP port: Cannot assign requested address
```

Any idea?

---

### Post by koenn on 2010-09-04
you have to put in the address of the server where mysql runs, not the address of the machine you want to connect from.

---

### Post by de0xyrib0se on 2010-09-04
On which server did you add the bind statement? 192.168.1.10 or 192.168.1.93?

If you added it on 192.168.1.10 then obviously it cant bind to that address and needs to bind to 192.168.1.10.

---

### Post by jeight on 2010-09-04
I think you are making it more complicated than it needs to be. Just make sure your server and client know each other in /etc/hosts. Then you could install something like webadmin to control mySQL from a browser on either computer.

---

### Post by de0xyrib0se on 2010-09-04
If his server is not binding to the proper IP he cant manage it from the network, just like he cant access it from other servers...

---

### Post by koenn on 2010-09-05
> **jeight said:**
> I think you are making it more complicated than it needs to be. Just make sure your server and client know each other in /etc/hosts. Then you could install something like webadmin to control mySQL from a browser on either computer.

nope, first you'd have to tell mysqld to listen on a network address (it only listens on the localhost address by default)

the OP's problem is not that he doesn't know *how* to configure mysql, it's that he's puting in wrong values.

---

### Post by TheFuturian on 2010-09-05
> **koenn said:**
> you have to put in the address of the server where mysql runs, not the address of the machine you want to connect from.

Agreed, in your example 192.168.1.10 is the value. You will also need to assign the correct permissions for users to access from remote hosts. I find the easiest way to accomplish this is with "PHPMyAdmin":-

```
sudo apt-get install phpmyadmin
```

Allow it to reconfigure apache as required, then access using [http://192.168.1.10/phpmyadmin](http://192.168.1.10/phpmyadmin).

Once you have the bind-address set correctly restart mysql:-

```
sudo service mysql restart
```

Now access your server through phpmyadmin and make sure either/or the correct global/database-specific privlidges are assigned. Once the privlidges are taken care of you should be able to use other remote tools to administer the database(s).

---

