---
title: "Optimize lamp server"
date: 2016-09-25
forum: Server Platforms
---

### Post by faggurten on 2016-09-25
Hello everyone, on friday im going to host a website from my IBM server. I would like to hear some recommendation about what the settings should be. Its my first time hosting a website with so many requests and clients.

Here are some details about the website:
12 static pages (html, css)
3 dymanic pages (php, mysql calls) (mostly login system and change of login data)
max 250 clients (totally max) i expect 150 online clients at all times
Mysql database with about 5 tables.
Phpmyadmin is also running
Without clients the server is using about 1500 mb ram

Details about my server:
IBM x3200 server (2006)
Intel (R) Xeon (R) X3210 2.13 GHz
8 GB of ram (4x Kingston 2 gb ddr2 667 ECC)

Network connection:
running only on lan (the clients are on the same lan)
1000mb connection to the switches where the clients are connected. But the clients switchs have only 100mb connection.

If you need more info or have any recommendation please comment :)

Sorry for bad english

---

### Post by SeijiSensei on 2016-09-25
Just use the stock configurations.  They'll work fine.  Web service is not a demanding task; I bet the load average on that machine will rarely break 0.1.  I have a virtual server at Linode that handles web service for about half-a-dozen sites (with both MySQL and PostgreSQL backends) and also accepts mail for the domains I manage.  Its current LA is 0.00, with a recent peak of 0.04.

---

