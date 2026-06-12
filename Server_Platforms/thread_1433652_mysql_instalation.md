---
title: "mysql instalation"
date: 2010-03-19
forum: Server Platforms
---

### Post by dayobiz on 2010-03-19
can anyone pls tell me how i can instal mysql,apache and php through my usb. what commands do i need?

---

### Post by jrssystemsnet on 2010-03-19
> **dayobiz said:**
> through my usbUm.  What?

I have no idea what you mean by "through my usb", but the commands to install php, mysql, and apache as a functioning unit are:

```
you@box:~$ sudo apt-get update
you@box:~$ sudo apt-get upgrade
you@box:~$ sudo tasksel install lamp-server
```

---

### Post by dudumomo on 2010-03-19
Do you mean from a Live USB ?
You should read some tutorials about LAMP to learn a bit more about that.

---

