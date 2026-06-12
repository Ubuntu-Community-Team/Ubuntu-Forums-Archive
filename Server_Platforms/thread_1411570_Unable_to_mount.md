---
title: "Unable to mount"
date: 2010-02-20
forum: Server Platforms
---

### Post by snake_eyes on 2010-02-20
Hello,

I'm trying to run this command:
```
mount --bind /var/www/ /home/user/www/
```
> mount: No such file or directory

how do I fix this? Although I'm working on Ubuntu 8.04.4 server 32 bit

Cheers,

---

### Post by nix4me on 2010-02-20
Use sudo before the mount command.  Only super user can use mount.

---

### Post by snake_eyes on 2010-02-20
I'm already logged in as root

```
root@ubuntu:~
```

another suggestion plz

---

### Post by nix4me on 2010-02-20
Does the /home/user/www dir exist?  It must exist first.  Thats the only other thing I can think of.  It should just work.

---

