---
title: "I can't see text with ubuntu 11.10 32 bits"
date: 2012-01-13
forum: Ubuntu Christian Edition
---

### Post by partos on 2012-01-13
I am using the e-sword installer and the script works fine, but when I run e-sword I can not see the text, the whole windows are blank (white). The search only works with REGEX and, for example, when I am looking for faith (REGEX EXPRESSION= ( faith )) the search windows reports 126 verses found, 126 matches, but there are not versicles to read

---

### Post by dshimer on 2012-01-18
I have had the exact same problem on all 3 of my 11.10 boxes when installing E-Sword using the installer found in the forum.  To fix it I have
Run the follwing in a terminal
```
env WINEPREFIX=~/.wine_Esword winecfg
```
Then in the winecfg program I set the following libraries
oleaut32 (builtin)
riched20 (builtin)

Note that in my install they default to (native,builtin) but after changing them and restarting everything works fine.

---

### Post by angelsguitar on 2012-06-16
> **dshimer said:**
> I have had the exact same problem on all 3 of my 11.10 boxes when installing E-Sword using the installer found in the forum.  To fix it I have
Run the follwing in a terminal
```
env WINEPREFIX=~/.wine_Esword winecfg
```
Then in the winecfg program I set the following libraries
oleaut32 (builtin)
riched20 (builtin)

Note that in my install they default to (native,builtin) but after changing them and restarting everything works fine.

Thank you very much.  I was having this same issue and these instructions solved it.

---

