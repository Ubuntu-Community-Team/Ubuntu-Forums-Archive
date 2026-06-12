---
title: "XAMPP for Linux 1.7.2 helpp me"
date: 2009-09-13
forum: Server Platforms
---

### Post by I WILL DO IT on 2009-09-13
Am trying to run XAMPP for Linux 1.7.2 but i get this error i did everything the web site told me to.....

[http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)

Can some one fix this?


root@cool-desktop:~/Desktop# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.2...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.
root@cool-desktop:~/Desktop#

---

### Post by yeats on 2009-09-13
So... what do you see when you point a browser to 

[http://localhost/](http://localhost/)

(assuming your browser is running on the same station as the server...)?

---

### Post by volkswagner on 2009-09-13
If it is already running try a restart.

```
/opt/lampp/lampp restart
```

or a stop then start command.

```
/opt/lampp/lampp stop
```

```
/opt/lampp/lampp start
```

---

