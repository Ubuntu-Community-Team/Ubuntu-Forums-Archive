---
title: "Wine Virus Help"
date: 2010-05-23
forum: Wine
---

### Post by 0akash0 on 2010-05-23
Dear All;

I recently executed New Folder.exe virus through wine, now it hides my shutdown button and all bars when I try to shutdown and causes other problems.

When I uninstall wine through Add/Remove everything works fine but, when I re-install it, all the problems resurrect. This virus seems to have added itself in startup as well.

Please Help,

I am using 8.04 LTS.

---

### Post by Elfy on 2010-05-23
uninstall wine then open a terminal (Apps > Accessories > Terminal), run this to remove the .wine configs 

```
rm -r .wine
```

---

### Post by 0akash0 on 2010-05-23
Thank You Very Much!

---

### Post by hikaricore on 2010-05-23
Sounds more like malware than a virus imho.
Actual viruses are quite rare these days.

In the future when messing with untrusted software I suggest using a wine prefix.
This will limit the program in question to a separate wine configuration and avoid affecting your main .wine directory.

> env WINEPREFIX="~/.wine-garbage" programname.exe

---

### Post by ronnielsen1 on 2010-05-23
Just a tad bit easier to remove in wine than in windows

---

