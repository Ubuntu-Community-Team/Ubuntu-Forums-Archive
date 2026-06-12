---
title: "reset sshd_config file to default"
date: 2007-07-28
forum: Server Platforms
---

### Post by deadrabbit on 2007-07-28
I was attempting to set up public key authenication, and I altered my sshd_config file . . . and I forgot to backup the original. What's the easiest way to reset or download the default sshd_config file for 7.04? I feel incredibily stupid asking this question . . .

Also, if anyone has recommendations about what kind of key encryption is best these days, I'd appreciate it.

Thanks

---

### Post by Peter76 on 2007-07-28
Maybe reinstall??

---

### Post by deadrabbit on 2007-07-29
I tried reinstall ssh - it didn't change the config file though . . .

---

### Post by Mr. C. on 2007-07-29
You can use the -P option to remove a package including configuration files

```
dpkg -P ssh-server
apt-get install ssh-server
```

MrC

---

### Post by deadrabbit on 2007-08-03
That did it! Thanks!:guitar:

---

