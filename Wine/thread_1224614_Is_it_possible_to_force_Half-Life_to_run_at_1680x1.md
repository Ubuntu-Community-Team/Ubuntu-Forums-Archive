---
title: "Is it possible to force Half-Life to run at 1680x1050?"
date: 2009-07-27
forum: Wine
---

### Post by s3a on 2009-07-27
Is it possible to force Half-Life (1) to run at 1680x1050? It is not one of the supported video modes. In fact, it is a larger resolution than the maximum supported resolution however a friend once told me that he forces games to a higher resolution. He uses Windows but I still think that what could be done with Windows could be done with Wine.

I would love to not only play the game at a higher resolution but to also not have to keep re-setting my resolution to 1680x1050 each time I exit the game.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by PureLoneWolf on 2009-07-27
I am not sure if this will work, as you say the res isn't supported - but if you goto the game list in Steam, right-click the game and choose Properties.  Then on the General tab, press the "Set Launch Options" button and specify:

```
-width 1680 -height 1050
```

See if that helps

---

