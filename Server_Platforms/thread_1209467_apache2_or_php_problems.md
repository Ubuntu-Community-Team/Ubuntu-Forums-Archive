---
title: "apache2 or php problems"
date: 2009-07-10
forum: Server Platforms
---

### Post by computerikon on 2009-07-10
I just set up my own web server on Ubuntu Server. I was able to upload my html files to the /var/www folder and view my site online. When I created a php script it was not working correctly. I had someone test the script on their server and it worked just fine. So I think something is going on with apache2 or php5 on my end. This is my first time using Ubuntu, so detail instructions would be appreciated. 
   
  Thanks,

---

### Post by masux594 on 2009-07-10
Have u installed the php extension of apache2?

Sysc, A

---

### Post by computerikon on 2009-07-10
Could you show me an example of a php extension of apache2

---

### Post by Wim Sturkenboom on 2009-07-10
> **computerikon said:**
> I just set up my own web server on Ubuntu Server. I was able to upload my html files to the /var/www folder and view my site online. When I created a php script **it was not working correctly**. I had someone test the script on their server and it worked just fine. So I think something is going on with apache2 or php5 on my end. This is my first time using Ubuntu, so detail instructions would be appreciated.I left my crystal ball at home ;) Can you please elaborate.

---

### Post by snek on 2009-07-10
Don't have much time to go into this problem, but I'm pretty much sure you can find your answer on how to configure Apache/PHP/MySQL in these articles:

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2)

There's many, many more excellent articles on [http://articles.slicehost.com](http://articles.slicehost.com) if you want to dive a bit deeper into setting up a webserver!

Example for VHOSTS setup (hosting multiple domains on one webserver):
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1)
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2)

Personally I use Zend Server CE a modded PHP5 version which is many, many times faster than the standard one that comes with Ubuntu repositories..
It's really simple to setup as well!!
[http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm](http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm)
If you do go with Zend Server CE be sure to also install **[B]php5-extra-extensions-zend-**[/B]**[B]ce**[/B]

---

### Post by computerikon on 2009-07-10
Thanks you all for the help! I will give it a try tonight

---

