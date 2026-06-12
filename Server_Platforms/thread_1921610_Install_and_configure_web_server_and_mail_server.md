---
title: "Install and configure web server and mail server"
date: 2012-02-07
forum: Server Platforms
---

### Post by warrior_king on 2012-02-07
Hello,

I want to know how to install web server apache, mail server, and dns server and how to configure? Please tell me simple if u have any refer video and picture for details  then it will help me. i m new. so its help me.



Thanks

---

### Post by eric_1982 on 2012-02-24
Lamp / Apache:

What are you looking to run on your apache server? Will you run a cms like wordpress or drupal? If so you may want to install the LAMP stack. This includes database and other needed items. If you are looking to install the LAMP stack you can do it with a quick command like at the link below. 


[http://mixeduperic.com/ubuntu/how-to-install-lamp-on-ubuntu-linux-apache-mysql-and-php-in-one-command.html+](http://mixeduperic.com/ubuntu/how-to-install-lamp-on-ubuntu-linux-apache-mysql-and-php-in-one-command.html+)




DNS / Bind9:

To setup a DNS server check out bind9

[https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html)
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)




Mail:

Is this server running at your house? often times ISP will block port 25 (mail port) so you may want to make sure that port is open before putting the time in. 

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

