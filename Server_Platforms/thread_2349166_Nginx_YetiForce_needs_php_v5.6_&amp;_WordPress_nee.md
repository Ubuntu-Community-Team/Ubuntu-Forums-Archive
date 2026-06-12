---
title: "Nginx: YetiForce needs php v5.6 &amp; WordPress needs php v7.0"
date: 2017-01-11
forum: Server Platforms
---

### Post by accounts0 on 2017-01-11
Hi,

Could someone point me to docs which detail how to install both php versions 5.6 & 7.0 at once- in Ubuntu Server 16.04 LTS?

I'm running nginx & YetiForce needs php 5.6 while WordPress needs php 7.0.

Thanks.

---

### Post by TheFu on 2017-01-11
Don't use the system php for any non-system installed tools.  I don't know how php does it, but perl has "perlbrew" and ruby has "rbenv" or "rvm" which create self contained environments for the specific versions of those tools AND make having 1, 2, 5, 20 different versions available for different needs pretty trivial.

Google found this: [https://stackoverflow.com/questions/3618944/rvm-equivalent-for-php](https://stackoverflow.com/questions/3618944/rvm-equivalent-for-php) - though I know we aren't supposed to just provide answers here that google can find. Sorry.

---

### Post by accounts0 on 2017-04-05
Someone elsewhere suggested this, though I have yet to try it. Posting here in case anyone else needing to know happens upon this thread looking for answers.

point to the correct FastCGI socket in each block.
So each block would be then:
5.6:
    fastcgi_pass unix:/var/run/php/php5.6-fpm.sock;
7.0:
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;

---

