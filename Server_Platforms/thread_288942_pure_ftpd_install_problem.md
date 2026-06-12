---
title: "pure ftpd install problem"
date: 2006-10-30
forum: Server Platforms
---

### Post by trisscross on 2006-10-30
i have installed lamp server and followed this how to [http://ubuntuforums.org/showthread.php?t=275451](http://ubuntuforums.org/showthread.php?t=275451) to install pure ftpd ,but when i run ```
./configure --with-everything --with-paranoidmsg --with-virtualchroot --with-tls --with-largefile --with-mysql
```i get a error libmysqlclint is needed for mysql support .
i have tryed reinstaling libmysqlclint15off but that made no diffrence
i feel that i have hit a brick wall now as its taken all day getting this far editing files to enable extra repositories with nano](*,)

---

### Post by dexmon on 2006-10-30
hello,
try this 
```
apt-get install libmysqlclient15-dev
```

---

### Post by trisscross on 2006-10-30
thanks mate that worked a treat :-D :-D .
all i need to do now is connect to my server remotely from my xp laptop so i can finish the config

---

