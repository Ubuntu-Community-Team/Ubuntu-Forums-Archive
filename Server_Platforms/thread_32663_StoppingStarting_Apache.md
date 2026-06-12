---
title: "Stopping/Starting Apache"
date: 2005-05-08
forum: Server Platforms
---

### Post by SychoSly on 2005-05-08
This is probably a real simple question but here goes. 

When I want to start or stop the server I have to do:

etc/init.d/apache start

but why can't I do it when I go to the actual folder:

When my pwd is etc/init.d/ then I can not just put apache stop it has to be the long way?

Thanks.

---

### Post by Sam on 2005-05-08
[QUOTE=SychoSly]This is probably a real simple question but here goes. 

When I want to start or stop the server I have to do:

etc/init.d/apache start

but why can't I do it when I go to the actual folder:

When my pwd is etc/init.d/ then I can not just put apache stop it has to be the long way?

Thanks.[/QUOTE]
If your on the same directory as the program, you have to begin the command name with ./
```
$ sudo ./apache2 start
```

---

### Post by SychoSly on 2005-05-08
[QUOTE=Sam]If your on the same directory as the program, you have to begin the command name with ./
```
$ sudo ./apache2 start
```[/QUOTE]

Thank You.

---

