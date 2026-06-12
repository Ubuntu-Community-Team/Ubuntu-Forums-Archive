---
title: "Ftp"
date: 2008-07-09
forum: Server Platforms
---

### Post by waterrr on 2008-07-09
I have just installed an FTP using
```
sudo apt-get install vsftpd
```
my question is how do I access the ftp?

---

### Post by osjak on 2008-07-09
[http://blog.mypapit.net/2007/09/how-to-use-ftp-in-ubuntu-linux.html](http://blog.mypapit.net/2007/09/how-to-use-ftp-in-ubuntu-linux.html)

---

### Post by curtis on 2008-07-09
Do not use FTP as it is very insecure. Use SFTP or SCP to transfer files.

FTP transfers login details and files all in plain text.

---

### Post by waterrr on 2008-07-10
How should I go about installing sftp?

---

### Post by highonv8splash on 2008-07-10
```

sudo apt-get install openssh-server

```

---

