---
title: "Joomla and phtml error"
date: 2009-12-10
forum: Server Platforms
---

### Post by any.linux12 on 2009-12-10
Hi!

I created a LAMP server and later I installed a mail server, zimbra by the way. I use joomla as a content manager but now I can't re-install it because my server is not able to run PHTML files, please see attachment.

I already googled a lot and tried to change my /etc/apache2/httpd.conf but no luck so far.

Thanks

---

### Post by any.linux12 on 2009-12-10
Hi!

I created a LAMP server and later I installed a mail server, zimbra by the way. I use joomla as a content manager but now I can't re-install it because my server is not able to run PHTML files, please see attachment.

I already googled a lot and tried to change my /etc/apache2/httpd.conf but no luck so far.

Thanks

---

### Post by cariboo on 2009-12-10
please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by munky99999 on 2009-12-10
Did you follow

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

As it appears you lack php. If you have done the php installation.

Perhaps a quick restart of apache.


sudo /etc/init.d/apache2 restart

---

### Post by any.linux12 on 2009-12-11
> **cariboo907 said:**
> please don't create multiple threads on the same subject, I have merged your two threads.

It's was not my fault...the server had problems yesterday and was not posting threads

---

### Post by any.linux12 on 2009-12-11
> **munky99999 said:**
> Did you follow

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

As it appears you lack php. If you have done the php installation.

Perhaps a quick restart of apache.


sudo /etc/init.d/apache2 restart

I had joomla working before the installation of the mail server. Also when I installed the server I choose the LAMP to be automatically installed...but I will re-install..

Thanks

---

### Post by any.linux12 on 2009-12-11
Thread SOLVED I hadn't install the php-cli and common or most likely I removed it for some reason

---

