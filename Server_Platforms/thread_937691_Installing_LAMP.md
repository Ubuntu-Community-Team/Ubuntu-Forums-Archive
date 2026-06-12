---
title: "Installing LAMP"
date: 2008-10-04
forum: Server Platforms
---

### Post by noren on 2008-10-04
Hi ,

I have been using the Ubuntu Hardy as a Desktop PC for a quit long time now, I wanted to start it as for my development platform also..

I need to work on Webserver, MySQL, and php..
How can I install LAMP on the existing platform.
Or I would have to install the Server version from scratch... :(

If yes, I  would like to get an updated tutorial to do so.
>> Installing LAMP on an existing Desktop PC version of the Ubuntu Hardy

Thankx in Advance

Rgds

---

### Post by windependence on 2008-10-04
For the desktop version you can do:

```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server php5-gd phpmyadmin
```

If you want to install Ubuntu Server (recommended) here is a tutorial:

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

Or you can use this one:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

Please note that although the above is a great guide, you probably don't need to install Bind9 like they recommend unless you have many servers on your network.

-Tim

---

