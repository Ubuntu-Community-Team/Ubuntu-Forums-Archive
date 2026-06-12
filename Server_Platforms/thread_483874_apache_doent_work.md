---
title: "apache doent work"
date: 2007-06-25
forum: Server Platforms
---

### Post by dinash on 2007-06-25
i had some problems with my apache server and removed.
I reisntalled it from the synaptic package manager. Now i cant get apache working again.
Everytime i try to access localhost i get a mesage saying its not found.
can anyone help me get thru this? thanks in advance.

---

### Post by EndPerform on 2007-06-25
> **dinash said:**
> i had some problems with my apache server and removed.
I reisntalled it from the synaptic package manager. Now i cant get apache working again.
Everytime i try to access localhost i get a mesage saying its not found.
can anyone help me get thru this? thanks in advance.

How did you remove it?  Through Synaptic?  Also, it might be that the server isn't started for some reason.  Open a terminal and try this:

```
sudo /etc/init.d/apache2 start
```

And see if it starts up.  If not, it should throw some errors to the console.

---

### Post by az on 2007-06-25
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

