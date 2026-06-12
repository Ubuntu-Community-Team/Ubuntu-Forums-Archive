---
title: "Gta3"
date: 2009-02-11
forum: Wine
---

### Post by amits on 2009-02-11
How can I install and play Gta3  on Ubuntu 8.10? Please help?

---

### Post by hikaricore on 2009-02-11
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=936](http://appdb.winehq.org/objectManager.php?sClass=application&iId=936)

---

### Post by amits on 2009-02-11
Can someone explain it to me? I am new to Ubuntu

---

### Post by cogadh on 2009-02-11
Perhaps you should spend some time reading about Wine and how to use it here:
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by rocky5051 on 2009-02-11
Once you understand how to use Wine, you might like to know downloading, patching and compiling the wine source code for that mouse hack they tell about for GTA III's appDB listing isn't really necessary. Instead you can enable the MouseWarpOverride function in Wine's registry.

Open a terminal, and type:

```
regedit
```

Then when the registry editor opens navigate to:

HKEY_CURRENT_USER\Software\Wine\DirectInput

When you get there add this string:

```
MouseWarpOverride
```

Then right click the string you just added, choose to add a value and type in:

```
force
```

This will force the mouse to warp so the mouse doesn't hit the edge of the screen while you play. But, it will make the pointer stay in the middle of the screen so you'll need to use the keyboard to navigate menus. If you want to look at other registry tweaks you can find them here.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

