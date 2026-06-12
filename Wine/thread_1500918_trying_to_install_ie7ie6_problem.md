---
title: "trying to install ie7/ie6 problem"
date: 2010-06-03
forum: Wine
---

### Post by Experimental on 2010-06-03
```
sh winetricks
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\cmd.exe" failed, status c0000005
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------

```

At first attempt of installation it downloaded ie and aborted at installing part. When I tried it later it says that. What can I do

---

### Post by asdfoo on 2010-06-03
> **Experimental said:**
> ```
sh winetricks
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\cmd.exe" failed, status c0000005
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------

```

At first attempt of installation it downloaded ie and aborted at installing part. When I tried it later it says that. What can I do


remove or move your wineprefix, update to wine-1.2rc2 and retry.

---

