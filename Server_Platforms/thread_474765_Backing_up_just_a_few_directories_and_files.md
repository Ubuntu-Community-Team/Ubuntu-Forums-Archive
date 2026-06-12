---
title: "Backing up just a few directories and files"
date: 2007-06-15
forum: Server Platforms
---

### Post by TheGameAh on 2007-06-15
Hey guys.

I know this is dirt simple and can probably be done with just tar and gzip, but I'm looking to backup just a few files and folders.  Namely:

/var/www
/var/ftp
/etc/proftpd/proftpd.conf

That's it really.  Just can't figure out syntax.

---

### Post by bashologist on 2007-06-15
This should work:
```
sudo tar -cvjf ~/backup.tar.bz2 /var/www /var/ftp /etc/proftpd/proftpd.conf
```

---

