---
title: "I am having problems with Ubuntu 12.10"
date: 2012-08-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrissy.millichamp on 2012-08-13
Help needed! Crash problems when loading error message: /usr/lib/upower/powerd??? 
Thanks in advance! :)

---

### Post by grahammechanical on 2012-08-13
Hi

Do you know that we have a section of this forum especially for those using 12.10? It is called Ubuntu+1 (Quantal Quetzal).

The folks there may or may not know what is wrong with your OS but at least they are using the same version of Ubuntu as you and may have experienced a similar problem.

upowerd is an executable file. What is does I have know idea. Maybe you need to re-install it. sometimes with the development version libraries are updated and then cause a conflict with other libraries that have not yet been updated. So, problems are sometimes solved by getting to a command-line and running an update.

You can get a command-line interface by choosing the recovery mode at the boot menu.

you can then try

```
sudo apt-get update
```

and

```
sudo apt-get install
```

to update the OS. Or

```
sudo apt-get -f install
```

to fix broken packages. Or

```
sudo apt-get install upowerd
```

to re-install the upowerd executable.

I hope that this helps a little bit.

regards.

---

### Post by coffeecat on 2012-08-13
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

