---
title: "How to change mysql data directory location in lampp?"
date: 2011-08-23
forum: Server Platforms
---

### Post by ovi0606 on 2011-08-23
I use dual boot with windos 7. i use xampp in win7. want to use lampp for ubuntu 10.04. i want to use one local server directoy for both . i successfuly changed htdocs location in lampp. but could not change mysql data directory location >< . can anyone help me with that please...

---

### Post by sam1948 on 2011-08-23
have you tried using soft-links?
for example:
```
ln -s -T /media/XP/xamp/web_sites /home/user/web_sites
```
should be great for file and directories

---

### Post by ovi0606 on 2011-08-24
> **dinu90 said:**
> You can either use a symlink or you can set up a different data directory in my.cnf:
[code]
datadir=/path/to/somedir
[code]

can you please tell me the location of the file  my.cnf. i cant find it. thanks.

---

### Post by volkswagner on 2011-08-24
> **ovi0606 said:**
> can you please tell me the location of the file  my.cnf. i cant find it. thanks.


You can use the find command.

```
man find
```

Since most configuration files are located under /etc that is always a good place to start, which will allow the find command to search quicker vs searching the entire / directory.

```
find /etc -name my.cnf
```

You should get a result including

```
/etc/mysql/my.cnf
```

---

