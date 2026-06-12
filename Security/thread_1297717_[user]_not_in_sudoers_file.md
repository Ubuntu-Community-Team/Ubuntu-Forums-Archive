---
title: "[user] not in sudoers file"
date: 2009-10-22
forum: Security
---

### Post by denvro on 2009-10-22
Please help!

Yesterday i have <snip> up my Ubuntu. I have run a usermod -G without the -a switch.

Now i'm not in the sudoers group anymore and i haven't set up root access.

Is there anything i can do??

Please help me!! :(

---

### Post by ad_267 on 2009-10-22
Restart your computer and select recovery mode, which will log you in as root to a terminal. Then enter:

```
adduser YOUR_USER_NAME admin
```

Then you can add yourself to whatever other groups you need. I'm in these ones by default:
```
adm dialout cdrom video plugdev lpadmin admin
```

---

### Post by denvro on 2009-10-22
Thanx that did it....

---

