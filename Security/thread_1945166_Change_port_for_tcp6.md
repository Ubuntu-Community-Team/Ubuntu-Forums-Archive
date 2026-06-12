---
title: "Change port for tcp6"
date: 2012-03-22
forum: Security
---

### Post by Meikrekel on 2012-03-22
Hello,

I'm having troubles connecting to my site with filezilla.I need port 21 for this, but that port is already taken by a process called TCP6. I don't know what this service is, but my question is: can I change the portnumber for TCP6?

Cheerz,
Meikrekel

---

### Post by CharlesA on 2012-03-22
Er what? Port 20 and 21 are used for FTP. Even if you have an FTP server listening on port 21, you should still be able to connect.

Run this on the server:

```
sudo netstat -nlp
```

---

### Post by Meikrekel on 2012-03-22
My site is hosted at an external company called antagonist, so I don't know how to run a command on their server

---

### Post by CharlesA on 2012-03-22
Contact them and have them help you troubleshoot ftp connectivity.

---

