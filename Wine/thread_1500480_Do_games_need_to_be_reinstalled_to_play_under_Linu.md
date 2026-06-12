---
title: "Do games need to be reinstalled to play under Linux?"
date: 2010-06-03
forum: Wine
---

### Post by Effect on 2010-06-03
If a game is already installed on a hard drive in a system, but it was done under windows, does this mean it has to be reinstalled via under Ubuntu or any other Linux OS to run via Wine or Cedega?

I usually install games to a different partition just so that Windows and some general programs were on it's own hard drive or even partition.

Thanks.

---

### Post by KrisInfinity on 2010-06-03
It depends on the game... Some games install required information in the windows registry so when using wine the game may not work if it depends on that information.

Just try and see

---

### Post by nashod on 2010-06-03
some games may cause problems that way but all in all yes u can activate a game u installed on windows that's how i ran tf2 using wine before i moved to ubuntu completely

---

### Post by cogadh on 2010-06-03
It is usually safest to just install the game in Wine and not try to run it off a Windows partition. Wine is not really designed to interact with an existing Windows installation and many, if not most, applications will not work properly via that method.

---

### Post by YokoZar on 2010-06-04
It's the same as taking a hard disk from one Windows machine to another.  Sometimes the application works, sometimes it doesn't.

The reason has to do with registry entries - by not reinstalling, you're not getting them.  Some applications require them, some don't really care.

---

