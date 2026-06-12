---
title: "Having touble with fallout 3+wine"
date: 2009-05-26
forum: Wine
---

### Post by Dark Aspect on 2009-05-26
I have installed xlive and all that crap, replaced all the dll libraries that were needed but from some reason I am still getting:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:attach_process_dlls "MSVCR90.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\Fallout3.exe" failed, status c0000142
```

I am confused because I already have msvcr90.dll in my system32 directory. Why did it fail, does msvcr90.dll require another dll? and if so how can I find out what dlls are required from a single dll?

---

### Post by Dark Aspect on 2009-05-26
EDIT: I am idiot, run vcredist_x86.exe on the fallout DVD and it will fix any msvcr90 errors. However, sadly the game is largely broken. Characters have no heads and crashes are very common; FPS seemed rather high though even in V.A.T.S. I do hope wine adds more support for this title.

---

