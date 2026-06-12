---
title: "force periodic password change"
date: 2009-11-18
forum: Security
---

### Post by b4nsh33 on 2009-11-18
Hello to all, due to some security regulatios (SOX) in my company, i need to force password change every 60 days to all users, i know the passwd -e force to next login, but i need to do it automatically without admin intervention,
Any help will be greatly appreciated
regards

---

### Post by Sarmacid on 2009-11-18
This can be done in the /etc/pam.d/common-password file. Try ```
man pam
man pam.d
``` for more info.

---

### Post by sisco311 on 2009-11-18
```
man chage
```

```
sudo chage -M 60 username
```

---

### Post by b4nsh33 on 2009-11-18
it seems like chage is what im looking for, the setting is permanent right?
I mean, once i set chage -M 60 to every user, they will be forced to change it every 60 days, not just 1 time for the following 60 days,
regards

---

### Post by sisco311 on 2009-11-18
> **b4nsh33 said:**
> it seems like chage is what im looking for, the setting is permanent right?
I mean, once i set chage -M 60 to every user, they will be forced to change it every 60 days, not just 1 time for the following 60 days,
regards

Yes, it's permanent.

You can accomplish the same task with the passwd command:
```
passwd -x 60 username
passwd --maxdays 60 username

```

Or by manually editing (the 5th field of) the /etc/shadow file.
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/")

---

