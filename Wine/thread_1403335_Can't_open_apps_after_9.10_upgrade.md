---
title: "Can't open apps after 9.10 upgrade"
date: 2010-02-10
forum: Wine
---

### Post by nikkkko on 2010-02-10
Hi,

I mostly use wine to run SketchUp, but since last night, after I upgraded from 9.04 to 9.10, it won't open.  I get a huge error list when running from the command line, much of which looks like this :

err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGMath.dll") not found
err:module:import_dll Library libIGMath.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGGfx.dll") not found
File '/home/nick/.local/share/applications/wine-extension-style.desktop' contains invalid MIME type 'STYLE' that is missing a slash
File '/home/nick/.local/share/applications/wine-extension-skpkmz.desktop' contains invalid MIME type 'SKPKMZ' that is missing a slash
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGGfx.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGGfx.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGGfx.dll") not found
err:module:import_dll Library libIGGfx.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGAttrs.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGUtils.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGMath.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGMath.dll") not found
err:module:import_dll Library libIGMath.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGUtils.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGUtils.dll") not found

Any help much appreciated.

Thanks

---

### Post by nikkkko on 2010-02-10
Well I re-installed SketchUp and now all is good. SU is much, much faster running under wine than running under windows under virtual box.  For what it's worth.

---

### Post by Grenage on 2010-02-10
**W**ine **i**s **n**ot an **e**mulater so you'll get near-native speeds (if it works).

---

### Post by nikkkko on 2010-02-10
I love it when it does.

---

