---
title: "Webmin &amp; ubuntu server php problem"
date: 2013-01-08
forum: Server Platforms
---

### Post by imchivaa on 2013-01-08
Hi guys,

I ma new here. I've setup ubuntu server 12.10 with webmin and installed php5 also enabled it. When i upload phpbb3 script, seems like the php is broken. Below is the attachment. Any solution ?

---

### Post by brent1975 on 2013-01-08
> **imchivaa said:**
> Hi guys,

I ma new here. I've setup ubuntu server 12.10 with webmin and installed php5 also enabled it. When i upload phpbb3 script, seems like the php is broken. Below is the attachment. Any solution ?

First of all is this going to be  a main server or just a testing server? If a main production server I would recommend using a lts version of the server. 10.04lts or 12.04lts lts for long term support.

Second I was told by a individual here when I first started and playing with my server to do everything you can manually. That is really the only way you are going to learn how things work. Sure webmin is pretty and takes all the going deep into your server but again you wont learn anything from it. 

Have to tried just the basic php info script to see if it is working?

from shell on the server:
```
sudo nano /var/www/index.php
```
and put this line in the file
```
<?php echo "Hello World";?>
```

once done. use ctrl x , y , enter to save the file

let me know if that displays hello world.

---

### Post by SeijiSensei on 2013-01-08
It looks like the page is not being parsed by PHP.  Run this 

```
sudo apt-get install libapache2-mod-php5
```

and see if the problem goes away.  If Ubuntu reports that that package is already installed, then you have a different problem.

---

