---
title: "PHP Pear Installation /usr/share/pear"
date: 2009-12-17
forum: Server Platforms
---

### Post by jonesyp on 2009-12-17
Hi,

I have installed the LAMP server with 'sudo tasksel install lamp-server' and installed 'PHP-PEAR' but I have no folder 'usr/share/pear'.

I am trying to follow a tutorial on the zend framework and it expects to see it in this place. Can you help?

I am on Ubuntu 9.10.  The actual tutorial I was following was for 9.04. Will this make a difference?

Kind regards

---

### Post by HighCommander540 on 2009-12-17
> **jonesyp said:**
> Hi,

I have installed the LAMP server with 'sudo tasksel install lamp-server' and installed 'PHP-PEAR' but I have no folder 'usr/share/pear'.

I am trying to follow a tutorial on the zend framework and it expects to see it in this place. Can you help?

I am on Ubuntu 9.10.  The actual tutorial I was following was for 9.04. Will this make a difference?

Kind regards

Just make the folder:

```
 sudo mkdir /usr/share/pear/
```

---

### Post by jonesyp on 2009-12-18
Thanks. But the folder would still be empty so that may not help.

---

### Post by Bachstelze on 2009-12-18
A lnk to the tutorial you're trying to follow would help. ;)

---

### Post by jonesyp on 2009-12-18
Hi,  Thanks for the reply. The tutorial is at

[http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework]("http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework")

Its about have way down the page when you are looking at php.ini

nano /etc/php5/apache2/php.ini

The example shows a path of 

/usr/share/php5:/usr/share/pear

When I try and run the zend server demos it complains becuase it can not find /usr/share/pear

Looking around it seems to have been installed in /usr/php/PEAR


Peter

---

### Post by HighCommander540 on 2009-12-18
> **jonesyp said:**
> Hi,  Thanks for the reply. The tutorial is at

[http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework]("http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework")

Its about have way down the page when you are looking at php.ini

nano /etc/php5/apache2/php.ini

The example shows a path of 

/usr/share/php5:/usr/share/pear

When I try and run the zend server demos it complains becuase it can not find /usr/share/pear

Looking around it seems to have been installed in /usr/php/PEAR


Peter

Then just change the setting to /usr/share/php5:/usr/php/PEAR

---

### Post by jonesyp on 2009-12-18
OK, thanks.  I will give it a go. DOes anyone know why Ubuntu does not install Pear in the default location?

Kind regards

---

### Post by HighCommander540 on 2009-12-18
> **jonesyp said:**
> OK, thanks.  I will give it a go. DOes anyone know why Ubuntu does not install Pear in the default location?

Kind regards

Because Ubuntu and Debian like to make their own standards. They think it is a better idea.

---

### Post by jonesyp on 2009-12-19
Hi,

Has any other user got a more technical anser please.  I can not see why Ubuntu would install php.ini with /usr/share/pear, then install it in a different folder.  Thanks

---

