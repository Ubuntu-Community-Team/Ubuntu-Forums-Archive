---
title: "php5-gd obsoleted"
date: 2016-04-13
forum: Ubuntu Development Version
---

### Post by makitso on 2016-04-13
So, a recent update obsoleted php5-gd.  My software requires this for Apache2/mysql/php.  Any ideas on where to find the replacement?

---

### Post by dino99 on 2016-04-13
Willy has it : [https://launchpad.net/ubuntu/+source/php5](https://launchpad.net/ubuntu/+source/php5)

---

### Post by makitso on 2016-04-13
Yes, I saw that.  But, unless it's in another library I can't find it.

---

### Post by wgarcia on 2016-04-14
Isn't it substituted by php7.0-gd?

```
$  apt-cache search php*-gd
php-gd - GD module for PHP [default]
php7.0-gd - GD module for PHP
```

---

### Post by makitso on 2016-04-14
I installed my LAMP server with the same commands that I used for ubuntu 15.10.  Turns out that a recent update changed the packages.  Where I was installing php5,  it is now referenced  as php.

---

