---
title: "cant get apache to run with php5 in Lubuntu"
date: 2015-02-27
forum: Server Platforms
---

### Post by tom-anzp on 2015-02-27
I was used to never had a problem with this issue.

I installed like im used to

sudo apt-get install apache2
sudo apt-get install php5

But apache won't execute the php

I tryed and checked various things, and read everything I found, but I cant get it run.

when I try:

```
sudo a2enmod php5
```

I get:

```
Module php5 already enabled
```

Also:
_/etc/apache2/mods-available/php5.conf_
is setup correct like all the manuals.

Im realy confused.
In general, the 3 commands and everything runs.

Please notice that im using **Lubuntu**, but I think this could not realy be the reason

---

### Post by tom-anzp on 2015-02-28
Now I found out what was the problem.
It was not any configuration problem with apache or php.

It seems, that the Value **short_open_tag** in default php.ini changed from **On** to **Off**.

All my php sources starts with **<?**

I did not come up with the idea that this could be the problem and I always tried out various configurations about apache.

I could not understand why to change values like this by default.

---

### Post by CharlesA on 2015-02-28
Glad you figured it out.

FWIW, it is one of the best practices to not use shorthand.

---

