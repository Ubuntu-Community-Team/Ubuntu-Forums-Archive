---
title: "[SOLVED] mysql no root user"
date: 2008-08-08
forum: Server Platforms
---

### Post by baudday on 2008-08-08
okay i followed the instructions on the ubuntu server documentation site for installing mysql on my server, and it says during the installation it says you will be prompted to provide a password for the root user, or something along those lines. when i installed it (through the terminal, cause that's what they were talking about) i was never prompted, now i have the problem of not having any root account. i tried uninstalling and installing it again, and i wasn't prompted then either. when i try to manage the db i can login as my usernam and no password, but i can't change anything at all. i'm not sure if this is a problem or justa  step i'm missing, but i would really appreciate some help.

thanks

P.S. I'm running Ubuntu 8.04 LTS Server Edition

---

### Post by y@w on 2008-08-08
So you can login as root with no password? If so, it's fine.. you'll just need to change your password: [http://www.cyberciti.biz/faq/mysql-change-root-password/](http://www.cyberciti.biz/faq/mysql-change-root-password/)

---

### Post by baudday on 2008-08-09
no root with no password does not work. my username with no password works, but i have no privelages when i do that. i can't even change my own password.

---

### Post by tinny on 2008-08-09
So you cant login like this...?

```

mysql -u root

```

If not you may need to run the MySQL install DB script.

```

cd /usr/bin/
./mysql_install_db

```

---

### Post by y@w on 2008-08-09
I found a guide on how to reset the mysql root password: [http://www.tech-faq.com/reset-mysql-password.shtml](http://www.tech-faq.com/reset-mysql-password.shtml)

---

### Post by baudday on 2008-08-09
> **tinny said:**
> So you cant login like this...?

```

mysql -u root

```

If not you may need to run the MySQL install DB script.

```

cd /usr/bin/
./mysql_install_db

```

this is what i got
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

I will take a look at that guide as soon as I get a chance.

---

### Post by tinny on 2008-08-09
> **baudday said:**
> this is what i got
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

I will take a look at that guide as soon as I get a chance.

I think that you have a root user but dont know the password.

Here is how you can reset the root password

```

sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables
mysql -u root
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 
mysql> flush privileges
mysql> quit
sudo killall mysqld
sudo /etc/init.d/mysql start

```

---

### Post by cariboo on 2008-08-09
The simplest way to reconfigure the root password in mysql is to do in a terminal:

```
sudo dpkg-reconfigure mysql-server-5.0
```

Jim

---

### Post by baudday on 2008-08-10
> **cariboo907 said:**
> The simplest way to reconfigure the root password in mysql is to do in a terminal:

```
sudo dpkg-reconfigure mysql-server-5.0
```

Jim

Thanks to everyone, Jim's way was quick and painless. But thanks to everyone that cared enough to post a solution.

---

