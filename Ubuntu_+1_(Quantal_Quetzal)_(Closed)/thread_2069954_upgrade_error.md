---
title: "upgrade error"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rburkartjo on 2012-10-11
trying to upgrade from ubuntu 12.04 to 12.10
enter update-manager -d in the terminal and everything goes fine until i get this error message

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

the upgrade then stops and my system reverts back to 12.04

---

### Post by zika on 2012-10-11
> **rburkartjo said:**
> trying to upgrade from ubuntu 12.04 to 12.10
enter update-manager -d in the terminal and everything goes fine until i get this error message

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

the upgrade then stops and my system reverts back to 12.04Check PPA's that You have "turned on". Especially xorg-egers... I would "turn them off" and try again...

---

### Post by rburkartjo on 2012-10-11
tks zika will give that a try

---

### Post by pqwoerituytrueiwoq on 2012-10-11
i had this happen because the update manager crashed while upgrading libreoffice
i ended up removing libreoffice and reinstalling it to fix it

---

### Post by grahammechanical on 2012-10-11
I did upgrade testing towards the end of the PP cycle. I tried going from 10.04 and 11.10 to 12.04.

This was the test case I followed

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade")

Note the suggested command

```
update-manager -d -c
```

It used to work for me. I have no idea what the 'c' option does.

Regards.

---

### Post by rburkartjo on 2012-10-11
zi didnt work still got same error message

---

### Post by rburkartjo on 2012-10-11
gra will give what you posted a shot

---

### Post by rburkartjo on 2012-10-11
gra did work.got plenty of time will try again later this weekend or just wait until final comes out. hopefully whatever the problem is will be solved by then. tks

---

### Post by zika on 2012-10-11
> **rburkartjo said:**
> tks zika will give that a tryForgot to say: use ppa-purge to revert from xorg-edgers (if You have it enabled) to mainline...

---

### Post by rburkartjo on 2012-10-11
zi tks did that and package is gone but still getting the error message. heck we have another week to see if it is fixed

---

### Post by rburkartjo on 2012-10-13
finally ran sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade in terminal and update fine

---

