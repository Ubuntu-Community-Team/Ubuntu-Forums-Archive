---
title: "can't have root permission in gnome"
date: 2010-10-21
forum: Security
---

### Post by gufide on 2010-10-21
Hi, my problem is very weird: I can do easily sudo, gksu and gksudo in terminal, but when I click for update but in the software center:
[ATTACH]173097[/ATTACH]
and my password don't work
I does this with update manager too
thank you for help me

---

### Post by sisco311 on 2010-10-21
> **gufide said:**
> Hi, my problem is very weird: I can do easily sudo, gksu and gksudo in terminal, but when I click for update but in the software center:
[ATTACH]173097[/ATTACH]
and my password don't work
I does this with update manager too
thank you for help me

Please post the output of:
```
grep admin /etc/group
```
and
```
groups
```

---

### Post by gufide on 2010-10-21
for grep /etc/group :
```
master@comput1:~$ grep admin /etc/group
lpadmin:x:111:
admin:x:119:
```

and for groups:
```
master@comput1:~$ groups
admin

```

---

### Post by sisco311 on 2010-10-21
> **gufide said:**
> for grep /etc/group :
```
master@comput1:~$ grep admin /etc/group
lpadmin:x:111:
admin:x:119:
```

and for groups:
```
master@comput1:~$ groups
admin

```

You removed yourself from the admin group. Run:
```
sudo gpasswd -a $USER admin
```
to (re-)add your user to the group.

---

### Post by gufide on 2010-10-21
thank you very much, I will take this in note

---

