---
title: "Commands with funny output"
date: 2009-12-01
forum: The Cafe
---

### Post by earthpigg on 2009-12-01
the new GDM encourages users to use crack if they can't get their fix from code...

...observe the introspective contemplations pertaining to addiction transfer of upstream GNOME programmers.

```
cat /etc/gdm/Init/Default | grep FIXME
```

(found while trying to change the default session for the next Masonux 9.10 beta)

---

### Post by Psumi on 2009-12-01
```
cat: /etc/gdm/Init/Default: No such file or directory
```

Why do you ask? Because I use wdm. ;)

---

### Post by Tibuda on 2009-12-01
You don't need to pipe cat to grep, you can use only grep:
```
grep FIXME /etc/gdm/Init/Default
```

---

### Post by earthpigg on 2009-12-01
> **danielrmt said:**
> You don't need to pipe cat to grep, you can use only grep:
```
grep FIXME /etc/gdm/Init/Default
```

i learn something new every day. ive been piping cat to grep for ages, lol....

---

### Post by cael_shadowhunter on 2009-12-05
I love 

'Kernal panic       atempting to kill init!'

provided its on my school's computer and not mine

---

