---
title: "Sketchup on 8.04"
date: 2009-02-19
forum: Wine
---

### Post by dmikulec on 2009-02-19
I'm having problems getting Sketchup7 to run on Ubuntu 8.03/Wine 1.0.3. I have an Nvidia GeForce 6200.  I've recently Wine and tried to upgrade the Nvidia drivers using Envy but it trashed the config pretty badly. Now when I try to launch SU I get the following:

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\gdal12.dll") not found
.
.
.

Any thoughts on where this code should be and how it can be loaded?

Thanks,

Don

---

### Post by cogadh on 2009-02-19
Sketchup doesn't work with any Wine version less than 1.1.12 and it does not work all that well with 1.1.12 or higher anyway:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14562](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14562)

If you want to pursue this, the first thing I would do is upgrade to a newer version of Wine.

---

### Post by lha on 2009-02-19
I got Sketchup6 working with Wine 1.0.0, but I would suggest you to upgrade to latest Wine: [http://winehq.org/download/deb]("http://winehq.org/download/deb"). 

Sketchup7 does work with Wine also (atleast for some people, including me). The Wine wiki has some instruction concerning Sketchup: [http://wiki.winehq.org/GoogleSketchup]("http://wiki.winehq.org/GoogleSketchup"). It does not, however, have a solution to the problem you are having now. Hopefully, new version of Wine does the trick. If upgrading doesn't help, you'll probably have to find the missing dll file somewhere.

---

