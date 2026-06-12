---
title: "Chromium Close/Minimize/Maximize Buttons on 'wrong' side"
date: 2012-10-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by DavidSommen on 2012-10-15
Since the update to quantal my close/minimize/maximize buttons are on the right side on chromium. All other applications have their buttons on the left side.

running
```

gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

```
does not seem to make a difference.

Is this a chromium bug?

---

### Post by oseb on 2012-10-15
check "Use System Title Bar and Borders" menu on the chromium title bar 
or Settings -> Appearance -> check use system title bar and borders.

---

### Post by DavidSommen on 2012-10-15
Thanks. That solved it.

---

