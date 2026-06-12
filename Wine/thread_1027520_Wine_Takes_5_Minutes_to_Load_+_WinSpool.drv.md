---
title: "Wine Takes 5 Minutes to Load + WinSpool.drv"
date: 2009-01-01
forum: Wine
---

### Post by RATM_Owns on 2009-01-01
Not sure what much to say.
I start something, takes way too long, Control+C it, and get this:
```
^Cerr:module:attach_process_dlls "winspool.drv" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\is-OFIKI.tmp\\Setup_WADder_1.2.tmp" failed, status c000013a
```

If I let it wait, it tells me something about __init_wine_kernel timing out.

---

### Post by FarJumper on 2009-01-01
Check if the cups is installed on your machine. It's weird, but wine supposes that cups ALWAYS have to be installed... This was an issue in my case.

---

### Post by RATM_Owns on 2009-01-01
Pacman said I already had cups installed.
So I reinstalled it.

Same thing.

---

### Post by illepic on 2009-02-28
I'm getting something very similar: 

```
err:process:__wine_kernel_init boot event wait timed out
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
```

Takes about a minute for any wine app to launch.

---

### Post by Aq32 on 2009-11-27
Same problem on here too wine-1.1.31 Ubuntu Karmic. Terminating from executing in terminal shows that it's something to do with winspool.

---

