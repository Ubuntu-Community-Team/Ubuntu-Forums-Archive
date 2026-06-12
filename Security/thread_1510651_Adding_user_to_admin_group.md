---
title: "Adding user to admin group"
date: 2010-06-15
forum: Security
---

### Post by GH1987 on 2010-06-15
Hi I'm tiring to edit a "xl2tpd.conf" file but it always says I have no write permission tried to add my account  to admin group but it says something about not able to lock on password try later ](*,)please help because it's really getting on my nerves and thanks in advance

---

### Post by cariboo on 2010-06-15
Did you try pressing Alt-F2 then typing:

```
gksu gedit <path to xl2tpd.conf> 
```

To see if your user in the admin group onpen a terminal and type:

```
groups
```

---

### Post by DCGStudios on 2010-06-16
You could also login to a root shell with 'sudo -s' and just do whatever you want from there.

---

### Post by Bachstelze on 2010-06-16
> **DCGStudios said:**
> You could also login to a root shell with 'sudo -s' and just do whatever you want from there.

sudo -i, please, not sudo -s.

---

