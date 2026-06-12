---
title: "Access MySQL in ubuntu guest from WinXP Host"
date: 2010-07-03
forum: Server Platforms
---

### Post by railsfan on 2010-07-03
I have Virtualbox setup
 
WinXP Host
Ubuntu 10.04 is the guest
Mysql is installed in ubuntu and it works fine in the guest (ubuntu)
Internet works fine in the host and the guest. Bridged Network.
 
 
Now, here is the thing... i want to access mysql from my host to load some data into it.
 
how do i access mysql from my host Win XP?
 
Please help
 
thanks

---

### Post by sjinks on 2010-07-04
You will need to set the proper IP address for bind-address directive in /etc/mysql/my.cnf and set up user permissions in MySQL.

---

### Post by dapperdanny77 on 2010-07-04
if your network is working properly you need a mysql client to reach your server.
on server side you have to enable mysql to listen for remote connections

```

/etc/mysql/my.cnf:
bind-address            =     <your servers ip address>

```

the mysql user used for the connect must be enabled for remote connection see [http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html) for details.

---

### Post by railsfan on 2010-07-08
Thanks for the instructions. I will try this and update you.
 
Also, I have ruby on rails installed in ubuntu guest and want to access it from XP host.
 
**_Question - 1:_**
What I mean is, I can access 127.0.0.1:3000/myrubyapp_1  from ubuntu guest
How can i access this from XP host?
I understand i have to update <windows>/drivers/etc/hosts file, but since it is 127.0.0.1 it will always look at the XP's localhost.
Oh! as i am typing i can realize that i should get the ip address from ubuntu guest and then put that in the hosts file in XP host.
For example, ifconfig may return, 192.168.0.101 or whatever and this goes into the XPs host hosts file.
But, here is the thing, everytime, when i disconnent from network and reconnect, this ip address changes. so does it mean, i need to update the hosts file everytime the ip changes?
 
Or is there any other route?
 
**_Question - 2:_**
My ubuntu guest gets a new ip when i key in "sudo dhclient eth0" in ubuntu guest terminal.
FYI: yes i run this dhclient eth0 , everytime, i re-connect to my internal network.
otherwise, it doesn't connect to internet or home internal network.
 
 
 
Thanks
Radha

---

