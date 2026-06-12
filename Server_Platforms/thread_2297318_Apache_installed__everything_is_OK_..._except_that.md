---
title: "Apache installed : everything is OK ... except that it does not work"
date: 2015-10-02
forum: Server Platforms
---

### Post by Dionisio_Dussart on 2015-10-02
[h=1]Forbidden[/h] You don't have permission to access / on this server.

 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80
[I]
That 403 page is what I get when I try to open with my browser the address [http://localhost](http://localhost)
Same result for [http://127.0.0.1](http://127.0.0.1)

Nonetheless I have entered as an administrator ("root") the instructions that I was told to execute ...
It's odd, isn't it ? How to debug that ? What is that (...) permission that I am asked before I can open localhost ?
What I did, without any error message displayed, is :
[/I]sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql

---

### Post by Habitual on 2015-10-02
usually
```
sudo chown www-data:www-data /var/www/html/
```

---

