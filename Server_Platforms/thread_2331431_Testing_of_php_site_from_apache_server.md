---
title: "Testing of php site from apache server"
date: 2016-07-22
forum: Server Platforms
---

### Post by doranlum on 2016-07-22
Hi all,

I have setup a apache/php ubuntu server and tested with a simple php file which works. I also setup a different mysql ubuntu server with myphpadmin.

On my laptop I was using XAMPP to code my php websites and after that I copy the php & html files over to /home/user/Sites on the apache/php server. I also load the db into the mysql server.

The website doesn't seem to be working. Am I missing something here ?

---

### Post by Habitual on 2016-07-22
what's in /var/www/html/ ?

---

### Post by SeijiSensei on 2016-07-22
Do you have configuration files in /etc/apache2/sites-available/ that point to /home/user/Sites as the DocumentRoot?

If the problem is that the scripts cannot talk to the MySQL server, that's because Ubuntu binds MySQL to the localhost interface by default so it is not visible over the network.  You need to edit /etc/mysql/my.cnf and disable that by putting a hash mark in front of the bind-address directive like this:
```

#bind-address = 127.0.0.1

```
Then restart MySQL.  However if the MySQL server is visible over the Internet, you'll need to add a firewalling rule to block access to port 3306 from anywhere other than your server(s).

---

### Post by doranlum on 2016-07-22
> **Habitual said:**
> what's in /var/www/html/ ?

Hi, I didn't configure /var/www/html/ because my understanding is that this is for static webpage. It's only index.html file inside that directory which I left it untouched.

---

### Post by howefield on 2016-07-22
Moved to the "*Server Platforms*" forum.

---

### Post by doranlum on 2016-07-22
> **SeijiSensei said:**
> Do you have configuration files in /etc/apache2/sites-available/ that point to /home/user/Sites as the DocumentRoot?

If the problem is that the scripts cannot talk to the MySQL server, that's because Ubuntu binds MySQL to the localhost interface by default so it is not visible over the network.  You need to edit /etc/mysql/my.cnf and disable that by putting a hash mark in front of the bind-address directive like this:
```

#bind-address = 127.0.0.1

```
Then restart MySQL.  However if the MySQL server is visible over the Internet, you'll need to add a firewalling rule to block access to port 3306 from anywhere other than your server(s).

I can see "000-default.conf" "default-ssl.conf" which I have not touch yet. Should I configure anything in this two conf file to point to mysql ?

let me check on mysql server my.cnf file first.

---

### Post by SeijiSensei on 2016-07-23
If you haven't created a custom configuration, then you are using the one in 000-default.conf.  That sets /var/www/html as the main website directory through the DocumentRoot directive.  If you want to use another directory, you have to either change 000-default.conf or create a new custom configuration with a different ServerName.  If this is your first time out, just put your files in /var/www/html and see how things go.  You'll need to copy the files with "sudo" since /var/www/html is owned by the root user.

---

