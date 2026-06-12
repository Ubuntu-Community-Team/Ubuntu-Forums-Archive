---
title: "Lost connection to MySQL server at 'reading initial communication packet', system err"
date: 2012-08-10
forum: Server Platforms
---

### Post by Maheriano on 2012-08-10
I'm trying to connect to the database on my server using MySQL Workbench and it gives me this error. All the credentials are correct and I can connect fine from the command line. Any ideas?

---

### Post by Maheriano on 2012-08-10
I managed to allow the connection but there's still a problem. I logged into the database and added my user with my host IP at home:
> grant all on database.* to user@'my-public-ip' identified by 'user-password';
and then
> flush privileges;
This allowed me to gain access from this specific IP at my house but how can I grant access from anywhere for this user?

---

### Post by SeijiSensei on 2012-08-10
Grant all privileges to 'user'@'%'.

If by "anywhere" you really mean anywhere, then you'd better have a strong password on this user's account.

---

### Post by Maheriano on 2012-08-21
> **SeijiSensei said:**
> Grant all privileges to 'user'@'%'.

If by "anywhere" you really mean anywhere, then you'd better have a strong password on this user's account.

Isn't this how CPanel works? I know with any CPanel created database I can access it from anywhere. Am I doing anything wrong?

---

### Post by Wim Sturkenboom on 2012-08-22
> 
Isn't this how CPanel works?


Not familiar with it but not likely. CPanel is a webbased interface running on a webserver (if I'm not mistaken), so you use a browser to connect. If you want to do something on the mysql server (e.g. add a table), it's executed by the webserver.

Unless you use a SSL connection on your mysql server, don't use any type of mysql client from a machine anywhere on the internet. Your password will be picked up in no time.

---

### Post by Maheriano on 2012-08-23
> **Wim Sturkenboom said:**
> Not familiar with it but not likely. CPanel is a webbased interface running on a webserver (if I'm not mistaken), so you use a browser to connect. If you want to do something on the mysql server (e.g. add a table), it's executed by the webserver.

Unless you use a SSL connection on your mysql server, don't use any type of mysql client from a machine anywhere on the internet. Your password will be picked up in no time.

All of my current MySQL databases set up in CPanel are accessible from any machine using MySQL Workbench which is an application from MySQL specifically for connecting to those databases. Does that mean they're unsafe?

---

### Post by Wim Sturkenboom on 2012-08-24
In my opinion, if you access database directly over the internet, it's unsafe unless you use SSL. You can start reading [http://dev.mysql.com/doc/refman/5.0/en/secure-basics.html](http://dev.mysql.com/doc/refman/5.0/en/secure-basics.html)

---

