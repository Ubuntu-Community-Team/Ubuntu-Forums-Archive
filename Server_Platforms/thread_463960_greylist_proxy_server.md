---
title: "greylist proxy server?"
date: 2007-06-04
forum: Server Platforms
---

### Post by mega on 2007-06-04
is there anyway to setup a linux greylisting server between the internet and my real mail server, which does not support greylisting?

Not sure if postgrey can do this


my mail server is a crappy imail windows server I dont have control of, and wont support greylisting


greylisting takes me from 300 spam per day to 15


anyone know if this is posisble?  All I want to do is update my mx record to go to the greylisting server, anything that passes the greylist check is then sent to the real mail server

---

### Post by jtc on 2007-06-04
Take a look at this README

[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#firewall](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#firewall)

It shouldn't be to hard to modify it to work with postgrey. If nothing else it points you in the right direction regarding what postfix-options to look at.

---

### Post by mega on 2007-06-04
that readme is not wrote in english I think

do they have a sample main.cf buried in there somewhere?

it looks like it'll work if I can translate that readme into something usable

---

### Post by Mr. C. on 2007-06-07
Here's a good solution:

[http://www.joreybump.com/code/howto/nolisting.html](http://www.joreybump.com/code/howto/nolisting.html)

MrC

---

