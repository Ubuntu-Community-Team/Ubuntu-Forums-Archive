---
title: "how to enter in root mod"
date: 2010-01-16
forum: Server Platforms
---

### Post by jimfuture12345 on 2010-01-16
[LEFT]hi,

i have ubuntu server 9.1 and i login as admin user ,but i need to login as root how ???? , so i can change some configration files ,,,,help:(
[/LEFT]

---

### Post by sisco311 on 2010-01-16
sudo allows admin users to run programs with root-level privileges.

i.e.:
```
sudo nano /path/tp/file
```
opens /path/to/file as root in the nano text editor.

For more details, please read the community documentation:
[uhelp]community/RootSudo[/uhelp]
and the manual pages:
```
man sudo_root
man sudo
```

---

### Post by Cheesemill on 2010-01-16
If you have several commands you need to run as root you can do:
```
sudo -i
```
to give yourself a temporary root shell, just type 'exit' to get out.

---

### Post by jimfuture12345 on 2010-01-16
hi it work it open root mode ( root@ubuntu) with sudo -i

---

