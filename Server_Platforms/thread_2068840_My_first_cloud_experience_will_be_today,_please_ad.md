---
title: "My first cloud experience will be today, please advise me .."
date: 2012-10-10
forum: Server Platforms
---

### Post by ELMIT on 2012-10-10
I am excited to have the chance today to use a cloud service. In case it matters I will use jiffybox.

Of course I have hundreds of questions, but for today I only got a few:

1. I want to setup 12.04 with the 2 cores and 2 GB RAM, It will run later on more cores and more RAM. Should I therefore use immediately 64 bit version? Should I use 2 instances, one for MySQL and one for all others?

2. Is there a forum, mailing list, user group available?

3. Are there tutorials, documents, ... available?

4. I will run on these:
webservice (virtual domains), typo3, wordpress, ... 
qmail, ...

5. I will install the packages (in this order):
apt-get install lamp-server^
apt-get update
apt-get upgrade --show-upgraded
nano /etc/apache2/ports.conf
 ...
apt-get install php5-gd
apt-get install php-pear
apt-get install make
pecl install uploadprogress
echo "extension = uploadprogress.so" > /etc/php5/apache2/conf.d/uploadprogress.ini 
echo "extension = uploadprogress.so" > /etc/php5/conf.d/uploadprogress.ini
service apache2 reload
apt-get install git
mysql_secure_installation
apt-get install php5-suhosin


What else do you suggest?

Thanks for your help!

---

### Post by nothingspecial on 2012-10-10
*Thread moved to **Server Platforms**.*

---

