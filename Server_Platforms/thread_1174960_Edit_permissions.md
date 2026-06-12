---
title: "Edit permissions"
date: 2009-05-31
forum: Server Platforms
---

### Post by user328 on 2009-05-31
Hey there

I am new to linux, so i really don't know how to do this. I need to edit access for var/www , since i can't edit it in ftp client. But the problem is that i can't because i am logged in as hlds@server1. I know that i need to be loged in as server1 to edit that. But how can i do this?
Any help is appriciated!

---

### Post by user328 on 2009-05-31
anyone?

---

### Post by Idefix82 on 2009-05-31
Firstly, you don't need to bump a thread after only 50 minutes. Give people a day or so, then bump.

Secondly, what exactly do you want to do? What do you mean by "edit access"?

---

### Post by user328 on 2009-05-31
I need to edit permission to this folder, var/www .

---

### Post by Idefix82 on 2009-05-31
The command to edit permissions is
```
chmod
```
Since you will need to execute it a superuser, you have to precede it by ```
sudo
```
In summary, you type something like
```
sudo chmod 755 /var
```
replacing 755 by the permission you need; then type in your password. If you want the change to be valid for all subdirectories, you use the -R option:
```
sudo chmod -R 755 /var
```

---

### Post by user328 on 2009-05-31
Yeah, that was i was looking for.
Thanks

---

### Post by Iowan on 2009-05-31
Besides editing permissions on /var/www, you could also relocate the files to a more accessible directory - as described (somewhere?) in [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page.

---

