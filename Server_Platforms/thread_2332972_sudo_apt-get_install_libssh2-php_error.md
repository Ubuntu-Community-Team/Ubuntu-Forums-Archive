---
title: "sudo apt-get install libssh2-php error"
date: 2016-08-05
forum: Server Platforms
---

### Post by Curlyp on 2016-08-05
Hello again! I'm going through some guides (that are a few years old) on how to get everything setup for my web server and I run across an error that I cannot find the fix for ```
[COLOR=#3A3A3A][FONT=monospace]sudo apt-get install libssh2-php[/FONT][/COLOR]
```

Here is the error: [https://i.imgur.com/mK1voSO.jpg](https://i.imgur.com/mK1voSO.jpg)

Before this install, I was told to install:
 ```
[COLOR=#3A3A3A][FONT=monospace]sudo apt-get install php5-gd[/FONT][/COLOR]
```

However, ubuntu server 16.04.1 comes with PHP7.0, so that was an pretty straight forward.  I did a quick Google search for [COLOR=#3A3A3A][FONT=monospace]sudo apt-get install libssh2-php[/FONT][/COLOR], but cannot find anything relevant for the never version of ubuntu.

Does anyone know the new command line to install libssh2-php?

Thanks!

---

### Post by steeldriver on 2016-08-05
It looks like the package may have been superseded by [php-ssh2]("http://packages.ubuntu.com/xenial/php-ssh2") ?

---

### Post by Graham_Willis on 2016-08-06
From the error message that you presented it seems to me that it's just been replaced by php-ssh2. So simply **apt-get install php-ssh2** .

---

### Post by Curlyp on 2016-08-06
> **steeldriver said:**
> It looks like the package may have been superseded by [php-ssh2]("http://packages.ubuntu.com/xenial/php-ssh2") ?

> **Graham_Willis said:**
> From the error message that you presented it seems to me that it's just been replaced by php-ssh2. So simply **apt-get install php-ssh2** .

Thank you both!

---

