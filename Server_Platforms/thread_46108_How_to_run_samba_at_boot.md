---
title: "How to run samba at boot?"
date: 2005-07-03
forum: Server Platforms
---

### Post by hyapadi on 2005-07-03
Samba by default running since the computer boot. But somehow after the update ( backport ). I have to run it manually ( /etc/init.d/samba start ). How to make it run during boot?

Thanks

---

### Post by LordHunter317 on 2005-07-03
[QUOTE=hyapadi]Samba by default running since the computer boot. But somehow after the update ( backport ). I have to run it manually ( /etc/init.d/samba start ). How to make it run during boot?

Thanks[/QUOTE]
 Use update-rc.d or add a symlink to /etc/rc2.d manually.  To use update-rc.d, the syntax would be:```
sudo update-rc.d samba defaults 20
```

---

