---
title: "Possible to set php version ubuntu 12.04 php 5.5.19"
date: 2014-12-16
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-12-16
Am ruuning PHP 5.5.19-1+deb.sury.org~precise+1 on ubuntu 12.04
When I upgraded php version one of my websites broke and JUST FOR THIS WEBSITE want to set the php version back to 5.2.17
How can I do this?

---

### Post by dragonfly41 on 2014-12-16
A couple of threads explaining PHPFarm .. i.e. use a different PHP version for each virtual host

[http://thejibe.com/blog/14/02/phpfarm](http://thejibe.com/blog/14/02/phpfarm)

[https://gist.github.com/gmodarelli/5887778](https://gist.github.com/gmodarelli/5887778)

---

### Post by astarmathsandphysics on 2014-12-16
Thanks for that. It is on my xmas list.

---

### Post by SeijiSensei on 2014-12-17
Doesn't the error log tell you why the site broke?  Maybe you should just fix the code so it works in 5.5.

---

