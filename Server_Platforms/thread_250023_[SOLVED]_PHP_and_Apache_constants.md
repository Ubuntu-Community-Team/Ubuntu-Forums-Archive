---
title: "[SOLVED] PHP and Apache constants"
date: 2006-09-03
forum: Server Platforms
---

### Post by altonbr on 2006-09-03
If,
PHP_VERSION gives 5.1.2
and
PHP_OS gives Linux

is there any constants that will say "Ubuntu 6.06" or give apache's version number... I haven't quite figured out global variables yet... such as _SERVER["SERVER_SOFTWARE"]

I want to do this so that if I ever change my operating system, php version or apache version, it will change with the system and not a user defined variable.

---

### Post by Miademora on 2006-09-03
```

$_SERVER["SERVER_SIGNATURE"]
$_SERVER["SERVER_SOFTWARE"]

```

Both of these return Apache Version Number for me in some way. Only if Apache runs these Scripts of course. It wont help you if you run something from Commandline. I wont rely on them though unless you run a selfcompiled Apache and set your own custom string.

---

### Post by Uluen on 2006-09-03
You can run regular shell commands from PHP as well, uname -a and such but you probably know that.

---

### Post by Miademora on 2006-09-03
Yeah **system()** and **exec()** is also possible. Usage depends on how secure your script needs to be.

---

### Post by altonbr on 2006-09-03
Hey guys,

I'm just looking for this script for aesthetics. I'm pretty new to PHP (although I'll be taking a server-side scripting course this semester).. so no, I didn't know you can do bash commands via PHP.. how would I go about doing that anyway?

Just so you know what I want as an example:

```
Running on "Ubuntu 6.06" || Using PHP "5.1.4" and Apache "2.0.55"
```

Something simple, but variable like that.

---

### Post by Uluen on 2006-09-04
Maybe you can find some hints [here]("http://no.php.net/manual/en/function.system.php") and [here]("http://no.php.net/manual/en/function.exec.php").

---

