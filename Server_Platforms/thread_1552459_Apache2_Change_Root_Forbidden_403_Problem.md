---
title: "Apache2 Change Root Forbidden 403 Problem"
date: 2010-08-13
forum: Server Platforms
---

### Post by ybmatters on 2010-08-13
Long story Short, I had to reinstall 9.10 (after a failed 10.04 upgrade) and therefore fresh install of everything.

I installed Apache2 as per [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp) and all works fine.

Changing the root in /etc/apache2/sites-available/default to a folder in my home directory /home/user/subfldr1/www results in a forbidden 403 error.

I've tried changing group owner, given 777 permissions, read and tried all sorts of solutions, but nothing seems to be working. I know I'm missing something, but I can't figure it out.

Can someone please point me in the right direction.

---

### Post by eric_1982 on 2010-08-14
May seem like a stupid question but have your tried to restart your apache server after making these changes?


sudo /etc/init.d/apache2 restart

---

### Post by Bachstelze on 2010-08-14
You need to also allow access to that directory in the Apache config. In /etc/apache2/conf.d/security, you have

```
<Directory /var/www>
        AllowOverride None
        Order Deny,Allow
        Allow from all
</Directory>

```

Add another similar block, but for the directory where your DocumentRoot is located, so:

```
<Directory /home/user/subfldr1/www>
        AllowOverride None
        Order Deny,Allow
        Allow from all
</Directory>

```

---

### Post by ybmatters on 2010-08-21
Thanks Eric & Bachstelze. Did nto see your replies s I thought i would be emailed if a reply came in and had given up on anyone responding to my request. I solved the problem by shifting the WWW folder up one level. It was something to do with the permisssions down the tree, but I couldn't get it to work. Moving it up overcame that.

---

