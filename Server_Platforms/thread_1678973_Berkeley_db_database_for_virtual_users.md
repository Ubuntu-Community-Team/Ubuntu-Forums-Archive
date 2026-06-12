---
title: "Berkeley db database for virtual users"
date: 2011-01-31
forum: Server Platforms
---

### Post by alfamuzjak on 2011-01-31
Can someone help me with this. Im configuring virtual users for ftp and in few guides i find that i need this database.
This guides were outdated so i cant follow them(by downloading with its commands), can anyone explain me something about this db(like, where to download, how, did i have installed other version of this db with ubuntu server default packages)...By the way i need to create login file with users and their passwords, for example: 

tom
foo
fred
bar

Then i must create actual database file like this:

```
db_load -T -t hash -f logins.txt /etc/vsftpd_login.db
```
(that requires the Berkeley db program installed)

---

### Post by alfamuzjak on 2011-01-31
I find something in this forum about using db3:
```
apt-get install libdb3-util
```
Then formula would be:
```
sudo db3_load ....
```

BUT, Im unable to locate package libdb3-util

HELP ME PLEASE

---

### Post by alfamuzjak on 2011-01-31
I finnaly found something - this works:
```
sudo apt-get install **db4.7-util**
```

Thanks to philavia

P.S. If someone have work with vsftpd lately and u have time, feel free to give me some tips,links,clues anything will work.
Thanks

---

