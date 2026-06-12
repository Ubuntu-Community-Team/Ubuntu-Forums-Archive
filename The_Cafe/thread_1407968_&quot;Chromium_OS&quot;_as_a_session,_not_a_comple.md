---
title: "&quot;Chromium OS&quot; as a session, not a complete OS"
date: 2010-02-15
forum: The Cafe
---

### Post by Aphoxema on 2010-02-15
Has anyone made any efforts into setting up Chromium OS as a drop-in desktop environment? I'm pretty impressed with what I've seen so far but what it takes away isn't worth what it offers. It's also a little painful that everything works just fine except for wireless and Chromium OS in no way makes it easy to actually administer the system.

I'm just interested in the browser-as-a-desktop attitude, but not to the point it eliminates the useful-tools-with-your-desktop.

---

### Post by markp1989 on 2010-02-15
that sounds like a nice idea , should be simple enough , run chromium form xinit rc without a window manager. i have tried , right now the browser isnt using up all the screen. but there is no reason why it cannot be done..

edit: i have goten a minimal wm, ratpoison + chromium on startup 

dont know how they added the battery meter to chrome or  what other parts of chrome os there are?

im just gona throw together a vm to see what i can try :)

---

### Post by Aphoxema on 2010-02-15
I'm looking forward to any progress you make.

---

### Post by Warpnow on 2010-02-15
If you create a gdm session with chrome being called instead of the WM it will just full screen chrome when you login that way.

---

### Post by markp1989 on 2010-02-15
> **Warpnow said:**
> If you create a gdm session with chrome being called instead of the WM it will just full screen chrome when you login that way.

I have tried running chrome from .xinitrc . and it wouldnt run full screen without a window manager.

edit: added a custom session to run google chrome and ratpoison  (both need to be installed) 

i add the following lines to this file /usr/share/xsessions/Chrome.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=google chrome
Comment=
Exec=~/.google.chrome
Icon=
Type=Application
```


and add the following to this file ~/.google.chrome 
```

#!/bin/sh
ratpoison &
exec chromium-browser
```

make sure you can execute .google.chrome file by running 

chmod a+x ~/.google.chrome 

when you login , under session select google chrome

if you quit chrome it will log you out

---

### Post by Aphoxema on 2010-02-16
Seems simple enough. "Chromium OS" launches a number a web-apps through the browser itself.

I'm starting to wonder if Firefox would be better for this. Is there a plugin that can spawn processes for Firefox, perhaps inside a tab?

---

