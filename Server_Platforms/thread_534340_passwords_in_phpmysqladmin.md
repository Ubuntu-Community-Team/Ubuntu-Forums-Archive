---
title: "passwords in phpmysqladmin????"
date: 2007-08-25
forum: Server Platforms
---

### Post by adza on 2007-08-25
Hi there, i've just installed phpmysqladmin and every time i click on a link it drops me back out to the login page and asks me to re-enter the password for the root user (i've logged on as root)?? This does this, every single time! does anyone know if a) this is a normal feature, or b) how to stop it?? I think i'll stick to CLI admin of mysql (less keystrokes!!)

:) cheers

---

### Post by 505 on 2007-08-25
Do you mean phpmyadmin? Anyway, the root password is not your Linux root password. MySQL has its own password, including a root user. As for phpMyAdmin, it depends on how you've set it up. See config.inc.php By default the authentication type is cookie, so maybe your browser is not accapting cookies. If your network is not reachable from outside you can just add your password to the config file, to bypass authentication. You can also add your password to the file, but let Apache protect the folder, so only peopkle with a Linux account can log in.

---

### Post by adza on 2007-08-25
thatnks 505, yeah i did mean phpmyadmin doh! since i am developing local machine only at this point, i will include pwd in config file... Then use mysql_dump() to dump down the db structure for installation on PRD server...

---

