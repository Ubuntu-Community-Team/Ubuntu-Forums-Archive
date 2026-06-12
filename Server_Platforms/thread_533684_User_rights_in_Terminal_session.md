---
title: "User rights in Terminal session"
date: 2007-08-24
forum: Server Platforms
---

### Post by ABX on 2007-08-24
I have just installed FreeNX for Terminal Server, but I have noticed that my test user has way too much rights on the system.

How can I lower the user rights in Ubuntu?

---

### Post by kidders on 2007-08-25
Hi there,

> **ABX said:**
> my test user has way too much rights on the system.What do you mean by that, exactly?

---

### Post by ABX on 2007-08-27
Like the  possibility to hibernate and suspend the system.


I 'd like to know if there are any predefined low permission groups.

---

### Post by kidders on 2007-08-27
Those kinds of things typically require root privileges, although that restriction is sometimes overridden for convenience. Most display managers allow you to restore a more sensible configuration though ... for instance, un-checking a box in the "control center", for kdm.

In general terms, all users have equally low privileges (ie almost none!) by default, on a Linux box ... except root.

---

### Post by ABX on 2007-08-28
I guess since I have installed Ubuntu desktop, users now have a little more permissions inside gnome desktop.

---

