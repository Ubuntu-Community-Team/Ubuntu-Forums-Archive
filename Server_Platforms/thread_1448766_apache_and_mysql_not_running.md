---
title: "apache and mysql not running"
date: 2010-04-07
forum: Server Platforms
---

### Post by tonjaa on 2010-04-07
i reinstall xampp 1.7.3a when i try open web localhost  at page show 
**IT WORKS !**   and at box of xampp Apache and MySQL  show not running 
how to fix this problem ?

---

### Post by johngreth on 2010-04-07
If you see IT WORKS!, Appache is running. It's probably a problem with xampp.  Maybe it's not configured right?

---

### Post by volkswagner on 2010-04-07
Perhaps you also have apache2 running in a standalone.  Did you choose install LAMP server or have you installed apache2?

You can check if it is running and if it is set to autostart.

```
ps aux | grep apache2
```

If it is set to autostart you will find apache2 entry in the following.

```
ls /etc/rc2.d
```

You can remove it or just stop it from autostarting with rc.d update.

```
sudo update-rc.d -f apache2 remove
```

---

