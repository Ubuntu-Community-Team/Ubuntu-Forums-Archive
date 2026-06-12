---
title: "Make program run fullscreen, launched from another user? KodiBuntu"
date: 2015-04-02
forum: Ubuntu/Debian BASED
---

### Post by pettergulbra on 2015-04-02
Hi

I have installed Kodibuntu on my Chromebox. This is build on Lubuntu as far as I know.

I have installed the Chrome Launcher and Chrome Stable. 
Inside Kodi, it will launch Chrome, but just on half the screen, so I can`t see the whole picture.

There are an option too run an script while the launcher is starting, and this script I have made run able, with chmod command.
The script is as follows:
```
[COLOR=#000000][FONT=monospace]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]blackbox &[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/usr/bin/google-chrome-stable "$@"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]killall blackbox[/FONT][/COLOR]
```

When this is run, it does not show at all.

I have updated the kernel to 3.18 also.

I`m not Linux/Ubuntu guy, so this is absolutly not my normal area.

Hope for some help, if it is possible to make this work at all?

kindly

Petter

---

### Post by howefield on 2015-04-02
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by pettergulbra on 2015-04-03
No one that can help me?

If more info is needed, please let me know. So I can try to find the info you will need.

Thanks in advanced.

---

### Post by bpiel on 2015-05-26
Did you ever solve this? I'm having the same problem.

---

### Post by pettergulbra on 2015-05-26
I'm not really sure it's working the way it should. But it is better. Read this forum:[http://forum.kodi.tv/showthread.php?tid=170965&pid=2004810#pid2004810](http://forum.kodi.tv/showthread.php?tid=170965&pid=2004810#pid2004810)

---

