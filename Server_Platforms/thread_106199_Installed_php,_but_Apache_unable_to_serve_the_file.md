---
title: "Installed php, but Apache unable to serve the file"
date: 2005-12-20
forum: Server Platforms
---

### Post by harisund on 2005-12-20
When I try to view the php page from another machine onthe network, the browser asks me whether I want to download or open the php file? 

I followed the instructions given in
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

exactly. 

Any suggestions? 

(Just in case, I changed the User and Group in apache2.conf to my own. Do I need to change some php settings to reflect the same too? )

---

### Post by lutrafobic on 2005-12-20
try installing "libapache2-mod-php4".

```
sudo aptitude install libapache2-mod-php4 
```

---

### Post by harisund on 2005-12-20
yes. That does get installed by default anyway. 

Initially it all works when the files are in /var/www. The problem starts when I change the DocumentRoot folder, and then the user and group. 

What I do is as suggested by the Ubuntu Apache Php MySql configuration wiki only.

---

### Post by harisund on 2005-12-20
Is there any proper tutorial / HOWTO out there which explains how to set up Apache2 and PHP under Ubuntu? 

The one in the wiki simply says apt-get install apache2 php4 (the rest is mySQL stuff.)

Here is what I want to do: 

1. Change my DocumentRoot folder, and still have php working. When I follow the instructions given in the wiki, all I end up with is php working in /var/www. And nowhere else. 
2. Change the apache2 / php user to me (or the current user.) and still have php working. 
3. Why is it that even after I do apt-get --purge remove apache2 there is the /etc/apache2 folder, an apache startup script in /etc/init.d? What does purge do anyway? 
4. Create aliases to directories in Ubuntu and have PHP scripts working even in those directories? 

I don't quite think there is such a HOWTO. If there isn't and I can get mine working I will gladly write one myself.

I am trying to do basic stuff such as setup WordPress / some other publishing blog, a php script written PhotoGallery (phpAutoGallery) and so forth. For that, I want to create multiple aliases and have php scripting enabled everywhere. 

Thanks !

---

