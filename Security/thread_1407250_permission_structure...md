---
title: "permission structure.."
date: 2010-02-15
forum: Security
---

### Post by manyu29 on 2010-02-15
could anybody direct me to the structure of ubuntu where it asks permissions to administratie tasks?i think i can make modifications to my own..plzz help..

---

### Post by Satoru-san on 2010-02-15
> **manyu29 said:**
> could anybody direct me to the structure of ubuntu where it asks permissions to administratie tasks?i think i can make modifications to my own..plzz help..
This would severly lower your security. All you have to do is make yourself a sudoer, and you can proform administrative tasks. What kind of changes do you wish to make?

---

### Post by manyu29 on 2010-02-15
mm,even so..will you plz help?i still dont really know what modifications to make but i would like to look into,maybe then i'l find out..im trying to learn more..

---

### Post by rookcifer on 2010-02-15
> **manyu29 said:**
> mm,even so..will you plz help?i still dont really know what modifications to make but i would like to look into,maybe then i'l find out..im trying to learn more..

man chmod
man chgrp
man chown

---

### Post by bodhi.zazen on 2010-02-15
> **manyu29 said:**
> mm,even so..will you plz help?i still dont really know what modifications to make but i would like to look into,maybe then i'l find out..im trying to learn more..


[https://wiki.ubuntu.com/FilePermissions](https://wiki.ubuntu.com/FilePermissions)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Just take care not to change permissions of system files without understanding the implications of what you are doing.

---

