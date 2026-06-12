---
title: "Problem with home webserver (XAMPP)"
date: 2009-09-14
forum: Server Platforms
---

### Post by maverick90 on 2009-09-14
Hi!

A few days ago I installed apache on my computer in order to configure webserver at home. Later, I deleted apache installation (/etc/apache2), and installed XAMPP (because of php and mySQL support).
I configured port forwarding in router:
External port: 8989
Internal port : 80

Now, when someone types "[my ip]:8989" in their browser they get default apache page saying "It works", instead of webpage i put in XAMPP folder. For some time my webpage used to work, but then it started to show that "It works" page.
I searched for all index.html files on computer, and neither of them contains "It works!".
Maybe you guys know how to resolve this problem.

//I have Ubuntu 9.04

---

### Post by abaden on 2009-09-14
What does 
```
sudo dpkg --get-selections | grep apache 
```
yield? Also, what happens when you type localhost in in your browser? Do you get the default page or your site? And is xampp running? If xampp is running properly you should be able to go to [http://localhost/xampp](http://localhost/xampp) and find a configuration page.


Alex

---

### Post by maverick90 on 2009-09-15
```
sudo dpkg --get-selections | grep apache
```gives one line:
```
libapache2-mod-php5                deinstall
```When I type localhost in my browser, I get my webpage. It only works when XAMPP is running.
But, "It works" page works always, when Xampp is running and also when Xampp is not running.

I also changed the default httpd folder for xampp (/opt/lampp/htdocs), and now it is /home/maverick/Public/WWW (and also made proper change in httpd.conf file).

---

### Post by abaden on 2009-09-15
Interesting. Have you rebooted since all this? I would check the httpd.conf file again just to make sure you didn't miss anything too. I'm not too familiar with xampp, but it sounds like you either have a configuration error or some sort of ghost apache process going. Did you try to compile apache from source?


Alex

---

### Post by maverick90 on 2009-09-15
I solved it. The problem was in router settings for port forwarding - the local IP address for my computer was not set properly. So I think that the router forwarded to the other computer in my LAN, and showed "It works" page from that computer.
Now everything works fine.
Anyway, thank you very much for trying to help.

---

