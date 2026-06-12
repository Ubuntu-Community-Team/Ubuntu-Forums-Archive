---
title: "Cannot run any wine programs"
date: 2010-03-17
forum: Wine
---

### Post by Lockheed on 2010-03-17
I manually copied my home folder from another disk, using root user, which was a mistake because it screwed file ownership. Anyway, I managed to restore most of it back to the proper values, but still none of wine programs work
Here is what's happening:
```
$ env WINEPREFIX="/home/juha/wine-bottles/utorrent/" wine "C:\Program Files\uTorrent\uTorrent.exe"
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
Warning: could not find DOS drive for current working directory '/home/juha', starting in the Windows directory.
wine: cannot find 'C:\Program Files\uTorrent\uTorrent.exe'

```

---

### Post by donkyhotay on 2010-03-17
Your paths are completely messed up, if you look at the error messages wine can't find/create key files and folders. This is probably because of the copying you were doing. Try reinstalling the windows programs you are trying to use. If that doesn't work I would delete your .wine directory and reinstall all your windows programs. Be aware deleting the .wine directory will wipe out all windows programs within wine.

---

