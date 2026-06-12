---
title: "Ubuntu Server 8.10"
date: 2008-11-26
forum: Server Platforms
---

### Post by dallastarsfan16 on 2008-11-26
hey guys i'm a total n00b when it comes to linux/ ubuntu. i have successfully installed ubuntu server 8.10. here's where i'm confused, after boot up it brings me to the place where i login, i type my user name and the press 'enter' and it asks for the password when i try and type my password nothing happens. any ideas?

also i'm running the server on an old dell dimension 4600.


thanks,
dallastarsfan16

---

### Post by spiderbatdad on 2008-11-26
you will not see any indication while in a shell that you are inputting a password; just be assured the keystrokes are detected. Finish typing your password and press enter. You realize you will not boot into a desktop environment with a new server install. You will only have a command prompt.

---

### Post by dallastarsfan16 on 2008-11-27
ok I was able to login, but now I honestly don't know what to do. Can you point at a good guide or website?

-dallastarsfan16

---

### Post by spiderbatdad on 2008-11-27
what are you try to do? Do you want to run an apache webserver? Would you prefer to have a desktop environment? If you need a graphical environment, but install the server edition you can run these commands:
```
sudo apt-get install ubuntu-desktop gdm
```then reboot and you will have a desktop environment. If you want to get a server running check out the community documentation:
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

