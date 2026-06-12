---
title: "How to replace native dll file?"
date: 2009-06-04
forum: Wine
---

### Post by golusweet on 2009-06-04
I have replaced built in COMCTL32.dll with native one in wine.

but It's still giving me error.

err:module:import_dll Library comctl32.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found

---

### Post by Dark Aspect on 2009-06-05
> **golusweet said:**
> I have replaced built in COMCTL32.dll with native one in wine.

but It's still giving me error.

err:module:import_dll Library comctl32.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found

Replacing a dll as native in winecfg **does not** actually add that library to your system32 folder. [Download shell32 here]("http://www.dll-files.com/dllindex/dll-files.shtml?shell32") and copy it to wine's system32 folder which is more than likely located here:

```
/home/{USERNAME}/.wine/drive_c/windows/system32
```

---

### Post by golusweet on 2009-06-05
I already did that, but still it isn't working.

---

### Post by Dark Aspect on 2009-06-05
> **golusweet said:**
> I already did that, but still it isn't working.

My bad its not shell32.dll its COMCTL32.dll, did you add it as native in winecfg? Plus, is the file name in the same letter case. I believe it is case sensitive.

---

### Post by golusweet on 2009-06-06
Yes, I did.

I think, This dll requires some additional  work.

---

### Post by NightMKoder on 2009-06-06
winetricks comctl32 installs it im pretty sure. Why do you need to do this? In most cases switching to native dlls is a bad idea.

---

