---
title: "Now What"
date: 2010-01-09
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-09
Ok I have Ubuntu 9.1 setup, with ISPCONFIG3, squirrel mail, apache2, mysql, phpmyadmin, phpbb3 so now what, what do i need to do next to setup to get apache to display my website and where do i need to put my web files?

---

### Post by stlsaint on 2010-01-09
put all files that you want for website in the www dir

```
 /var/www 
```

then go to your ip address: 192.168.1.XXX or your public ip if you have port forwarding. Actually you can test now by going to your ip address now in your web browser and you should see the infamous: It Works!! showing that apache is up and running fine. If not than you need to start apache 
```
 sudo /etc/init.d/apache2 restart 
```
thats assuming you have apache2 from repos installed...then go back to web browser and enter ip address. 

NOTE: Before you add your own website files you need to remove the apache index.html file or else you will enter conflict if you have two index.html files.

Then you will see your own website or whatever you want displayed.

---

