---
title: "Apache2/PHP: Any way to see running scripts?"
date: 2007-07-24
forum: Server Platforms
---

### Post by krazyj on 2007-07-24
Is there any way to see what scripts are executing on Apache/PHP?

I have a script that scrapes data from the internet on my local ubuntu server and I want to see if its still running after I execute it from the command line.

Thanks!

---

### Post by bbzbryce on 2007-07-24
> **krazyj said:**
> Is there any way to see what scripts are executing on Apache/PHP?

I have a script that scrapes data from the internet on my local ubuntu server and I want to see if its still running after I execute it from the command line.

Thanks!

If you execute it from the command line then it's not interacting with apache. If you open the system monitor look for an instance of a php process. If it's there then it is still running, otherwise it has completed.

---

### Post by krazyj on 2007-07-24
Well, in that case, is there any way to see what PHP script threads are running?

You are correct in that, if i execute it via command line its TECHNICALLY not interfacing with Apache. PHP is what I meant, the same idea still applies.

---

### Post by bbzbryce on 2007-07-24
> **krazyj said:**
> Well, in that case, is there any way to see what PHP script threads are running?

Ok so I just tested this out. If you have a script named test.php and say it looks like this:

```


#!/usr/bin/php

<?

while(1) {
	print 'hello';
}

?>
```

Save the file then chmod +x test.php and execute it by doing:

```
./test.php
```

In the process list this will appear as test.php. However if you execute it by doing:

```
php test.php
```
It will only show up under the process list as php.

Thus I suggest doing it the first way and you should be all set.

---

### Post by krazyj on 2007-07-24
Awesome answer! Thanks for the response. Ill check it out tomorrow when I get my hands on that sexy sever. :)

---

