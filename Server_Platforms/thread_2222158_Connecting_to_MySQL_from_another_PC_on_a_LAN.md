---
title: "Connecting to MySQL from another PC on a LAN"
date: 2014-05-05
forum: Server Platforms
---

### Post by Eric_Snyder on 2014-05-05
I have a MySQL server running and different software packaged locally installed connecting. I am trying to connect from another computer on the LAN. I have created a user with permission from any host but I still cannot connect.

I am using MySQL Workbench to attempt the connection with. I get no helpful message from Workbench.

Checking with nmap I see that 3306 is mapped to MySQL and is open.

I had this ability 6 months ago but not now.

I have also tried root with the admin password. NO luck.

I am stumped.

---

### Post by SeijiSensei on 2014-05-05
You checked with nmap from the machine you are trying to connect from, right?  You cannot check from the server itself, since nmap will use localhost which is generally permitted to connect to anything.

Install **mysql-client-core-5.5** on the client machine if it's not installed already, then try
```
mysql -u username -p -h ip.of.the.server dbname
```
Does that work?

It's possible that MySQL on the server is configured only to listen on localhost; that's the Ubuntu default for security reasons.  Look in my.cnf for this:
```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

```
Comment out the bind-address line and restart the server with "sudo service mysql restart".

---

### Post by Eric_Snyder on 2014-05-05
It was the bind. Thankls

---

