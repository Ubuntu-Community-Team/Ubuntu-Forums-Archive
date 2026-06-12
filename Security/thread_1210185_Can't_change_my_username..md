---
title: "Can't change my username."
date: 2009-07-11
forum: Security
---

### Post by Steam. on 2009-07-11
Ok, after reading thousand's of ways to change my username, i still can't.

Here's a pic to show you that i can't.

[IMG]http://www.imagelodge.net/imgs/xlr8/Screenshot-25s6.png[/IMG]

---

### Post by mikewhatever on 2009-07-11
I really don't think you can change the username. You can simply add another user with admin privileges, and once sure everything works as expected, delete the original one.

---

### Post by sisco311 on 2009-07-11
```
sudo usermod -md /home/newname -l newname oldname
```
the above command renames your user(oldname) to *newname* and moves your home directory to /home/newname.

EDIT:

oh, you should also change the name of your user's primary group:
```
sudo groupmod -n newname oldname
```

---

### Post by Steam. on 2009-07-11
Thanks all.

---

