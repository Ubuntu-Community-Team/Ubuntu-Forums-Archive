---
title: "Re-Installing PHP 5"
date: 2009-01-15
forum: Server Platforms
---

### Post by ryezak on 2009-01-15
I am a complete Nubie with Linux. 
I am attempting at installing a LAMP server.
I had issues with the mysql at first. So I removed it complete then re-installed and it worked.
Now the PHP5 will not work. When I put the localhost address of my webserver in my browser with the testphp.php. It just wants to open the .php as a text file. 
How do completely purge and re-install the PHP5 and get it to work with Apache2?
tks

---

### Post by mregister on 2009-01-15
I would first try to re-install PHP5 with 
```
sudo apt-get -f install php5
```

---

### Post by mregister on 2009-01-15
also, I should have asked, will apache serve up any files correctly? Like can you pull up a test.html? If so then I would try the re-install of php above. If not then I would focus my attention on apache2.

---

### Post by mr.generic.user on 2009-01-15
maybe also reinstall libapache2-mod-php5 and php5-mysql packages....

---

