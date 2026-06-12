---
title: "Changing location of .wine"
date: 2010-12-16
forum: Wine
---

### Post by indike on 2010-12-16
whenever wine is running it uses [COLOR=Red]/home/user1/.wine[/COLOR] to store the .exe files, etc.....
But as it is [COLOR=Red]not accessible[/COLOR] to other users, they cannot use the softwares installed by user1.
As I do not have a large storage space, it is [COLOR=Red]not possible[/COLOR] to install the same software twice.:confused:

When I copy the .wine to somewhere else, it recreates a .wine inside my home folder.

Is there any way to make Wine create the .wine folder somewhere else (like /usr/.wine)?????

I'm new to Ubuntu and trying to switch totally to Ubuntu. So can anyone help me with this?????????[-o<

---

### Post by sanderd17 on 2010-12-16
you can use softlinks.

cut-paste the wine direcotry to lets say /usr/.wine, than execute
```

ln -s /usr/.wine /home/user1/.wine

```
A link will be created from .wine in the users home to /usr/.wine

I believe this should work.

---

### Post by indike on 2010-12-17
It seems to work.......
Thanks a lot :D

---

