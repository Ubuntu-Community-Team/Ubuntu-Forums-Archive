---
title: "I can no longer sudo !?!"
date: 2009-02-05
forum: Security
---

### Post by dargaud on 2009-02-05
I switched to kubuntu 2 days ago, so it's been a continuous process of installation and configuration ever since. But since the last reboot a few minutes ago, I can no longer use sudo (or gksudo)... That happened ?

Note: I know I can use the livecd to edit the passwd and group files, but what is wrong with them ? I don't have a root password...

```
$ grep dargaud /etc/passwd /etc/group
/etc/passwd:dargaud:x:1000:1000:Guillaume Dargaud:/home/dargaud:/bin/bash
/etc/group:adm:x:4:dargaud
/etc/group:lp:*:7:lp,hplip,dargaud
/etc/group:dialout:x:20:dargaud
/etc/group:cdrom:x:24:dargaud
/etc/group:floppy:x:25:dargaud
/etc/group:sudo:x:27:dargaud
/etc/group:www-data:x:33:dargaud
/etc/group:plugdev:x:46:dargaud
/etc/group:users:*:100:jenny,dargaud
/etc/group:fuse:x:106:dargaud
/etc/group:lpadmin:x:112:dargaud
/etc/group:admin:x:119:dargaud
/etc/group:dargaud:x:1000:
/etc/group:sambashare:x:120:dargaud
/etc/group:mysql:x:123:dargaud
/etc/group:jenny:*:1001:dargaud
/etc/group:vboxusers:*:124:dargaud

```

---

### Post by jerome1232 on 2009-02-05
Looks fine to me what about your sudoer's file what does it look like

```
sudo cat /etc/sudoers
```

--edit-- and what is the error you get when you try and sudo?

---

### Post by dargaud on 2009-02-06
Well, I solved it and it was completely stupid... the keyboard repetition rate was a bit too high and was generating double letters... so all my password entries were wrong !!! That's a new one to me. But since I reverted the passwd/group files, I now need to put them back...

---

