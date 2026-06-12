---
title: "can't make mysql server work"
date: 2012-10-09
forum: Server Platforms
---

### Post by muzycales on 2012-10-09
Hi guys. I have finally moved away from OS-X. After a few days of unsuccessful attempts I was finally able to install apache2, php5 and I almost got mysql. I've managed to start apache2 and mysql. Both can be stopped/started or/and restarted from the /etc/init.d/...

The first issue I'd like to work on is to be able to see any mysql modules when testing the php server with the "phpinfo()" function. Currently there isn't any mysql module displayed.  

The second issue is related to accessing  phpmyadmin (that I installed using synaptic). 

When I go to [http://localhost/myphpadmin](http://localhost/myphpadmin)   -- I get this error: " The [*mysqli*]("http://localhost/phpmyadmin/url.php?url=http%3A%2F%2Fphp.net%2Fmanual%2Fen%2Fbook.mysqli.php&token=80beb14c2fcdea0742fcfd59a36fdcf5") extension is missing. Please check your PHP configuration.
----

Things I've tried :

I changed and enabled the "mysqli.allow.onfile" in the php.ini file (with no success)
I changed and enabled the "extension=mysql.so" to "mysqli" (with no result). 

----

I was wondering if somebody could walk me really quickly through the process of connecting mysql server to the php. My Ubuntu version is 12.0.4. Thank you very much in advance.

---

### Post by Cheesemill on 2012-10-09
Have you installed php5-mysql ?

Also it shouldn't take days to set up a LAMP server, you only need one command on a fresh installation to install Apache, MySQL and PHP:
```
sudo apt-get install lamp-server^
```

---

### Post by muzycales on 2012-10-10
> **Cheesemill said:**
> Have you installed php5-mysql ?

Also it shouldn't take days to set up a LAMP server, you only need one command on a fresh installation to install Apache, MySQL and PHP:
```
sudo apt-get install lamp-server^
```

Hi Cheesemill

Thank you for your answer. I've finally managed to install the three servers. Unfortunately it took me more than three days. I got a bunch of random errors and because this was the first time I've installed lamp I did it wrong -for a few times. But the good news is that I've finally managed to have lamp running and it's beautiful. I love it. Thanks much.

---

