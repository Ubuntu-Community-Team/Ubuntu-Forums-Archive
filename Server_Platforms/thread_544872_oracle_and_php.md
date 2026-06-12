---
title: "oracle and php"
date: 2007-09-06
forum: Server Platforms
---

### Post by mtuller on 2007-09-06
Has anyone been able to get the Oracle connector for PHP install on Ubuntu 7.04 server? I can find different instructions on the web, but have been unable to get them to work. The last one calls for using phpize, which doesn't seem to be installed.

Any help would be greatly appreciated. 


Mike

---

### Post by James79 on 2007-09-22
> **mtuller said:**
> The last one calls for using phpize, which doesn't seem to be installed.


Try:

```
sudo apt-get install php5-dev
```

---

### Post by cjbj on 2007-09-25
Generally I recommend building PHP from scratch.  The prebuilt packages on Linux tend to be old. 

There are steps to rebuild PHP with Oracle support on Oracle's free OTN site.  Also see the free Underground PHP and Oracle Manual at [http://www.oracle.com/technology/tech/php/pdf/underground-php-oracle-manual.pdf](http://www.oracle.com/technology/tech/php/pdf/underground-php-oracle-manual.pdf)

---

