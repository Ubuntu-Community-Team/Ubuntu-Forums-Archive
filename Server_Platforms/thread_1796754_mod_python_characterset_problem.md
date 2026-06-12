---
title: "mod_python characterset problem"
date: 2011-07-04
forum: Server Platforms
---

### Post by pnmoslo on 2011-07-04
Following system upgrade from 10.10 (Python2.6) to 11.04 (Python2.7) a mod_python application has begun sending utf8 to the browser. Using only repository versions of the software.

As far as i can establish the entire application behind mod_python still works (also with the "new" Python2.7) with only 8859-1 strings, which was what was being passed to the browser before the upgrade. 

My assumption is that something has changed in the mod_python compiled against Python2.7.

Has anyone else experienced this? Any ideas about how to fix it (apart form converting the whole ancient application to unicode-compatible)?

---

