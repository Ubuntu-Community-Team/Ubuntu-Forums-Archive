---
title: "Ubuntu 12.04 PHP version"
date: 2013-02-21
forum: Server Platforms
---

### Post by Frank P on 2013-02-21
I'm running ubuntu server 12.04LTS. The PHP version installed is 5.3.10-1ubuntu3.5
I'd like to move to PHP5.4
I've seem info on upgrading via other repositories but I'd rather stay away from that.
Is the current version of PHP included with 12.10 or will 12.04 ever be upgrraded to include PHP5.4
 
Thanks
 
Frank P

---

### Post by CharlesA on 2013-02-21
It is unlikely that the version of PHP in 12.04 will be upgraded.

The only way you'll get 5.4 on a 12.04 box is to use a PPA, or compile it from source (PPA is easier to deal with).

[http://www.barryodonovan.com/index.php/2012/05/22/ubuntu-12-04-precise-pangolin-and-php-5-4-again](http://www.barryodonovan.com/index.php/2012/05/22/ubuntu-12-04-precise-pangolin-and-php-5-4-again)

---

### Post by Frank P on 2013-02-21
Charles
 
Is PHP5.4 available in 12.10
If it is, would you recommend using the PPA in 12.04 or moving to 12.10
(I checked your link and it looks like I should be able to do it)
 
Thanks
 
Frank P

---

### Post by CharlesA on 2013-02-21
Not sure, but according to this page:
[http://www.ubuntugeek.com/how-to-downgrade-php-version-from-5-4-to-5-3-in-ubuntu-12-10-quantal.html](http://www.ubuntugeek.com/how-to-downgrade-php-version-from-5-4-to-5-3-in-ubuntu-12-10-quantal.html)

12.10 ships with 5.4, but I wouldn't run any anything other than a LTS on a production machine.

---

### Post by Frank P on 2013-02-21
Ok, Thanks for your help
 
Frank P

---

