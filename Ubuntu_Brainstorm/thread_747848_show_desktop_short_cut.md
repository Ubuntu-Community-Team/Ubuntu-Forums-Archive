---
title: "show desktop short cut"
date: 2008-04-06
forum: Ubuntu Brainstorm
---

### Post by marine63 on 2008-04-06
the show desktop is something like ctrl +alt + d or something couldnt it be the button that that have windows logo on it?

---

### Post by xelapond on 2008-04-07
I think Compiz already has this feature built in.  Try Show Desktop or Hide Windows.  I don't know exactly what its called, I haven't used Compiz for awhile.

---

### Post by nhandler on 2008-04-07
I believe the Windows key is usually referred to as the "Super" key. I know you can make Super+D show the desktop (like in windows) using compiz. I also think you can use gconf-editor to setup that shortcut, but I'm not sure.

---

### Post by sebth on 2008-04-26
You will have to use gconf-editor. In the Keyboard Shortcuts GUI, you can't use the WinKey with other keys like you would do with ctrl or alt.

Start gconf-editor, then go to /apps/metacity/global_keybindings and set show_desktop to <Mod4>d .

---

### Post by nawitus on 2008-04-27
And if you want to create a graphical icon on the taskbar you can use this script:
```

#!/bin/bash
wmctrl -k on
wmctrl -a DesktopConsole
exit

```

---

### Post by damoxc on 2008-04-27
that requires wmctl to be installed.

could always just press the button on the left of the bottom panel in a default install... :)

---

### Post by spamzilla on 2008-04-27
There's already a "show desktop" icon on the default bottom panel :confused:

---

### Post by MacUntu on 2008-04-28
I didn't like that "blocky" icon so I've replaced it with such a script. ;)

---

