---
title: "WoW login help?"
date: 2010-09-28
forum: Wine
---

### Post by terencek93 on 2010-09-28
okay so i have wow installed and it starts up fine and then the login screen is supposed to come up. but doesn't. the dragon just keeps flying around growling. instead it is just a black box in the login spot. anyone know the issue here?

---

### Post by lazymangaka on 2010-09-29
Alot of the problems I've experienced when running WoW under Ubuntu with Wine have involved just what you're describing there: A black something or other where something else is supposed to be. I've found that I can fix most of these problems by doing one of two things.
 
First, by adding this line to your Config.wtf file:
 
```
 
SET gxApi "opengl"

```
 
Or, second, by installing the Direct X options under Winetricks:
 
```
sh winetricks d3dx9
```
 
Both of those have solved virtually any problem I've had on both laptops that I have running Ubuntu and WoW. Hopefully one of them will work for you.

---

