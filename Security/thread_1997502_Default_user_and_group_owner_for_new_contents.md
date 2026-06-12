---
title: "Default user and group owner for new contents"
date: 2012-06-05
forum: Security
---

### Post by Inderpreet Singh on 2012-06-05
Hi,

Is there any way that whenever any user will create any file or directory . The root will become its user and group owner by default. Basically I want this scenario in **/var/www/html **directory..

---

### Post by Inderpreet Singh on 2012-06-06
Please give me suggestions........

---

### Post by zombifier25 on 2012-06-06
You can setgid a folder so that all files and folders created in that folder will automatically take the group ownership of that folder's owner.
```
chmod g+s /folder/name
```
You may need to sudo.

I don't know how to make all files set to a specific owner though, because Linux ignores setuid on folders.

---

### Post by Inderpreet Singh on 2012-06-07
> **zombifier25 said:**
> You can setgid a folder so that all files and folders created in that folder will automatically take the group ownership of that folder's owner.
```
chmod g+s /folder/name
```You may need to sudo.

I don't know how to make all files set to a specific owner though, because Linux ignores setuid on folders.

This solved my problem partially...but still how can I do this in a way that root will become its user owner ??

---

### Post by paul_be on 2012-06-08
chown will change the owner of a file / dir

file
```
chown <user> <file>
```directory
```
chown -R <user> <dir>
```

---

