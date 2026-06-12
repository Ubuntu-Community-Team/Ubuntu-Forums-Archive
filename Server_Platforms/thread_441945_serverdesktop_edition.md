---
title: "server/desktop edition?"
date: 2007-05-13
forum: Server Platforms
---

### Post by rygar on 2007-05-13
I've been using the ubuntu desktop edition on my laptop for a few weeks, and i'm a big fan.

i want to install a LAMP and DNS server on my desktop pc.  it's mostly for my own experiments and certainly not for any commercial purposes.  i'm no linux guru, so i want to have gnome on there too.  (i figure--gnome is just excluded to increase efficiency, but i can just close gnome when im not using it, no?)

my question is, should i install the desktop edition, then add LAMP and DNS, or should i install the server edition then install gnome?  is there even a difference?  is it harder to add LAMP/DNS than it is to add gnome?

also, how hard is it to set up LAMP and DNS in ubuntu?  i've set up apache/mysql/php on windows machines before, but there are a plethora of tutorials that tell you what to do, and the whole process was pretty quick.  is it just as easy on ubuntu?  what about dns servers?

---

### Post by StarMonkee on 2007-05-13
LAMP on ubuntu is easy, and it will take less time than installing gnome on the server version.

This is what I do to install LAMP on debian boxes (it will be either identical or very similar on ubuntu, you'll probably need to enable universe for things like php5-imap)

apt-get install apache2 libapache2-mod-php5 php5-cli php5-curl php5-gd php5-imap php5-common php5-mysql php5-sqlite mysql-client-5.0 mysql-server-5.0

The first part of this tutorial will get DNS working in about 10 minutes for you:

[http://www.howtoforge.com/debian_bind9_master_slave_system](http://www.howtoforge.com/debian_bind9_master_slave_system)

---

