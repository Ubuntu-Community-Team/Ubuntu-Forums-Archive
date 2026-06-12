---
title: "looking for game creator software"
date: 2009-04-03
forum: Wine
---

### Post by phillip1882 on 2009-04-03
i would like to try my hand at making a few ubuntu games, but i can't seem to find a good editor, as most require windows. the only one i could find doesnt seem to be working, [http://game-editor.com/download.html](http://game-editor.com/download.html). when i try to run it form command line, get the following error, "error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory".
thanks for any help.

---

### Post by Meow27 on 2009-04-03
did you try using blender? from what i understand, it might be what you want to use

[http://www.blender.org/](http://www.blender.org/)

---

### Post by aninaiian on 2009-04-03
I think you don't have libstdc++5 installed.

So, just
```
sudo apt-get install libstdc++5
```

Hope that helps.

---

