---
title: "Problems php5 IMAP"
date: 2008-04-16
forum: Server Platforms
---

### Post by ryjal on 2008-04-16
I am trying to use IMAP in php5 I have install the php-imap package but I tried using the imap_open function and I receive the following error.

Fatal error: Call to undefined function imap_open()

I ran the phpinfo() function and it did not list IMAP anywhere.

Thanks

Ryjal

---

### Post by GigaVolt on 2008-04-16
php5-imap
/etc/init.d/apache2 restart

---

### Post by ryjal on 2008-04-16
Thank you it worked:)

I thought that apt-get would automaticly restart apache I will need to remember this.

Thanks again

ryajl

---

