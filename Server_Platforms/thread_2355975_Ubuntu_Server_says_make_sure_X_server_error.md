---
title: "Ubuntu Server says make sure X server error"
date: 2017-03-18
forum: Server Platforms
---

### Post by bededtotes on 2017-03-18
```
steam@UbuntuServer:~/Steam/steamapps/common/HellionDedicatedServer$ wineconsole Start_ALL.bat
err:winediag:nodrv_CreateWindow Application tried to create a window, but no driver could be loaded.
err:winediag:nodrv_CreateWindow Make sure that your X server is running and that $DISPLAY is set correctly.
steam@UbuntuServer:~/Steam/steamapps/common/HellionDedicatedServer$

```
```
steam@UbuntuServer:~/Steam/steamapps/common/HellionDedicatedServer$ xrandr --query
Can't open display :0
```
when trying to start a dedicated server it gives me an error as well as trying to do xrandr --query returns that, any ideas on how to fix it?

---

### Post by TheFu on 2017-03-19
Load X/Windows.  

That sorts defeats the "server" aspect. Unix servers often don't have a GPU, so a GUI is not desired.  If you want a GUI, you have to load it manually, which will impact overall system performance and system stability negatively.  GUIs are bloated.  On fast hardware not running heavy "server loads", this may not matter to you.

WINE will assume a GUI exists, since Windows always has a GUI.

---

