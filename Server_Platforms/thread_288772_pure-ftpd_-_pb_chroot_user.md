---
title: "pure-ftpd - pb chroot user"
date: 2006-10-30
forum: Server Platforms
---

### Post by cyrilforever on 2006-10-30
Hello everybody,


I need some help. i've installed pure-ftpd and pureadmin. I can log to my ftp server with an user which exists (on my computer) but not with a chroot user.

i read many answers but my pb is different. I used this pages for installing:
[http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd]("http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd")
[http://planet.ubuntu-fr.org/index.php?q=pureadmin]("http://planet.ubuntu-fr.org/index.php?q=pureadmin")

I don't understand that. if someone had a idea to resolve that..... 
thanks

---

### Post by dexmon on 2006-10-30
hello,
try this :
```
echo "yes" >> /etc/pure-ftpd/conf/ChrootEveryone
```
and restart pure-ftpd
```
/etc/init.d/pure-ftpd restart
```

---

### Post by cyrilforever on 2006-10-30
i've already tried it but i've tried again....the result is the same (530 Login authentication failed)

i've put this:
echo "no" > /etc/pure-ftp/conf/AnonymousOnly
echo "yes" > /etc/pure-ftp/conf/NoAnonymous 
echo "/etc/pure-ftpd/pureftpd.pdb" > /etc/pure-ftp/conf/PureDB 
echo "yes" > /etc/pure-ftp/conf/PAMAuthentication
echo "yes" > /etc/pure-ftp/conf/CreateHomeDir
like at [http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd]("http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd")

---

