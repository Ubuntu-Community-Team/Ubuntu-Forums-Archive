---
title: "mysql server hostname"
date: 2008-09-07
forum: Server Platforms
---

### Post by gjj391 on 2008-09-07
Playing around with managing my own VPS.

How would set it up so I connect to my mysqlserver remotely from like mysqlAdministator on my computer at home ?

I did the default mysqlserver package...

---

### Post by gishaust on 2008-09-07
there is to ways I use to access mysql server remotely are the following
1.putty for mirosoft machines
2. I my linux laptop ssh from the terminal eg gishaust@mycomputernameoripaddress

note that your server would need ssh server. Using putty or you have to make sure that you open ports and firewall is another issue on your server. But you can do it. It also depends on your work situation any what type of access that you are allowed to use???

3 You can use phpadmin that will allow you to access through a webpage.

---

### Post by cariboo on 2008-09-08
Another way to setup remote access is like this open mysql in a terminal then type:

```
grant all privileges on *.* to <user>@'%'
identified by '<password>' with grant option;
``` 

where <user> is you username without the brackets and <password> is your mysql password without the brackets.

I not sure if this will work from outside your local network, but give it a try.

Jim

---

