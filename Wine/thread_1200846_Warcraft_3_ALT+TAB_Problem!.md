---
title: "Warcraft 3 ALT+TAB Problem!"
date: 2009-06-30
forum: Wine
---

### Post by keylog on 2009-06-30
Hi, everyone;

i'm trying to play DoTA ubuntu 9.04 with wine 1.1.24.
It's working without a problem. But i want to connect to battle.net. I can connect battle.net but there is problem about ping and/or delay. So i wan't to use delay reducer. But when i use alt+tab to switch delay reducer, it's graphics'll be crashed. (when i came back). compiz is already closed.

sorry for my pretty good english =)

---

### Post by beastrace91 on 2009-07-02
You could try one of a couple things. First you could try toggling off compiz while running your game (the application fusion-icon from the repositories is good for this).Another option is running WC3 in a virtual desktop so that what it is if effect a Windowed application and it does not have to fully alt-tab. And third idea (and I use this for my full screen games) is to run it on a separate X server so you can change between Xes by using ctrl+alt+f7-9. Information on setting up the extra X server can be found in full circle #25 - [http://fullcirclemagazine.org/2009/05/29/fcm-issue-25-coming-your-way/](http://fullcirclemagazine.org/2009/05/29/fcm-issue-25-coming-your-way/)

Hopes this helps some,
~Jeff

---

### Post by keylog on 2009-07-02
thx for your help i guess your third suggestion will help me..

---

### Post by keylog on 2009-07-02
i tried it but nothing happens on anyother x  :S
that is my bash file

```
#!/bin/bash
X :4 -ac -terminate -config only_one_monitor.conf & sleep 2
DISPLAY=:4 nice -20 env
WINEPREFIX="/home/keylog/.wine" 
wine "/media/DATA/Oyunlar/WarcraftIII/w3l.exe"
```

---

### Post by beastrace91 on 2009-07-02
Your last three lines should all be one, like the following: ```
#!/bin/bash
X :4 -ac -terminate -config only_one_monitor.conf & sleep 2
DISPLAY=:4 nice -20 env WINEPREFIX="/home/keylog/.wine" wine "/media/DATA/Oyunlar/WarcraftIII/w3l.exe"
```

Also be sure you edited the proper file so anyone can create X servers (not just console)

~Jeff

---

### Post by keylog on 2009-07-02
i change it and checked ctrl+alt+f7-11 but all of the Xes are black screen but some of them has a _(blinking) but some of only black screen...

---

### Post by keylog on 2009-07-03
is there anyone knows anything about it?

---

### Post by beastrace91 on 2009-07-03
> **beastrace91 said:**
> 
Also be sure you edited the proper file so anyone can create X servers (not just console)

Did you do this? If not it will prevent it from working.

~Jeff

---

### Post by keylog on 2009-07-06
> **beastrace91 said:**
> Did you do this? If not it will prevent it from working.

~Jeff

i did this at first...

---

### Post by elitenoobboy on 2009-07-06
For me, it was easier to just keep war3 confined to a virtual desktop, as another desktop session can be cumbersome.
[http://ubuntuforums.org/showthread.php?t=906957](http://ubuntuforums.org/showthread.php?t=906957)
Works just as well as the normal fullscreen configuration, plus you can multitask with multiple desktops.

---

