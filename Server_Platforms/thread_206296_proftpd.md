---
title: "proftpd"
date: 2006-06-29
forum: Server Platforms
---

### Post by involutaryhaxor on 2006-06-29
I have heard several great things about proftpd, I would love to use it but I can't. I have tried to apt-get it like everyone has suggested, but when I do this, it can't find the package. Could anyone help me out?

---

### Post by taurus on 2006-06-29
Maybe you need to remove the # sign in front of the lines for universe and multiverse in /etc/apt/sources.list...
```

sudo gedit /etc/apt/sources.list <-- to edit it from a terminal...
sudo apt-get update <-- to update the list...
sudo apt-get install proftpd <-- to install it
-or-
sudo apt-get install vsftpd <-- is another ftp server you can try...

```

---

### Post by involutaryhaxor on 2006-07-01
[QUOTE=taurus]Maybe you need to remove the # sign in front of the lines for universe and multiverse in /etc/apt/sources.list...
```

sudo gedit /etc/apt/sources.list <-- to edit it from a terminal...
sudo apt-get update <-- to update the list...
sudo apt-get install proftpd <-- to install it
-or-
sudo apt-get install vsftpd <-- is another ftp server you can try...

```[/QUOTE]
thankyou, it turned out that my problem was that i didnt do the apt-get update command.

---

### Post by nameiwantistaken on 2006-07-01
I've updated and the damn thing still doesn't find it.

---

### Post by lyncis on 2006-07-06
Have the same problem (

**upd**: after *apt-get update*  - nothing, but after *apt-get upgrade* - proftpd was found at *archive.ubuntu.com* and downloaded )

---

### Post by lamego on 2006-07-06
You must be missing the universe/multiverse repositories, for sure.

---

