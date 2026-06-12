---
title: "How to connect with MySQL in Ubuntu?"
date: 2014-01-23
forum: Server Platforms
---

### Post by uzumakifahim on 2014-01-23
Hi,

I've installed XAMPP on my Ubuntu machine successfully. Everything is running fine. I can start all services by issuing the following command:

```
sudo /opt/lampp/lampp start
```

All services starts successfully.

Now I need to test MySQL from terminal, but when I'm giving the following command:

```
mysql -u root
```

to set root password. Or 

```
mysql -u root -p
```

it's showing the following message:

```
The program 'mysql' is currently not installed. You can install it by typing:sudo apt-get install mysql-client-core-5.5

```

I can't understand where the problem is. Please help me on this regard.

Thanks in advance.

---

### Post by sandyd on 2014-01-23
try
```

/opt/lampp/bin/mysql -u root
```
afaik, it is best to install mysql/php/apache from the Ubuntu repositories directly because security updates are provided automatically

---

### Post by uzumakifahim on 2014-01-24
Really thanks Sandyd. Your solution works perfectly for me. I can connect to MySQL now.

---

