---
title: "apt pinning not working"
date: 2016-12-23
forum: Server Platforms
---

### Post by accounts0 on 2016-12-23
I did
```
sudo add-apt-repository ppa:ondrej/php
```
...then I made this file:

```
/etc/apt/preferences.d/php5.6

```with this in it:
```
Package: php*
Pin: version 5.6*
Pin-Priority: -1

```

...But when I do 
```
sudo aptitude update && sudo aptitude install --without-recommends php

```
It still tries to install v. 7!

How do I get this to keep version 5.6??!

---

### Post by bashiergui on 2016-12-30
This thread contains several suggestions: [http://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04](http://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04)

---

