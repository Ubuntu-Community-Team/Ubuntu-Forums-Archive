---
title: "Wine Virtual Desktop and the Taskbar Icon"
date: 2010-07-24
forum: Wine
---

### Post by t.rei on 2010-07-24
Hi there.

Maybe someone here can help me with this little smoothness issue, that I have not found a way around.

I am currently running games on wine just perfectly. There is just one issue, one tiny, non-game-breaking one:

I have more than one screen, so in order for many applications to detect the proper resolution, I need to run them like this:
```

wine explorer /desktop=0,1920x1200 "/home/myuser/.wine/drive_c/Programme/someapp/someprog.exe" -opengl

```
Now there is only the rather ugly and not-quite-correct 'desktopish like' icon in the taskbar.

If I run it like this:
```

wine "/home/myuser/.wine/drive_c/Programme/someapp/someprog.exe" -opengl

```
The apps correct icon shows in the taskbar.

Is there any way to combine this: have the virtual desktop setting AND the proper icon?

Thanks

---

