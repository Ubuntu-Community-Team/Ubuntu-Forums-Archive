---
title: "SSH Server"
date: 2008-06-05
forum: Server Platforms
---

### Post by colsandurz on 2008-06-05
Hi all,

I installed ubuntu server edition and installed an openssh server with it.  Is there a way to start/configure?  I've looked all around the internet but every site seems to be concerned with SSH client usage... or am I missing something, does the server automatically come up when I boot?

---

### Post by bluefrog on 2008-06-05
the latest and it's also effective as sson as you install it.

you can tweak
/etc/ssh/ssh_config
/etc/ssh/sshd_config

---

### Post by az on 2008-06-05
The ssh server is started as part of the package installation.  It is also started upon boot.  Look in /etc/init.d and /etc/rc.d*

---

### Post by Dr Small on 2008-06-05
The configuration file for the SSH server is located at:
```
/etc/ssh/sshd_config
```

To see extra options that you can use in this file, see:
```
man sshd_config
```

Dr Small

---

### Post by hyper_ch on 2008-06-06
and use strong passwords on your user account and maybe also use denyhosts to block brute-froce attacks.

---

