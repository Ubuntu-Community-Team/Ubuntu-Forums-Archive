---
title: "proftpd: useradd fails but adduser OK"
date: 2010-08-04
forum: Server Platforms
---

### Post by opus_az on 2010-08-04
Proftpd is installed and running fine on 8.04 server. I want to streamline the process of adding users.

Adding a ftp user with USERADD fails (user is created but connection fails when trying to connect with ftp client)
```
useradd -d /ftp/ftphome/myuser -g ftp -m -p mypassword -s /usr/sbin/nologin myuser
```

But, ADDUSER works:
```
adduser myuser
usermod -d /ftp/ftphome/myuser -g ftp -m -p mypassword -s /usr/sbin/nologin myuser
```

It's a bother because I want to automate the process, and ADDUSER has all those prompts and asks for the password twice.

Any suggestions? Hopefully I'm not missing anything too obvious!

---

### Post by opus_az on 2010-08-05
Nevermind. Brain fart. The -p was hosing me, not usermod:( 

Remove that command, and added a passwd line. Still not great though. Curious that -p makes the ftp logins fail.

---

### Post by szabouk on 2011-01-15
is the
```

useradd -d /ftp/ftphome/myuser -g ftp -m -p `mkpasswd mypassword` -s /usr/sbin/nologin myuser

```
what you looking for?

---

