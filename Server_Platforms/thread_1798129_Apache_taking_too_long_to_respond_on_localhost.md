---
title: "Apache taking too long to respond on localhost"
date: 2011-07-05
forum: Server Platforms
---

### Post by ufarmer on 2011-07-05
Hi,

I am following this howto to install Apache, MySQL, and PHP5:

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)

I have just installed Apache and I am pointing my browser to:

[http://192.168.0.100](http://192.168.0.100)

but I am getting the error message that the server is taking too long to respond.  I'm really new at this so any advice is appreciated.

Regards.

---

### Post by An Sanct on 2011-07-06
Try this: [localhost]("http://localhost") or through [IP]("http://127.0.0.1")

Or try reinstalling LAMP with this command

```
sudo apt-get install lamp-server^
```

---

