---
title: "Bitdefender appears in login menu"
date: 2013-05-13
forum: Security
---

### Post by SuperFreak on 2013-05-13
I recently & with a great deal of difficulty installed Bitdefender . It appears in my System tools menu (running Cinnamon on 12.04.2 Precise). I noticed when loggging our Bitdefender appears as a choice in the login screen above my login name. Is this something that should be corrected or is it supposed to be that way?

I realize I don't need antivirus for Ubuntu but I transfer files to my Win 7 machine occassionally

---

### Post by CharlesA on 2013-05-13
What what userid the bitdefender user is set for.

```
id bitdefender
```

Only users whose userid is 1000 or above should be visible.

---

### Post by SuperFreak on 2013-05-13
That looks OK
```
$ id bitdefender
uid=1001(bitdefender) gid=1001(bitdefender) groups=1001(bitdefender)

```
If I click on bitdefender in the login page it asks for password. If I click on the Ubuntu icon next to bitdefender (same line) it opens up the option for choosing several DEs such as Unity , Gnome Classic, cinnamon etc

---

### Post by CharlesA on 2013-05-13
It's been a while since I had bitdefender installed, but it should have installed as a system user, not with a uid of 1001.

---

### Post by SuperFreak on 2013-05-13
Is it best to uninstall the program, and if so how?

It does appear in Ubuntu Software Centre so I could remove it there,


Edit: OK uninstalling through Ubuntu Software Center corrected the login screen. I will google the directions on installing Bitdefender and hopefully won't have this issue again
Thanks

---

### Post by CharlesA on 2013-05-13
It's been a while since I had bitdefender installed, but it should have installed as a system user, not with a uid of 1001.

---

### Post by SuperFreak on 2013-05-13
The correct way to install BitDefender is [HERE]("https://help.ubuntu.com/community/BitDefender")

---

### Post by CharlesA on 2013-05-13
> **SuperFreak said:**
> The correct way to install BitDefender is [HERE]("https://help.ubuntu.com/community/BitDefender")

Glad you got is sorted out. :)

---

