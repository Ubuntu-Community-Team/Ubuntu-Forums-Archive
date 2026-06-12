---
title: "R6034/Torchlight"
date: 2010-07-09
forum: Wine
---

### Post by vuroth on 2010-07-09
Running Wine 1.2-rc6.  Previously, I had been able to run Torchlight in wine, but I guess I broke something.  Now I get:

```

R6034
An Application has made an attempt to load the C runtime library incorrectly.  Please contact the application's support team for more information.
```

Running in the terminal gives me this:

```
$ wine Torchlight.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:attach_process_dlls "MSVCR90.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steam\\steamapps\\common\\torchlight\\Torchlight.exe" failed, status c0000142
me@me-laptop:~/.wine/drive_c/Program Files/Steam/steamapps/common/torchlight$ 
```

EDIT:

Decided to try to uninstall/reinstall vcrun2008, but reinstall fails.  Google seems to indicate that this is a common problem, but not finding a workaround that works.

ARGH

---

### Post by 1337 on 2010-07-10
Got the same problem tried copying/renaming/installing different lib sets with no use.

---

### Post by wirespot on 2010-11-18
Had the same problem, solved by completely deleting ~/.wine/ directory and reinstalling required libs (with winetricks) and then reinstalling Torchlight.

**WARNING: deleting ~/.wine/ will delete all the Wine stuff you have installed!** So it's not a solution unless you're willing to lose that.

---

