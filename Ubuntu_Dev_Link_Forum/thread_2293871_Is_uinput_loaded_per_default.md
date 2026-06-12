---
title: "Is uinput loaded per default?"
date: 2015-09-08
forum: Ubuntu Dev Link Forum
---

### Post by Vantskruv on 2015-09-08
I don't currently have access to Ubuntu so I need to ask this question.

Is uinput loaded per default in Ubuntu?

I am asking because my application requires uinput to be loaded.

If the answer is not, how do I attack this problem with users? Should my application ask the user to manually load uinput at OS startup or before starting application? Or should the application silently enable uinput at OS startup (preferable). I'm asking this as I don't know if uinput may be unsafe because of security reasons, and also loading uinput needs root privilegies, I don't want users to manually load uinput as admins every time application is started.

---

### Post by Vantskruv on 2016-01-03
Sorry for bumping this.

I hope someone insighted can answer how appropriate it is to silently load module uinput at system startup.

---

### Post by ian-weisser on 2016-01-03
Here you go for 15.10:
```
$ cat /boot/config-4.2.0-22-generic | grep UINPUT
CONFIG_INPUT_UINPUT=y
```

Note the 'y', not 'm'. It's already built-in, not a loadable module.

---

### Post by Vantskruv on 2016-01-03
Thank you very much sir!

---

