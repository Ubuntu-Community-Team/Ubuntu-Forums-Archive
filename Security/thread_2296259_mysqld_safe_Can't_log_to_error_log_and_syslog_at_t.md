---
title: "mysqld_safe Can't log to error log and syslog at the same time."
date: 2015-09-24
forum: Security
---

### Post by Nayara on 2015-09-24
Hello, I forgot my MySQL password, and following these steps to reset it...
[https://www.digitalocean.com/community/tutorials/how-to-import-and-export-databases-and-reset-a-root-password-in-mysql#how-to-reset-a-root-password-](https://www.digitalocean.com/community/tutorials/how-to-import-and-export-databases-and-reset-a-root-password-in-mysql#how-to-reset-a-root-password-)



When I type that command....


```
# mysqld_safe --skip-grant-tables
```


I get that message... How I fix it?
```
150924 14:01:12 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
150924 14:01:12 mysqld_safe Logging to '/var/log/mysql/error.log'.
150924 14:01:12 mysqld_safe A mysqld process already exists
```

---

### Post by Habitual on 2015-09-24
You could try 
```
sudo dpkg-reconfigure mysql-server
```
and it should prompt you for new root password, twice.

Start mysql-server normally after doing so.

---

### Post by Nayara on 2015-09-24
> **Habitual said:**
> You could try 
```
sudo dpkg-reconfigure mysql-server
```
and it should prompt you for new root password, twice.

Start mysql-server normally after doing so.

Hello!

I type that command you recommend me, but nothing was showed...

---

### Post by Habitual on 2015-09-24
show us the output of 
```
sudo dpkg -l | grep mysql
``` please.

---

### Post by Nayara on 2015-09-24
> **Habitual said:**
> show us the output of 
```
sudo dpkg -l | grep mysql
``` please.

Hello, that is the screen of my SSH console with that command:

[IMG]https://dl.dropboxusercontent.com/u/11826717/off/sudo.jpg[/IMG]

---

### Post by Habitual on 2015-09-25
Maybe try ```
sudo dpkg-reconfigure mysql-server-5.5
```?

---

