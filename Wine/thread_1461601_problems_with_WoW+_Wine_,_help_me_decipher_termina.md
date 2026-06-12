---
title: "problems with WoW+ Wine , help me decipher terminal output please."
date: 2010-04-24
forum: Wine
---

### Post by Darzak on 2010-04-24
Hi, im really new to Ubuntu and linux. Tried to install WoW and that went fine , updating and the launcher worked "perfectly" but the game only showed a black screen but I could hear the intro music. I later updated the drivers and now WoW wont even start ,tried to open it using the terminal and got this

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  159
  Current serial number in output stream:  159

```


I got wine 1.1.43 and WoW is up-to-date.
using windows xp as OS in wine
added the opengl to config file
added the disabled extensions registry file
.
Thanks for reading this ^^'


sry if this is in the wrong section, I just found out about the Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions > Gaming & Leisure  , sorry.

---

### Post by mooreted on 2010-04-25
What video card do you have? Did you install the latest drivers for your video card?

Open a terminal and enter:

glxinfo

Does it show direct rendering enabled?

More info:

[http://www.wowwiki.com/Wine_troubleshooting](http://www.wowwiki.com/Wine_troubleshooting)

---

