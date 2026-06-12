---
title: "What commands do you sysadmins run when you connect to a new server?"
date: 2010-04-22
forum: Server Platforms
---

### Post by altonbr on 2010-04-22
**What type of server am I on?**
```
lsb_release -a
```**What kind of disk space is there?**
```
df -h
```**Does the server reboot often?**
```
uptime
```**Is my home directory /home/username or something else?**
```
pwd
```[B]Set preferences
[/B]```
vim .bashrc
```Pretty basic but useful for me :)

---

### Post by altonbr on 2010-05-04
Bump.

---

### Post by ghost_ryder35 on 2010-05-04
**What does the performance on the server look like**
```

sar

```
and
```

top

```
**Any IP's trying to SSH brute force the server?**
```

grep Failed /var/log/auth.log | egrep '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}'

```

---

### Post by tgalati4 on 2010-05-04
sudo apt-get update

sudo apt-get upgrade

(Be selective with your updates.)

cat /etc/issue

uprecords

rwho

ruptime

htop

mail

w

---

