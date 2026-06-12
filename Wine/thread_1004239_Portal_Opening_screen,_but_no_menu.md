---
title: "Portal: Opening screen, but no menu"
date: 2008-12-07
forum: Wine
---

### Post by LordPi on 2008-12-07
So I installed steam fine, and it seems to work, and running portal show the valve logo fullscreen, but when the menu should come up, it's just a black screen. Complete with main menu type music. Can't get out of it. Checking the command line after yields a full buffer of stuff along the lines of:
```
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x185dd0)->(0x32c6c8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x185dd0)->(0x32c6c8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x185dd0)->(0x32c6c8)
```

Please help.

---

### Post by Ameneon on 2008-12-07
Disable compiz, run with dxlevel 81 or 80, also makes a world of difference in how well the game runs. If you run it through Steam first, you can set launch options for the game there; -dxlevel 81

---

### Post by LordPi on 2008-12-07
So.. I disabled compiz, as you said, and played with dxlevel.  dxlevel 70 lets it try to start, getting to the menu screen, but it immediately whines about not having shader support and quits. dxlevel 80 and 81 give same behavior as before.

---

