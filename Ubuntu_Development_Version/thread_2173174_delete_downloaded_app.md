---
title: "delete downloaded app"
date: 2013-09-08
forum: Ubuntu Development Version
---

### Post by kaj_rumpff on 2013-09-08
hello there,
i've downloaded an app but i wanne earse it
thats couse it stops evrything
(example) if i try to downlaod an other app the USC is doing applylng chances
i've waiting day's before it was done but it's still 0%!!

so i wanna known how to delete an app at the fast and not the safest way

---

### Post by grahammechanical on 2013-09-08
Are you using Saucy Salamander (13.10)? If not you should ask questions like this in the General help section. What application is it? How did you install it?

---

### Post by kaj_rumpff on 2013-09-13
yes i do, the app. called: platinum arts sandbox gamemaker, ive installed it wilh ubuntu software center

---

### Post by cariboo on 2013-09-13
Have you tried:

```
apt-get purge sandboxgamemaker
```

What error are you getting when you try to remove the application?

---

### Post by kaj_rumpff on 2013-09-15
it say's
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

but i'm the admin

---

### Post by ibjsb4 on 2013-09-15
Close all other programs and then try:

```
sudo apt-get purge sandboxgamemaker
```

---

